
[__SOURCE](README.md)
# ${cont_model} Controller Function Manual - Spot Welding

[__SOURCE](0-about-this-manual/precautions.md)
# Precautions

{% include file="en/precautions.md" %}

[__SOURCE](1-overview/README.md)
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

[__SOURCE](1-overview/1-1-main-specification.md)
# 1.1 Main specifications

|       **Item**       |                          **Specification**                          |
| :----------------: | :------------------------------------------------------: |
|     Spot welding setting file     |           spotweld.json            |
|      Maximum welder count     |              4 units                 |
| Count of multiple guns for simultaneous welding</br>(the same gun type) |           4 units                   |
|            |                 16 units                   |
|       Welding condition number      |                         1 - 1024                        |
|   Output data dependent on welding condition   |                         1 - 1024                        |
|       Welding sequence number      |                   1 -  63 (64 is exclusively for tip dressing)                   |
|     Position modification (servo gun)    | SPOT command step - Consumption amount automatic compensation position</br>Other steps - Positions that do not consider the consumption amount |
|    Inspection of the tool number corresponding to the gun umber   |                     Inspection of robot guns and no inspection of stationary guns                    |
|     Welding condition signal output     |   To be outputted in sync with the output of the welding execution signal</br>Impossible to output only the welding condition signal   |

[__SOURCE](1-overview/1-2-operating-order/README.md)
# 1.2 Operation sequence

Two procedures are provided for the servo gun setting: manual setting and automatic setting.
[__SOURCE](1-overview/1-2-operating-order/1-servo-gun-auto-setting.md)
### 1.2.1  Operation sequence that uses the servo gun automatic setting

The procedure for the servo gun automatic setting is as shown in the flowchart below.

---

<p align="center">
 <img src="../../_assets/image_78_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 1.1 Operation sequence of the servo gun automatic setting </p></em>
</p>
[__SOURCE](1-overview/1-2-operating-order/2-servo-gun-manual-setting.md)
### 1.2.2 Operation sequence that uses the servo gun manual setting

The procedure for the servo gun manual setting is as shown in the flowchart below.

---

<p align="center">
 <img src="../../_assets/image_46_eng.PNG" width="80%"></img>
 <em><p align="center">Figure 1.2 Operation sequence of the servo gun manual setting</p></em>
</p>
[__SOURCE](1-overview/1-3-servo-gun-terms-for-movement-between-electrodes.md)
# 1.3 Servo gun electrode movement terms


<p align="center">
 <img src="../_assets/image_8_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 1.3 Terms for the moving and fixed electrodes</p></em>
</p>
[__SOURCE](2-servo-gun-initial-setting/README.md)
# 2. Initial setting of the servo gun


[__SOURCE](2-servo-gun-initial-setting/2-1-initial-setting-procedure/README.md)
# 2.1 Procedure for initial setting of the servo gun

This function is related to spot welding and other applications that use a servo gun. If necessary to use a gun other than a servo gun (pneumatic gun, etc.), refer to only [2.1.1 Setting of the tool number and gun type corresponding to the gun number](1-tool-number-gun-type-setting.md) and [2.1.2 Setting of the tool angle/distance](2-tool-angle-distance-setting.md) in this chapter, and [3. Related functions](../../3-Related-functions/README.md) in the next chapter.

The initial setting of the servo gun is an essential process to makie it possible to perform spot welding using a servo gun. After completing the procedure for the initial setting of the servo gun, the following items will be possible.

* Operation of the moving electrode of the servo gun
* Squeeze with the specified squeezing force
* Signal input and output for spot welding

After completing the procedure for initial setting, you need to set related functions and spot welding parameters (welding conditions, sequence, etc.) according to the purpose of use, and then teach the work.

Through the `[6: Servo gun auto setting]` function (`[F2: system] - 4: Application parameter - 1: Spot welding`), our company provides settings and procedures for the environment for spot welding and servo gun operation.

<p align="center">
 <img src="../../_assets/image_60_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 2.1 Screen for entering the 'Servo gun automatic setting' menu</p></em>
</p>

{% hint style="warning" %}
You can enter the menu only when the currently selected gun number is for the servo gun.
("**Additional axis parameter setting**", "**Load estimation**", "**Tool data inputting**", "**Welding gun paramater**" are the contents that should be essentially set prior to the servo gun automatic setting.) If multiple guns are to be used, their individual settings should be performed by chaning the gun number.
{% endhint %}

</br>

---

The initial setting for the servo gun and spot welding is performed largely in five steps as shown below, and the progress of each step will be indicated, allowing you to monitor the progress.


<p align="center">
 <img src="../../_assets/image_3_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 2.1.2 Procedure for 'servo gun automatic setting'</p></em>
</p>

The standard procedure for the servo gun initial setting is as follows.

* [Step 0. Pre-inspection](../2-2-step-0-pre-inspection.md): Inspection of essential pre-setting items for the setting of the servo gun operation environment 
  * Additional axis parameter
  * Setting of the tool number corresponding to the gun number
  * Tool data setting (including load estimation)
  * Servo gun parameter setting
* [Step 1. Default setting](../2-3-step-1-default-setting/README.md): Setting of the servo gun operation environment
  * Encoder offset compensation
  * Axis origin setting
  * Soft limit setting
  * Squeezing force-current table setting
* [Step 2. Application setting](../2-4-step-2-application-setting/README.md): Setting of application functions that use the servo gun
  * Gun search
  * Gun arm deflection amount compensation
  * Panel thickness measurement compensation
* [Step 3. Setting check](../2-5-step-3-setting-check.md): Process for checking the current setting
* [Step 4. Signal setting](../2-6-step-4-signal-setting.md): Assignment of input and output signals for spot welding application

</br>

The servo gun initial setting procedure screen not only shows the indication process and the status about completion, but also makes it possible to proceed with related items or move to the screen where related items can be performed.

In other words, the initial setting related to the servo gun can all be completed from the above screen without going to relevant menus. The initial setting can be proceeded with in the following two ways.

1. Move the cursor to the relevant procedure and then input by selecting `[Enter]`.
2. Press `[F1: Go to unset items]` to automatically proceed with the initial setting not yet conducted.

The `[F1: Go to unset items]` butten makes it possible to inspect the procedures not yet conducted among all procedures, allowing them to be performed automatically. At the time of initial setting, you can complete the setting by following the guide just by clicking `[F1: Go to unset items]`.

[__SOURCE](2-servo-gun-initial-setting/2-1-initial-setting-procedure/1-tool-number-gun-type-setting.md)
### 2.1.1 Setting of the tool number and gun type corresponding to the gun number

This function sets the tool number and gun type corresponding to each spot welding gun number.

It allows various welding guns to be configured according to the welder and tool number assigned to each. Since the welding method differs depending on the gun type, these settings must be configured correctly.

Guns can be added using the `[+]` button on the right, and up to 16 guns can be registered.

<p align="center">
 <img src="../../_assets/image_31_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 2.2 Gun default setting</p></em>
</p>

(1) Tool number  
Tool refers to an object attached to the tip of the robot's R1 axis, and the robot must have the corresponding tool information registered. The tool number is the number assigned to match the corresponding gun number. The selected tool number must have the appropriate load estimation and tool data entered. Since each gun typically has a different shape, a unique tool number should be assigned to each gun number. Because stationary guns are not attached to the tip of the R1 axis, they may be assigned arbitrary tool settings without issue. During work teaching, if the gun number specified in the Spot command does not match the tool number specified in the `move` command, playback will not be possible. Please ensure these values are consistent.



(2) Welder number
Welder designates the welder associated with the corresponding gun number. When welding is performed with that gun, signals are input to and output from the ports assigned to the selected welder. Multiple guns can share and use the same welder through the servo tool change function.

(3) Gun type
Gun type indicates the type of the selected gun. One of three types can be chosen.
If the selected gun is a servo gun, the information for the additional axis assigned to that gun must be specified. For the additional axis information, the same additional axis may be assigned to multiple guns when using the servo tool change function.

</br>

{% hint style="info" %}
-	If the gun number corresponding to the tool number is not set, the tool number may be used for other purposes.

-	When setting the gun type as servo gun, it is required to set the additional axis number corresponding to the gun number in the following method.  

{% endhint %}

<center>

|Gun number	|Gun usage|	Additional axis number|
|:---:|:---:|:---:|
|G1, G2|	Change of welding guns including the servo gun|	Additional axis 1|
|G5|	Stationary servo gun 1|	Additional axis 2|
|G6|	Stationary servo gun 2|	Additional axis 3|

</center>
[__SOURCE](2-servo-gun-initial-setting/2-1-initial-setting-procedure/2-tool-angle-distance-setting.md)
### 2.1.2 Setting of the tool angle/distance

When performing spot welding, the equalizing operation (the process in which the fixed electrode contacts the panel after passing through the clearance position) is essential. This operation requires the tool coordinate system to be set correctly. 
The +Z axis of the tool coordinate system must be aligned in the direction from the fixed electrode toward the moving electrode. (Note: [Controller Operation Manual](https://hrbook-hrc.web.app/#/view/doc-hi6-operation/en-tp630/README?cont_model=${cont_model})).

<p align="center">
 <img src="../../_assets/image_38_eng.png">
  <em><p align="center">Figure 2.3 Setting of the tool length and angle of the welding gun : {0˚, 180˚, 0˚}</p></em>
 </img>
</p>

<br>

*   Tool length

    When setting the tool length, measure the distance from the center of the robot R1-axis flange to the tool tip (upper part of the fixed electrode) with a new, unused electrode installed.

    Use the reference tool coordinate system and follow its positive (+) axis directions.
    Input the measured X, Y, and Z length values accordingly.

    Alternatively, the tool length can be set by using `[F1: Auto calibration]` function in the menu of tool data setting.

<br>

*   Tool angle

    Input the rotation angles (Rx, Ry, Rz) for the three axes based on the flange coordinate system, or use the `[F2: Angle calibration]` function.

    Set the tool angle so that the upward direction of the fixed electrode corresponds to +Z of the tool coordinate system.

    To verify the setting:

    1. Set the teach pendant coordinate system to `[crd.sys tool]` (4th button in the Status Display window).

    2. Press the `[Z+]` jog key.

    3. Check the movement direction.

    If the movement direction matches the squeezing direction of the fixed electrode (upward direction shown in Figure 2.3), the tool angle setting is correct.
[__SOURCE](2-servo-gun-initial-setting/2-2-step-0-pre-inspection.md)
# 2.2 Step 0. Pre-inspection

Pre-inspection is an item that must be performed in advance for the initial setting of the servo gun, and it is required to complete the following setting before entering main menus.

* **Additional axis parameter**
  * To input the motor and amp specifications, etc. of the motor of the servo gun that is to be used for the designated additional axis.
  * Soft limit can be set arbitrarily because it is changed during the initial setting procedure.
* **Setting of the tool number corresponding to the gun number**&#x20;
  * To designate the servo gun and gun number that you want to set now.
* **Tool data setting**
  * To input load estimation, tool angle/length, etc.
* **Servo gun parameter setting**
  * To set necessary items such as command value offset, squeezing force permissible error.

Pre-inspection is a step to check whether the pre-setting items have been completed. If they are not performed, you can move to the screen where you can perform relevant settings. You must complete the relevant settings before proceeding with the initial setting of the servo gun.

<p align="center">
 <img src="../_assets/image_27_eng.PNG" width="90%"></img>
 <em><p align="center">Figure 2.4 Pre-inspection proceeding procedure</p></em>
</p>

{% hint style="warning" %}
If you complete the setting on the "**Additional axis parameter setting**" screen, you will be asked to reboot after completing the pre-inspection.  

After rebooting, you should enter the "**Servo gun automatic setting**" screen and continue the setting. 
{% endhint %}

[__SOURCE](2-servo-gun-initial-setting/2-3-step-1-default-setting/README.md)
# 2.3 Step 1. Default setting

After the pre-inspection is completed, the default setting can be performed. The default setting is an essential setting process to determine the reference position of the moving electrode of the servo gun, move the servo gun to a desired position, and supply the desired squeezing force.

The default setting consists of four items as shown in the figure below.

<p align="center">
 <img src="../../_assets/image_17_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 2.5 Default setting proceeding screen</p></em>
</p>

</br>

(1) **Encoder offset compensation**
   * Normally, when the encoder data is changed because of replacement of the servo gun motor, etc., the origin of the encoder should be set at a position that can have the same mechanical position. In the case of the servo gun, the setting should be performed with the moving electrode in the mechanically maximum open state.
   * For manual setting, refer to the chapter [2.3.2.1 Servo gun encoder offset setting](2-3-2-manual-setting/1-servo-gun-encoder-offset-setting.md).
  
(2) **Axis origing setting**
   * In general, the setting of the axis origin of the servo gun should be performed at the position where both the moving and fixed electrodes, with a new tip attached individually, meet each other. As most operations of the servo gun are performed with this axis origin as the reference, it is very important to carry out setting for this.
   * For manual setting, refer to the chapter [2.3.2.2 Servo gun axis origin](2-3-2-manual-setting/2-servo-gun-axis-origin.md).
   
  
(3) **Soft limit setting**
   * In general, the soft limit of the servo gun should be set to '**Minimum**' while the moving electrode is fully open, and set to '**Maximum**' while the moving electrode is at the closest position with all tips removed.
   * For manual setting, refer to the chapter [2.3.2.3 Servo gun soft limit](2-3-2-manual-setting/3-servo-gun-soft-limit.md).
    
(4) **Squeezing force - current table setting**
   * To squeeze the various servo guns, which are to be installed to the robot, with the desired squeezing force, it is necessary to make the current supplied to the servo gun correspond to the generated squeezing force. For this, our company provides a servo gun squeezing force - current table. It is necessary to tune this table to match with the servo gun..
   * To use this function, it is necessary to select five representative values among the areas of the squeezing force to be used. Tuning the servo gun squeezing force - current table is a process to find the currents that match with these five representative squeezing forces. This table can vary depending on the posture of the servo gun, so it is necessary to perform tuning for each case of when the direction of the moving electrode is in the direction of gravity and when it is in direction of anti-gravity, and, through this method, squeezing can be performed with high accuracy in various postures of the servo gun.
   * For more details, refer to the chapter [2.3.3 Servo gun squeezing force - current table tunning](2-3-3-servo-gun-force-current-table-tuning/README.md).

</br>

The default setting can be performed with automatic settng and manual setting.

(1) **Automatic setting**: The servo gun automatically moves to the designated position and then perform the designated setting.
   * Items that can be automatically set
     * Encoder offset compensation
     * Axis origin setting
     * Soft limit setting
   * The setting of the squeezing force - current table cann not be automatically performed because it requires user intervention such as the installation of a squeezing force gauge.
   
(2) **Manual setting**: The servo gun needs to be moved to the designated position through the operation by the user and the designated function will be performed on the dedicated setting screen.
  
[__SOURCE](2-servo-gun-initial-setting/2-3-step-1-default-setting/1-auto-setting.md)
### 2.3.1 Automatic setting

Progress the automatic setting of the default setting of the servo gun by pressing the `[All auto setup]` button. As the moving electrode of the servo gun moves automatically, the following conditions must be satisfied in advance.

* Moving and fixed electrodes with new tipes attached
* No worker around the servo gun
* No workpiece between the moving electrode and fixed electrode
* Manual mode
* Motor on
* Prohibition of maximum opening of the moving electrode (a gap of certain distance from the maximum opening position)

In the case of `[All auto setup]`, the following procedures will proceed automatically.

  *  (1) Encoder offset compensation  
      - The moving electrode moves to the maximum opening position.  
      - The servo gun stops at the maximum opening position and then encoder offset compenation will be executed.
  *  (2) Axis origin setting
      - The servo gun performs the squeezing operation three times and opening operation two times.
      - After the third squeezing operation, the servo gun moves to the position where the two electrodes meet with each other.
      - Confirms the relevant position with the user.
      - Executes the setting of the axis origin.
  *  (3) Soft limit setting  
      - Will be automatically executed after the axis origin setting.
  *  (4) Squeezing force - current table setting 
      - Automatic change to the menu for the setting will occur.

In the case of automatic setting of the servo gun's default setting, the servo gun's '**encoder offset compensation**' position and '**axis origin compensation**' position are automatically recognized, allowing the '**encoder offset compensation**', '**axis origin compensation**' and '**soft limit setting**' to proceed at the relevant positions. When it comes to automatic setting of the servo gun's default setting, the '**squeeze force - current table setting**' does not proceed automatically. Please refer to the chapter [2.3.3 Squeeze force - current table setting](./2-3-3-servo-gun-force-current-table-tuning/README.md) for setting.

In the case of '**all automatic setting**', the servo gun moves to the position of the axis origin and performs confirmation with the user on the position of the axis origin. In this process, check the position of the moving electrode and the feedback current (1A or less). If the moving electrode are in a position of slightly contacting the fixed electrode, press '**Yes**' to continue the setting. If the feedback current is high or the moving electrode and the fixed electrode are not in contact, carry out fine adjustment using the jog key and then press 'Yes'. If you do not want automatic setting, please click '**No**' to end the setting.

<p align="center">
 <img src="../../_assets/image_76_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 2.6 Confirmation with the user on the position of the axis origin</p></em>
</p>

{% hint style="warning" %}
`Warning` If the servo gun has a stopper other than a metal material such as a bumper attached at the maximum opening position of the servo gun, it may be difficult to estimate the maximum opening position. It is recommended to perform setting after removing the stopper.
{% endhint %}

The configuration and functionality of the servo gun default setting screen is as follows.

<p align="center">
 <img src="../../_assets/image_62_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 2.7 Configuration of the default setting</p></em>
</p>

<br>

1. **Status**: Shows the current setting status of the servo gun (X: Before setting, O: Either complete or changed)

2. **Individual auto-set**:  Supports the function of automatically setting the checked items only, not all. Pressing the `[Checked auto setup]` button will allow automatic setting to be performed only for the checked items.

3. **Manual setting**: Moves to the screen for setting the relevant items.  
    - Encoder offset compensation: Moves to the screen of `[F2: system] - 3: Robot parameter - 4: Encoder offset`
    - Axis origin setting: Moves to the screen of `[F2: system] - 3: Robot parameter - 2: Axis origin`
    - Soft limit setting: Moves to the screen of `[F2: system] - 3: Robot parameter - 3: Soft limit`
    - Squeeze force - current table setting: Moves to the screen of `[F2: system] - 4: Application parameter - 1: Spot welding- 7: Servo gun squeeze force tuning`

4. **Guide**: Indicates the current status of settings or the cause and measure in case of occurrence of an error.

5. **Monitoring**: Indicates the current status of settings and the position of the servo gun, the feedback current, the set values, etc.

6. `[All auto setup]`: Commands the execution of all automatic setting of all items

7. `[Checked auto setup]`: Automatically sets only the items that are designated as the items of individual automatic setting

8. **Execution stop**: Stops the setting that is in progress.
[__SOURCE](2-servo-gun-initial-setting/2-3-step-1-default-setting/2-3-2-manual-setting/README.md)
### 2.3.2 Manual setting

The procedure for manually performing the default setting of the servo gun is as follows.

1. Servo gun encoder offset setting
2. Servo gun axis orign setting
3. Servo gun soft limit setting

[__SOURCE](2-servo-gun-initial-setting/2-3-step-1-default-setting/2-3-2-manual-setting/1-servo-gun-encoder-offset-setting.md)
#### 2.3.2.1 Servo gun encoder offset setting

Normally, when the encoder data is changed because of replacement of the servo gun motor, etc., the origin of the encoder should be set at a position that can match the same mechanical position. In the case of the servo gun, the setting should be performed with the moving electrode in the mechanically maximum open state.

The encoder compensation procedure for the axis of the servo gun is as follows.

(1) Manually release the brake of the axis of the servo gun and then open the moving electrode to the maximum.

<p align="center">
 <img src="../../../_assets/image_71_eng.PNG"></img>
 <em><p align="center">Figure 2.8 Servo gun's maximum open position</p></em>
</p>

<br>

(2) In the default setting screen of the'**Servo gun auto setting**' menu, press the `Manual setting` button of the '**Encoder offset compensation**' menu (Figure 2.9), or select the relevant servo gun axis in  `[F2: system] - 3: Robot parameter - 4: Encoder offset` with the cursor and then press the `[Reset]` button. When the current encoder value becomes "**00400000**", press the `[F7: OK]` button. 

<p align="center">
 <img src="../../../_assets/image_36_eng.PNG" width=80%></img>
 <em><p align="center">Figure 2.9 Moving to the encoder offset compensation screen</p></em>
</p>
[__SOURCE](2-servo-gun-initial-setting/2-3-step-1-default-setting/2-3-2-manual-setting/2-servo-gun-axis-origin.md)
#### 2.3.2.2 Servo gun axis origin

In general, the axis origin of the servo gun should be set at the position where both the moving and fixed electrodes, with a new tip attached individually, meet each other. As most operations of the servo gun are performed with this axis origin as the reference, it is very important to carry out setting for this.

The axis origin setting procedure for the axis of the servo gun is as follows.

1) Manually operate the axis of the servo gun to bring it into the state as shown in the figure below.

<p align="center">
 <img src="../../../_assets/image_19_eng.PNG"></img>
 <em><p align="center">Figure 2.10 Position of the origin of the servo gun</p></em>
</p>

1) In the default setting screen of the '**Servo gun automatic setting**' menu, press the `Manual setting` button of the '**Axis origin setting**' menu (figure below), or select the relevant axis of the servo gun in `[F2: system] - 3: Robot parameter - 2: Axis origin` with the cursor and then press the `[Reset]` button. When the current position of the axis is indicated as 0.0 mm, input by selecting the `[F7: OK]` button. 


