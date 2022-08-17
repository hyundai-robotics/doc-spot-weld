# 5.2.1.1.1 Real-time squeezing force control

Real-time squeezing force control is a function to improve the accuracy of servo gun's squeezing force by using the data, measured by the squeezing force gauge, for control. For real-time squeezing force control, the squeezing force gauge should communicate with the robot controller and should be set to relevant communication specifications using the menus below.

<p align=center>
<img src="../../../../_assets/image_30_eng.png" width="70%"></img>
<em><p align="center">Figure 5.6 Setting of real-time squeezing force control</p></em>
</p>

(1)  **Communication method**

    Sets an analog or digital communication method. The digital method is recommended for fast and stable control.
(2)  **Additional use of controller filter**

    To be used when an additional controller filter is needed.
(3)  **Cut-off frequency**

    Will be activated when the additional use of the controller filter is set to valid. The size of the filter necessary for the control should be set.
(4)  **Reset signal output**

    Assigns a signal that is to be outputted for resetting the squeezing force gauge.&#x20;
(5)  **<Analog>**

    Will be activated when analog is selected as the communication method.

    * Squeezing force input port: The number of the signal assigned for input
    * Magnification: Magnification of the analog input value
(6)  **<Digital>**

    Will be activated when digital is selected as the communication method.

    * Communication range: Minimum and maximum ranges of the assigned signal
    * Value range: Minimum and maximum values of the assigned signal
    * Port: The number of the signal assigned for input
    * Port assignment: Bit count assigned to a signal


