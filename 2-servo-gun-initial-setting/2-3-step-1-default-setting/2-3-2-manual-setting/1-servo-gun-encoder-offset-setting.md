# 2.3.2.1 Servo gun encoder offset setting

Normally, when the encoder data is changed because of replacement of the servo gun motor, etc., the origin of the encoder should be set at a position that can match the same mechanical position. In the case of the servo gun, the setting should be performed with the moving electrode in the mechanically maximum open state.

The encoder compensation procedure for the axis of the servo gun is as follows.

(1) Manually release the brake of the axis of the servo gun and then open the moving electrode to the maximum.

<p align="center">
 <img src="../../../_assets/image_71.png"></img>
 <em><p align="center">Figure 2.8 Servo gun's maximum open position</p></em>
</p>


(2) In the default setting screen of the‘**Servo gun automatic setting**’ menu, press the [**Manual setting**] button of the ‘**Encoder offset compensation**’ menu (Figure 2.9), or select the relevant servo gun axis in  『**Setting**』 → 『**3: Robot parameter**』 → 『**4: Encoder offset**』 with the cursor and then press the [**Reset**] button. When the current encoder value becomes “**00400000**”, press the [**OK**] button. 

<p align="center">
 <img src="../../../_assets/image_36.png" width=80%></img>
 <em><p align="center">Figure 2.9 Moving to the encoder offset compensation screen</p></em>
</p>