<p align="center">
 <img src="../../../_assets/image_80_eng.PNG" width="80%"></img>
 <em><p align="center">Figure 2.11 Moving to the axis origin screen</p></em>
</p>

[__SOURCE](2-servo-gun-initial-setting/2-3-step-1-default-setting/2-3-2-manual-setting/3-servo-gun-soft-limit.md)
#### 2.3.2.3 Servo gun soft limit

In general, the soft limit of the servo gun should be set to 'Minimum' while the moving electrode is fully open, and set to 'Maximum' while the moving electrode is at the closest position with all tips removed.

The soft limit setting procedure for the axis of the servo gun.

1. Manually operate the servo gun to bring it to the condition as shown in the figure below


<p align="center">
 <img src="../../../_assets/image_90_eng.PNG" ></img>
 <img src="../../../_assets/image_2_eng.PNG" ></img>
 <em><p align="center">Figure 2.12 Setting of the servo gun soft limit</p></em>
</p>

<br>

2. In the default setting screen of the '**Servo gun automatic setting**' menu, press the `[Manual setting]` button of the '**Soft limit setting**' menu (Figure below), or select the relevant axis of the servo gun in `[F2: system] - 3: Robot parameter - 3: Soft limit` with the cursor and then press the `[Reset]` button. If the indication is performed normally, input by selecting the `[F7: OK]` button.

<p align="center">
 <img src="../../../_assets/image_41_eng.PNG" width="80%"></img>
 <em><p align="center">Figure 2.13 Moving to the servo gun soft limit setting screen </p></em>
</p>


[__SOURCE](2-servo-gun-initial-setting/2-3-step-1-default-setting/2-3-3-servo-gun-force-current-table-tuning/README.md)
### 2.3.3 Servo gun squeezing force - current table tunning

To squeeze the various servo guns, which are to be installed to the robot, with the desired squeezing force, it is necessary to make the current supplied to the servo gun correspond to the generated squeezing force. For this, our company provides a servo gun squeezing force - current table. It is necessary to tune this table to match with the servo gun. The accuracy of this tuning determines the accuracy of the servo gun squeezing force. In consideratin of it, tuning must be performed before using the servo gun.

To use this function, it is necessary to select five representative values among the squeezing forces to be used. Tuning the servo gun squeezing force - current table is a process to find the currents that match with these five representative squeezing forces. This table can vary depending on the posture of the servo gun, so it is necessary to perform tuning for each case of when the direction of the moving electrode is in the gravity direction and in anti-gravity direction, and, through this method, squeezing can be performed with high accuracy in various postures of the servo gun.

Our company provide manual mode for the tuning of the servo gun squeezing force - current table.

*   Tuning in manual mode

    Tuning can be performed regardless of the communication with the squeezing force gauge, and the user can directly tune the table by inputting the measured squeezing force.

[__SOURCE](2-servo-gun-initial-setting/2-3-step-1-default-setting/2-3-3-servo-gun-force-current-table-tuning/1-manual-tuning-mode.md)
#### 2.3.3.1 Manual tuning mode

The manual tuning mode is a function to manually perform the servo gun squeezing force - current table setting. After the servo gun squeezing occurs, if the user directly inputs the measured squeezing force by using the teaching pendant, the optimal command current will be automatically calculated. This process should be repeated to increase the accuracy. The accuracy can be verified by the degree of convergence and test squeezing.

The procedure for setting the servo gun squeezing force - current table in manual mode, recommended by our company, is as follows.

<p align="center">
 <img src="../../../_assets/image_84_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.14 Servo gun manual tuning screen</p></em>
</p>
 

1. Set the direction of the moving electrode that needs tuning (gravity or anti-gravity).

2. With the `[SHIFT]` key + `[Servo gun manual pressure]` button or by jogging the axis of the servo gun, bring the moving electrode to the position where it can contact the squeezing force gauge, and then measure the thickness of the squeezing force gauge (distance between electrodes).

3.  Input the measured thickness into the squeezing force gauge thicknes section shown at the upper part of the screen (distance between electrodes).

4. Input the desired representative value of the squeezing force that you want to set into the '**Set squeezing force**' section.

5. Squeeze the servo gun according to the line that indicates the set squeezing force with which you want to perform squeezing. (In the figure below, squeezing is performed with 100 kfg currently indicated with a green focus. svgun man press: `[CTRL]`,`[SHIFT]` + `[Servo gun manual pressure]`)

6. Input the squeezing force measured with the squeezing force gauge into the '**Measured squeezing force**' section.

7. Repeat steps 3-6 for all set squeezing forces.

8. After completing the inputting, press the `[Command current calculation]` button to calculate the command current that matches the set squeezing force.

9. When necessary to check the degree of convergence and perform repetead calculation of the command current through test squeezing, repeat steps 3-8.

10. If you want to calculate only the command current for a specific squeezing force, input the measured squeezing force and then execute the `[Command current individual calculation]` process.

11. Save the current setting by pressing `[Save]`. After that, change the direction of the moving electrode and then repeat steps 1-8 above.

</br>

To squeeze the servo gun, you should press `[SHIFT]` + `[Servo gun manual pressure]`  or `[CTRL]` + `[Servo gun manual pressure]`. Considering that with the `[CTRL]` + `[Servo gun manual pressure]`, you can perform controlling in the same manner as the automatic mode does, it is recommended to use `[CTRL]` + `[Servo gun manual pressure]`. 

The figure below is a screen showing the state after performing `[command current calculation]` twice. If the degree of convergence is low enough, it is needed to carry out squeezing with the set squeezing force and check the difference with the measured pressure, and then decide whether to continute to proceed.

At least one measured squeezing force should be entered for the command current calculation. If the initial command current exceeds the range where the servo gun can perform squeezing, you can reset the initial value by inputting only one or two measured squeezing forces and then performing the 'command current calculation.' If the command current calculation is performed without inputting all of the measured squeezing forces, the overall accuracy will be lower. Considering it, it is recommended to perform 'command current calculation' after inputting all measured squeezing forces, except for the case of resetting the initial command current.

The explanation for the setting items is as follow.

*   **Direction of the moving electrode**

    This is the direction of the moving electrode of the servo gun currently being tuned. The direction should be set once each for the direction of gravity direction of anti-gravity direction.
*   **Set squeezing force**

    This is the representative value of the squeezing force that is to be used. This is for finding the command current corresponding to the set squeezing force.
*   **Measured squeezing force**

    This is the squeezing force measured when squeezing is performed with the current command current. The user should input the value directly by using the squeezing force gauage.
*   **Command current**

    This is the command current corresponding to the currently set sequeeze force.
*   **Degree of convergence**

   This value is the amount of variation of the calculated command current compared to the previous command current after the current calculation is performed. The lower this value, the higher the accuracy of the tuning of the squeezing force.
*   **Permissible error for the set squeezing force**

    This is the squeezing force permissible error among the servo gun parameters and can be used to check the current state after the test squeezing.
*   **Distance between electrodes**

    This allows you to monitor the distance between the electrodes of the servo gun (possible to monitor the state of squeezing and opening).
*   **Count of repeated calculations**

    This is the number of times the command current has been updated by pressing the `[Command current calculation]` button so far. If the degree of convergence does not decrease after several repetitions, use the `[Command current individual calculation]` button or check the state of the squeezing force gauge and servo gun.
*   **Measured currrent**

    This is the currently measured current and will be monitored in a way that it can get close to the command current when squeezing is performed.

<br>

{% hint style="info" %}  
The operation by selecting `[CTRL]` key + `[Servo gun manual pressure]` button will work until the squeezing is completed with one execution, making it impossible to stop the operation by releasing the button in the middle. Therefore, stopping the squeeze operation requires you to release the enable switch or press the emergency stop button. Also, if the squeezing force gauge thickness is different from the actual value, the squeezing force will be different in automatic mode. So please input the correct value.

You can set and operate the servo gun using the function buttons on the right side of the current screen. The related settings and operations are as follows.

* `[SHIFT]` + `[Servo gun wide opening]`: Opens the servo gun wide (by the specified opening distance).
* `[SHIFT]` + `[Servo gun narrow opening]`: Opens the servo gun narrowly (by the specified opening distance).
* `[SHIFT]` + `[Servo gun manual pressure]`: Squeezes the servo gun using the squeezing force at the current cursor position.
* `[CTRL]` + `[Servo gun wide opening]`: Sets the distance for servo gun wide opening.
* `[CTRL]` + `[Servo gun narrow opening]`: Sets the distance for servo gun narrow opening.
* `[CTRL]` + `[Servo gun manual pressure]`: Squeezes the servo gun using the squeezing force at the current cursor position and applies the same control as in automatic mode.

{% endhint %}
[__SOURCE](2-servo-gun-initial-setting/2-3-step-1-default-setting/2-3-3-servo-gun-force-current-table-tuning/2-auto-tuning-mode.md)
#### 2.3.3.2 Auto tuning mode

This function is used to automatically set the servo gun squeezing force-current table.
To use this function, data communication between the squeezing force gauge and the robot controller must be available. Please make sure to check whether the selected squeezing force gauge is supported before use.


<p align="center">
 <img src="../../../_assets/image_25_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.14-1 Servo Gun Auto Tuning Screen</p></em>
</p>

<br>


Before using this function, position the squeezing force gauge on top of the fixed electrode as shown in the figure above, and manually move the moving electrode to bring it into contact with the gauge.

Then, enter the servo gun squeezing force-current table auto tuning setting screen and press the `[Execute]` button to start tuning.

During auto tuning, the moving electrode repeatedly moves several times. Therefore, the process must be carried out in manual mode with the motor turned ON. (If the motor is OFF, the process will stop.)

If you need to forcibly stop the tuning during operation, press the `[Clear]` button. After completing the tuning, perform test squeezing for each force level. If there are any accuracy issues, repeat the tuning process.


<br>


The settings are described below:

 -  Squeeze system maker
Select the manufacturer of the squeezing force gauge to be used.

 - Serial port  
Select the number of the connected serial port.

 - Direction of moving tip
Select whether the moving direction of the servo gun electrode is in the gravity direction or the anti-gravity direction.

 - Iteration number 
Set the number of repetitions for auto tuning to reduce variation in the commanded current. (1-10)

 - Commanded Squeeze[kgf]  
Set the desired squeezing force range in five levels for the table.
[__SOURCE](2-servo-gun-initial-setting/2-4-step-2-application-setting/README.md)
# 2.4 Step 2. Application setting

When the default setting is completed, the application setting can be performed. The application setting is the item that can be performed after the **squeezing force - current table tuning**. It consists of a procedure for setting the reference position for the gun search, a procedure for estimating the amount of the servo gun arm deflection during the squeeze operation, and a compensation procedure for accurate measurement of the panel thickness.

The application setting consists of three items as shown in the figure below.

<p align="center">
 <img src="../../_assets/image_58_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.15 Servo gun application setting screen</p></em>
</p>

<br>

1. **Gun search**
     * Sets the reference position for measuring the consumption amount of the tip and checks the consumption amount once.
     * For manual setting, refer to [4.1 Gun search](../../4-work-teaching/4-1-gun-search/README.md).

2. **Gun arm deflection amount compensation**
      * The gun arm deflection amount compensation should be set to compensate for the gun arm deflection that occurs when the servo gun performs squeezing. Sets the deflection amount according to the squeeze force set in the squeezing force - current table.
      * For manual setting, press the Manual setting button in the figure above, or, in the screen of `[F2: system] - 4: Application parameter - 1: Spot welding - 2: Welding gun parameter`, set the gun number that needs to be set and then press `[Advanced condition]` to enter.

3. **Panel thickness measurement compensation**
      * The panel thickness measurement compensation is a setting to improve the accuracy of the panel thickness measured with the ThickCheck command.
      * For manual setting, press the Manual setting button in the figure above, or, in the screen of `[F2: system] - 4: Application parameter - 1: Spot welding - 2: Welding gun parameter`, set the gun number that needs to be set and the press the `[Advanced condition]` button to enter.

