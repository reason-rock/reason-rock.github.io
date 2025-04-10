---
title: RSID와 OpenCV 활용 출입감지시스템
date: 2022-08-14 12:34:01 +9:00
categories: [Projects, RealsenseID]
tags: [리얼센스, 인텔, 인텔 리얼센스, 얼굴인식, Intel Realsense, RSID, F450, F455, Face authentication, authentication, Face recognition]
---


<h1>RealSenseID 활용 출입관리시스템</h1>
우연찮게 RealSenseID(이하 RSID)를 접할 기회가 있어 이를 활용한 출입관리시스템을 만들어 보았다.<br>
코딩이라고는 파이썬 조금밖에 모르는 코린이인지라, 코드가 몹시 비효율적일 수 있으니 단순히 작동방식에 대한 참고용도로만 사용하시길 바란다.

<img src="/assets/img/FID/demo.gif"alt="RSID demo">

<h3>준비물</h3>
 - 젯슨나노<br>
 - Intel RealSenseID<br>
 - 리눅스 개발환경<br>
 - RSID SDK<br>
 - Open CV(선택사항)<br>
 - 약간의 파이썬 지식
 

<h4>STEP1. 기본 환경 구축</h4>
1. RSID 펌업 및 연결<br>
아래 글을 참고하여 펌업과 연결을 진행한다.<br>
[# 인텔 RealsenseID F455/F450 첫걸음](https://reason-rock.github.io/posts/%EC%9D%B8%ED%85%94-RealsenseID-F455,F450-%EC%B2%AB%EA%B1%B8%EC%9D%8C/)<br>
2. RSID 샘플 코드 분석<br>
RealSenseID/Samples/python 폴더의 예제코드를 참조

<h4>STEP2. 얼굴 탐지 코드 작성</h4>
해당 코드는 얼굴 탐지(OpenCV)->사용자 인증(RSID)->문 개방(PWM)의 구조로 이루어져 있기에, 첫번째 단계는 OpenCV를 활용하여 얼굴이 있는지 감지하여야 한다.

```
import numpy as np

import cv2

xml = 'haarcascade_frontface.xml'

face_cascade = cv2.CascadeClassifier(xml) #사전학습데이터 불러오기

cap = cv2.VideoCapture(-1) #카메라 번호(바뀔 수 있음)

ret, frame = cap.read()

cap.set(3,640)

cap.set(4,480)

facelen = 0

facedelay = 0

while(True):

ret, frame = cap.read() #카메라에서 프레임 읽어오기

frame = cv2.flip(frame, 1) #카메라에서 읽어온 프레임 좌우반전

frame = cv2.rotate(frame, cv2.ROTATE_90_CLOCKWISE) #카메라에서 읽어온 프레임 회전해서 표시

gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY) #cvt color 함수로 gray로 추출

faces = face_cascade.detectMultiScale(gray, 1.05, 5) #학습데이터 기반 얼굴 검출(프레임, 스케일팩터, 선두께 지정)

facelen = str(len(faces))

facelenint=int(facelen)

print("Number of faces detected: " + facelen)

if len(faces):

for (x,y,w,h) in faces:

cv2.rectangle(frame,(x,y),(x+w,y+h),(255,0,0), 5)

cv2.imshow('FACEID', frame)#카메라 영상 프레임으로 새창 열어 표시

if facelenint != 0:

facedelay += 1

print('delay')

print(facedelay)

else:

facedelay = 0

if facedelay == 10:

exec(open("RSID_Authenticate.py").read())

facedelay = 0

k = cv2.waitKey(30) & 0xff

if k == 27: # Esc 키를 누르면 종료

break

cap.release()

cv2.destroyAllWindows()
```

<h4>STEP3.  사용자 식별</h4>
OpenCV를 통해 얼굴의 존재를 확인한 후, 신원확인을 요하는 얼굴이 있을 경우, RSID를 통해 식별한다.

```
"""

License: Apache 2.0. See LICENSE file in root directory.

Copyright(c) 2020-2021 Intel Corporation. All Rights Reserved.

"""

import rsid_py

import time

import Jetson.GPIO as GPIO

SERVO_PIN = 33

GPIO.setwarnings(False)

GPIO.setmode(GPIO.BOARD)

GPIO.setup(SERVO_PIN, GPIO.OUT)

pwm = GPIO.PWM(SERVO_PIN, 50)

pwm.start((1./18.)*90+2)

PORT='/dev/ttyACM0'

def on_result(result, user_id):

print('on_result', result)

if result == rsid_py.AuthenticateStatus.Success:

print('Authenticated user:', user_id)

exec(open("RSID_Unlock.py").read())

print('unlocked')

def on_faces(faces, timestamp):

print(f'detected {len(faces)} face(s)')

for f in faces:

print(f'\tface {f.x},{f.y} {f.w}x{f.h}')

if __name__ == '__main__':

with rsid_py.FaceAuthenticator(PORT) as f:

f.authenticate(on_faces=on_faces, on_result=on_result)
```


<h4>STEP4.  문 개폐</h4>
젯슨 GPIO 핀을 통해 서보모터로 PWM 신호를 주어 문을 개폐한다.

```
import Jetson.GPIO as GPIO

import time

SERVO_PIN = 33

GPIO.setwarnings(False)

GPIO.setmode(GPIO.BOARD)

GPIO.setup(SERVO_PIN, GPIO.OUT)

pwm = GPIO.PWM(SERVO_PIN, 50)

pwm.start((1./18.)*90+2)

for i in range(0, 20):

pwm.ChangeDutyCycle((1./18.)*100+2)

time.sleep(0.02)

pwm.ChangeDutyCycle(3.0)

time.sleep(1.0)

pwm.ChangeDutyCycle(0.0)

pwm.stop()

GPIO.cleanup()
```
