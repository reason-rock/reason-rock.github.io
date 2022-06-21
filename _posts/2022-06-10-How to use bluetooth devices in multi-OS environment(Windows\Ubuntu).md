<h1>Step 1. </h1>
 Pair your bluetooth devices in linux OS <br/>
 This will make the connection file named 'info' <br/>
 You can see this file in admin:///var/lib/bluetooth/"your computer BT MAC"/"your BT Devcie MAC" <br/>
 <img src="/assets/img/BT_linuxdir.png">
 Then, everything you have to do on Linux is done.
 Let's move to Windows

<h1>Step 2.</h1>
Pair your bluetooth device in Windows OS <br/>
This will make the connection data in regedit <br/>
Open the pstools with CMD administrator "psexec.exe -s -i regedit.jpg"<br/>
 You can see the regedit <br/>
 Move to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTHPORT\Parameters\keys\"your computer BT MAC"/"your BT Devcie MAC" 
<img src="/assets/img/BT_regedit.jpg">
 Take ScreenCapture of the page (Make sure Not just export it!)
 Then, everything you have to do on Windows is done. <br/>
 Lets move to linux again

<h1>Step 3.</h1>
move to admin:///var/lib/bluetooth/"your computer BT MAC"/"your BT Devcie MAC" <br/>
Open 'info' and replace value to window's one
Each of the following is Linux name -> Windows value
1. LongTermKey -> LTK value (Change the value with Capital)
2. IdentityResolvingKey -> IRK value (Change the value with Capital)
3. EDiv -> EDIV value (PUT THE VALUE WHICH IS IN THE BRACKET!)
4. RAND -> ERAND value (PUT THE VALUE WHICH IS IN THE BRACKET!)
*Note that the LTK and IRK value's alpahbet must be Capital and EDIV and ERAND value must be the value in bracket

And Save it


<h1>Step 4.</h1>
Restart the Bluetooth service 
'''sudo service bluetooth restart'''