Among spot setting items, the 'gun search' setting is essential. If 'gun search' is not set, it is impossible to execute and teach commands related to spot welding (for example, spot gn=1,...). On the other hand, **gun arm deflection amount compensation** and **panel thickness measurement compensation** has nothing to do with the execution and teaching of commands related to spot welding, but are necessary settings for accurate operation and accurate panel thickness measurement.

The application setting can be progressed in automatic setting and manual setting.

(1) Automatic setting  

   * The servo gun automatically moves to execute **gun search**, **gun arm deflection amount compensation** and **panel thickness measurement compensation**. All items of the application setting can be performed automatically.  
  
(2) Manual setting

   * The user directly performs **gun search** and inputs the **gun arm deflection amount compensation** and **panel thickness measurement compensation** values.  

[__SOURCE](2-servo-gun-initial-setting/2-4-step-2-application-setting/1-auto-setting.md)
### 2.4.1 Automatic setting

Progress the automatic setting of the application setting of the servo gun by pressing the `[All auto setup]` button. The moving electrode of the servo gun moves automatically. In addition, the set values are affected by the squeezing force, so the following conditions must be satisfied.

* Moving and fixed electrodes with new tipes attached
* No worker around the servo gun
* No workpiece between the moving electrode and fixed electrode
* Manual mode
* Motor on
* Completion of the servo gun's default setting (step 1) 


In the case of `[All auto setup]`, the following procedures will proceed automatically.

1. Gun search
   * Gun search will be performed while servo gun squeezing occurs two times.
   * First time: 'Gun search reference position record' valid
   * Second time: 'Gun search reference position record' invalid 
2. Gun arm deflection amount compensation
   * Gun arm deflection amount compensation will be performed while servo gun squeezing occurs five times.
3. Panel thickness measurement compensation  
   * Gun arm deflection amount compensation will be performed while servo gun squeezing occurs five times.

{% hint style="info" %}
The gun search that can be performed through '**automatic setting**' is only for gun search 1. When using other gun searches other than gun search 1, you should refer to [4.1 Gun search](../../4-work-teaching/4-1-gun-search/README.md).  
{% endhint %}

In the case of 'all automatic setting', the 'gun arm deflection amount compensation' and 'panel thickness measurement compensation' will be performed at the same time, so the servo gun performs squeezing only five times. For execution of 'gun search', the squeezing force and gun search speed should be designated. If you press the `[Gunsea cond setup]` button, the squeezing force and moving speed that will be used during gun search can be set as shown in the figure below.


<p align="center">
 <img src="../../_assets/image_22_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.16 Gun search condition setting screen</p></em>
</p>

{% hint style="info" %}
In the case of '**gun arm deflection compensation**' and '**panel thickness measurement compensation**', it is difficult to manually measure and fill in the values, so it is recommended to use automatic setting.

The 'gun arm deflection amount compensation' value is a value used instead of the 'gun arm deflection amount/100 kgf\[mm]' among the servo gun parameters. When the 'gun arm deflection amount compensation' value is set, the already set 'gun arm deflection amount/100 kgf\[mm]' will not be used. On the contrary, if a 'gun arm deflection amount compensation' value is not set, the 'gun arm deflection amount/100 kgf\[mm] will be used.'
{% endhint %}

The configuration and functionality of the servo gun application setting screen is as follows.

<p align="center">
 <img src="../../_assets/image_55_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.17 Servo gun applicaiton setting screen</p></em>
</p>


<br>

1. **Status**: Shows the current setting status of the servo gun (before setting, complete or changed).

2. **Individual auto-set**: Supports the function of automatically setting the checked items only, not all. Pressing the `[Checked auto setup]` button will allow automatic setting to be performed only for the checked items.

3. **Manual setting**: Moves to the screen for setting the relevant items
     *   Gun arm deflection amount compensation  
         Automatically moves to the screen of `[F2: system] - 4: Application parameter - 1: Spot welding - 3: Welding gun parameter`
     *   Panel thickness measurement compensation  
         Automatically moves to the screen of `[F2: system] - 4: Application parameter - 1: Spot welding - 3: Welding gun parameter`

4. **Guide**: Indicates the current status of settings or the cause and measure in case of occurrence of an error.

5. **Monitoring**: Indicates the current status of settings and the position of the servo gun, the feedback current, the set values, etc.

6. `[All auto setup]`: Commands the execution of all automatic setting of all items.

7. `[Checked auto setup]`: Automatically sets only the items that are designated as the items of individual automatic setting.

8. **Execution stop**: Stops the setting that is in progress.

9. **Gun search condition setting**: Sets the speed and squeeze force for gun search.

[__SOURCE](2-servo-gun-initial-setting/2-5-step-3-setting-check.md)
# 2.5 Step 3. Setting check

When the application setting is completed, you can check the setting performed so far through the 'setting check' procedure. The setting check procedure can be executed only when the default and application settings are completed.

 As shown below, When '**Step 0. Pre-inspection**', '**Step 1. Default setting**', and '**Step 2. Application setting**' are completed, press the 『**Proceed with the prior-to-setting items**』 key or bring the focus onto the '**Step 3. Setting check**' section and then press the Enter key to progress the setting check procedure.


<p align="center">
 <img src="../_assets/image_21_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.18 Servo gun setting check screen</p></em>
</p>

>The setting check will proceed while the servo gun is moving, so the following conditions must be satisfie.
>
>* Attachment of a tip that is in the same state as the tip used for the setting (impossible to check correctly if a new tip is attached and tip dressing is performed)
>* No worker around the servo gun
>* No workpiece between the moving electrode and fixed electrode
>* Manual mode
>* Motor on
>* Completion of the default setting of the servo gun
>* Completion of the application setting of the servo gun

When the setting check proceeds as the above conditions are satisfied, the screen changes to the 'Application Setting' screen to make it possible to monitor the movement status of the servo gun.

When the 'setting check' is completed, the error estimated during verification will be displayed. Considering that the displayed value is an error, if a value close to 0 is indicated, the setting can be regarded as normal. If the error is a value greater than zero, the setting should be performed again or it is needed to check for any change with the servo gun or surrounding environment. If the setting check result is satisfactory, press 'Yes' to end the 'setting check' procedure. If the result is unsastisfactory, press 'No' to perform resetting or check the servo gun or surrounding environment.

[__SOURCE](2-servo-gun-initial-setting/2-6-step-4-signal-setting.md)
# 2.6 Step 4. Signal setting

Step 3. When Step 3. 'Setting check' is completed, it is now possible to move and squeeze the servo gun normally. However, for spot welding, it is necessary to set the inputs and outputs of the spot welding machine signals and other signals. In 'Signal setting', input and output signals related to spot welding can be set.

As shown in the figure below, move the cursor to '**Step 4. Input signal setting**' or '**Step 4. Output signal setting**' and then press the \`Enter` key or, while previous items are completed, if you press the 『**Proceed with the prior-to-setting items**』 key, you can enter the screen for setting relevant items.

<p align="center">
 <img src="../_assets/image_85_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.19 Servo gun signal setting</p></em>
</p>

<br>

1. **Input signal setting**
       * Refer to the chapter [5.4 Input signal assignment](../5-spot-weld-parameter/5-4-input-signal-assign.md). 
2. **Output signal setting**
       * Refer to the chapter [5.5 Output signal assignment](../5-spot-weld-parameter/5-5-output-signal-assign.md).
 


[__SOURCE](3-Related-functions/README.md)
# 3. Related functions


[__SOURCE](3-Related-functions/3-1-monitoring/README.md)
# 3.1 Monitoring

Various current data and setting states that are used in spot welding are provided to the user in a way that they can be monitored. The monitoring screen related to spot welding is as follow.

* Spot welding gun axis data
* Spot welding input and output signals
* Spot welding operation information
[__SOURCE](3-Related-functions/3-1-monitoring/1-spot-gun-axis-data.md)
### 3.1.1 Spot gun axis data

This indicates the data of the currently selected spot gun in real time.  
(`[pane layout] - [F1: select] - spot gun data`)


<p align="center">
 <img src="../../_assets/image_18_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.1 Spot monitoring pane</p></em>
</p>

<p align="center">
 <img src="../../_assets/image_89_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.2 Spot gun data monitoring</p></em>
</p>

<br>

*  Current data (servo gun)

      Cur indicates the feedback current of the axis of the servo gun and Cmd indicates the current limit command value (A).

*  Squeezing force data (servo gun)

     The command current and feedback current are converted into squeezing force and displayed using the 'squeezing force - current table' of the welding gun parameter. Cmd indicates the command squeezing force and Cur indicates the feedback squeeze.

*  Actual squeezing force during weling (servo gun)

     Indicates the average squeezing force from the point of the matching of the squeezing force to the time of opening.

*  Distance between electrodes (servo gun)

     Indicates the distance (mm) from the axis origin to the moving electrode.

*   Electrode consumption amount (servo gun, equalizerless gun)  

     Inidicates the consumption amount (mm) detected through gun search. (In the case of the equalizerless gun, only the consumption amount of the fixed electrode is managed.)

*  Gun search status (servo gun, equalizerless gun) 

     Indicates whether gun search is performed.

*   Welder number

     Indicates the welder number corredponding to the currently selected gun number.

*  SvClamp (servo gun)

     Indicates the status of the clamping operation of the currently selected gun.

[__SOURCE](3-Related-functions/3-1-monitoring/2-input-output-signal.md)
### 3.1.2 Input and output signals

The input/output status of the assigned signals related to spot welding is organized and monitored for convenient use.
(`[pane layout] - [F1: select] - spot i/o data`)

<br>

<p align="center">
 <img src="../../_assets/image_40_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.3 Spot welding input/output signal monitoring</p></em>
</p>
[__SOURCE](3-Related-functions/3-1-monitoring/3-operating-info.md)
### 3.1.3 Information of the operating time

This allows you to check the information of the operating time related to the spot welding.

(`[pane layout] - [F1: select] - spot run info.`)

<br>

<p align="center">
 <img src="../../_assets/image_91_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.4 Spot welding operation information monitoring</p></em>
</p>

<br>

*   **Total (after initialization)**

      Indicates the operation time and welding count of each welder since initialization of the system.
*   **Total (after input of power)**

     Indicates the operation time and welding count of each welder since input of the power.
*   **Latest cycle**

     Indicates the operation time and welding count of each welder of the immediately preceeding cycle.
*   **Current cycle**

     Indicates the operation time and welding count of each welder of the current cycle.

---
-	Spot welding operation information clearing

When the spot welding operation information window is activated, the `[Clear]` button will be displayed. Pressing the button will bring up a dialog box for clearing the operation information as shown in Figure 3.5.

<p align="center">
 <img src="../../_assets/image_92_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.5 Spot welding operation information initialization screen</p></em>
</p>
[__SOURCE](3-Related-functions/3-1-monitoring/4-state-flag.md)
### 3.1.4 State flag

Various necessary states related to spot welding will be indicate as shown in the screen below.

<p align="center">
 <img src="../../_assets/image_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.6 Indication of spot welding related states</p></em>
</p>


-  Welding condition and welding sequence (panel thickness)

    - Indicates the currently selected welding condition number and welding sequence number.
    - Indicates the currently set panel thickness. Accurate setting is required because the position of the axis of the servo gun will be automatically created based on the set panel thickness during the recording of the welding steps of the servo gun. It is also possible to perform manual setting with R220. When the recording of the welding steps is performed after the manual squeezing operation, the setting will be automatically performed by taking into consideration the current position of the servo gun.

-  Tool number

    - Indicates the tool number corresponding to the currently selected gun number. In other words, if you change the gun number, the tool number will automatically change to the tool number set in `[F2: system] - 4: Application parameter - 1: Spot welding - 2: Welding gun parameter`.

-  Gun number

    - This indicates the currently selected gun number, numbers of multiple guns, and servo gun separation state (![](<../../_assets/image_39_eng.PNG>)). For example, if G5 and G6 are indicated, it means that stationary guns G5 and G6 are selected for simultaneous welding. In addition , there is a mark of a lock, so you can konw that the servo gun is disconnected. 


[__SOURCE](3-Related-functions/3-2-servo-gun-simple-maintenance.md)
# 3.2 Simple maintenance of the servo gun

This provides support to simply conduct a series of settings to restart the servo gun from a single window after repairing it. When you press the \`CTRL`+\`GUN` keys on the initial screen, a dialog box for simple maintenance will be displayed.

<p align="center">
 <img src="../_assets/image_26_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.7 Simple maintenance of the servo gun</p></em>
</p>

>*   **Serial encoder reset**  
>    Executes the "**encoder reset**" or "**error clear**" operation for the serial encoder attached to the servo gun motor. Power must be supplied again for the changed setting to be applied. When "encoder reset" is performed, the encoder information will be initialized after that, requiring you to newly perform the encoder offset setting, axis origin setting, and gun search reference position recording.
>*   **Encoder offset**  
>    Sets the encoder origin of the axis of the servo gun.  It should be set at the position where the moving electrode is maximally opened through the releasing of the brake manually.
>*   **Axis origin**  
>    Sets the axis origin of the servo gun. The axis origin of the servo gun should be set at the poistion where electrodes are in contact with each other after new electrodes are installed.
>*   **Gun search execution**  
>    Executes the gunsea command only by operating the axis of the servo gun at the current position.
>*   **Welding execution**  
>    Executes the spot command only by operating the axis of the servo gun at the current position.

[__SOURCE](3-Related-functions/3-3-user-key.md)
# 3.3 User keys

This is a description of the user keys related to spot welding. There is a button for the user keys at the bottom right of the initial main screen. Each time you press the button, the registered menu changes. Press each user key related to spot welding twice to enter the relevant menu.


<p align="center">
 <img src="../_assets/image_33_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.8 Spot welding user keys</p></em>
</p>


>*   **Servo gun wide opening**  
>    Manually moves the servo gun to the wide opening position.
>*   **Servo gun manual closing**  
>    Manually moves the servo gun to the narrow opening position.
>*   **Servo gun manual squeezing**  
>    Manually spueezes the servo gun. 
>*   **Welding condition change**  
>    Manually changes the currently selected welding condition number.
>*   **Welding sequence change**  
>    Manually changes the currently selected welding sequence number.

[__SOURCE](3-Related-functions/3-4-weld-gun-manual-open-close-pressure.md)
# 3.4 Welding gun manual closing and squeezing

The procedure for manual closing and squeezing of the welding gun is as follows.

</br>

1. Check whether the mode is manual. In the case of the servo gun, input the operation preparation signal to drive the axis of the servo gun. 
2.  Select the gun number for the manual closing or squeezing operation. The method to select a gun number is as follows.

    | **Gun type** |   Whether to change  | R code |
    | :-----: | :---------: | :--------------: |
    | single gun |    For change of the welding gun  | R358 (welding gun connection/separation) |
    |    single gun     | Not for change of the welding gun |   R210 (welding gun selection)  |
    | Multiple guns |      -       |  R214 (selection of guns for simultaneous welding) |


3.  Check whether the following user keys are registerd.



    |       **Wide opening**  |       **Narrow opening**    | **Manual squeezing**   |
    | :--------------------------------------: | :--------------------------------------: | :--------------------------------------: |
    | <img src="../_assets/image_86_eng.PNG"></img>|<img src="../_assets/image_16_eng.PNG"></img> | <img src="../_assets/image_43_eng.PNG"></img> |


1.  When you press the `[SHIFT]+[user key]` at the same time, the following operation will be performed. When multiple guns are selected, all of the selected guns will operate in the same way.

    |                  **Servo gun**                 |
    | :--------------------------------------: |
    | <img src="../_assets/image_13_eng.PNG"></img> |



The servo gun has the following characteristics during the manual closing and squeezing operations.

* The servo gun automatically stops at the wide opening position, the narrow opening position, and the position where the squeezing force reaches the set value.
* The moving speed is the speed entered at **Step FWD/BWD maximum speed** by `[F7: cond.set]`.
* If the set squeezing force is small, the servo gun will not move even when it is operated. Considering it, set a sufficient squeezing force (R211: Squeezing force setting).
* When it comes to multiple guns, if there is a difference in the moving distance between two guns, the gun that reaches first will stop while the other gun will stop after moving as much as the remaining distance.

<p align="center">
 <img src="../_assets/image_53_eng.PNG"></img>
 <em><p align="center">Figure 3.9 Spot gun manual operation</p></em>
</p>

[__SOURCE](4-work-teaching/README.md)
# 4. Work teaching


[__SOURCE](4-work-teaching/4-1-gun-search/README.md)
# 4.1 Gun search

Gun search is a function to measure the consumption amount of an electrode. Use this function when you need to re-measure the consumption amount of the electrode after polishing it through tip dressing or after replacing the existing tip with a new one. If  the gun type is servo gun or equalizerless gun, the gun automatically compensates the squeezing position as much as the consumption amount when executing the spot command, which makes it essential to manage the consumption amount and shows that the accuracy of the consumption amount affects the welding quality.

 The types of gun search provided by our company and their simple characteristics are as follows.

