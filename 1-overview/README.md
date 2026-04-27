# 1. Overview

This manual describes the controller settings and functions required when performing spot welding using Hyundai Robotics robots and controllers.
Please refer to this manual and apply it appropriately to your on-site system conditions.

### Definition and Principle

Spot welding is a type of resistance welding in which two or more metal sheets (thin plates) are overlapped and pressed together by copper alloy electrodes. A high electric current is then passed through the materials, generating heat due to electrical resistance at the contact surfaces. This heat locally melts the metal, forming a weld joint. During the welding process, the molten metal solidifies and forms a round bonded zone called a nugget.

### Three Major Factors of Resistance Welding

The quality of spot welding is primarily determined by the following three factors:

  -  Welding Current  
    The amount of current must be sufficient to generate enough heat to melt the metal at the interface.

  - Electrode Force (Pressure)  
    Proper pressure ensures good contact between the workpieces and stabilizes the welding process. Too little force may cause spatter, while excessive force can reduce resistance and lower heat generation.

  - Welding Time  
    This is the duration for which current is applied. It must be optimized to allow proper nugget formation without overheating or material damage.


### Types of Spot Welding Guns
  -  Servo Gun  
    A servo gun operates by transmitting the rotational force of a servo motor to a ball screw, which drives the gun tip to perform pressing and opening motions. It is configured as an additional axis of the robot and controlled accordingly. During welding, the equalizing motion is performed by the robot.

  - EQ Gun  
    An EQ gun is a spot welding gun that uses pneumatic pressure for pressing and opening motions. It is controlled by welding conditions and welding (current output) signals. During welding, the equalizing motion is performed mechanically by the gun itself.

  - EQ-less Gun  
    An EQ-less gun is also a pneumatic-type spot welding gun that performs pressing and opening motions using air pressure. It is controlled by welding conditions and welding (current output) signals. However, since it does not have a cylinder for equalizing motion, this function is performed by the robot during welding.

  - EQ-Brake Gun  
    The EQ-Brake gun is similar to the EQ gun in its basic operation. However, it is specifically used in cases where a large reaction force is generated during welding. In this method, welding is performed while the brakes of each robot axis are engaged to maintain positional stability. This type of gun is only used with robot-mounted welding guns (robot guns).

   
</br>
</br>

**[Essential manuals]**

- [${cont_model} Controller Operation Manual](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/en-tp630/README?cont_model=${cont_model})

- [${cont_model} Additional Axis Function Manual](https://hrbook-hrc.web.app/#/view/doc-add-axes/en/README?cont_model=${cont_model})
