### 4.2.2.1 Servo gun

If the gun type is servo gun, the spot welding function is played back as shown in the figure below.

<p align="center">
 <img src="../../../_assets/image_66_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.8 Playback motions of servo gun spot welding</p></em>
</p>


<br>


1. At the N-1 step position, the moving and fixed electrodes move away from their recorded positions by the moving electrode clearance and fixed electrode clearance, respectively.

2. Through the robot equalizing operation, the fixed electrode moves to the recorded position of the step, and the moving electrode moves to the recorded position while being shifted by the consumption amount.

3. The moving electrode performs the squeezing operation using the specified squeezing force. When the target squeezing force is reached, the welding execution signal is output together with the welding condition signal at that position.

4. When the welding completion signal (WI) is received, the moving and fixed electrodes open by their respective clearance amounts.

5. The system moves to the next step.