* gunsea
  + This is the gun search function for a servo gun and is executed with one squeezing operation.
  + The total consumption amount of the moving and fixed electrodes is measured and distributed according to the designated ratio.
  + This function is used if the consumption ratio between the moving electrode and fixed electrode is the same or fixed.

* gunsea 2
  + This is the gun search function for a servo gun and is executed with one squeezing operation and one moving operation.
  + The total consumption amount of the moving and fixed electrodes is measured (one squeezing operation) and then the moving electrode consumption amount is measured separately.
  + This function is used if the consumption ratio between the moving electrode and fixed electrode is not fixed.

* igunsea
  + In the same way as gun search  2, this is the gun search function for a servo gun and executed with one squeezing operation and one moving operation. However, the moving electrode consumption amount is measured using a sensor.
  + The total consumption amount of the moving and fixed electrodes is measured (one sequeezing operation) and then the moving electrode consumption amount is measured (one moving operation) separately.
  + This function is used if the consumption ratio between the moving electrode and fixed electrode is not fixed.

* egunsea
  + This is the gun search function for an equalizerless gun and, in the same way as the igunsea function, the consumption amount is measured by receiving a sensor signal.

</br>
The gun search state can be checked from the /Monitoring/Spot section.

[__SOURCE](4-work-teaching/4-1-gun-search/1-execute-order.md)
### 4.1.1 Execution sequence

<p align="center">
 <img src="../../_assets/image_23_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.1 Gun search execution sequence of the servo gun</p></em>
</p>
[__SOURCE](4-work-teaching/4-1-gun-search/2-command-sentence-about-gun-search.md)
### 4.1.2 Commands related to gun search


(1) gunsea

 This is a statement to be used for executing gun search 1 when the gun type is servo gun or executing gun search 2 by using the squeezing force.


```gunsea gun=<gun number>,sea=<search number>,pre=<squeezing force>,spd=<search speed>```

|   **Item**   | <p align="center">   **Content**   </p>| 
|:--------: | ----------------------------------------------------------------- |
|   **Gun number**  |  the gun number to measure the tip length (array[ ] for multi inputs)  | 
|  **Search number**  |  the gun search 1 operation or gun search operation 2             |
|   **Squeezing force**  |  the command squeezing force for detection of squeezing force matching.(array[ ] for multi inputs)       |
|  **Search speed**  |the operation speed of the gun's axis for the search operation (10 mm/s recommended)|


<br>

{% hint style="info" %}
[Use example]    

A case of executing gun search 1 for the servo guns 5 and 6 with the equalizing force 100 kgf and 200 kgf respectively

 --> ```gunsea gun=[5,6],sea=1,pre=[100,200],spd=50```

{% endhint %}

---
(2) igunsea

This is a statement to be used for executing gun search 2 based on the input signal when the gun type is servo gun.

```igunsea gun=<gun number>,spd=<search speed>,di=<input signal>```

|  **Item**  |   <p align="center">   **Content**   </p>  |
| :------: | ---------------------------------------------------------------------- |
| **Gun number** |  the gun number to search                  |
| **Search speed** | the operation speed of the gun's axis for the search operation (10 mm/s recommended)|
| **Input signal** |  the input signal address for the reception of the phottube output    |

</br>

---
(2) egunsea

This is used when the gun type is equalizerless gun.

```egunsea gun=<gun number>,spd=<search speed>,dist=<search distance>,di=<input signal>```

|  **Item**  |  <p align="center">   **Content**   </p>   |
| :------: | ---------------------------------------------------------------------- |
| **Gun number** |   the gun number to search                                                            |
| **Search speed** | the operation speed of the gun's axis for the search operation (10 mm/s recommended)  |
| **Input signal** |  the input signal address for reception of the phot tube output |     
[__SOURCE](4-work-teaching/4-1-gun-search/3-gun-search-standard-position-record.md)
### 4.1.3 Gun search reference position record

The consumption amount of an electrode is measured based on an unconsumed new tip. Therefore, the process of registering the reference position with a new tip is absolutely necessary at least once in the beginning, and this is called gun search reference position record.

{% hint style="info" %}
**The gun search reference position must be recorded at least once before the execution of gun search**
{% endhint %}

 When it comes to the method of recording a gun search reference position, new tips should be attached first and then the recording should be executed according to the following procedures.


<p align="center">
 <img src="../../_assets/image_51_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.2 Use environment setting screen</p></em>
</p>


>1. Set 'Gun search reference position record' to 'enable'.
>2. Execute the created gun search program. In the spot monitoring screen, the state of the gun search will be initialized to 'incomplete'.
>3. Set 'Gun search reference position record' to 'disable'. After that, the amount of variation compared to the reference position will be calculated as a consumption amount by using the gun search program.

[__SOURCE](4-work-teaching/4-1-gun-search/4-1-4-gun-search-movements-by-gun-type/README.md)
#### 4.1.4 Gun search operation by gun type


[__SOURCE](4-work-teaching/4-1-gun-search/4-1-4-gun-search-movements-by-gun-type/1-servo-gun.md)
#### 4.1.4.1 Servo gun

The gun search function of the servo gun is initially set in a way that the total electrode consumption amount reflects 50% of each of the fixed electrode consumption amount and moving electrode consumption amount. Therefore, the electrode consumption amount can be calculated by using only gun search 1. If you want to calculate the consumption amounts of the fixed and moving electrodes respectively, please refer to the description of gun search 2.

{% hint style="info" %}
If the set value of **Moving electrode consumption amount/Total consumption amount (%)** is "0", the gun search 2 operation must be performed. If it is not "0", the total consumption amount will be distributed according to the set ratio through the gun search 1 operation.
{% endhint %}


<br>

(1) Gun search 1  
  - Measures the total electrode consumption amount by making the moving electrode squeeze the fixed electrode.

<p align="center">
 <img src="../../../_assets/image_47_eng.PNG"></img>
 <img src="../../../_assets/image_7_eng.PNG" width="55%"></img>
 <em><p align="center">Firgure 4.3 Gun search 1</p></em>
</p>


1. The servo gun moves to the record position of the step.  

2. The fixed electrode is squeezed with the moving electrode until the set squeeze force is reached.  

3.  When the squeezing force matching is detected, the total electrode consumption amount is measured and the opening operation is executed. Total electrode consumption amount = Squeezing force matching detection position  - gun search 1 reference position

4. The servo gun opens up to the record position of the step.  

5. In an environment where only gun search 1 is operating, the measured total electrode consumption amount is distributed according to the ratio between the moving electrode and fixed electrode as shown in the figure below. (default is 50 : 50.)

<p align="center">
  <img src="../../../_assets/image_70_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.4 Calculation of the electrode consumption amount through gun search 1</p></em>
</p>


(2) Gun search 2

- Measures the moving electrode consumption amount. The measurement can be performed by using a squeezing force or an external signal.

-   **By using a squeezing force**

    Measures the moving electrode consumption amount by making the moving electrode squeeze the calibration jig.

-   **By using an external signal**

    When the moving electrode moves to the position where the sensor is located and then the input from the sensor is detected, the moving electrode consumption amount is measured.

<p align="center">
 <img src="../../../_assets/image_29_eng.PNG"></img>
 <img src="../../../_assets/image_4_eng.PNG" width="55%"></img>
 <em><p align="center">Figure 4.5 Gun search by using a squeezing force</p></em>
</p>

<Br>

1. Movement to the record position of the step occurs.

2. The calibration jig is squeezed with the moving electrode through searching unitil the set squeezing force is reached.

3.  When the squeezing force matching is detected, the moving electrode consumption amount is detected and the opening operation is executed.   
    - Moving electrode consumption amount = Squeezing force matching detection position - reference position for gun search 2 that uses the squeezing force
    - Fixed electrode consumption amount = total consumption amount detected by gun search 1 - moving electrode consumption amount

4. When the opening is completed, the consumption amounts of the moving and fixed electrodes are updated. 




<p align="center">
 <img src="../../../_assets/image_79_eng.PNG"></img>
 <img src="../../../_assets/image_73_eng.PNG" width="55%"></img>
 <em><p align="center">Figure 4.6 Gun search 2 that uses an external signal input</p></em>
</p>

<Br>

1. Movement to the record position of the step occurs.  

2. The moving electrode approaches at the search speed and switches the phototube contact signal.  

3.  When a signal is detected by the photo tube, the moving electrode consumption amount is detected and the opening operation is executed.  
    - Moving electrode consumption amount = External signal detection position - reference position for gun search 2 that uses the external signal
    - Fixed electrode consumption amount = total consumption amount detected by gun search 1 - moving electrode consumption amount

4. When the opening is completed, the consumption amounts of the moving and fixed electrodes are updated.

[__SOURCE](4-work-teaching/4-1-gun-search/4-1-4-gun-search-movements-by-gun-type/2-eqless-gun.md)
#### 4.1.4.2 Equalizerless gun

As an equalizerless gun only manages the consumption amount on the fixed electrode, so the gun search function here measures the fixed electrode consumption amount.


<p align=center>
 <img src="../../../_assets/image_64_eng.PNG"></img>
 <img src="../../../_assets/image_34_eng.PNG" width="55%"></img>
 <em><p align="center">Figure 4.7 Gun search of an equalizerless gun</p></em>
</p>

<br>



1. The robot moves to the recorded position of the step.

2. The fixed electrode approaches at the search speed and activates the phototube contact signal.

3. When the phototube detects a signal, the fixed electrode consumption amount is measured and the opening operation is executed.

   Fixed electrode consumption  = sensor detection position - gun search recorded position

4. When the opening operation is completed, the fixed electrode consumption amount is updated.
[__SOURCE](4-work-teaching/4-2-spot-weld/README.md)
# 4.2 Spot welding

While the fixed and moving electrodes are squeezing, the current flows from the welder, allowing the spot welding to be performed.

[__SOURCE](4-work-teaching/4-2-spot-weld/1-spot-command-sentence.md)
### 4.2.1 Spot statement

The Spot command performs a series of operations required for spot welding, including gun pressing, weld standby, and opening.

</br>

### Description
  - Supports Servo Gun, EQ Gun, EQ-less Gun, and EQ-Brake Gun.
  - For multi-gun configurations, parameters are entered in an array format.
  - If the system is stopped before the spot welding process is completed and then restarted, the spot welding step is executed again.
  - When recording a step using the `[Record]` key, if the LED of the `[GUN]` key is turned on, the `spot` command is recorded together with the `move` command (one-touch recording method).
  - When recording a welding step:
     - Bring the fixed electrode into contact with the panel using jog operation.
     - Apply pressure to the panel using manual pressing.
     - Then record the Spot command using the one-touch recording method.  
       -> The panel thickness will be automatically set.
  - After the panel thickness has been set, bring the fixed electrode into contact with the panel using jog operation. Then, record the `spot` command using the one-touch recording method without performing manual pressing.  
-> The recorded position will automatically reflect compensation for both panel thickness and electrode wear.
  - When the gun type is set to Servo Gun, if a `spot` command exists during `[POS.MOD]`, the position is automatically corrected to include compensation for electrode wear.

<br>


### Grammar
```python
spot gun=<gun number>,cnd=<condition number>,seq=<sequence number>,pre=<pressure>,out=<output data>
```

</br>

### Parameters

<center>

|   Item    |       Content      | Note |
| :--------: |:---------: |:---------: |
|    Gun number    |  the welding gun number | mandatory |
|    Condition number   |  the welding condition |mandatory |
|  Sequence number  |  the welding sequence |mandatory |
|  Pressure value  |  the pressurization force value  |optional |
|  Output data  | the output value transmitted in 12-bit format |optional |

</center>

</br>

{% hint style="info" %}

\[Example of use\]  
- All parameters of  `spot` command can be entered in array format [ ] when using multiple guns.

{% endhint %}

{% hint style="info" %}
\[Example of use\]  
- When performing spot welding using servo guns 5 and 6 with welding conditions 7 and 8, welding sequences 9 and 10, and welding pressures of 100 kgf and 200 kgf, respectively.

  ```python
  spot gun=[5,6],cnd=[7,8],seq=[9,10],pre=[100,200]
  ```

{% endhint %}
[__SOURCE](4-work-teaching/4-2-spot-weld/4-2-2-weld-sequence-by-gun-type/README.md)
### 4.2.2 Welding sequence by gun type

The controller executes the `spot` statement in the program to make the welding work take place and the playback of the spot welding function may vary depending on gun type.

[__SOURCE](4-work-teaching/4-2-spot-weld/4-2-2-weld-sequence-by-gun-type/1-servo-gun.md)
### 4.2.2.1 Servo gun

If the gun type is servo gun, the spot welding function is played back as shown in the figure below.

<p align="center">
 <img src="../../../_assets/image_66_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.8 Playback motions of servo gun spot welding</p></em>
</p>


<br>


1. At the N-1 step position, the moving and fixed electrodes move away from their recorded positions by the moving electrode clearance and fixed electrode clearance, respectively.

2. Through the robot equalizing operation, the fixed electrode moves to the recorded position of the step, and the moving electrode moves to the recorded position while being shifted by the consumption amount.

3. The moving electrode performs the squeezing operation using the specified squeezing force. When the target squeezing force is reached, the welding execution signal is output together with the welding condition signal at that position.

4. When the welding completion signal (WI) is received, the moving and fixed electrodes open by their respective clearance amounts.

5. The system moves to the next step.
[__SOURCE](4-work-teaching/4-2-spot-weld/4-2-2-weld-sequence-by-gun-type/2-eqless-gun.md)
### 4.2.2.2 Equalizerless gun

If the gun type is equalizerless gun, the spot welding function is played back as shown in the figure below.

<p align="center">
 <img src="../../../_assets/image_5_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.9 Playback of spot welding by ann equalizerless gun</p></em>
</p>

<Br>


1. At the N-1 step position, the fixed electrode moves away from the recorded position by the fixed electrode clearance.

2. Through the robot equalizing operation, the fixed electrode moves to the recorded position of the step, and pneumatic pressure causes the moving electrode to squeeze the panel.

3. When the target squeezing force is reached, the welding execution signal is output together with the welding condition signal at that position.

4. When the welding completion signal (WI) is received, the fixed electrode moves away from the recorded position by the fixed electrode clearance, and the moving electrode moves to a position where pneumatic pressure is not supplied.

5. The system moves to the next step.
[__SOURCE](4-work-teaching/4-2-spot-weld/4-2-2-weld-sequence-by-gun-type/3-eq-gun.md)
### 4.2.2.3 Equalizer-fitted gun

If the gun type is equalizer-fitted gun, the spot welding function is played back as shown in the figure below.

<p align="center">
 <img src="../../../_assets/image_82_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.10 Playback of spot welding by an equalizer-fitted gun</p></em>
</p>

<br>



1. At the N-1 step position, the robot moves to the recorded position of the step.

2. The welding execution signal is output together with the welding condition signal.
The equalizing device causes the fixed electrode to squeeze the panel, and pneumatic pressure causes the moving electrode to squeeze the panel.

3. When the welding completion signal (WI) is received, the fixed electrode moves to a position where the equalizing device is inactive, and the moving electrode moves to a position where pneumatic pressure is not supplied.

4. The system moves to the next step.
[__SOURCE](4-work-teaching/4-3-servo-gun-tip-dressing/README.md)
# 4.3 Servo gun trip dressing


[__SOURCE](4-work-teaching/4-3-servo-gun-tip-dressing/1-condition-setting.md)
### 4.3.1 Condition setting

The tip dressing condition for the servo gun can be set in `[F2: system] - 4: Application parameter - 1: Spot welding - 4: Welding data (Cnd, Seq) - 4:Servo gun tip dressing condition` Refer to the relevant menus.

[__SOURCE](4-work-teaching/4-3-servo-gun-tip-dressing/2-type-of-motion.md)
### 4.3.2 Type of operation

To perform a tip dressing operation using the servo tip dressing condition, the welding sequence number in the `spot` statement must be designated as 64 as shown below.


<p align="center">
 <img src="../../_assets/image_77_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.11 Servo gun tip dressing operation</p></em>
</p>

<Br>

1. At the N-1 step position, the moving electrode moves away from the recorded position by the amount of the moving electrode clearance, and the fixed electrode moves away from the recorded position by the amount of the fixed electrode clearance.

2. The robot moves to the recorded position of the step.

3. The moving electrode performs the squeezing operation using the squeezing force set in the welding condition. When the target squeezing force is reached, the welding condition signal is output at that position. Whether the welding execution signal is also output at this time depends on the "Welding signal output" setting in the tip dressing condition.

4. After the configured tip dressing time has elapsed, the moving and fixed electrodes open by their respective clearance amounts.

