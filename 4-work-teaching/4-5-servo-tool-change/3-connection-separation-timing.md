# 4.5.3 Connection/separation timing


<p align="center">
 <img src="../../_assets/image_10.png" width="60%"></img>
 <em><p align="center">Figure 4.17 Connection and seperation timing chart</p></em>
</p>

*   Connection

    If the robot and servo gun are mechanically connected during the execution of the connection command (toolchng on), the connection completion signal will be inputted, the connection will be processed inside the controller, the encoder power for driving the axis of the servo gun will be inputted, and the motor on operation will be executed.
*   Separation

     The separation command will execute the processing of the separation according to the sequence opposite to that of the connection command.
