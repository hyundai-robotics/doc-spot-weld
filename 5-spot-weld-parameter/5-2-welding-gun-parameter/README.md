# 5.2 Welding gun parameter

This section describes how to add a welding gun for spot welding operations and configure detailed settings according to the gun type.

<p align=center>
<img src="../../_assets/image_28_eng.png" width="70%"></img>
<em><p align="center">Figure 5.2.0 Spot gun general settings</p></em>
</p>

<br>


## General Settings

(1) Adding and Deleting Welding Guns
  - Use the `[+]` and `[-]` buttons on the right to add or delete spot welding guns.
  - Up to 16 guns can be registered.

(2) Tool Number  
  - The geometric information of each gun must be stored in advance in the Tool Data.
  - Enter the corresponding Tool Data number for each welding gun.

(3) Welder Number
  - Assign the welder connected to the corresponding gun number. When welding is performed with the selected gun, input/output signals are transmitted through the port configured for that welder.
  - Up to four welders are supported, allowing simultaneous welding with a maximum of four spot welding guns.

(4) Gun Type
  - Servo Gun
    - A gun that performs pressing and position control using a servo motor as an additional axis.
    - When selected, the additional axis number must be entered additionally.
    - The additional axis must be configured according to the servo gun specifications using the additional axis setup function.

  - EQ Gun
    - A pneumatic spot welding gun equipped with a built-in equalizing mechanism.
    - When executing a spot welding command, the robot does not move to a clearance position as in the case of a servo gun.

  - EQless Gun
    - A pneumatic spot welding gun that does not have a built-in equalizing function.
    - Therefore, equalizing is performed by robot control.
    - When executing a spot welding command, the robot includes a movement to the clearance position.

  - EQ-Brake Gun
    - An EQ-type gun that performs equalizing while the robot axes are held by brakes to prevent displacement caused by welding reaction force.
    - Additional settings are required in the welding sequence configuration.
    - Supported only for robot-mounted guns attached to the robot R1 axis. For stationary guns, select the EQ gun type.




<br>

When the gun type is set to servo gun or equalizerless gun, individual parameters must be configured for each respective gun.