5. The system moves to the next step.
[__SOURCE](4-work-teaching/4-4-servo-gun-open-position-record/README.md)
# 4.4 Servo gun opening position recording

The recording of the spot welding step of the servo gun is usually performed according to the following procedure.

1. Check that the state is the one-touch record state. (\[GUN] key LED turned on.)
2. Contact the fixed electrode of the servo gun to the workpiece.
3. Squeeze the moving electrode to the workpiece by performing manual squeezing operation.
4. Press the `[Record]` key to record the Spot statement together with the  step. -> Automatic registration of the panel thickness
5. Separate the moving electrode with a manual closing operation.
6. Movement to the next position occurs.

 Servo gun opening position recording is a procedure without the steps (3) and (5) above, making it possible to save a significant amount of time. For this, the controller should know the thickness of the panel to weld.

[__SOURCE](4-work-teaching/4-4-servo-gun-open-position-record/4-4-1-panel-thickness-registration/README.md)
### 4.4.1 Panel thickness registration

When it comes to the servo gun opening position recording, the position of the moving electrode will be calculated by using the pre-designated panel thickness, so the panel thickness should be registered. There are two provided methods of registering the panel thickness. One is that the user inputs it manually and the other is that the panel thickness is automatically registered while the panel is squeezed.

[__SOURCE](4-work-teaching/4-4-servo-gun-open-position-record/4-4-1-panel-thickness-registration/1-manual-input-method.md)
### 4.4.1.1 Manual input method

Execute "**R220: Set the panel thickness**" to input the panel thickness.


<p align="center">
 <img src="../../../_assets/image_14_eng.PNG" ></img>
 <em><p align="center">Figure 4.12 Panel thickness input</p></em>
</p>
[__SOURCE](4-work-teaching/4-4-servo-gun-open-position-record/4-4-1-panel-thickness-registration/2-auto-registration-method.md)
#### 4.4.1.2 Auto registration method

While the `[GUN]` key LED is turned on, perform manual squeezing and then press the `[Record]` key. Then the panel thickness will be automatically registered.

[__SOURCE](4-work-teaching/4-4-servo-gun-open-position-record/2-how-to-teaching.md)
### 4.4.2 How to teach

(1)  In a state that the panel thickness is registered, proceed with teaching while keeping the moving electrode open and only the fixed electrode in contact with the panel.



<p align="center">
 <img src="../../_assets/image_83_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.13 Method of working when the panel thickness is the same</p></em>
</p>

</br>

(2) When the panel thickness is changed, perform teaching after registering the panel thickness again.

[__SOURCE](4-work-teaching/4-5-servo-tool-change/README.md)
# 4.5 Servo tool change

