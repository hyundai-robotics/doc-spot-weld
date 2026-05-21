# 4.10 Spot system variables


Some setting values can be accessed and controlled using spot system variables. These variables store the clearance values for each condition, individual wear values for the moving and fixed electrodes, and the total wear amount. As shown in the illustration below, you can read or modify these values by using variable assignment statements in the command window. 

<p align="center">
 <img src="../_assets/image_93_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.23 Spot tip-consumption system variable usage</p></em>
</p>

</br>


|category	|system variable	|content|
|:--:	|:--:	|:--:|
|welding condition|_spotcnd[#].fixed_tip_clearance|	fixed tip clearance value of the conditon nuymber(#)|
|welding condition|_spotcnd[#].moving_tip_clearance|moving tip clearance value of the conditon nuymber(#)|
|welding gun|_spotgun[#].fixed_tip_consump|	fixed tip consumption fo the gun number(#)|
|welding gun|_spotgun[#].moving_tip_consump|	moving tip consumption fo the gun number(#)|
|welding gun|_spotgun[#].total_tip_consump|	total consumption fo the gun number(#)|

<br>

{% hint style="warning" %}
- The cunsumption-related variables can apply only to servo and equalizerless guns. 
- In the case of the equalizerless gun, the total consumption amount equals the fixed electrode consumption amount.  
- Any manually set wear amount values will be overwritten by the measured values after a gun search is performed.  
{% endhint %}
