### 5.3.3 Welding sequence

Sets the spot welding sequence to define robot operation according to the work environment.


<p align=center>
<img src="../../_assets/image_1_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.14 Welding sequence setting</p></em>
</p>

(1)  **Sequence number**
  - Allows quick selection of the desired welding sequence. This number usually corresponds to the sequence name.

(2)  **Welding signal output delay time (GWT)**
  - Servo gun: Defines the waiting time before the welding signal is output after squeezing force matching is completed.
  - Pneumatic gun: Defines the waiting time before the welding signal is output after execution of the `spot` statement.

(3)  **Welding signal pulse output (0=level)**
  - Specifies the duration for which the welding signal is output.
If this value is set to 0, the welding signal continues to be output until the welding completion (WI) signal is received.

(4)  **Welding completion (WI) wait time**
  - Specifies the waiting time for the welding completion (WI) signal to be received.
If this value is set to 0, the system waits indefinitely until the signal is received.

(5)  **Robot wait time after welding completion (RWT)**
  - Generally specifies the waiting time for deposition detection after the welding completion (WI) signal is received. If this value is set to 0.0, deposition detection is not performed. When using the deposition detection signal, a value greater than 0.3 seconds (300 ms) is recommended. However, increasing this value will lengthen the welding time and increase the overall cycle time.
