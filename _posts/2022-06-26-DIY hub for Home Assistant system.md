---
title: DIY hub for Home Assistant system.
date: 2022-06-26 14:57:10  
categories: [Projects(En), IoT(En)]
tags: [3D printing, 3D modeling, Iot, HA, Home Assistant, Nest Hub, Google home]
---
Although I established Google home voice control with Home assistant, I realized the need of intuitive touch control system.<br>
The Nest Hub was Ideal, but my wallet is so empty that I should DIY.<br>
This is the story about making HA Hub with an old smartphone and 3D printing.<br>

<h3>Required materials</h3>
 - An old smart phone in your drawer<br>
 - An old PLA filament(only for me)<br>
 - A little bit of 3D modling ability<br>
 - Already established HA server<br>
 - A phone charger with broken connector<br>
 

<h4>STEP1. Modification of Smartphone</h4>
1. Install newer OS in your phone(Optional)<br>
In my case, the target of this modification was Vega No'6, which has android 4.4.2, So I need to update the version up to 7 to install the HA app.(Of course, you can operate with the web, but it's not cool.)<br>
<img src="/assets/img/VN6/VN6_2.jpg" width="200"><img src="/assets/img/VN6/VN6_11.jpg" width="200"><br>
The detailed updating process will be written in another post<br>
2. Permanent power input modification.(Optional)(For battery-detachable phones.)<br>
As I wrote before, my phone was old, so I decided to remove battery to prevent swelling and other bad events.(Also possible just connect your charger always without these step.)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. Detach the battery, remove the Cell and just take BMS<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. Cut the old charger's broken connector and solder to bms beware with the electrical polarity<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3. Fill the empty remaining space of cell to BMS got original position.<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="/assets/img/HA_HUB/HA_HUB_2.jpg" width="200"><img src="/assets/img/HA_HUB/HA_HUB_1.jpg" width="200"><br>
3. Install HA app.<br>


<h4>STEP2. Design your custom hub frame</h4>
1. Model your phone to design the angle roughly.<br>
2. Tried to design the model similar to the other hubs, hide the frame, expose only LCD, and set the angle about 45 degrees to control easily.<br>
**☆NOTE:** Take note that you need to make space for the power and volume switch not to be pressed. Otherwise, you can see the phone turns off periodically without a specific reason. And send meaningless time just suspecting the innocent charger and soldered spot. In addition, your precious printed frame will go to the garbage can.<br>
<img src="/assets/img/HA_HUB/HA_HUB_5.jpg" width="200"><img src="/assets/img/HA_HUB/HA_HUB_6.jpg" width="200"><br>

<h4>STEP3. The end</h4>
1. Join the phone and frame you made, the DIY hub project is over.<br>
<img src="/assets/img/HA_HUB/HA_HUB_7.jpg" width="300"><br>
2. Go to your HA server and make a new dashboard and customized layout.<br>
3. Congratulations! Now you can have your own hub with customized design.<br>
<img src="/assets/img/HA_HUB/HA_HUB_10.jpg" width="300"><br>


☆Question: To achieve the same goal, why don't we just put the phone on a wireless charging stand?<br>
☆Answer: That's right. But isn't ours more cool? A little sense of accomplishment is a bonus. :D


