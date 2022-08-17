# 4.3.2 Type of operation

To perform a tip dressing operation using the servo tip dressing condition, the welding sequence number in the Spot statement must be designated as 64 as shown below.


<p align="center">
 <img src="../../_assets/image_77_eng.png" width="60%"></img>
 <em><p align="center">Figure 4.11 Servo gun tip dressing operation</p></em>
</p>

>1. At the N-1 step position, the moving electrode moves to the position away from the record position as much as the moving electrode clearance and the fixed electrode moves to the position away from the record position as much as the fixed electrode clerance.
>2. Movement to the record position of the step occurs.
>3. The moving electrode performs the squeezing operation with the squeezing force set in the welding condition. When the squeezing force is matched, the welding condition signal is outputted at the position. Whether the welding execution signal is outputted together at this time can be determined by the state of the “**Welding signal output**” setting in the tip dressing condition.
>4. When the set tip dressing time passes, the moving and fixed electrodes open as much as the clearance of each, respectively.
>5. Movement to the next step occurs.
