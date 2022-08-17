# 5.2.2. Equalizerless gun

If the gun type is “eqaulizerless gun”, a screen for setting the parameters related to the equalizerless gun will be indicated as shown below.


<p align=center>
<img src="../../_assets/image_42_eng.png" width="70%"></img>
<em><p align="center">Figure 5.8 Equalizerless gun setting</p></em>
</p>


(1)  **Maximum fixed electrode consumption amount (mm)**

    If the consumption amount measured by the egunsea statement exceeds the value set here, an error will be generated.
(2)  **Fixed electrode replacement required consumption amount (mm)**

    If the consumption amount measured by the egunsea statement exceeds the value set here, a warining will be outputted.
(3)  **Equalizing speeed (mm/s)**

    Sets the robot's equalizing speed.
(4)  **Gun type**

    Selects whether the selected equalizerless gun is a ‘robot gun’ or a ‘stationary gun’. Please refer to 『**2.3.1 Servo gun parameter**.』
(5)  **Gun arm deflection amount/100\[Kgf]\(mm)**

     Sets the deflection amount caused by the squeezing force as the deflection amount for 100 kgf. For the position of the fixed electrode for the execution of spot welding, calculate the gun arm deflection amount both from this value and the command squeezing force and then make some compensation for it and then perform squeezing. 
