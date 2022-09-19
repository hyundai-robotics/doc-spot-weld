# 4.7  Detection of panel thickness abnormality during the welding with servo gun

 This is a function to measure the panel thickness during the welding with a servo gun to detect any abnormality with parts and any missing of installation of materials. The function can be executed simply by adding the “thickcheck” statement. Whether the panel thickness is abnormal should be determined based on whether the measured value is within the normal range.

<p align="center">
 <img src="../_assets/image_49_eng.PNG" width="40%"></img>
 <em><p align="center">Figure 4.20 Inspection of the panel thickness with the servo gun</p></em>
</p>

* **thick**

    Designates the variable to store the measured panel thickness by squeezing the servo gun.
* **ref**

    Designates the normal panel thickness.
* **tol**

    Designates the toleranc.
* **addr(branch line)**

   Designates the method of handling when panel's abnormality is detected. If the branch line is not recorded, the situation “**E1493 Measured panel thickness exceeded the normal range**” occurs and then the robot stops and the output signal set in the “**Panel thickness abnormal**” section is turned on. If the branch line is recorded, the situation “**W0152 Measured panel thickness exceeded the normal range**” occurs and the robot continues to operate as the program jumps to the branch line. In this case, the output signal set in the “**Panel thickness abnormal**” section is turned on only for 200 ms.



{% hint style="warning" %}
[Caution]  

The following should be in place first for accurate measurement of the panel.

1. Gun search (precise management of the consumption amounts of the moving and fixed electrodes)
2. Setting of gun arm deflection amount (Setting of the gun arm deflection amount for each squeezing force)
3. Setting of panel thickness(Setting of the panel thickness for each squeezing force)
{% endhint %}
