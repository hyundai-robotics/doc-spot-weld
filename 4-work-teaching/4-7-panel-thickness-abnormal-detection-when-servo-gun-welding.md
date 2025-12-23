# 4.7  Detection of panel thickness abnormality during the welding with servo gun

 This is a function to measure the panel thickness during the welding with a servo gun to detect any abnormality with parts and any missing of installation of materials. The function can be executed simply by adding the “thickcheck” statement. Whether the panel thickness is abnormal should be determined based on whether the measured value is within the normal range.

<br>

```thickcheck thick=<thickness variable>, ref=<reference value>, tol=<tolerance value>, addr=<go to>```

<br>

* **thick**

    Specipies the variable to store the measured panel thickness by squeezing the servo gun.

* **ref**

    Specipies the normal panel thickness.

* **tol**

    Specipies the tolerance.

* **addr(branch line)**

   Specipies the method of handling when panel's abnormality is detected. If the branch line is not recorded, the situation “**E1493 Measured panel thickness exceeded the normal range**” occurs and then the robot stops and the output signal set in the “**Panel thickness abnormal**” section is turned on. If the branch line is recorded, the situation “**W0152 Measured panel thickness exceeded the normal range**” occurs and the robot continues to operate as the program jumps to the branch line. In this case, the output signal set in the “**Panel thickness abnormal**” section is turned on only for 200 ms.

 *  Sample code 

```python

S10   move L, ...                               # Move to a spot point
      thickcheck thick=v0,ref=4.0,tol=1.0       # Check the panel thickness
      spot gun=1, cnd=1, seq=1                  # perform spot welding

```
<Br>

{% hint style="warning" %}  
The following should be in place first for accurate measurement of the panel.

1. Gun search (precise management of the consumption amounts of the moving and fixed electrodes)
2. Setting of gun arm deflection amount (Setting of the gun arm deflection amount for each squeezing force)
3. Setting of panel thickness(Setting of the panel thickness for each squeezing force)
{% endhint %}


