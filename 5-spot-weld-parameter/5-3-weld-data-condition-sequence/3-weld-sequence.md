# 5.3.3 Welding sequence

Sets the sequence related to the spot welding to determine the robot operation according to the work environment.


<p align=center>
<img src="../../_assets/image_1_eng.png" width="70%"></img>
<em><p align="center">Figure 5.14 Welding sequence setting</p></em>
</p>

(1)  **Sequence number**

    Selects the desired welding sequence quickly among the welding sequences.
(2)  **Welding signal output delay time (GWT)**

    In the case of the servo gun, this refers to the time of waiting until the welding signal is outputted after the squeezing force matching occurs

    In the case of a pneumatic gun, this refers to a time of waiting until the welding signal is outputted after the execution of the Spot statement.
(3)  **Welding signal pulse output (0=level)**

    This is to allow the welding signal to be outputted for a certain period of time. If the value is set to “0”, the welding signal continues to be outputted until the welding completion (WI) signal is inputted.
(4)  **Welding completion (WI) wait time**

    This is the time of waiting until the welding completion signal is inputted. If this value is set to “0”, waiting continues until there is an input.
(5)  **Robot wait time after welding completion (RWT)**

    In general, this the time of waiting for deposition detection after the welding completion (WI) signal is inputted. If the value is set to “0.0”, the deposition detection does not occur. When the deposition detection signal is to be used, it is recommended to use a value greater than “0.3 secs (300 msec).” However, if the value is large, the welding time will get longer and the cycle time will increase. 
