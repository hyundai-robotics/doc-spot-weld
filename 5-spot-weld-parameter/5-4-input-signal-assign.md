# 5.4 Input signal assignment for each welder

Assigns the signals related to spot welding, allowing the controller to monitor their state and perform necessary processing.


<p align=center>
<img src="../_assets/image_15_eng.png" width="70%"></img>
<em><p align="center">Figure 5.15 Input signal assignment</p></em>
</p>

(1)  **Welding completion**

    Only when this welding completion signal is inputted during the execution of spot welding, the controller executes the handling of welding completion. There are four welding completion signals in total and they are individually controllable. 
(2)  **Deposition error**

    To be used when receiving and handling the input of the gun's deposition signal.
(3)  **Welder abnormal**

    To be used to stop the operation of the robot when the signal of welder abnormal is inputted.
