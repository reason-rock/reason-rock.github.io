---
title: Simple tutorial for Intel RealsenseID F455/F450
date: 2022-07-10 13:34:11 +9:00	
categories: [Projects(En), RealsenseID(En)]
tags: [Intel Realsense, RSID, F450, F455, Face authentication, authentication, Face recognition]
---
It seemed that the general 'Intel realsense SDK' is not compatible with RealSenseID(after this, referred to as RSID)<br>
So we need to use RSID SDK from [https://github.com/IntelRealSense/RealSenseID](https://github.com/IntelRealSense/RealSenseID)

<h4>Step 1.</h4>
Clone the package.
```
git clone https://github.com/IntelRealSense/RealSenseID.git
```

<h4>Step 2.</h4>
Move to folder
```
cd RealSenseID
```

<h4>Step 3.</h4>
Make build dir
```
mkdir build && cd build
```

<h4>Step 4.</h4>
Cmake with preview option
```
cmake .. -DRSID_PREVIEW=1
```

<h4>Step 5.</h4>
Make
```
make -j16
```

<h4>Step 6.</h4>
We can operate RSID
```
cd RealSenseID/build/bin
./rsid-cli /dev/ttyACM0
```

<h4>Wanna use GUI?</h4>
Move to samples folder and run viewer.py
```
cd RealsenseID/samples/python
python3 viewer.py
```


<h3>Note</h3>
 1. **Be careful when you use the Secured option. It remains on the RSID device and cannot work with other pc. Make sure that you disable the Secured option before unplugging.**

<h3>Trouble Shooting</h3>
 1. $ [PacketSender] Got invalid crc. Expected: 561. Actual: 20100 error : Need to give permission to access to sub -> run ```sudo chmod 666 /dev/ttyACM0```
 2. 'can't open device "/dev/ttyACM0": Device or resource busy' -> ```sudo usermod -a -G dialout USERNAME```
 3. $ "Firmware cannot be updated directly to the chosen version.
Flash firmware version 3.1.#.# first. Firmware cannot be updated directly to the chosen version.
Flash firmware version 3.1.#.# first." -> We cannot update the RSID firmware 2.x to 4.x directly, so we need to update 2.x -> 3.1.x -> 4.x
 4. The SKU version of the Firmware: There are two variations in the same version. SKU1 and 2. -> We need to Check the serial number. If our RSID's serial number consisted with:
	120X6228XXXXXXXXXXXXXXXX-X	XX
	122X6228XXXXXXXXXXXXXXXX-XXX
	XXXX6229XXXXXXXXXXXXXXXX-XXX
	We need to use SKU2 version. I was the first case.
 5. If you use OpenCV with RSID, the camera number may be -1
 6. Cannot find rsid.so : check build/lib folder


