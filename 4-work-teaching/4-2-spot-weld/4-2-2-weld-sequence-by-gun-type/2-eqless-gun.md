### 4.2.2.2 Equalizerless gun

If the gun type is equalizerless gun, the spot welding function is played back as shown in the figure below.

<p align="center">
 <img src="../../../_assets/image_5_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.9 Playback of spot welding by ann equalizerless gun</p></em>
</p>

<Br>


1. At the N-1 step position, the fixed electrode moves away from the recorded position by the fixed electrode clearance.

2. Through the robot equalizing operation, the fixed electrode moves to the recorded position of the step, and pneumatic pressure causes the moving electrode to squeeze the panel.

3. When the target squeezing force is reached, the welding execution signal is output together with the welding condition signal at that position.

4. When the welding completion signal (WI) is received, the fixed electrode moves away from the recorded position by the fixed electrode clearance, and the moving electrode moves to a position where pneumatic pressure is not supplied.

5. The system moves to the next step.