The servo tool change function is used to connect and separate the robot R1 axis and welding gun if there are two or more guns to perform work in combination with the robot R1 axis. For more details, refer to [Servo Tool Change Function Manual](https://hrbook-hrc.web.app/#/view/doc-svtool-change/en/README?cont_model=${cont_model}).

[__SOURCE](4-work-teaching/4-5-servo-tool-change/4-5-1-environment-setting/README.md)
### 4.5.1 Environment setting

The environment setting for servo tool change can be progressed according to the following order.

A.   Setting the tool number and gun type corresponding to the gun number

B.   Setting the servo tool parameter

[__SOURCE](4-work-teaching/4-5-servo-tool-change/4-5-1-environment-setting/1-tool-number-gun-type-setting.md)
### 4.5.1.1 Setting of the tool number and gun type corresponding to the gun number

In the `[F2: system] - 4: Application parameter - 1: Spot welding - 2: Welding gun parameter` menu, set the gun type and tool number targeted for the servo tool change.

<p align="center">
 <img src="../../../_assets/image_24_eng.PNG" width="90%"></img>
 <em><p align="center">Figure 4.14 Addition of a spot gun</p></em>
</p>


The figure 4.14 shows a case in which four spot guns are set as below.

* **Gun1**: Welder 1, tool number 1, servo gun, additional axis 2 -> Required to set the servo tool parameters
* **Gun2**: Welder 1, tool number 2, servo gun, additional axis 1 -> Required to set the servo tool parameters
* **Gun3**: Welder 1, tool number 3, Eq gun, additional axis X -> Not required to set the servo tool parameters
* **Gun4**: Welder 1, tool number 4, servo gun, additional axis 1 -> Required to set the servo tool parameters

 In the case of s gun set as servo gun, among the targets for servo tool change, the servo tool parameters of the concerned servo gun should be set as shown in the next section.


<br>


{% hint style="warning" %}
 
 All welding guns used for servo tool change must use the same welder.
  
{% endhint %}
[__SOURCE](4-work-teaching/4-5-servo-tool-change/4-5-1-environment-setting/2-servo-tool-parameter-setting.md)
### 4.5.1.2 Servo tool parameter setting

 In the `[F2: system] - 4: Application parameter - 11: Servo tool change - 2: Servo tool parameter setting` menu, set the gun type and tool number targeted for the servo tool change.

If the gun targeted for servo tool change is a Servo Gun, the currently set additional axis parameters may differ from the parameters of the Servo Gun to be used. Therefore, the parameters of the Servo Gun to be used must be set.

The configured parameters will replace the values of the existing additional axis parameters, as shown in the figure below, when using another welding gun through the servo tool change function. Therefore, the same setting items as the additional axis parameters are used.

<p align="center">
 <img src="../../../_assets/image_67_eng.PNG" width="75%"></img>
 <em><p align="center">Figure 4.15 Application of the parameter for the additional axis during tool change</p></em>
</p>


The setting items of the parameter for the servo tool are mostly the same as the setting items of the parameter for the additional axis. You need to add the servo gun that you have set in the screen for setting the tool number and gun type corresponding to the gun number. When the OK button is clicked, the additional axis number corresponding to the gun number will be automatically set.

The Servo Tool parameter setting items are mostly the same as the additional axis parameter setting items. The Servo Gun set in the Gun Number-corresponding Tool Number and Gun Type setting screen must be added. When the `[OK]` button is pressed, the additional axis number corresponding to the gun number is automatically set.

<p align="center">
 <img src="../../../_assets/image_88_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.16 Additional axis parameter setting screen</p></em>
</p>
[__SOURCE](4-work-teaching/4-5-servo-tool-change/2-connection-separation-command.md)
### 4.5.2 Connection/disconnection commands 

In the servo tool change environment, connection/disconnection of the servo gun can be done in two ways as below. When the servo gun is connected, the gun number and tool number are automatically changed according to the set values, and when the servo gun is separated, the gun number and tool number are automatically changed to 0.

(1) R358

This is a function for servo gun change by using a R code, and can be used in the motor on state (the enable switch is on) in manual mode.

 - Operation = `R358 --> 1 --> 2`

| **Parameter** |   **#1**   | **#2** | 
| :------: | :--------: | :----: | 
|    Meaning    |    Connection/disconnection  |     Gun number     |
|   Setting value   | Connection=1, Disconnection=0 | The number of the gun targeted for change |

 - Example of use  

| Connection | Disconnection|
| :--: | :--:|
| Gun #2 connection |Gun #1 disconnection|
| `R358 + 1 + 2` | `R358 + 0 + 1` |
|  ![](../../_assets/image_108_eng.PNG) | ![](../../_assets/image_109_eng.PNG)  |

<br>

(2) toolchng

This is a function for welding gun change through the execution of a work program. 

```python
toolchng on/off/fixed,tg=<target guns for change>,is=<connection complete signal>,wait=<connection complete wait time>
```

<br>

|    parameter |       input       |     function     |   note   |
| :-----------: | :----------: | :---------: | :-----------: |
|     connection |       on       |      connection of the servo tool     |      |
|  disconnection |       off     |        disconnection of the servo tool   |      |
|  fixed change |       fixed      |      power-on tool change   | single motor multi-tool     |
|     target guns for change |     G1\~G16    |        numbers of the welding guns, <br> array [ ] for multi guns (ex. ["G1", "G2"])        | connection/disconnection of the relevant additional axes  |
|mechanical connection check signal|     1~4096    | number of the input signal <br> for mechanical connection completion |    parameter to be ignored in off state |  
| connection wait time  | <0~5.0> <br> (sec) | connection completion wait time <br> (limitless waiting if no parameter exists or the value is 0)</p> |  parameter to be ignored in off state  |

<br>

Connection completion will be finalized only after the mechanical connection and the internal processing of the robot controller are completed. The connection completion wait time is the time for waiting until both of the above two processes are completed.

[__SOURCE](4-work-teaching/4-5-servo-tool-change/3-connection-separation-timing.md)
### 4.5.3 Connection/disconnection timing


<p align="center">
 <img src="../../_assets/image_10_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.17 Connection and seperation timing chart</p></em>
</p>

*   Connection

    If the robot and servo gun are mechanically connected during the execution of the connection command (toolchng on), the connection completion signal will be entered, the connection will be processed inside the controller, the encoder power for driving the axis of the servo gun will be entered, and the motor on operation will be executed.

*   Disconnection

     The separation command will execute the processing of the separation according to the sequence opposite to that of the connection command.

[__SOURCE](4-work-teaching/4-5-servo-tool-change/4-sample-program.md)
### 4.5.4 Sample program


<br>

```python

S10   move L, ...                    # Move to servo tool disengagement position
      toolchng off,tg=G1,is=di1      # Execute servo tool disengagement (current connection state)
                                     # Servo tool disengagement output (dedicated output)
      do11=1                         # ATC cam open output
      wait di11                      # Check ATC cam open completion signal
S11   move L, ...                    # Robot movement
S12   move L, ...                    # Robot movement
S13   move L, ...                    # Robot movement
S14   move L, ...                    # Move to servo tool connection position
      wait di12                      # Check connection-ready signal
      do11=0                         # ATC cam close output
      toolchng on,tg=G1,is=di1       # Execute mechanical connection
                                     # Servo tool connection processing
S15   move L, ...                    # Robot movement

```
[__SOURCE](4-work-teaching/4-5-servo-tool-change/5-fixed-toolchng.md)
### 4.5.5 Servo gun change with position-variable fixed electrodes  



When the entire servo gun is replaced, additional equipment such as an ATC (Automatic Tool Changer) and a gun stand is required. However, by operating a system in which the moving electrode remains fixed and only the fixed electrode is changed, no additional equipment is necessary, and the time required for changeover can be reduced.

To support this function, wear amount and soft limits must be managed for each fixed electrode. Therefore, an operation similar to the Welding Gun Change (Servo Tool Change) function is required. Accordingly, before using this function, users must first become familiar with the Welding Gun Change (Servo Tool Change) function.

The difference between this function and the Servo Gun Change function is that no mechanical or electrical connection/disconnection operations are performed. In addition, since the motor and encoder information always remain the same, these data are not updated.

<br>

```python

S10   move L, ...                    # Move to fixed electrode 1
      toolchng fixed,tg=G1,is=di1    # Change to fixed electrode 1
S11   move L, ...                    # Robot movement
      spot gun=1,cnd=1, seq=1        # Perform welding with gun No. 1
S12   move L, ...                    # Move to fixed electrode 2
      toolchng fixed,tg=G2,is=di1    # Change to fixed electrode 2
S13   move L, ...                    # Robot movement
      spot gun=2,cnd=2, seq=2        # Perform welding with gun No. 2

```
[__SOURCE](4-work-teaching/4-6-multi-gun-simultaneous-weld/README.md)
# 4.6 Simultaneous welding with multiple guns

In general, spot welding is performed with one welding gun at a time. The function of simultaneous welding with multiple guns is the act of welding with multiple welding guns at the same time. For this, the gun type (servo gun, equalizerless gun, or equalizer-fitted gun) should be all the same.

[__SOURCE](4-work-teaching/4-6-multi-gun-simultaneous-weld/1-multi-gun-manual-selection.md)
### 4.6.1 Manual selection of multiple guns

<p align="center">
 <img src="../../_assets/image_32_eng_.PNG" width="60%"></img>
 <em><p align="center">Figure 4.19 Screen with multi-gun applied</p></em>
</p>

The procedure for selecting G1 (master) and G2 (slave) as multiple guns through the servo tool change function is as follows.

1. Select `R358` and then connect G1. After the connection is completed, the parameter related to the additional axis to which G1 is assigned should be set.
2. Select `R358` and then connect G2. After the connection is completed, the parameter related to the additional axis to which G2 is assigned should be set.
3. The state of the selected gun is indicated in state flag as follows.

<br>

{% hint style="info" %}
* `R210` for changing the master gun number
  - Environment with a single gun  --> `R210 + 3`  --> Environment with a single gun (Example: G1  --> G3)
  - Environment with multiple guns  --> `R210 + 1`  --> Environment with a single gun (Example: G1 and G3  --> G1)
* `R214` for selecting multiple guns
  -  When selecting another number different from the set gun number

      A. Environment with a single gun  --> `R214 + 3`  --> Environment with multiple guns (Example: G1  --> G1 and G3)

      B. Environment with multiple guns  --> `R214 + 2`  --> Environment with multiple guns(Example: G1 and G3  --> G1, G3, and G2)
  -  When selecting the same number as the set gun number

      A. Environment with multiple guns  --> `R214 + 3`  -->  Environment with multiple guns(Example: G1, G3 and G2  --> G1 and G2)

      B. Environment with multiple guns  --> `R214 + 1`  --> Environment with a single gun (Example: G1 and G2  --> G1)

      C. The master gun number (G1) does not change.  
{% endhint %}


[__SOURCE](4-work-teaching/4-6-multi-gun-simultaneous-weld/2-support-function.md)
### 4.6.2 Support functions

The functions to be provided for simultaneous weldig with multiple guns are as follows.

1. Manual opening and closing
2. Manual squeezing
3. `spot` statement
4. `gunsea` statement

[__SOURCE](4-work-teaching/4-7-panel-thickness-abnormal-detection-when-servo-gun-welding.md)
# 4.7  Detection of panel thickness abnormality

 This is a function to measure the panel thickness during the welding with a servo gun to detect any abnormality with parts and any missing of installation of materials. The function can be executed simply by adding the `thickcheck` statement. Whether the panel thickness is abnormal should be determined based on whether the measured value is within the normal range.

<br>

```python

thickcheck thick=<thickness variable>, ref=<reference value>, tol=<tolerance value>, addr=<go to>

```

<br>

* **thick**

    Specipies the variable to store the measured panel thickness by squeezing the servo gun.

* **ref**

    Specipies the normal panel thickness.

* **tol**

    Specipies the tolerance.

* **addr(branch line)**

   Specipies the method of handling when panel's abnormality is detected. If the branch line is not recorded, the situation "**E1493 Measured panel thickness exceeded the normal range**" occurs and then the robot stops and the output signal set in the "**Panel thickness abnormal**" section is turned on. If the branch line is recorded, the situation "**W0152 Measured panel thickness exceeded the normal range**" occurs and the robot continues to operate as the program jumps to the branch line. In this case, the output signal set in the "**Panel thickness abnormal**" section is turned on only for 200 ms.

 *  Sample code 

```python

S10   move L, ...                               # Move to a spot point
      thickcheck thick=v0,ref=4.0,tol=1.0       # Check the panel thickness
      spot gun=1, cnd=1, seq=1                  # perform spot welding

```
<Br>

{% hint style="warning" %}  
The following should be in place first for accurate measurement of the panel.

1. Gun search (precise management of the consumption amounts of the moving and fixed electrodes)
2. Setting of gun arm deflection amount (Setting of the gun arm deflection amount for each squeezing force)
3. Setting of panel thickness(Setting of the panel thickness for each squeezing force)
{% endhint %}



[__SOURCE](4-work-teaching/4-8-servo-gun-based-work-product-handling.md)
# 4.8 Handling of workpieces with the servo gun

 This is a function to transport a workpiece in small size without using a separate hanger.

<p align="center">
 <img src="../_assets/image_52_eng_.PNG" width="50%"></img>
 <em><p align="center">Figure 4.21 Servo gun's handling function</p></em>
</p>

</br>

```svclamp on/off gun=<gun number>,cnd=<condition number>```




|   **Item**    |        **Content**       |
| :--------: |:---------: |
|    **on/off**    |  on: clamping, off: releasing |
|    **Gun number**    |  the welding gun number (array [ ] for multi-guns) |
|    **Condition number**   |  the welding condition |


<br>



The `svclamp` statement can be used to hold a workpiece and perform opening operation. In the svclamp on state, the servo gun does not open.



<br>

```python

S10   move L, ...                    # Move to a holding position
      svclamp on, gun=1, cnd=1       # Hold the workpiece using a servo gun
S11   move L, ...                    # Robot movement
S12   move L, ...                    # Robot movement
S13   move L, ...                    # Move to a releasing position
      svclamp off, gun=1, cnd=1      # Release the workpiece 
S12   move L, ...                    # Robot movement

```
[__SOURCE](4-work-teaching/4-9-spot-weld-calculation.md)
# 4.9 Calculation of spots in spot welding

The function for storing spot welding point counts is provided by the built-in PLC. The PLC stores the number of welding points for initialization, power-on, the previous cycle, and the current cycle, respectively, and the user can reset these values manually.

For more details, refer to "[3.4.3 S Relay - OP_TIME](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/en/3-relay/4-sw-relay/3-slot-op-time?cont_model=${cont_model})" in the Built-in PLC Manual.


<p align="center">
 <img src="../_assets/image_94_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.22 Spot count</p></em>
</p>

</br>

{% hint style="warning" %}
The spot command executed in the sub task will not be calculated.
{% endhint %}


[__SOURCE](4-work-teaching/4-10-amount-of-abrasion-setting.md)
# 4.10 Spot system variables


Some setting values can be accessed and controlled using spot system variables. These variables store the clearance values for each condition, individual wear values for the moving and fixed electrodes, and the total wear amount. As shown in the illustration below, you can read or modify these values by using variable assignment statements in the command window. 

<p align="center">
 <img src="../_assets/image_93_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.23 Spot tip-consumption system variable usage</p></em>
</p>

</br>


|category	|system variable	|content|
|:--:	|:--:	|:--:|
|welding condition|_spotcnd[#].fixed_tip_clearance|	fixed tip clearance value of the conditon nuymber(#)|
|welding condition|_spotcnd[#].moving_tip_clearance|moving tip clearance value of the conditon nuymber(#)|
|welding gun|_spotgun[#].fixed_tip_consump|	fixed tip consumption fo the gun number(#)|
|welding gun|_spotgun[#].moving_tip_consump|	moving tip consumption fo the gun number(#)|
|welding gun|_spotgun[#].total_tip_consump|	total consumption fo the gun number(#)|

<br>

{% hint style="warning" %}
- The cunsumption-related variables can apply only to servo and equalizerless guns. 
- In the case of the equalizerless gun, the total consumption amount equals the fixed electrode consumption amount.  
- Any manually set wear amount values will be overwritten by the measured values after a gun search is performed.  
{% endhint %}

[__SOURCE](5-spot-weld-parameter/README.md)
# 5.  Spot welding parameters


[__SOURCE](5-spot-weld-parameter/5-1-use-environment-setting.md)
# 5.1 Use environment setting

Sets the use environment related to spot welding to perform appropriate operation for given situations.

<p align="center">
 <img src="../_assets/image_20_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 5.1 Spot use environment setting screen</p></em>
</p>

</br>

(1)  **Servo gun spot statement execution method**
  - During the execution of the `spot` statement, if the selected gun type is a servo gun, the squeezing operation and welding signal output can be inhibited regardless of the welding sequence. This function is useful for verifying the teaching position. The spot welding execution sequence will vary depending on the status of this setting.


<center>

|Output method| <p align=center> Content </p>|  
|:---:|----------------------------------------------------|  
|Wd-On|Executes every welding sequence designated in the spot welding function. </br> Clearance position  --> Squeezing  --> Squeezing force matching inspection  --> Welding signal output </br>  --> Welding completion wait  --> Clearance position |
|Sq-On|Executes the welding sequence except for the signals related to welding. </br> Clerance position  --> Squeezing  --> Squeezing force matching inspection  --> Clerance position|
|Sq-Off|Does not perform squeezing operation, electrification signal output, WI wait, etc.</br>Clearance position|

</center>


</br>

(2)  **Gun search reference position record**
  - In the case of a gun type (servo gun, equalizerless gun) for which the controller manages the tip consumption amount, the reference position should be determined first, and then the actual c35onsumption amount will be calculated based on it.
    
  - disable  
   The actual consumption amount is calculated based on the determined reference position.
  - enable  
    As the reference position is to be determined to calculate the consumption amount,  it would be no problem to perform recording once initially while new tips are attached.


(3)  **Unit of the servo gun force**  
  - Selects the unit of the squeezing force for the control of the servo gun.

(4)  **Automatic adjustment of servo gun welding step record position**
  - Selects whether to adjust the position of the servo gun in the `move` statement recorded in consideration of the panel thickness measured while the gun is squeezed during the execution of the `spot` statement. Set it to "enable" after teaching is completed or deformation of the servo gun has occurred. After that, play back the work program once in automatic mode, then the record position will be simply adjusted based on optimal conditoins. With those features, this function can be usefully applied.

(5) **Servo Gun Real-Time Data Storage Function**
  - During spot welding, specified data are saved to a file at 2 ms intervals. The stored data can be used for welding quality inspection and analysis.
      
      -  Collection time, position, current, pressurization force, welding progress status    

<p align="center">
 <img src="../_assets/image_20_1_eng.png" width="70%"></img>
 <em><p align="center">Figure 5.1.1 Real-Time Data Storage</p></em>
</p>
  
  - Each time a gun search is performed, specified data are saved to a file.
      
      -  Collection time, robot tool-end position, moving electrode wear amount, fixed electrode wear amount

<p align="center">
 <img src="../_assets/image_20_2_eng.png" width="70%"></img>
 <em><p align="center">Figure 5.1.2 Gun Search Data Storage</p></em>
</p>

<br>

{% hint style="info" %}  
 To enable this function, the "Spot Welding Option Function" must be set to Enabled on the license key registration screen.  
{% endhint %}
[__SOURCE](5-spot-weld-parameter/5-2-welding-gun-parameter/README.md)
# 5.2 Welding gun parameter

This section describes how to add a welding gun for spot welding operations and configure detailed settings according to the gun type.

<p align=center>
<img src="../../_assets/image_28_eng.png" width="70%"></img>
<em><p align="center">Figure 5.2.0 Spot gun general settings</p></em>
</p>

<br>


### General Settings

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

{% hint style="warning" %}
Since the Eq-Brake gun type engages the robot axis brakes during welding, robot motion via MOVE statements is disabled during the independent execution of the instruction.
{% endhint %}

[__SOURCE](5-spot-weld-parameter/5-2-welding-gun-parameter/5-2-1-servo-gun/README.md)
### 5.2.1 Servo gun

 Servo guns are currently the most widely used type of spot welding gun. Since the servo gun is controlled as an additional axis separate from the robot axes, extensive control settings are required in addition to the additional axis configuration.

[__SOURCE](5-spot-weld-parameter/5-2-welding-gun-parameter/5-2-1-servo-gun/1-basic-setting/README.md)
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
[__SOURCE](5-spot-weld-parameter/5-2-welding-gun-parameter/5-2-1-servo-gun/1-basic-setting/1-1-real-time-force-control.md)
### 5.2.1.1.1 Real-time squeezing force control

Real-time pressurization force control improves the accuracy of servo gun force by using data measured by a force sensor for control. To enable real-time pressurization force control, the force sensor must communicate with the robot controller, and the communication specifications are configured in the menu below.

Since only digital data can be received, the sensor's analog output signal must be input to the controller through an analog-to-digital converter (ADC).

<p align=center>
<img src="../../../../_assets/image_30_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.6 Setting of real-time squeezing force control</p></em>
</p>

<br>


-  Controller filter use (optional): Enable if an additional controller filter is required.

-  Cut-off frequency: Activated when the controller filter is enabled; sets the filter bandwidth.

-  Reset signal output: Assigns an output signal for force sensor initialization, which is triggered each time the servo gun applies pressure (e.g., Kistler).

-  Communication range: Sets the minimum and maximum range of the assigned signal.

-  Value Range: Sets the value range of the assigned signal.

-  Pressurization input port: The address of the signal assigned for input.

-  Input port length: The number of bits assigned to the signal.

-  Gains (p, i, d, pr): Pressurization force control tuning parameters (modifiable only in Developer Mode).
[__SOURCE](5-spot-weld-parameter/5-2-welding-gun-parameter/5-2-1-servo-gun/2-application-setting.md)
### 5.2.1.2 Servo gun application setting


<p align=center>
<img src="../../../_assets/image_6_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.7 Servo gun application setting</p></em>
</p>


(1)  **Gun arm deflection amount (mm)**  

 - Sets the gun arm deflection amount for the squeezing force set on the left. Considering that it is difficult to manually measure and fill in the values, it is recommended to use servo gun automatic setting. If you press 'Default value calculation', the value of 0.31 mm per 100 kgf will be set as the default value.
 
(2)  **Panel thickness compensation(mm)**  

  - Sets the panel thickness compensation amount for the squeezing force set on the left. Considering that it is difficult to manually measure and fill in the values, it is recommended to use servo gun automatic setting.

{% hint style="warning" %}  

When it comes to 'gun arm deflection amount compensation' and 'panel thickness measurement compensation', it is difficult to manually measure and fill in the values, it is recommended to use servo gun automatic setting.

The 'gun arm deflection amount compensation' value is a value used instead of the 'gun arm deflection amount/100 kgf\[mm]' among the servo gun parameters. When the 'gun arm deflection amount compensation' value is set, the already set 'gun arm deflection amount/100 kgf\[mm]' will not be used. On the contrary, if a 'gun arm deflection amount compensation' value is not set, the 'gun arm deflection amount/100 kgf\[mm] will be used.'  
{% endhint %}

[__SOURCE](5-spot-weld-parameter/5-2-welding-gun-parameter/2-eqless-gun.md)
### 5.2.2. Equalizerless gun

If the gun type is "equalizerless gun," the parameter setting screen for the equalizerless gun will be displayed as shown below.


<p align=center>
<img src="../../_assets/image_42_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.8 Equalizerless gun setting</p></em>
</p>

<br>

(1)  **Fixed tip maximum consumption (mm)**
   - If the consumption amount measured by the `egunsea` statement exceeds the value set here, an error will be generated.

(2)  **Fixed tip change consumption (mm)**
   - If the consumption amount measured by the `egunsea` statement exceeds the value set here, a warning will be issued.

(3)  **Bend offset per 100kgf**
   - Sets the bend compensation amount per 100 kgf.

(4)  **Installed site**
   - Selects whether the chosen equalizerless gun is a robot gun or a stationary gun.


[__SOURCE](5-spot-weld-parameter/5-3-weld-data-condition-sequence/README.md)
# 5.3 Welding data (condition, sequence)

Sets various parameters related to spot welding to perform appropriate operation in line with the work environment.



<p align=center>
<img src="../../_assets/image_59_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.9 Welding data setting</p></em>
</p>

[__SOURCE](5-spot-weld-parameter/5-3-weld-data-condition-sequence/1-common-data.md)
### 5.3.1 Common data

Sets the data to be commonly applied regardless of the spot welding sequence.


<p align=center>
<img src="../../_assets/image_63_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.10 Common data setting</p></em>
</p>

</br>

*  Number of re-weld attempts

    If the welding completion (WI) signal is not received within the configured welding completion wait time, re-welding will be performed. The number of re-weld attempts can be set up to three. If the WI signal is still not received after the specified number of re-weld attempts, an error will be generated.

[__SOURCE](5-spot-weld-parameter/5-3-weld-data-condition-sequence/5-3-2-weld-condition/README.md)
### 5.3.2 Welding condition

Sets spot welding conditions to perform welding in accordance with the work environment.

<p align=center>
<img src="../../../_assets/image_75_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.11 Welding condition setting</p></em>
</p>

(1)  **Condition number**  
  - Allows quick selection of the desired welding condition. This number usually corresponds to the condition name.

(2)  **Output data (binary)**  
  - Sets the data to be transmitted to the welder for the specified welding condition number during execution of the `spot` statement.

(3)  **Initial squeezing force**

  - Sets the panel squeezing force applied during execution of the `spot` statement. This value is used as the initial squeezing force when configuring multi-step squeezing force control.

(4)  **Multi-step squeezing force and auxiliary condition**

  -  Specifies the auxiliary condition number used to manage multi-step squeezing force and pivoting settings. If a number is entered, the corresponding condition must be edited in the `5: Multi-level Press Condition` menu.

(5)  **Moving electrode clearance**
  - Sets the opening position of the moving electrode before and after execution of the `spot` statement.

(6)  **Fixed electrode clearance**
  - Sets the opening position of the fixed electrode before and after execution of the `spot` statement.

[__SOURCE](5-spot-weld-parameter/5-3-weld-data-condition-sequence/5-3-2-weld-condition/1-multiple-pressure-additional-condition/README.md)
#### 5.3.2.1. Multi-step pressurizations and auxiliary conditions


[__SOURCE](5-spot-weld-parameter/5-3-weld-data-condition-sequence/5-3-2-weld-condition/1-multiple-pressure-additional-condition/1-multi-pressure-ctrl.md)
#### 5.3.2.1.1 Multi-step squeezing force control

This function changes the pressurization force during pressurization in servo gun spot welding. The pressurization force can be changed either by generating a predefined profile or by a signal input.

<p align=center>
<img src="../../../../_assets/image_65_eng.PNG" width="70%"></img>
<img src="../../../../_assets/image_37_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.12 Setting of multi-step squeezing force</p></em>
</p>

<br>

(1)  **Condition number**  
  - Indicates the condition numbers for the multi-step squeezing condition and auxiliary conditions.  

(2)  **Force change type**  

   - Indicates the method to change the squeezing force. "Profile creation" is a method in which the point of time for change and the time required for change are designated and then the squeezing force is changed in order at the relevant point of time for change. "Signal input" is a method in which the squeezing force is changed when there is a signal input from an external device.

(3)  **State change process**  
   - When a WI signal is input while executing multi-stage pressurization conditions, select whether to process the WI signal immediately upon receipt or to process the WI signal after all multi-stage pressurization conditions have been completed. 

(4)  **\<Profile creation>**  
   - Will be activated when profile creation is selected as the method to change the squeezing force.

        * Point of time for change:  Specipies the point of time for starting multi-step squeezing by dividing the spot welding steps into `Initial squeezing force reached` -> `Welding execution output` -> `Welding completion input`.
        * Time required for change:  The squeezing force will be changed after the time required for change after the point of time for change is reached.
        * Squeezing force:  The target squeezing force to change to
        * Output data:  Output value transmitted in 12-bit format upon completion of pressurization
  
(5)  **\<Signal input>**  
  - Will be activated when the selected method to change the squeezing force is input of a signal. The information necessary for communication with external devices needs to be entered.

    * Communication range:  Range from minimum to maximum of the assigned signal
    * Value range:  Minimum and maximum values of the assigned signal
    * Squeezing force port:  The number of the signal assigned for input
    * Port assignment:  The number of bits assigned to the signal
    * Request for change:  Port for the input signal for the request for change
    * Time of delay:  For inputting the time if a delay is needed after the input of the request
    * Squeezing force:  The requested squeezing force to change to. You can designate the squeezing force or receive an input signal. When the squeezing force is designated, the squeezing force for which a signal is received will be ignored.

[__SOURCE](5-spot-weld-parameter/5-3-weld-data-condition-sequence/5-3-2-weld-condition/1-multiple-pressure-additional-condition/2-moving-when-pressing-pivot.md)
#### 5.3.2.1.2 Gun Movement During Pressurization (Pivot)

This function moves the gun during the pressurization phase in servo gun spot welding. At the specified movement timing, the robot moves by the defined distance, speed, and direction.

Since this function moves the robot based on the tool coordinate system, servo gun tool data, wear amount, gun arm deflection, teaching posture, and robot calibration can affect performance. To apply this function effectively, the above factors must be continuously monitored and managed.

<p align=center>
<img src="../../../../_assets/image_57_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.13 Pivot setup</p></em>
</p>

(1)  **Condition number**

-   Indicates the condition numbers for the multi-step squeezing condition and auxiliary conditions.
  
(2)  **Point to start movement**
-   Specifies the start timing of movement by dividing the spot welding stages into
`Initial squeeze arrived`  --> `Welding execution output`  --> `Welding complete input`.

(3)  **Shift value (sft)**
-   Regardless of whether a robot-mounted gun or a stationary gun is used, the coordinate system and movement position for shift movement are determined.

(4)  **Move speed\[mm/s, sec, %]**
-   Sets the movement speed.

(5)  **Process for WI during motion**
-   Selects whether to stop the movement immediately when welding completion occurs during robot movement, or to complete the movement and then proceed to the next step.

(6)  **Movement start delay**
-   When the movement timing is reached, the robot waits for the specified delay time before starting the movement.

[__SOURCE](5-spot-weld-parameter/5-3-weld-data-condition-sequence/5-3-2-weld-condition/1-multiple-pressure-additional-condition/3-initial-sequence.md)
#### 5.3.2.1.3 Initial sequence

The multi-stage pressure setting conditions can be applied not only to spot welding but also to other welding applications such as dissimilar material joining. Some applications (e.g., RSR) require an input/output signal sequence after reaching the initial pressure.

By registering the input/output signals required for the sequence procedure as shown below, the system proceeds to the multi-stage pressurization process after completing the signal input/output sequence once the initial pressure has been reached.

Up to five sequences are available, and users may configure as many as required.

<br>

<p align=center>
<img src="../../../../_assets/image_56.png" width="70%"></img>
<em><p align="center">Figure 5.13_1 Initial sequence setting</p></em>
</p>

[__SOURCE](5-spot-weld-parameter/5-3-weld-data-condition-sequence/3-weld-sequence.md)
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

[__SOURCE](5-spot-weld-parameter/5-3-weld-data-condition-sequence/4-servo-gun-tip-dressing-condition.md)
### 5.3.4 Servo gun tip dressing condition

Sets various conditions for the execution of tip dressing for the servo gun

<p align="center">
 <img src="../../_assets/image_61_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 5.15 Servo gun tip dressing condition setting </p></em>
</p>

</br>

(1)  **Welding signal output**
  - Selects whether to output the welding signal for the tip dressing operation.

(2)  **Tip dressing time**
  - Sets the time necessary for executing tip dressing. Tip dressing should be performed in the same manner by using the `spot` statement. However, the welding sequence number should be set to "**64**".

(3)  **Execution of gun search during tip dressing**
  - Selects whether to execute gun search during tip dressing.

(4)  **Tip dresser thickness**
  - Inputs the tip dresser thickness.

[__SOURCE](5-spot-weld-parameter/5-4-input-signal-assign.md)
# 5.4 Input signal assignment for each welder

Assigns the signals related to spot welding, allowing the controller to monitor their state and perform necessary processing.


<p align=center>
<img src="../_assets/image_15_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.15 Input signal assignment</p></em>
</p>

(1)  **Welding completion**
  - Only when this welding completion signal is entered during the execution of spot welding, the controller executes the handling of welding completion. There are four welding completion signals in total and they are individually controllable. 

(2)  **Deposition error**
  - To be used when receiving and handling the input of the gun's deposition signal.

(3)  **Welder abnormal**
  - To be used to stop the operation of the robot when the signal of welder abnormal is entered.

[__SOURCE](5-spot-weld-parameter/5-5-output-signal-assign.md)
# 5.5 Output signal assignment for each welder

Assigns the signals related to spot welding and transfers their state to the outside.

<p align=center>
<img src="../_assets/image_45_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.17 Output signal assignment</p></em>
</p>

(1)  **Welder number**
  - Selects the welder number to set. Up to four welders can be added.

(2)  **Welding condition**
  - Assigns the number of the signal to output the output data corresponding to the welding condition during the execution of the `spot` statement.

(3)  **Welding execution**
  - To be used to output a command for welding to the welder during the execution of the `spot` statement.

(4)  **Welder abnormal**
  - To be used to output the entered spot welder abnormal signal to the outside.

(5)  **Electrode consumption alarm**
  - To be used to output a signal if the consumption amount detected by the gun search is larger than the electrode replacement required consumption amount.

(6) **Deposition error**
  - To be used to output to the outside the state that deposition has occurred to the spot gun.

(7)  **Servo gun squeezing in progress**
  - This is a signal that is turned on when squeezing starts upon the execution of the `spot` statement and turned off when the opening procedure starts.

(8)  **Welding gun search in progress**
  - This is a signal that is turned on when gun search starts upon the execution of the `gunsea`, `igunsea` or `egunsea` statement and turned off when the opening procedure starts.
    
[__SOURCE](6-spotpak/README.md)
# 6. Spot-Pak



Spot-Pak is the name of Hyundai Robotics' integrated control system for spot welding.
This manual describes the settings related to the interface between the welder and the robot controller, as well as TP (Teach Pendant) operations.

<br>

{% hint style="info" %}
 *Available from ${cont_model} V60.28 official release.
 *Currently supports three welders: Chowel, Obara, and Hyosung.
{% endhint %}

<br>

{% hint style="info" %}
 * If you want a Quick Start, please refer to [6.1.4 Operating Procedure](6-1-spotpak-overall/4-procedure.md).
{% endhint %}

[__SOURCE](6-spotpak/6-1-spotpak-overall/README.md)
# 6.1 Overview of the Welder Interface

This function enables the robot controller to integrally control the spot welding timer through DeviceNet communication.
The ${cont_model} controller and the spot welder share data with each other via DeviceNet.

By combining the robot controller and the spot welding timer into a single integrated system, users can perform welding program editing and file management using the ${cont_model} Teach Pendant (TP).

The robot controller performs the major functions that are normally handled through the welder's teaching box-such as welding schedule programming, stepper programming, weld result monitoring, and history file management-directly from the robot controller's Teaching Pendant.

In other words, the system provides a user interface that allows the robot Teach Pendant to perform the functions of the Teaching Box-the operation panel of a standalone welder. It also enables monitoring by displaying welding results, various signals, and the status of errors or faults.

Communication between the robot controller and the timer uses DeviceNet.
The robot controller is configured as the master, and the timer is configured as the slave.

<p align="center"> <img src="../../_assets/6_1.png"> </p> <p align="center"><em>Figure 6.1 (a) Spot welding system with a separate welder (b) Integrated spot welding system</em></p>
[__SOURCE](6-spotpak/6-1-spotpak-overall/1-features.md)

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


[__SOURCE](6-spotpak/6-1-spotpak-overall/2-configure.md)
### 6.1.2 System Configuration

The DeviceNet used in ${cont_model} is part of its industrial communication functionality and utilizes the CifX communication card manufactured by Hilscher.


<p align=center>
<img src="../../_assets/6_2_eng.png" width="60%"></img>
<em><p align="center">Figure 6.2 DeviceNet Communication Configuration</p></em>
</p>



[__SOURCE](6-spotpak/6-1-spotpak-overall/3-menu.md)
### 6.1.3 Menu Structure

The menu structure of the welder interface is dynamically configured according to the controller settings below.
To access these menus, the communication settings must first be correctly configured.

<br>

<p align=center>
<img src="../../_assets/6_3_eng.png"></img>
<em><p align="center">Figure 6.3 Menu Tree</p></em>
</p>
[__SOURCE](6-spotpak/6-1-spotpak-overall/4-procedure.md)
### 6.1.4 Operating Procedure

Operation of the welder interface proceeds in the following order:

- Industrial communication configuration, starting with DeviceNet settings

- Editing welding conditions on the welder

- Configuring input/output signals on the Spot Welding Setup screen

- Creating PLC programs according to the timer specifications

- Creating robot programs (jobs)

<br>

<p align=center>
<img src="../../_assets/6_4_eng.png"></img>
<em><p align="center">Figure 6.4 Operation Flow</p></em>
</p>





{% hint style="info" %}

 * For industrial communication settings required for DeviceNet configuration, refer to [Industrial Communication Function Manual](https://hrbook-hrc.web.app/#/view/doc-industrial-communication/en-${cont_model}/README?cont_model=${cont_model})


{% endhint %}






[__SOURCE](6-spotpak/6-1-spotpak-overall/5-install.md)
### 6.1.5 Installation Method

SPOTPAK is developed as a plug-in type application.
The content displayed on the TP is written in HTML and JavaScript, and it communicates with a Python program that transfers the user's operation requests to the main program.

The provided software contains all the functions described in this manual, but it may be modified to meet user-specific requirements.
Please follow the procedure below to install the plug-in program.


<br>



 [Installation Procedure]

 - 1. Save the "spotpak" plug-in program to a USB drive.

 - 2. Connect the USB drive to the TP.

 - 3. Navigate to: Service > 5: File Management > USB > 'spotpak' folder > Copy

 - 4. Go to: MAIN > apps > Paste

 - 5. Reboot the controller.

 - 6. Navigate to: System > 5: Application Parameters > SPOTPAK

 <br>

 {% hint style="info" %}  
Currently, the "spotpak" folder is provided individually upon request by the spot function development team. However, once a plugin installation/distribution program is deployed on the website, users will be able to download it directly.

When the development of this function is completed, a link to the relevant page will be provided.  
{% endhint %}
[__SOURCE](6-spotpak/6-2-spotpak-functions/README.md)
# 6.2 Main Functions of the Welder Interface
[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-1-data-management/README.md)
### 6.2.1 Data Management
[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-1-data-management/1-specfile.md)
### 6.2.1.1 Importing Characteristic Data



<br>

<p align=center>
<img src="../../../_assets/6_5_eng.png" width="70%"></img>
<em><p align="center">Figure 6.5 Characteristic Data Import Screen</p></em>
</p>

<br>

The characteristic data is essential information that must be prepared in advance in order to use the welder interface functions.
It contains the structure of the welder's configuration data, menu composition, and other necessary elements.
All functions of the welder interface require this characteristic data.

<br>

The functions of each part of the screen shown in Figure 6.5 are as follows:
- ① Welder Status: Indicates the ON/OFF-LINE status of the welder.
Red indicates ON-LINE, and black indicates OFF-LINE.

- ② Welder selection: Select the number of the welder from which the characteristic data will be downloaded.

- ③ Characteristic Data: Displays characteristics related to the current welder using the downloaded characteristic data.

- ④ `[Download]` Button: Downloads the characteristic data of the welder specified in [Select Welder Number].
When the download is completed successfully, a message saying "Characteristic data has been saved." will appear.

[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-1-data-management/2-backup.md)
#### 6.2.1.2 Data Backup


<br>

<p align=center>
<img src="../../../_assets/6_6_eng.png" width="70%"></img>
<em><p align="center">Figure 6.6 Data Backup</p></em>
</p>

<br>


The Data Backup function is used when you want to back up the welder's configuration data to the ${cont_model} controller.
Enter the number of the welder from which the data will be retrieved, then press OK to start the backup.
The process takes approximately 1 to 2 minutes.
Once the backup is completed, a message will appear stating: "Data has been successfully backed up."

The backed-up data can be effectively used in the following cases:

- ① When you want to store a backup of the welder's configuration values

- ② When you want to modify the data of another welder connected to the ${cont_model} controller

- ③ When you want to apply batch updates to welders connected to another ${cont_model} controller
[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-1-data-management/3-datacopy.md)
#### 6.2.1.3 Data Copy

<br>

<p align=center>
<img src="../../../_assets/6_7_eng.png" width="70%"></img>
<em><p align="center">Figure 6.7 Data Copy</p></em>
</p>

<br>


The Data Copy function allows you to copy the data of one welder to another welder.
Additionally, by using the Use Saved Data checkbox, you can copy data that has been stored in the controller through the Data Backup function.

Only PROGRAM data is copied through the Data Copy function; MONITOR data is not included.
[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-1-data-management/4-sericopy.md)
#### 6.2.1.4 Series Copy


<br>

<p align=center>
<img src="../../../_assets/6_8_eng.png" width="70%"></img>
<em><p align="center">Figure 6.8 Data Series Copy</p></em>
</p>

<br>


The Series Copy function is used when you want to copy only the data that contains group (series) information.
From the programs shown in the screen, you can select the desired items and specify both the target welder and the group range to be copied.
[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-1-data-management/5-initialize.md)
#### 6.2.1.5 Initialization

<br>

<p align=center>
<img src="../../../_assets/6_9_eng.png" width="70%"></img>
<em><p align="center">Figure 6.9 Welder Data Initialization</p></em>
</p>

<br>

The Initialization menu is used when you need to reset the status of the welder.
[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-1-data-management/6-clock.md)
#### 6.2.1.6 Time Synchronization

<br>

<p align=center>
<img src="../../../_assets/6_10_eng.png" width="70%"></img>
<em><p align="center">Figure 6.10 Welder Time Setting</p></em>
</p>

<br>

This function is used to synchronize the welder's time with the robot controller by transferring the controller's current time to the welder.
[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-2-data-setting-monitoring/README.md)
#### 6.2.2 Data Setup/Monitoring
[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-2-data-setting-monitoring/1-progmon.md)
#### 6.2.2.1 Program / Monitoring


<br>

<p align=center>
<img src="../../../_assets/6_11_eng.png" width="70%"></img>
<em><p align="center">Figure 6.11 Program Class</p></em>
</p>

<br>

<br>

<p align=center>
<img src="../../../_assets/6_12_eng.png"  width="70%"></img>
<em><p align="center">Figure 6.12 Monitoring Class</p></em>
</p>

<br>
The welder data is largely categorized into PROGRAM and MONITOR, and the contents within each menu may vary depending on the welder version.
[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-2-data-setting-monitoring/2-siglesched.md)
#### 6.2.2.2 Single Scheduled Program

<br>

<p align=center>
<img src="../../../_assets/6_13_eng.png"  width="70%"></img>
<em><p align="center">Figure 6.13 Single Scheduled Program</p></em>
</p>

<br>

A single scheduled program refers to a program that is applied commonly to all welding conditions, similar to a COMMON PROGRAM.
[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-2-data-setting-monitoring/3-multisched.md)
#### 6.2.2.3 Multi-Scheduled Program
<br>

<p align=center>
<img src="../../../_assets/6_14_eng.png"  width="70%"></img>
<em><p align="center">Figure 6.14 Multi-Scheduled Program</p></em>
</p>

<br>

A multi-scheduled program refers to a program in which the user can select a specific series.
In this case, the series can be selected using the `[Series Number]` button.

If you want to copy a specific single data item to a desired range of series, you can use the `[Batch Write Data]` button to access the batch write menu.
[__SOURCE](6-spotpak/6-2-spotpak-functions/6-2-2-data-setting-monitoring/4-batch.md)
#### 6.2.2.4 Batch Write Data




<br>

<p align=center>
<img src="../../../_assets/6_15_eng.png"  width="70%"></img>
<em><p align="center">Figure 6.15 Batch Write Data</p></em>
</p>

<br>

You can copy the data of a specific row from a multi-schedued program to a selected series range of another welder.
[__SOURCE](6-spotpak/6-3-spotpak-error/README.md)
# 6.3 Abnormalities and Errors

<br>

  - Code: There is an error in the characteristic data file.
  - Description: A problem has occurred with the stored characteristic data file.
Please update the characteristic data through Data Management  --> Import Characteristic Data.


<br>
 
   - Code: The value exceeds the allowable range. [Range]
   - Description: The entered value is outside the permitted range.
Please re-enter a value within the valid range.

<br>

   - Code: The source welder number and the destination welder number are the same.
   - Description: This error occurs in Data Copy when the same welder number is entered for both the source and destination.

<br>

   - Code: Class information was not saved correctly.
   - Description: A problem has occurred with the class-related information in the characteristic data.
Please update the characteristic data through Data Management  --> Import Characteristic Data.

<br>

   - Code: Error information was not saved correctly.
   - Description: A problem has occurred in the welder-error-related information within the characteristic data.
Please update the characteristic data through Data Management  --> Import Characteristic Data.

<br>

 - Code: Data transmission between the main board and the T/P has failed.
 - Description: This error appears when a communication fault occurs while writing or retrieving welder data.
Please check the connection status between the controller and the T/P.

<br>

  -  Code: The welder is not connected.
  -  Description: The welder with the specified number is not properly connected via DeviceNet.
Please check the connection status.

<br>

  -  Code: Copy operation failed.
  -  Description: Data copying between welders was not completed successfully.
Please verify the welder's network and communication status, then try again.

<br>

 - Code: There is an error in the welder data file.
 - Description: A problem occurred while loading the welder data file.
Please check whether the file exists and verify the integrity of the data.

<br>

  - Code: Characteristic data was not saved correctly.
  - Description: An error occurred while saving the characteristic data file.
Please check that sufficient storage space is available on the T/P, then try again.
<br>

  - Code: Failed to save data.
  - Description: An error occurred during the data saving process.
Please ensure that there is enough storage space on the T/P and try again.

<br>

   - Code: Welder versions do not match.
   - Description: The versions of the welders involved in the data copy operation do not match, so the copy cannot be performed.
Please check whether the file version or the welder version has been changed.

<br>

   - Code: Timeout occurred.
   - Description: This occurs when communication between the main board and the T/P is unstable, or when the controller's processing time is excessively long.
Please try again.
<br>

   - Code: Data contains errors.
   - Description: Some values in the backed-up data file fall outside the valid range.

[__SOURCE](7-faq.md)
# 7. Frequently Asked Questions

* How does the servo gun axis operate when using the shift function? 

  All shift-related functions (Offline, Online, Search, and Palletizing) are applied only to the robot axes. The servo gun axis moves to the positions recorded in the program and is not affected by the shift operation.

* What happens to the servo gun axis during coordinate conversion?  
  Only the robot motion elements are subject to coordinate conversion. The servo gun axis is not converted.

* How does the system operate when the counterpart program call function is used?  

  Shifting is applied by adding the relative position offset to the robot axes.

* What happens to the servo gun axis during mirror image conversion?  

  Mirror image conversion is applied to an additional axis only when the axis specification is set to Base and the axis configuration is Linear. Therefore, the servo gun axis is not subject to mirror image conversion.

* How can I change the currently selected gun number?  

  You can change the selected gun number using R210: Spot Gun Number Selection.
  If the selected gun is a robot-mounted gun, the corresponding tool number will automatically be updated based on the tool number assigned to that gun.
  When the gun number is changed using R210 in a multi-gun environment, the system switches to a single-gun environment corresponding to the selected gun.

* How can I select and manually squeeze multiple guns?  

  Multiple guns can be selected only if they are of the same gun type.   Use R214: Selection of Simultaneous Welding Guns to select multiple guns. To deselect a gun after multiple guns have been selected, enter the gun number to be deselected using R214. However, the first selected gun (Master Gun) cannot be deselected.

* How can I change the squeezing force during the servo gun squeezing process?  

  If the selected gun type is a servo gun, the squeezing force can be adjusted using R211: Servo Gun Squeezing Force Setting.

* How can I manually change the moving electrode wear amount of the servo gun? 

  If the selected gun type is a servo gun, the moving electrode wear amount can be modified using R212: Servo Gun Moving Electrode Wear Preset. When a gun search is performed, this value is automatically updated.

* How can I manually change the fixed electrode wear amount of the servo gun? 

  If the selected gun type is a servo gun, the fixed electrode wear amount can be modified using R213: Servo Gun Fixed Electrode Wear Preset. When a gun search is performed, this value is automatically updated.

* How can I manually change the fixed electrode wear amount of an equalizerless gun?   

  If the selected gun type is an equalizerless gun, the fixed electrode wear amount can be modified using R220: Equalizerless Gun Fixed Electrode Wear Preset. When a gun search is performed, this value is automatically updated.

* The robot is currently operating in automatic mode, and I want to change the squeezing force defined in the welding condition. How can I do this?   

  Use R215: Spot Welding Condition Squeezing Force Setting to change the squeezing force value defined in the welding condition, even while the robot is operating in automatic mode.

* Can I manually change the currently selected welding condition and welding sequence numbers?  

  To change the welding condition number, press cond.sel. To change the welding sequence number, press seq.sel, and then select the desired number.  

* Is there a shortcut to access the menu path `[F2: system] - 4: Application parameter - 1: Spot welding`?  
  
  Yes. In Manual Mode, place the cursor on a spot welding-related command (e.g., spot, gunsea, igunsea, or egunsea) on the initial screen, and press the `[property]` button to quickly access the corresponding menu.

* How can I manually change the panel thickness?  

  If the selected gun type is a servo gun, the panel thickness can be changed using R220: Panel Thickness Setting (Sv).

* How can I reset the recorded positions of the spot welding steps to normal values at once?  

  Set <Valid> for the item "Automatic Adjustment of Servo Gun Welding Step Record Position" under `[F2: system] - 4: Application parameter - 1: Spot welding - 2: Welding gun parameter - 1: Environment Setting`, and then play back the work program.

* Is it possible to detect any missed welding points?  
  
  Yes. When you initialize the welding count in the Work Program Start menu and then perform welding normally, the welding count will increase accordingly.
  To detect missed welding points, you must compare:
  the total number of welding spots required for completion, and the actual number of weldings performed. Refer to the chapter [ 4.9 Calculation of spots in spot welding](./4-work-teaching/4-9-spot-weld-calculation.md).


* It seems that the working time could be reduced if tip dressing and gun search operations for a stationary servo gun were performed independently from handling operations. Is there any way to achieve this?  

  Yes. This can be easily implemented by using the multi-task function.  By separating handling operations and stationary servo gun operations into different tasks, they can be executed independently and simultaneously. Please refer to the [Multi-task Function Manual](https://hrbook-hrc.web.app/#/view/doc-multi-task/en/README?cont_model=${cont_model}) for detailed instructions.
[__SOURCE](8-error-warning/README.md)
# 8. Errors and warnings
[__SOURCE](8-error-warning/8.1.md)
# 8.1 Error messages

|                          Code                          |       <p align=center> Content </p>                                    |       <p align=center> Measure              </p>                                                          |
| :---------------------------------------------------: | -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
|               <p>E0007 </p><p>Deposition detection</p>               | A deposition signal is entered upon the ending of the welding sequence.                                                              | <ul><li>Check the deposition detection signal.</li><li>Remove the deposition.</li></ul>                                                                 |
|        <p>E0154 </p><p>Maximum electrode </p><p>consumption amount exceeded</p>        | The total electrode consumption amount detected by gun search exceeded the maximum electrode consumption amount (of both moving and fixed electrodes) set in the welding gun parameter.                        | <ul><li> Check the maximum electrode consumption amount in the welding gun parameter.</li><li>Replace the electrode.</li></ul>                                                   |
|       <p>E0155 </p><p>Maximum moving electrode </p><p>consumption amount exceeded</p>       | The moving electrode consumption amount detected by gun search exceeded the maximum (moving) electrode consumption amount set in the welding gun parameter.                              | <ul><li>Check the maximum (moving) electrode consumption amount in the welding gun parameter.</li><li>Replace the electrode.</li></ul>                                                |
|       <p>E0156 </p><p>Maximum fixed electrode </p><p>consumption amount exceeded</p>       | The fixed electrode consumption amount detected by gun search exceeded the maximum (fixed) electrode consumption amount set in the welding gun parameter.                              | <ul><li>Check the maximum (fixed) electrode consumption amount in the welding gun parameter.</li><li>Replace the electrode.</li></ul>                                                |
|        <p>E0171 </p><p>Gun opening time (five seconds) </p><p>exceeded</p>       | After the squeezing operation in the spot welding and gun search function was performed, the opening time exceeded five seconds.                                               | <ul><li>Check whether the gun has deposited to the welding workpiece or any interference has occurred.</li><li>Check whether deposition or interference has occurred to the gun of the moving side.</li></ul>                                |
|         <p>E1036 </p><p>Electrification wait time</p><p>exceeded</p>        | During the execution of the welding by the servo gun, the welding completion (WI) signal has not been entered during the welding completion (WI) wait time in the welding sequence menu.                        | Check the wiring diagram of the welding completion (WI) signal and related peripheral facilities.                                                                                   |
|     <p>E1038 </p><p>Position where the electrode consumption</p><p>amount compensation cannot be performed</p>    | At the time of recording the position by performing the electrode consumption amount compensation, the robot posture was created in a way that the electrode consumption amount compensation cannot be performed.                            | Required to make sure that the robot posture does not deviate from the operation area while trying to perform compensation for as much as the detected electrode consumption amount.                                                                      |
|           <p>E1281 </p><p>The welder abnormal signal is entered.</p>          | Occurs when the welder abnormal signal is entered during welding.                                                           | 1) Check the welding power supply unit.                                                                                                    |
|     <p>E1306 </p><p>Gun search reference position </p><p>not recorded</p>     | An error that occurs when the gun search function or spot welding function is played back without performing the gun search reference position record.                           | Attach unconsumed new electrodes and then perform the gun search reference position record operation.                                                                            |
|           <p>E1307 </p><p>Gun search not completed normally</p>          | An error that occurs if the spot welding function is played back without completing the gun search normally, or if gun search 2 is performed without performing gun search 1.           |  Execute gun search 1 and 2 to detect the tip consumption amount first. Then start the work.                                                                             |
|        <p>E1308 </p><p>The tool number designation for steps is false.</p>        | An error that occurs if a tool number corresponding to the welding gun number is designated wrongly for the execution of the steps where the spot welding function and gun search function are recorded.                | Match between the gun number in the function and the tool number in the step by checking the setting status of the menu of Setting of the tool number and gun type corresponding to the gun number.                                                       |
|        <p>E1310 </p><p>Set squeezing force exceeded the current limit range.</p>       |  An error that occurs if the current limit value calculated from the command squeezing force exceeds the current limit value (IP) of the servo amp.                            | Required to lower the set squeezing force or increase the capacity of the servo gun driving motor.                                                                                 |
| <p>E1311 </p><p>The set squeezing force</p><p>exceeded the overload</p><p>detection level.</p> | This error occurs if the command squeezing force exceeds the overload detection level.                                                     | Lower the set squeezing force in anticipation of an overload error.                                                                                         |
|     <p>E1312 </p><p>The gun squeezing target position</p><p>calculation result shows deviation from the operation area.</p>    | An error that occurs when the servo gun squeezing position (sample position) calculation result shows that the robot deviates from the operation area.                                      | Change the robot posture and then record the position.                                                                                            |
|       <p>E1313 </p><p>The set squeezing force </p><p>exceeded the range</p>      | This error occurs if the squeezing force set in the welding condition exceeded the squeezing force range set in the squeezing table of the welding gun parameter.                     | Lower the set squeezing force.                                                                                                    |
|        <p>E1314 </p><p>Squeezing force matching </p><p>detection time exceeded</p>       | An error that occurs if squeezing force matching does not occur even after the passage of the squeezing force abnormality detection time in the welding gun parameter after the moving electrode started squeezing at the record position.          | <ol><li>Check the offset value of the command value. </li><li>Check the squeezing force abnormality detection time. </li><li>Check the accuracy of the squeezing force.</li></ol>                             |
|      <p>E1320 </p><p>The sensor does not work </p><p>during gun search</p>      | This error occurs if the sensor does not work even when the robot moves to the target position during the consumption amount detection operation by the sensor in line with the gun search function of the servo gun or equalizerless gun. | <ol><li>Check whether the sensor works when the electrodes approach the sensor.</li><li>Check the wiring diagram and connection of connectors.</li><li>Check whether the specification of the contact of the sensor is appropriate.</li></ol><p></p> |
|         <p>E1326 </p><p>Gun search 2 </p><p>environment inappropriate</p>        | This error occurs if gun search 2 is executed in an environment where the consumption amount is to be measured only by gun search 1.                    | Set the environment in a way that the gun's consumption amount compensation can be performed by gun search 1 and gun search 2.                                                                                |




|  Code        |      Content          |       Measure    |
|-------------| ------------- | ----------------- |
|               E0007  Deposition detection              | A deposition signal is entered upon the ending of the welding sequence. | Check the deposition detection signal. Remove the deposition.    |
[__SOURCE](8-error-warning/8.2.md)
# 8.2 Warning messages

|                  Code             |       Content                                                                  |       Measure                                                                                                   |
| :----------------------------------------------------: | -------------------------------------- | ---------------------------------------------------- |
|      <p>W0009 </p><p>Brake slip occurred</p><p>(the set value exceeded)</p>     | The brake slip measured during Eq-Brake welding exceeded the brake deviation detection range set in the welding sequence.                  | Check the set brake deviation detection range, and, if necessary, change the value to a greater one.                                                               |
|       <p>W0105 </p><p>Electrode replacement required total consumption amount </p><p>exceeded</p>       | This warning occurs if the total consumption amount detected by gun search exceeded the electrode replacement required consumption amount (both of moving and fixed electrodes) set in the welding gun parameter.       | <ol><li>Check the set maximum electrode consumption amount.</li><li>Check whether the gun search reference position is registered normally.</li><li>Replace the electrode.</li></ol>        |
|      <p>W0106 </p><p>The moving electrode exceeded </p><p>the electrode replacement required consumption amount</p>      | This warning occurs if the moving electrode consumption amount detected by gun search exceeded the (moving) electrode replacement required consumption amount set in the welding gun parameter.             | <ol><li>Check the set (moving) electrode replacement required consumption amount. </li><li>Check whether the gun search reference position is registered normally.</li><li>Replace the electrode.</li></ol>   |
|      <p>W0107 </p><p>The fixed electrode exceeded </p><p>the electrode replacement required consumption amount</p>     | This warning occurs if the fixed electrode consumption amount detected by gun search exceeded the (fixed) electrode replacement required consumption amount set in the welding gun parameter.             | <ol><li>Check the set (fixed) electrode replacement required consumption amount. </li><li>Check whether the gun search reference position is registered normally.</li><li>Replace the electrode.</li></ol> |
| <p>W0108 </p><p>During the jog operation, </p><p>the actual squeezing force exceeded </p><p>the set value</p> | When squeezing is performed through manual operation of the axis, the actual squeezing force exceeds the set squeezing force. When this occurs, operate the servo gun axis in the opposite direction. | <ol><li>Check whether the squeezing force of the axis that will be operated is sufficiently set.</li><li>As a mechanical problem with the servo gun is anticipated, you need to contact the servo gun manufacturer for inquiry. </li></ol><p></p> |
|  <p>W0109 </p><p>Impossible to manually </p><p>operate the servo gun not </p><p>selected</p> | The servo gun you want to operate is different from the selected servo gun.                                             | When you select a servo gun, you need to perform manual jog operation. First, select the servo gun you want to operate with the R210 code and then perform the operation.                                          |

[__SOURCE](9-spot-monitoring/README.md)
# 9. Spot Monitoring Function

The Spot Monitoring function visualizes data generated during spot welding in graph form, enabling rapid identification of the root cause when a problem occurs. In addition, when checking function behavior, users can review the magnitude and timing of each data item displayed in the graph, helping to determine normal or abnormal conditions directly on the TP without the inconvenience of analyzing data files on a PC.

### Installation Method

This function is developed using a plugin-based approach. By simply saving the corresponding code to the designated folder, the menu is automatically displayed without requiring a separate build process, allowing users to select and execute the desired function.

Until dedicated features for plugin program installation and security are officially provided, obtain the source code from the spot welding developer (spot function administrator) and copy it to the following path:

[MAIN > apps > spot_mon]


</br>

<p align=center>
<img src="../_assets/image_95_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.1 Spot Data Monitoring Function Menu</p></em>
</p>


[__SOURCE](9-spot-monitoring/9-1-spot-data.md)
## 9.1 Spot Data Monitoring Function

Spot data monitoring allows selective visualization of data generated while executing the spot command. Data collection is created using the existing gathering function, and the generated data file is utilized for monitoring.

### Data File Creation

To collect data for spot data monitoring, edit the options as shown below:
([Service > 16: Data Gathering], Engineer Mode)

<p align=center>
<img src="../_assets/image_96_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.2 Spot Data Collection Option Input</p></em>
</p>

<br>

Execute the gathering command in the user program.
<p align=center>
<img src="../_assets/image_97_eng.PNG" width="50%"></img>
<em><p align="center">Figure 9.3 Execution of Gathering Command</p></em>
</p>


### - Data File and Graph Option Selection

Enter the Spot Data Monitoring function and select the Spot Data menu.
<p align=center>
<img src="../_assets/image_98_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.4 Spot Data Graph Menu</p></em>
</p>

An option selection window for graph creation and function buttons at the bottom of the screen are displayed.
<p align=center>
<img src="../_assets/image_99_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.5 Graph Creation Options and Function Buttons</p></em>
</p>


By pressing the `[file choice]` button, select the GDT file to be used for graph generation from the saved files, and then press the `[save]` button.
<p align=center>
<img src="../_assets/image_100_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.6 GDT File Selection</p></em>
</p>


### - Graph Creation and Zoom Function
When the `[Graph]` button is pressed from the function buttons shown in Figure 9.5, graphs are displayed for the selected options as shown below.
<p align=center>
<img src="../_assets/image_101_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.7 Graph Generation for Selected Items</p></em>
</p>

To view details more closely, use a finger or stylus to select an area on the screen. The selected area will be displayed as an enlarged graph.
<p align=center>
<img src="../_assets/image_102_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.8 Graph Zoom Function</p></em>
</p>
[__SOURCE](9-spot-monitoring/9-2-gunsea-history.md)
## 9.2 Gun Search Data History Management

No separate user procedure is required for gun search data history management. Each time the gunsea command is executed, the wear amount of each tip is automatically saved to a history file.

The files are stored under the 'MAIN > log' folder with the name gunsearchlog_x.txt, and up to 10 files are stored in a rotating manner.


<p align=center>
<img src="../_assets/image_103_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.9 Gun Search History Management Files</p></em>
</p>

[__SOURCE](9-spot-monitoring/9-3-gunsea-data.md)
## 9.3 Gun Search Data Monitoring Function

By selecting a saved wear history file, users can view the trend of tip wear changes in graph form. To access this function, select the following menu item:

<p align=center>
<img src="../_assets/image_104_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.10 Gun Search Data Menu</p></em>
</p>


### - Data File and Graph Option Selection

An option selection window for graph creation and function buttons at the bottom of the screen are displayed.
<p align=center>
<img src="../_assets/image_105_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.11 Graph Creation Options and Function Buttons</p></em>
</p>


Click the `[file choice]` button, choose the desired log file from the saved files, and then click the `[save]` button.
<p align=center>
<img src="../_assets/image_106_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.12 Log File Selection</p></em>
</p>


### - Graph Creation and Zoom Function

Press the `[Graph]` button among the function buttons shown in Figure 9.5 to display graphs for the selected options, as shown below.
<p align=center>
<img src="../_assets/image_107_eng.PNG" width="70%"></img>
<em><p align="center">Figure 9.13 Graph Creation for Selected Items</p></em>
</p>

