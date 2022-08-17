# 5.5 Output signal assignment for each welder

Assigns the signals related to spot welding and transfers their state to the outside.

<p align=center>
<img src="../_assets/image_45.png" width="70%"></img>
<em><p align="center">Figure 5.17 Output signal assignment</p></em>
</p>

(1)  **Welder number**

    Selects the welder number to set. Up to four welders can be added.
(2)  **Welding condition**

    Assigns the number of the signal to output the output data corresponding to the welding condition during the execution of the Spot statement.
(3)  **Welding execution**

    To be used to output a command for welding to the welder during the execution of the Spot statement.
(4)  **Welder abnormal**

    To be used to output the inputted spot welder abnormal signal to the outside.
(5)  **Electrode consumption alarm**

    To be used to output a signal if the consumption amount detected by the gun search is larger than the electrode replacement required consumption amount.
(6) **Deposition error**

    To be used to output to the outside the state that deposition has occurred to the spot gun.
(7)  **Servo gun squeezing in progress**

    This is a signal that is turned on when squeezing starts upon the execution of the Spot statement and turned off when the opening procedure starts.
(8)  **Welding gun search in progress**

    This is a signal that is turned on when gun search starts upon the execution of the gunsea, igunsea or egunsea statement and turned off when the opening procedure starts.
    