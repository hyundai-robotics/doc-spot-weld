### 5.2.1.1 Servo gun default setting

<p align=center>
<img src="../../../../_assets/image_44_eng.PNG" width="70%"></img>
<img src="../../../../_assets/image_87_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.2 Servo gun default setting screen</p></em>
</p>

(1)  **Manual stroke distance (mm)**  
  Specifies the target position for performing wide and narrow opening operations of the servo gun using the user key.

(2)  **Maximum tip consumption (mm)**  
  If the moving or fixed electrode consumption amount detected through gun search exceeds the set value, an error will be generated and operation will stop.

(3)  **Tip change consumption (mm)**  
  If the moving or fixed electrode consumption amount detected by gun search exceeds the value set here, an electrode consumption alarm signal will be output together with a warning message to indicate that electrode replacement is required.
  If it is set to 0.0 mm, no abnormality will be detected.

(4)  **Bend offset per 100kgf (mm)**  
  Sets the gun arm deflection caused by the squeezing force as a deflection amount per 100 kgf. During spot welding, the squeezing operation is performed by calculating the gun arm deflection based on both this setting and the commanded squeezing force.


<p align=center>
<img src="../../../../_assets/image_50_eng.PNG" ></img>
<em><p align="center">Figure 5.3 Gun arm deflection amount/100Kgf graph</p></em>
</p>

(5)  **Pressure tolerance (%)**  
  During the squeezing force matching process, force matching is considered complete when the actual squeezing force falls within the specified accuracy range of the commanded squeezing force.
  If this value is set to 0, the notification "W0110: Set in a way that squeezing force detection does not occur" will be displayed, and squeezing force matching will not be performed.

(6)  **Press fault check time (s)**  

  Sets the time from the start of squeezing until squeezing force matching is achieved.

  If squeezing force matching occurs within this time, the welding signal will be output immediately. If squeezing force matching does not occur within this time, the notification "E1314: Exceeds the time for detection of abnormal squeezing force" will be issued and operation will stop.

  If the time is set to 0.0 sec, squeezing force matching  detection will continue to wait.


(7)  **Command offset (mm)**  
  When the `spot` statement is executed, the servo gun must generate the specified squeezing force. To do this, the moving electrode is commanded to move to the squeezing position. The squeezing position is defined as the position obtained by adding the command value offset to the recorded position in the squeezing direction.

(8)  **Installed site**   
  Selects the type (robot gun or stationary gun) of the selected servo gun.
  When using a stationary servo gun, set the user coordinate system number in which the coordinate system of the stationary gun has been defined in advance. (If the value is 0, the robot coordinate system will be used.)

  The user coordinate system should be defined so that the travel direction of the fixed electrode corresponds to the positive Z (+) direction.

<p align=center>
<img src="../../../../_assets/image_81_eng.PNG" ></img>
<em><p align="center">Figure 5.4 Stationary gun coordinate system</p></em>
</p>
 
(9)  **Moving tip / total consumption (%)**  
  Regarding the method for measuring the consumption amount of the servo gun, one option is to measure it using Gun Search 1 only, and the other is to measure it using both Gun Search 1 and Gun Search 2.

  If the value is set to 0, the consumption amount will be calculated using both Gun Search 1 and Gun Search 2. If the value is set to a value other than 0, the total consumption amount measured through Gun Search 1 will be distributed between the moving electrode consumption amount and the fixed electrode consumption amount according to the specified ratio (%).

(10)  **Real-time pressure control**

  Sets whether to use the real-time squeezing force control function.

  This function controls the system to ensure that the specified squeezing force is achieved by using the actual squeezing force measured with a squeezing force gauge.

  If this function is enabled, the `[Realtime signal]` button will be activated, allowing the related parameters to be configured.
  
(11)  **Current - force table**  

  A squeezing force table with up to five levels can be created by measuring the squeezing force using a force gauge. If different squeezing forces are set for the gravity direction and the anti-gravity direction, compensation will be applied according to the operating direction of the gun.

  The squeezing force-current table defines the current values corresponding to each of the five squeezing force levels. The table must be configured so that both the squeezing force and the current value increase as the level increases.

  The upper and lower limits set for the squeezing force are used as the allowable range during playback or manual operation.

<p align=center>
<img src="../../../../_assets/image_54_eng.PNG" ></img>
<img src="../../../../_assets/image_11_eng.PNG" ></img>
<em><p align="center">Figure 5.5 Gravitation direction and anti-gravitation direction</p></em>
</p>