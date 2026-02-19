### 4.2.2.3 Equalizer-fitted gun

If the gun type is equalizer-fitted gun, the spot welding function is played back as shown in the figure below.

<p align="center">
 <img src="../../../_assets/image_82_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.10 Playback of spot welding by an equalizer-fitted gun</p></em>
</p>

<br>



1. At the N-1 step position, the robot moves to the recorded position of the step.

2. The welding execution signal is output together with the welding condition signal.
The equalizing device causes the fixed electrode to squeeze the panel, and pneumatic pressure causes the moving electrode to squeeze the panel.

3. When the welding completion signal (WI) is received, the fixed electrode moves to a position where the equalizing device is inactive, and the moving electrode moves to a position where pneumatic pressure is not supplied.

4. The system moves to the next step.