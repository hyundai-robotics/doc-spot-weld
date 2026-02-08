# 6.1 Overview of the Welder Interface

This function enables the robot controller to integrally control the spot welding timer through DeviceNet communication.
The ${cont_model} controller and the spot welder share data with each other via DeviceNet.

By combining the robot controller and the spot welding timer into a single integrated system, users can perform welding program editing and file management using the ${cont_model} Teach Pendant (TP).

The robot controller performs the major functions that are normally handled through the welder's teaching box-such as welding schedule programming, stepper programming, weld result monitoring, and history file management-directly from the robot controller's Teaching Pendant.

In other words, the system provides a user interface that allows the robot Teach Pendant to perform the functions of the Teaching Box-the operation panel of a standalone welder. It also enables monitoring by displaying welding results, various signals, and the status of errors or faults.

Communication between the robot controller and the timer uses DeviceNet.
The robot controller is configured as the master, and the timer is configured as the slave.

<p align="center"> <img src="../../_assets/6_1.png"> </p> <p align="center"><em>Figure 6.1 (a) Spot welding system with a separate welder (b) Integrated spot welding system</em></p>