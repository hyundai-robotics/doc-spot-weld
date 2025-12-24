# 4.10 Consumption amount setting

Consumption amount information for the spot gun can be accessed using spot system variables. The spot system variables display the wear amount of the moving electrode, the fixed electrode, and the total wear amount for each gun. These values can be modified or read using variable assignment statements in the command window.


<p align="center">
 <img src="../_assets/image_93_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.23 Spot tip-consumption system variable</p></em>
</p>

</br>

<br>

{% hint style="warning" %}
- This variable can apply only to servo and equalizerless guns. 
- In the case of the equalizerless gun, the total consumption amount equals the fixed electrode consumption amount.  
- Any manually set wear amount values will be overwritten by the measured values after a gun search is performed.  
{% endhint %}
