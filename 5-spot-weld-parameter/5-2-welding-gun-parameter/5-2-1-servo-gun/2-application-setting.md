### 5.2.1.2 Servo gun application setting


<p align=center>
<img src="../../../_assets/image_6_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.7 Servo gun application setting</p></em>
</p>


(1)  **Gun arm deflection amount (mm)**  

 - Sets the gun arm deflection amount of the z-direction for the squeezing force set on the left. Considering that it is difficult to manually measure and fill in the values, it is recommended to use servo gun automatic setting. If you press 'Default value calculation', the value of 0.31 mm per 100 kgf will be set as the default value.
 
(2)  **Panel thickness compensation(mm)**  

  - Sets the panel thickness compensation amount for the squeezing force set on the left. Considering that it is difficult to manually measure and fill in the values, it is recommended to use servo gun automatic setting.

{% hint style="warning" %}  

The 'gun arm deflection amount compensation' value is a value used instead of the 'gun arm deflection amount/100 kgf\[mm]' among the servo gun parameters. When the 'gun arm deflection amount compensation' value is set, the already set 'z-direction gun arm deflection amount/100 kgf\[mm]' will not be used. On the contrary, if a 'gun arm deflection amount compensation' value is not set, the 'gun arm deflection amount/100 kgf\[mm] will be used.'  
{% endhint %}
