
#### 6.1.1 Advantages and Features

### Advantages

- Easy connection with other peripheral devices, reducing overall system setup time (Short start-up time)

- Use of DeviceNet reduces wiring requirements (Lower capital costs)

- Reduced downtime

- A single controller : the robot Teach Pendant for robot and welder operations

### Features

- Ensures reliable communication between the robot controller and the welder through the DeviceNet message method.

- Supports connection of up to four welding timers (applicable to both servo guns and pneumatic guns).

- No modification of the robot controller software is required even when the timer model is changed.

- The robot controller can handle individual files such as welding schedules, common welding data, and stepper data.

- Weld result data is managed by the controller, enabling sharing of error and abnormality history and allowing error analysis.

- Welding quality can be improved by monitoring real-time weld results via the robot TP and modifying the schedule and stepper programs accordingly.

<Br>

Table 6.1 File Types and Descriptions

|File Type |	File Name <br> (# = Timer No.)  |	Description  |
|:--:|:--:|:--:|
|Timer characteristic data |	ROBOT.NS# |	Stores timer-related information |
|Welding program data	| ROBOT.ND# |	Stores various welding program data |

