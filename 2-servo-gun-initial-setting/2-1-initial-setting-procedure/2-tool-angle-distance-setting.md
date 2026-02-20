### 2.1.2 Setting of the tool angle/distance

When performing spot welding, the equalizing operation (the process in which the fixed electrode contacts the panel after passing through the clearance position) is essential. This operation requires the tool coordinate system to be set correctly. 
The +Z axis of the tool coordinate system must be aligned in the direction from the fixed electrode toward the moving electrode. (Note: [Controller Operation Manual](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/en-tp630/README?cont_model=${cont_model})).

<p align="center">
 <img src="../../_assets/image_38_eng.PNG">
  <em><p align="center">Figure 2.3 Setting of the tool length and angle of the welding gun : {0˚, 180˚, 0˚}</p></em>
 </img>
</p>

<br>

*   Tool length

    When setting the tool length, measure the distance from the center of the robot R1-axis flange to the tool tip (upper part of the fixed electrode) with a new, unused electrode installed.

    Use the reference tool coordinate system and follow its positive (+) axis directions.
    Input the measured X, Y, and Z length values accordingly.

    Alternatively, the tool length can be set by using `[F1: Auto calibration]` function in the menu of tool data setting.

<br>

*   Tool angle

    Input the rotation angles (Rx, Ry, Rz) for the three axes based on the flange coordinate system, or use the `[F2: Angle calibration]` function.

    Set the tool angle so that the upward direction of the fixed electrode corresponds to +Z of the tool coordinate system.

    To verify the setting:

    1. Set the teach pendant coordinate system to `[crd.sys tool]` (4th button in the Status Display window).

    2. Press the `[Z+]` jog key.

    3. Check the movement direction.

    If the movement direction matches the squeezing direction of the fixed electrode (upward direction shown in Figure 2.3), the tool angle setting is correct.