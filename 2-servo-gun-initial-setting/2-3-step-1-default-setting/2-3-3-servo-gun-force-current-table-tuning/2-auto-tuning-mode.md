#### 2.3.3.2 Auto tuning mode

This function is used to automatically set the servo gun squeezing force–current table.
To use this function, data communication between the squeezing force gauge and the robot controller must be available. Please make sure to check whether the selected squeezing force gauge is supported before use.


<p align="center">
 <img src="../../../_assets/image_25_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.14-1 Servo Gun Auto Tuning Screen</p></em>
</p>

<br>


Before using this function, position the squeezing force gauge on top of the fixed electrode as shown in the figure above, and manually move the moving electrode to bring it into contact with the gauge.

Then, enter the servo gun squeezing force–current table auto tuning setting screen and press the `[Execute]` button to start tuning.

During auto tuning, the moving electrode repeatedly moves several times. Therefore, the process must be carried out in manual mode with the motor turned ON. (If the motor is OFF, the process will stop.)

If you need to forcibly stop the tuning during operation, press the `[Clear]` button. After completing the tuning, perform test squeezing for each force level. If there are any accuracy issues, repeat the tuning process.


<br>


The settings are described below:

 -  Squeezing Force Gauge Manufacturer  
Select the manufacturer of the squeezing force gauge to be used.

 - Serial Port  
Select the number of the connected serial port.

 - Moving Electrode Direction  
Select whether the moving direction of the servo gun electrode is in the gravity direction or the anti-gravity direction.

 - Number of Repetitions  
Set the number of repetitions for auto tuning to reduce variation in the commanded current. (1–10)

 - Commanded Squeezing Force  
Set the desired squeezing force range in five levels for the table.