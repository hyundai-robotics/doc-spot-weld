# 5.6 Assignment of input and output signals common to  welders

Assigns the common input and output signals, regardless of the welder number, and transfers their state to the outside or receives their input.

<p align=center>
<img src="../_assets/image_72_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.18 Assignment of input and output signals common to welders</p></em>
</p>

(1)  **Spot command execution method (sv)**

    To be used to output a signal if the “servo gun spot welding output method” in the spot gun common parameter setting menu is set to Wd-On.
(2)  **Panel thickness error**

    To be used to output a panel thickness abnormal signal generated during the welding by the servo gun.
(3)  **Moving electrode consumption amount reset**

    To be used to receive an input of the moving electrode consumption amount reset command as a signal.
(4)  **Fixed electrode consumption amount reset**

    To be used to receive an input of the fixed electrode consumption amount reset command as a signal.
(5)  **Command for wide opening**

    To be used to receive an input of the command for wide opening as a signal.
(6)  **Command for narrow opening**

    To be used to receive an input of the command for narrow opening as a signal.

