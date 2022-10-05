# Hi6 Robot Controller Function Manual - Spot Welding

The information provided in this manual is the property of Hyundai Robotics.

It cannot be reproduced or redistributed in whole or in part without the written consent of Hyundai Robotics, and cannot be provided to a third party or used for other purposes.

This manual is subject to change without prior notice.

<br>
<br>
<br>

**Copyright ⓒ 2020 by Hyundai Robotics Co., Ltd**# 1. Overview

This manual provides explanations based on the systems below. If the system used in the field is different from the ones described here, the worker on the site should refer to and use this manual according to the on-site system.

*   **System specifications described in the manual**

    Robot guns (for change of welding guns): A servo gun (G1), a servo gun (G2), an equalizerless gun (G3), and an equalizer-fitted gun (G4)

    Stationary guns: Servo gun (G5), servo gun (G6), and equalizerless gun (G7)

1.  Servo gun

    The servo gun is set as an additional axis of the robot. It is used in a way that the rotational force of the servo motor is transmitted to the ball screw to operate the gun tips, thereby controlling the squeezing and opening operations.
2.  Equalizer-fitted gun

     This is a spot welding gun that performs squeezing and opening motions using pneumatic pressure and is controlled by the welding condition output signal and welding (electrification) output signals, and is based on a method of mechanically performing the equalizing operation during welding.
3.  Equalizerless gun

    This is a spot welding gun that performs squeezing and opening motions using pneumatic pressure and is controlled by the welding condition output signal and welding (electrification) output signal, and is based on a method in which the equalizing operation is performed by the robot as the gun has no cylinder for the equalizing operation for the welding.
   
</br>
</br>

**[Essential manuals]**

- [**Hi6 Controller Operation Manual**](https://hyundai-robotics.gitbook.io/hi6-operation-manual/)

- Hi6 Additional Axis Function Manual
# 1.1 Main specifications

|       **Item**       |                          **Specification**                          |
| :----------------: | :------------------------------------------------------: |
|     Spot welding setting file     |           spotweld.json            |
|      Maximum welder count     |              4 units                 |
| Count of multiple guns for simultaneous welding</br>(the same gun type) |           4 units                   |
|            |                 16 units                   |
|       Welding condition number      |                         1 – 1024                        |
|   Output data dependent on welding condition   |                         1 – 1024                        |
|       Welding sequence number      |                   1 –  63 (64 is exclusively for tip dressing)                   |
|     Position modification (servo gun)    | SPOT command step – Consumption amount automatic compensation position</br>Other steps – Positions that do not consider the consumption amount |
|    Inspection of the tool number corresponding to the gun umber   |                     Inspection of robot guns and no inspection of stationary guns                    |
|     Welding condition signal output     |   To be outputted in sync with the output of the welding execution signal</br>Impossible to output only the welding condition signal   |
# 1.2 Operation sequence

Two procedures are provided for the servo gun setting: manual setting and automatic setting.# 1.2.1  Operation sequence that uses the servo gun automatic setting

The procedure for the servo gun automatic setting is as shown in the flowchart below.

---

<p align="center">
 <img src="../../_assets/image_78_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 1.1 Operation sequence of the servo gun automatic setting </p></em>
</p># 1.2.2 Operation sequence that uses the servo gun manual setting

The procedure for the servo gun manual setting is as shown in the flowchart below.

---

<p align="center">
 <img src="../../_assets/image_46_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 1.2 Operation sequence of the servo gun manual setting</p></em>
</p># 1.3 Terms in line with the movement between the electrodes of the servo gun


<p align="center">
 <img src="../_assets/image_8_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 1.3 Terms for the moving and fixed electrodes</p></em>
</p># 2. Initial setting of the servo gun

# 2.1 Procedure for initial setting of the servo gun

This function is related to spot welding and other applications that use a servo gun. If necessary to use a gun other than a servo gun (pneumatic gun, etc.), refer to only “[**2.1.1 Setting of the tool number and gun type corresponding to the gun number**](1-tool-number-gun-type-setting.md)” and “[**2.1.2 Setting of the tool angle/distance**](2-tool-angle-distance-setting.md)” in this chapter, and “[**3. Related functions**](../../3-Related-functions/)” in the next chapter.

The initial setting of the servo gun is an essential process to makie it possible to perform spot welding using a servo gun. After completing the procedure for the initial setting of the servo gun, the following items will be possible.

* Operation of the moving electrode of the servo gun
* Squeeze with the specified squeezing force
* Signal input and output for spot welding

After completing the procedure for initial setting, you need to set related functions and spot welding parameters (welding conditions, sequence, etc.) according to the purpose of use, and then teach the work.

Through the “**Servo gun automatic setting**” function (『**Setting**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 → 『**6: Servo gun automatic setting**』), our company provides settings and procedures for the environment for spot welding and servo gun operation.

<p align="center">
 <img src="../../_assets/image_60_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 2.1 Screen for entering the ‘Servo gun automatic setting’ menu</p></em>
</p>

{% hint style="warning" %}
\[**Caution**\] You can enter the menu only when the currently selected gun number is for the servo gun.
(“**Additional axis parameter setting**”, “**Load estimation**”, “**Tool data inputting**”, “**Tool number and gun type corresponding to the gun number**” are the items that should be essentially set prior to the servo gun automatic setting.) If multiple guns are to be used, their individual settings should be performed by chaning the gun number.
{% endhint %}

</br>

---

The initial setting for the servo gun and spot welding is performed largely in five steps as shown below, and the progress of each step will be indicated, allowing you to monitor the progress.


<p align="center">
 <img src="../../_assets/image_3_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 2.1.2 Procedure for ‘servo gun automatic setting’</p></em>
</p>

The standard procedure for the servo gun initial setting is as follows.

* **[**Step 0. Pre-inspection**](../2-2-step-0-pre-inspection.md)**: Inspection of essential pre-setting items for the setting of the servo gun operation environment 
  * Additional axis parameter
  * Setting of the tool number corresponding to the gun number
  * Tool data setting (including load estimation)
  * Servo gun parameter setting
* **[**Step 1. Default setting**](../2-3-step-1-default-setting/)**: Setting of the servo gun operation environment
  * Encoder offset compensation
  * Axis origin setting
  * Soft limit setting
  * Squeezing force-current table setting
* **[**Step 2. Application setting**](../2-4-step-2-application-setting/)**: Setting of application functions that use the servo gun
  * Gun search
  * Gun arm deflection amount compensation
  * Panel thickness measurement compensation
* **[**Step 3. Setting check**](../2-5-step-3-setting-check.md)**: Process for checking the current setting
* **[**Step 4. Signal setting**](../2-6-step-4-signal-setting.md)**: Assignment of input and output signals for spot welding application

</br>

The “**Standard procedure for servo gun initial setting**” screen not only shows the indication process and the status about completion, but also makes it possible to proceed with related items or move to the screen where related items can be performed.

In other words, the initial setting related to the servo gun can all be completed from the above screen without going to relevant menus. The initial setting can be proceeded with in the following two ways.

1. Move the cursor to the relevant procedure and then input by selecting 『**Enter**.』
2. Press 『**Proceed with the pirot-to-setting items**』 to automatically proceed with the initial setting not yet conducted.

The 『**Proceed with the pirot-to-setting items**』 key makes it possible to inspect the procedures not yet conducted among all procedures, allowing them to be performed automatically. At the time of initial setting, you can complete the setting by following the guide just by clicking 『**Proceed with the pirot-to-setting items**』.
# 2.1.1 Setting of the tool number and gun type corresponding to the gun number

This function sets the tool number and gun type corresponding to the spot welding gun number. It supports in a way that a vriety of welding guns can be configured to match with the use of individual welders and tool numbers. Because the welding method varies depending on the gun type, the setting must be performed correctly. Guns can be added using the '+' sign on the right and up to 16 guns can be added.


<p align="center">
 <img src="../../_assets/image_31_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 2.2 Gun default setting</p></em>
</p>


‘Welder’ is for designating the welder linked with the relevant gun number. When welding is performed with the relevant gun, the signal is inputted to and outputted from the port that matches with the setting of the relevant welder. Multiple guns can be shared and used through the servo tool change function. 

‘Tool’ refers to an object coupled with the tip of the R1 axis of the robot, and the robot should know the tool information. ‘Tool number’ refers to the tool number to be matched with the relevant gun number, and there should be load estimation and tool data inputted in the relelvant tool number. In general, individual gun have different shapes, so a unique ‘tool number’ should be selected for each gun number.As stationary guns are not to be coupled with the tip of the R1 axis, it would be no problem to perform arbitrary setting for them. During the work teaching, if the gun number of the Spot command and the tool number of the Move command are not matched with eath other, playback will not be possible. Please note this.  

‘Gun type’ refers to the gun type of the relevant gun. You can select one among three types. If the gun type of the relevant gun is servo gun, the information of the additional axis assigned to the relevant gun should be inputted. When it comes to the information of the additional axis, the same additional axis can be assigned to multiple guns during the use of the servo tool change function. Please note this.

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

</center># 2.1.2 Setting of the tool angle/distance

When spot welding is performed, the equalizing operation (operation in which the fixed electrode contacts the panel after passing through the clearance position) is absolutely necessary. This operation requires the correct setting of the tool coordinate system. The +Z axis of the tool coordinate system should be set correctly in the direction from the fixed electrode to the moving electrode (Note: [**Hi6 Controller Operation Manual**](https://hyundai-robotics.gitbook.io/hi6-operation-manual/)).

<p align="center">
 <img src="../../_assets/image_38_eng.PNG">
  <em><p align="center">Figure 2.3 Setting of the tool length and angle of the welding gun</p></em>
 </img>
</p>

*   **Tool length**

    When it comes to tool length, input the length from the center of the flange of the robot's R1 axis to the tip of the tool (the upper part of the fixed electrode), measured with a new, unconsumed electrode attached. Set the coordinate direction of the reference tool coordinate system as positive (+) and input the measured length X, Y, and Z values, or set the tool length using the automatic calibration function.
*   **Tool angle**

    Input the rotation angles (Rx, Ry, Rz) in three directions based on the flange coordinate system, or use the ‘Angle compensation’ function. Set the tool angle in a way that the upward direction of the fixed electrode can be +Z. To check it, set \[**Coordinate system**] of the teach pendant to 『**Tool**』, and press the \[**Up**] key of the jog key. Then, if thus set direction matches with the Z+ direction (the squeezing direction of the fixed electrode), the setting would suffice.

</br>

>    **In the case of the above figure, set the tool angle as {0 deg, 180 deg, 0 deg}.**

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
\[**Caution**]  If you complete the setting on the “**Additional axis parameter setting**” screen, you will be asked to reboot after completing the pre-inspection.

After rebooting, you should enter the “**Servo gun automatic setting**” screen and continue the setting. 
{% endhint %}
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
   * For manual setting, refer to “[**2.3.2.1 Servo gun encoder offset setting**](2-3-2-manual-setting/1-servo-gun-encoder-offset-setting.md)” of “[**2.3.2** **Manual setting**](2-3-2-manual-setting/).”
  
(2) **Axis origing setting**
   * In general, the setting of the axis origin of the servo gun should be performed at the position where both the moving and fixed electrodes, with a new tip attached individually, meet each other. As most operations of the servo gun are performed with this axis origin as the reference, it is very important to carry out setting for this.
   * For manual setting, refer to “[**2.3.2.2 Servo gun axis origin**](2-3-2-manual-setting/2-servo-gun-axis-origin.md)” of “[**2.3.2** **Manual setting**](2-3-2-manual-setting/).”
   
  
(3) **Soft limit setting**
   * In general, the soft limit of the servo gun should be set to ‘**Minimum**’ while the moving electrode is fully open, and set to ‘**Maximum**’ while the moving electrode is at the closest position with all tips removed.
   * For manual setting, refer to “[**2.3.2.3 Servo gun soft limit**](2-3-2-manual-setting/3-servo-gun-soft-limit.md)” of “[**2.3.2** **Manual setting**](2-3-2-manual-setting/).”
    
(4) **Squeezing force - current table setting**
   * To squeeze the various servo guns, which are to be installed to the robot, with the desired squeezing force, it is necessary to make the current supplied to the servo gun correspond to the generated squeezing force. For this, our company provides a servo gun squeezing force - current table. It is necessary to tune this table to match with the servo gun..
   * To use this function, it is necessary to select five representative values among the areas of the squeezing force to be used. Tuning the servo gun squeezing force - current table is a process to find the currents that match with these five representative squeezing forces. This table can vary depending on the posture of the servo gun, so it is necessary to perform tuning for each case of when the direction of the moving electrode is in the direction of gravity and when it is in direction of anti-gravity, and, through this method, squeezing can be performed with high accuracy in various postures of the servo gun.
   * For more details, refer to “[**Servo gun squeezing force - current table tunning**](2-3-3-servo-gun-force-current-table-tuning/).”

</br>

The default setting can be performed with automatic settng and manual setting.

(1) **Automatic setting**: The servo gun automatically moves to the designated position and then perform the designated setting.
   * Items that can be automatically set
     * Encoder offset compensation
     * Axis origin setting
     * Soft limit setting
   * The setting of the squeezing force - current table cann not be automatically performed because it requires user intervention such as the installation of a squeezing force gauge.
   
(2) **Manual setting**: The servo gun needs to be moved to the designated position through the operation by the user and the designated function will be performed on the dedicated setting screen.
# 2.3.1 Automatic setting

Progress the automatic setting of the ‘**default setting**’ of the servo gun by pressing the 『**All automatic setting**』 key. In the case of ‘**all automatic setting**’, the moving electrode of the servo gun moves automatically, so the following conditions must be satisfied.

* Moving and fixed electrodes with new tipes attached
* No worker around the servo gun
* No workpiece between the moving electrode and fixed electrode
* Manual mode
* Motor on
* Prohibition of maximum opening of the moving electrode (a gap of certain distance from the maximum opening position)

In the case of ‘**all automatic setting**’, the following procedures will proceed automatically.

    (1) Encoder offset compensation  
      - The moving electrode moves to the maximum opening position.  
      - The servo gun stops at the maximum opening position and then encoder offset compenation will be executed.
    (2) Axis origin setting
      - The servo gun performs the squeezing operation three times and opening operation two times.
      - After the third squeezing operation, the servo gun moves to the position where the two electrodes meet with each other.
      - Confirms the relevant position with the user.
      - Executes the setting of the axis origin.
    (3) Soft limit setting  
      - Will be automatically executed after the axis origin setting.
    (4) Squeezing force - current table setting 
      - Automatic change to the menu for the setting will occur.

In the case of automatic setting of the servo gun's default setting, the servo gun's ‘**encoder offset compensation**’ position and ‘**axis origin compensation**’ position are automatically recognized, allowing the ‘**encoder offset compensation**’, ‘**axis origin compensation**’ and ‘**soft limit setting**’ to proceed at the relevant positions. When it comes to automatic setting of the servo gun's default setting, the ‘**squeeze force - current table setting**’ does not proceed automatically. Please refer to the chapter “[**2.3.3 Squeeze force - current table setting**](2-3-3-3-servo-gun-force-current-table-tuning/)” for setting.

In the case of ‘**all automatic setting**’, the servo gun moves to the position of the axis origin and performs confirmation with the user on the position of the axis origin. In this process, check the position of the moving electrode and the feedback current (1A or less). If the moving electrode are in a position of slightly contacting the fixed electrode, press ‘**Yes**’ to continue the setting. If the feedback current is high or the moving electrode and the fixed electrode are not in contact, carry out fine adjustment using the jog key and then press ‘Yes’. If you do not want automatic setting, please click ‘**No**’ to end the setting.

<p align="center">
 <img src="../../_assets/image_76_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 2.6 Confirmation with the user on the position of the axis origin</p></em>
</p>

{% hint style="warning" %}
[**Warning**] If the servo gun has a stopper other than a metal material such as a bumper attached at the maximum opening position of the servo gun, it may be difficult to estimate the maximum opening position. It is recommended to perform setting after removing the stopper.
{% endhint %}

The configuration and functionality of the servo gun default setting screen is as follows.

<p align="center">
 <img src="../../_assets/image_62_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 2.7 Configuration of the default setting</p></em>
</p>

>1. **Status**: Shows the current setting status of the servo gun (X: Before setting, O: Either complete or changed)
>2. **Individual automatic setting**:  Supports the function of automatically setting the checked items only, not all. Pressing the 『**Selected item automatic setting**』 key will allow automatic setting to be performed only for the checked items.
>3. **Manual setting**: To move to the screen for setting the relevant items.  
    - Encoder offset compensation: To move to the screen of 『**Setting**』 → 『**3: Robot parameter**』 → 『**4: Encoder offset**』   
    - Axis origin setting: To move to the screen of 『**Setting**』 → 『**3: Robot parameter**』 → 『**2: Axis origin**』   
    - Soft limit setting: To move to the screen of『**Setting**』 → 『**3: Robot parameter**』 → 『**3: Soft limit**』   
    - Squeeze force - current table setting: To move to the screen of 『**Setting**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 → 『**7: Servo gun squeeze force tuning**』  
>4. **Guide**: Indicates the current status of settings or the cause and measure in case of occurrence of an error.
>5. **Monitoring**: Indicates the current status of settings and the position of the servo gun, the feedback current, the set values, etc.
>6. **All automatic setting**: Commands the execution of all automatic setting of all items
>7. **Selected item automatic setting**: Automatically sets only the items that are designated as the items of individual automatic setting
>8. **Execution stop**: Stops the setting that is in progress.# 2.3.2 Manual setting

The procedure for manually performing the default setting of the servo gun is as follows.

1. Servo gun encoder offset setting
2. Servo gun axis orign setting
3. Servo gun soft limit setting
# 2.3.2.1 Servo gun encoder offset setting

Normally, when the encoder data is changed because of replacement of the servo gun motor, etc., the origin of the encoder should be set at a position that can match the same mechanical position. In the case of the servo gun, the setting should be performed with the moving electrode in the mechanically maximum open state.

The encoder compensation procedure for the axis of the servo gun is as follows.

(1) Manually release the brake of the axis of the servo gun and then open the moving electrode to the maximum.

<p align="center">
 <img src="../../../_assets/image_71_eng.PNG"></img>
 <em><p align="center">Figure 2.8 Servo gun's maximum open position</p></em>
</p>


(2) In the default setting screen of the‘**Servo gun automatic setting**’ menu, press the [**Manual setting**] button of the ‘**Encoder offset compensation**’ menu (Figure 2.9), or select the relevant servo gun axis in  『**Setting**』 → 『**3: Robot parameter**』 → 『**4: Encoder offset**』 with the cursor and then press the [**Reset**] button. When the current encoder value becomes “**00400000**”, press the [**OK**] button. 

<p align="center">
 <img src="../../../_assets/image_36_eng.PNG" width=80%></img>
 <em><p align="center">Figure 2.9 Moving to the encoder offset compensation screen</p></em>
</p># 2.3.2.2 Servo gun axis origin

In general, the axis origin of the servo gun should be set at the position where both the moving and fixed electrodes, with a new tip attached individually, meet each other. As most operations of the servo gun are performed with this axis origin as the reference, it is very important to carry out setting for this.

The axis origin setting procedure for the axis of the servo gun is as follows.

1) Manually operate the axis of the servo gun to bring it into the state as shown in the figure below.

<p align="center">
 <img src="../../../_assets/image_19_eng.PNG"></img>
 <em><p align="center">Figure 2.10 Position of the origin of the servo gun</p></em>
</p>

1) In the default setting screen of the ‘**Servo gun automatic setting**’ menu, press the [**Manual setting**] button of the ‘**Axis origin setting**’ menu (figure below), or select the relevant axis of the servo gun in 『**Setting**』 → 『**3: Robot parameter**』 → 『**2: Axis origin**』 with the cursor and then press the \[**Reset**] button. When the current position of the axis is indicated as 0.0 mm, input by selecting the \[**OK**] button. 


<p align="center">
 <img src="../../../_assets/image_80_eng.PNG" width="80%"></img>
 <em><p align="center">Figure 2.11 Moving to the axis origin screen</p></em>
</p>
# 2.3.2.3 Servo gun soft limit

In general, the soft limit of the servo gun should be set to 'Minimum' while the moving electrode is fully open, and set to 'Maximum' while the moving electrode is at the closest position with all tips removed.

The soft limit setting procedure for the axis of the servo gun.

1. Manually operate the servo gun to bring it to the condition as shown in the figure below


<p align="center">
 <img src="../../../_assets/image_90_eng.PNG" ></img>
 <img src="../../../_assets/image_2_eng.PNG" ></img>
 <em><p align="center">Figure 2.12 Setting of the servo gun soft limit</p></em>
</p>

2. In the default setting screen of the ‘**Servo gun automatic setting**’ menu, press the [**Manual setting**] button of the ‘**Soft limit setting**’ menu (Figure below), or select the relevant axis of the servo gun in 『**Setting**』 → 『**3: Robot parameter**』 → 『**3: Soft limit**』 with the cursor and then press the \[**Reset**] button. If the indication is performed normally, input by selecting the \[**OK**] button.

<p align="center">
 <img src="../../../_assets/image_41_eng.PNG" width="80%"></img>
 <em><p align="center">Figure 2.13 Moving to the servo gun soft limit setting screen </p></em>
</p># 2.3.3 Servo gun squeezing force - current table tunning

To squeeze the various servo guns, which are to be installed to the robot, with the desired squeezing force, it is necessary to make the current supplied to the servo gun correspond to the generated squeezing force. For this, our company provides a servo gun squeezing force - current table. It is necessary to tune this table to match with the servo gun. The accuracy of this tuning determines the accuracy of the servo gun squeezing force. In consideratin of it, tuning must be performed before using the servo gun.

To use this function, it is necessary to select five representative values among the squeezing forces to be used. Tuning the servo gun squeezing force - current table is a process to find the currents that match with these five representative squeezing forces. This table can vary depending on the posture of the servo gun, so it is necessary to perform tuning for each case of when the direction of the moving electrode is in the gravity direction and in anti-gravity direction, and, through this method, squeezing can be performed with high accuracy in various postures of the servo gun.

Our company provide manual mode for the tuning of the servo gun squeezing force - current table.

*   Tuning in manual mode

    Tuning can be performed regardless of the communication with the squeezing force gauge, and the user can directly tune the table by inputting the measured squeezing force.
# 2.3.3.1 Manual tuning mode

The manual tuning mode is a function to manually perform the servo gun squeezing force – current table setting. After the servo gun squeezing occurs, if the user directly inputs the measured squeezing force by using the teaching pendant, the optimal command current will be automatically calculated. This process should be repeated to increase the accuracy. The accuracy can be verified by the degree of convergence and test squeezing.

The procedure for setting the servo gun squeezing force – current table in manual mode, recommended by our company, is as follows.

<p align="center">
 <img src="../../../_assets/image_84_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.14 Servo gun manual tuning screen</p></em>
</p>
 

>1. Set the direction of the moving electrode that needs tuning (gravity or anti-gravity).
>2. With the \[**Shift**] + \[**Servo gun manual pressure**] keys or by jogging the axis of the servo gun, bring the moving electrode to the position where it can contact the squeezing force gauge, and then measure the thickness of the squeezing force gauge (distance between electrodes).
>3.  Input the measured thickness into the squeezing force gauge thicknes section shown at the upper part of the screen (distance between electrodes).
>4. Input the desired representative value of the squeezing force that you want to set into the ‘**Set squeezing force**’ section.
>5. Squeeze the servo gun according to the line that indicates the set squeezing force with which you want to perform squeezing. (In the figure below, squeezing is performed with 100 kfg currently indicated with a green focus. svgun man press: \[**Ctrl**]/\[**Shift**] + \[**Servo gun manual pressure**])
>6. Input the squeezing force measured with the squeezing force gauge into the ‘**Measured squeezing force**’ section.
>7. Repeat steps 3–6 for all set squeezing forces.
>8. After completing the inputting, press the \[**Command current calculation**] button to calculate the command current that matches the set squeezing force.
>9. When necessary to check the degree of convergence and perform repetead calculation of the command current through test squeezing, repeat steps 3–8.
>10. If you want to calculate only the command current for a specific squeezing force, input the measured squeezing force and then execute the \[**Command current individual calculation**] process.
>11. Save the current setting by pressing \[**Save**]. After that, change the direction of the moving electrode and then repeat steps 1–8 above.

</br>

To squeeze the servo gun, you should press \[**Shift**] + \[**Servo gun manual pressure**] keys or \[**Ctrl**] + \[**Servo gun manual pressure**] keys. Considering that with the \[**Ctrl**] + \[**Servo gun manual pressure**] keys, you can perform controlling in the same manner as the automatic mode does, it is recommended to use \[**Ctrl**] + \[**Servo gun manual pressure**] keys. 

The figure below is a screen showing the state after performing ‘command current calculation’ twice. If the degree of convergence is low enough, it is needed to carry out squeezing with the set squeezing force and check the difference with the measured pressure, and then decide whether to continute to proceed.

At least one measured squeezing force should be inputted for the command current calculation. If the initial command current exceeds the range where the servo gun can perform squeezing, you can reset the initial value by inputting only one or two measured squeezing forces and then performing the ‘command current calculation.’ If the command current calculation is performed without inputting all of the measured squeezing forces, the overall accuracy will be lower. Considering it, it is recommended to perform ‘command current calculation’ after inputting all measured squeezing forces, except for the case of resetting the initial command current.

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

    This is the number of times the command current has been updated by pressing the ‘Command current calculation’ key so far. If the degree of convergence does not decrease after several repetitions, use the ‘Command current individual calculation’ key or check the state of the squeezing force gauge and servo gun.
*   **Measured currrent**

    This is the currently measured current and will be monitored in a way that it can get close to the command current when squeezing is performed.

{% hint style="info" %} \[**Caution**]
The operation by selecting \[**Ctrl**] + \[**Servo gun manual pressure**] keys will work until the squeezing is completed with one execution, making it impossible to stop the operation by releasing the button in the middle. Therefore, stopping the squeeze operation requires you to release the enable switch or press the emergency stop button. Also, if the squeezing force gauge thickness is different from the actual value, the squeezing force will be different in automatic mode. So please input the correct value.

You can set and operate the servo gun using the function buttons on the right side of the current screen. The related settings and operations are as follows.

* \[**Shift**] + \[**Servo gun wide opening**]: To open the servo gun wide (opening it as much as the indicated opening distance)
* \[**Shift**] + \[**Servo gun narrow opening**]: To open the servo gun narrow (opening it as much as the indicated opening distance)72 open
* \[**Shift**] + \[**Servo gun manual pressure**]: To squeeze the servo gun (squeezing with the squeezing force at which the cursor is currently located)
* \[**Ctrl**] + \[**Servo gun wide opening**]: To set the distance for the servo gun wide opening
* \[**Ctrl**] + \[**Servo gun narrow opening**]: To set the distance for the servo gun narrow opening
* \[**Ctrl**] + \[**Servo gun manual pressure**]: To squeeze the servo gun (squeezing with the squeezing force at which the cursor is currently located and performing the same controlling as in automatic mode)
{% endhint %}# 2.4 Step 2. Application setting

When the default setting is completed, the application setting can be performed. The application setting is the item that can be performed after the ‘**squeezing force - current table tuning**.’ It consists of a procedure for setting the reference position for the gun search, a procedure for estimating the amount of the servo gun arm deflection during the squeeze operation, and a compensation procedure for accurate measurement of the panel thickness.

The application setting consists of three items as shown in the figure below.

<p align="center">
 <img src="../../_assets/image_58_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.15 Servo gun application setting screen</p></em>
</p>

>1. **Gun search**
>     * Sets the reference position for measuring the consumption amount of the tip and checks the consumption amount once.
>     * For manual setting, refer to “[**4.1 Gun search**](../../4-work-teaching/4-1-gun-search/).”
>2. **Gun arm deflection amount compensation**
>      * The gun arm deflection amount compensation should be set to compensate for the gun arm deflection that occurs when the servo gun performs squeezing. Sets the deflection amount according to the squeeze force set in the squeezing force – current table.
>      * For manual setting, press the Manual setting key in the figure above, or, in the screen of『**Setting**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 → 『**3: Weldin gun parameter**』, set the gun number that needs to be set and then press 『**Application condition**』 to enter.
>3. **Panel thickness measurement compensation**
>      * The panel thickness measurement compensation is a setting to improve the accuracy of the panel thickness measured with the ThickCheck command.
>     * For manual setting, press the Manual setting button in the figure above, or, in the screen of『**Setting**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 → 『**3: Welding gun parameter**』, set the gun number that needs to be set and the press the 『**Application condition**』 key to enter.

Among the application setting items, the ‘gun search’ setting is essential. If ‘gun search’ is not set, it is impossible to execute and teach commands related to spot welding (for example, spot gn=1,…). On the other hand, '**gun arm deflection amount compensation**' and '**panel thickness measurement compensation**' has nothing to do with the execution and teaching of commands related to spot welding, but are necessary settings for accurate operation and accurate panel thickness measurement.

The application setting can be progressed in automatic setting and manual setting.

   (1) **Automatic setting**  
   * The servo gun automatically moves to execute ‘**gun search**’, ‘**gun arm deflection amount compensation**’ and ‘**panel thickness measurement compensation**’. All items of the application setting can be performed automatically.  
  
   (2) **Manual setting**  
   * The user directly performs ‘**gun search**’ and inputs the ‘**gun arm deflection amount compensation**’ and ‘**panel thickness measurement compensation**’ values.  
# 2.4.1 Automatic setting

Progress the automatic setting of the application setting of the servo gun by pressing the 『**All automatic setting**』 key. In the case of ‘**all automatic setting**’, the moving electrode of the servo gun moves automatically. In addition, the set values are affected by the squeezing force, so the following conditions must be satisfied.

* Moving and fixed electrodes with new tipes attached
* No worker around the servo gun
* No workpiece between the moving electrode and fixed electrode
* Manual mode
* Motor on
* Completion of the servo gun's default setting (step 1) 


In the case of ‘**all automatic setting**’, the following procedures will proceed automatically.

1. Gun search
   * Gun search will be performed while servo gun squeezing occurs two times.
   * First time: ‘Gun search reference position record’ valid
   * Second time: ‘Gun search reference position record’ invalid 
2. Gun arm deflection amount compensation
   * Gun arm deflection amount compensation will be performed while servo gun squeezing occurs five times.
3. Panel thickness measurement compensation  
   * Gun arm deflection amount compensation will be performed while servo gun squeezing occurs five times.

{% hint style="info" %}
\[**Caution**] The gun search that can be performed through ‘**automatic setting**’ is only for gun search 1. When using other gun searches other than gun search 1, you should refer to “[**4.1** **Gun search**](../../4-work-teaching/4-1-gun-search/)” of “[**4.** **Work teaching**](../../4-work-teaching/).”
{% endhint %}

&#x20;In the case of ‘all automatic setting’, the ‘gun arm deflection amount compensation’ and ‘panel thickness measurement compensation’ will be performed at the same time, so the servo gun performs squeezing only five times. For execution of ‘gun search’, the squeezing force and gun search speed should be designated. If you press the『Gun search condition setting』key in the aformentioned ‘Application setting’ screen, the squeezing force and moving speed that will be used during gun search can be set as shown in the figure below.


<p align="center">
 <img src="../../_assets/image_22_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.16 Gun search condition setting screen</p></em>
</p>

{% hint style="info" %}
\[**Caution**] In the case of ‘**gun arm deflection compensation**’ and ‘**panel thickness measurement compensation**’, it is difficult to manually measure and fill in the values, so it is recommended to use automatic setting.

The ‘gun arm deflection amount compensation’ value is a value used instead of the ‘gun arm deflection amount/100 kgf\[mm]’ among the servo gun parameters. When the ‘gun arm deflection amount compensation’ value is set, the already set ‘gun arm deflection amount/100 kgf\[mm]’ will not be used. On the contrary, if a ‘gun arm deflection amount compensation’ value is not set, the ‘gun arm deflection amount/100 kgf\[mm] will be used.’
{% endhint %}

The configuration and functionality of the servo gun application setting screen is as follows.

<p align="center">
 <img src="../../_assets/image_55_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.17 Servo gun applicaiton setting screen</p></em>
</p>

>1. **Status**: Shows the current setting status of the servo gun (before setting, complete or changed).
>2. **Individual automatic setting**: Supports the function of automatically setting the checked items only, not all. Pressing the 『**Selected item automatic setting**』 key will allow automatic setting to be performed only for the checked items.
>3. **Manual setting**: To move to the screen for setting the relevant items
>     *   Gun arm deflection amount compensation  
>       To automatically move to the screen of 『**Setting**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 → 『**3: Welding gun parameter**』
>     *   Panel thickness measurement compensation  
>         To automatically move to the screen of 『**Setting**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 → 『**3: >Welding gun parameter**』
>4. **Guide**: Indicates the current status of settings or the cause and measure in case of occurrence of an error.
>5. **Monitoring**: Indicates the current status of settings and the position of the servo gun, the feedback current, the set values, etc.
>6. **All automatic setting**: Commands the execution of all automatic setting of all items.
>7. **Selected item automatic setting**: Automatically sets only the items that are designated as the items of individual automatic setting.
>8. **Execution stop**: Stops the setting that is in progress.
>9. **Gun search condition setting**: Sets the speed and squeeze force for gun search.
# 2.5 Step 3. Setting check

When the application setting is completed, you can check the setting performed so far through the ‘setting check’ procedure. The setting check procedure can be executed only when the default and application settings are completed.

 As shown below, When ‘**Step 0. Pre-inspection**', '**Step 1. Default setting**', and '**Step 2. Application setting**' are completed, press the 『**Proceed with the prior-to-setting items**』 key or bring the focus onto the '**Step 3. Setting check**' section and then press the Enter key to progress the setting check procedure.


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

When the setting check proceeds as the above conditions are satisfied, the screen changes to the ‘Application Setting’ screen to make it possible to monitor the movement status of the servo gun.

When the ‘setting check’ is completed, the error estimated during verification will be displayed. Considering that the displayed value is an error, if a value close to 0 is indicated, the setting can be regarded as normal. If the error is a value greater than zero, the setting should be performed again or it is needed to check for any change with the servo gun or surrounding environment. If the setting check result is satisfactory, press ‘Yes’ to end the ‘setting check’ procedure. If the result is unsastisfactory, press ‘No’ to perform resetting or check the servo gun or surrounding environment.
# 2.6 Step 4. Signal setting

Step 3. When Step 3. ‘Setting check’ is completed, it is now possible to move and squeeze the servo gun normally. However, for spot welding, it is necessary to set the inputs and outputs of the spot welding machine signals and other signals. In ‘Signal setting’, input and output signals related to spot welding can be set.

As shown in the figure below, move the cursor to '**Step 4. Input signal setting**' or '**Step 4. Output signal setting**' and then press the \[**Enter**] key or, while previous items are completed, if you press the 『**Proceed with the prior-to-setting items**』 key, you can enter the screen for setting relevant items.

<p align="center">
 <img src="../_assets/image_85_eng.PNG" width=70%></img>
 <em><p align="center">Figure 2.19 Servo gun signal setting</p></em>
</p>

>1. **Input signal setting**
>       * Refer to “[**5.4** **Input signal assignment**](../5-spot-weld-parameter/5-4-input-signal-assign.md)” of “[**5.** **Spot welding parameter**](../5-spot-weld-parameter/).”
>2. **Output signal setting**
>       * Refer to “[**5.5** **Output signal assignment**](../5-spot-weld-parameter/5-5-output-signal-assign.md)” of “[**5. Spot welding parameter**](../5-spot-weld-parameter/).”
> 
# 3. Related functions

# 3.1 Monitoring

Various current data and setting states that are used in spot welding are provided to the user in a way that they can be monitored. The monitoring screen related to spot welding is as follow.

* Spot welding gun axis data
* Spot welding input and output signals
* Spot welding operation information# 3.1.1 Spot gun axis data

This indicates the data of the currently selected spot gun in real time.

(『**Selection**』 → 『**Spot**』 → 『**Gun data**』)

<p align="center">
 <img src="../../_assets/image_18_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.1 Spot monitoring pane</p></em>
</p>

<p align="center">
 <img src="../../_assets/image_89_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.2 Spot gun data monitoring</p></em>
</p>

>*   **Current data (servo gun)**
>
>      Cur indicates the feedback current of the axis of the servo gun and Cmd indicates the current limit command value (A).
>*   **Squeezing force data (servo gun)**
>
>     ‘**The command current and feedback current are converted into squeezing force and displayed using the “squeezing force - current table**” of the welding gun parameter. Cmd indicates the command squeezing force and Cur indicates the feedback squeeze.&#x20;
>*   **Actual squeezing force during weling (servo gun)**
>
>     Indicates the average squeezing force from the point of the matching of the squeezing force to the time of opening.
>*   **Distance between electrodes (servo gun)**
>
>     Indicates the distance (mm) from the axis origin to the moving electrode.
>*   **Electrode consumption amount (servo gun, equalizerless gun)**
>
>     Inidicates the consumption amount (mm) detected through gun search. (In the case of the equalizerless gun, only the consumption amount of the fixed electrode is managed.)
>*   **Gun search status (servo gun, equalizerless gun)**
>
>     Indicates whether gun search is performed.
>*   **Welder number**
>
>     Indicates the welder number corredponding to the currently selected gun number.
>*   **SvClamp (servo gun)**
>
>     Indicates the status of the clamping operation of the currently selected gun.
# 3.1.2 Input and output signals

The input/output status of the assigned signals related to spot welding is organized and monitored for convenient use.

(『**Selection**』 → 『**Spot**』 → 『**Input and output signals**』)

<p align="center">
 <img src="../../_assets/image_40_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.3 Spot welding input/output signal monitoring</p></em>
</p># 3.1.3 Information of the operating time

This allows you to check the information of the operating time related to the spot welding.

(『**Selection**』 → 『**Spot**』 → 『**Operation information**』)

<p align="center">
 <img src="../../_assets/image_91_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.4 Spot welding operation information monitoring</p></em>
</p>

>*   **Total (after initialization)**
>
>      Indicates the operation time and welding count of each welder since initialization of the system.
>*   **Total (after input of power)**
>
>     Indicates the operation time and welding count of each welder since input of the power.
>*   **Latest cycle**
>
>     Indicates the operation time and welding count of each welder of the immediately preceeding cycle.
>*   **Current cycle**
>
>     Indicates the operation time and welding count of each welder of the current cycle.

---
-	Spot welding operation information clearing

When the spot welding operation information window is activated, the 『Clear』 button will be displayed. Pressing the button will bring up a dialog box for clearing the operation information as shown in Figure 3.5.

<p align="center">
 <img src="../../_assets/image_92_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.5 Spot welding operation information initialization screen</p></em>
</p># 3.1.3 State flag

Various necessary states related to spot welding will be indicate as shown in the screen below.

<p align="center">
 <img src="../../_assets/image_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.6 Indication of spot welding related states</p></em>
</p>


>-  **Welding condition and welding sequence (panel thickness)**
>       - Indicates the currently selected welding condition number and welding sequence number.
>       - Indicates the currently set panel thickness. Accurate setting is required because the position of the axis of the servo gun will be automatically created based on the set panel thickness during the recording of the welding steps of the servo gun. It is also possible to perform manual setting with R220. When the recording of the welding steps is performed after the \[**manual squeezing**] operation, the setting will be automatically performed by taking into consideration the current position of the servo gun.
>-  **Tool number**
>       - Indicates the tool number corresponding to the currently selected gun number. In other words, if you change the gun number, the tool number will automatically change to the tool number set in『**Setting]: >System**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 → 『**1: Setting of the tool number and gun type corresponding to the gun number**.
>-  **Gun number**
>       - This indicates the currently selected gun number, numbers of multiple guns, and servo gun separation state (![](<../../_assets/image_39_eng.PNG>)). For example, if G5 and G6 are indicated, it means that stationary guns G5 and G6 are selected for simultaneous welding. In addition , there is a mark of a lock, so you can konw that the servo gun is disconnected.&#x20;
>

# 3.2 Simple maintenance of the servo gun

This provides support to simply conduct a series of settings to restart the servo gun from a single window after repairing it. When you press the \[**CTRL**]+\[**GUN**] keys on the initial screen, a dialog box for simple maintenance will be displayed.

<p align="center">
 <img src="../_assets/image_26_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.7 Simple maintenance of the servo gun</p></em>
</p>

>*   **Serial encoder reset**  
>    Executes the “**encoder reset**” or “**error clear**” operation for the serial encoder attached to the servo gun motor. Power must be supplied again for the changed setting to be applied. When “encoder reset” is performed, the encoder information will be initialized after that, requiring you to newly perform the encoder offset setting, axis origin setting, and gun search reference position recording.
>*   **Encoder offset**  
>    Sets the encoder origin of the axis of the servo gun.  It should be set at the position where the moving electrode is maximally opened through the releasing of the brake manually.
>*   **Axis origin**  
>    Sets the axis origin of the servo gun. The axis origin of the servo gun should be set at the poistion where electrodes are in contact with each other after new electrodes are installed.
>*   **Gun search execution**  
>    Executes the gunsea command only by operating the axis of the servo gun at the current position.
>*   **Welding execution**  
>    Executes the spot command only by operating the axis of the servo gun at the current position.
# 3.3 User keys

This is a description of the user keys related to spot welding. There is a button for the user keys at the bottom right of the initial main screen. Each time you press the button, the registered menu changes. Press each user key related to spot welding twice to enter the relevant menu.


<p align="center">
 <img src="../_assets/image_33_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 3.8 Spot welding user keys</p></em>
</p>


>*   **Servo gun wide opening **  
>    Manually moves the servo gun to the wide opening position.
>*   **Servo gun manual closing**  
>    Manually moves the servo gun to the narrow opening position.
>*   **Servo gun manual squeezing**  
>    Manually spueezes the servo gun. 
>*   **Welding condition change**  
>    Manually changes the currently selected welding condition number.
>*   **Welding sequence change**  
>    Manually changes the currently selected welding sequence number.
# 3.4 Welding gun manual closing and squeezing

The procedure for manual closing and squeezing of the welding gun is as follows.

</br>

1. Check whether the mode is manual. In the case of the servo gun, input the operation preparation signal to drive the axis of the servo gun. 
2.  Select the gun number for the manual closing or squeezing operation. The method to select a gun number is as follows.

    | **Gun type** |   Whether to change  | R code |
    | :-----: | :---------: | :--------------: |
    | Sole gun |    For change of the welding gun  | R358 (welding gun connection/separation) |
    |    Sole gun     | Not for change of the welding gun |   R210 (welding gun selection)  |
    | Multiple guns |      -       |  R214 (selection of guns for simultaneous welding) |


3.  Check whether the following \[**user**] keys are registerd.



    |       **Wide opening**  |       **Narrow opening**    | **Manual squeezing**   |
    | :--------------------------------------: | :--------------------------------------: | :--------------------------------------: |
    | <img src="../_assets/image_86_eng.PNG"></img>|<img src="../_assets/image_16_eng.PNG"></img> | <img src="../_assets/image_43_eng.PNG"></img> |


1.  When you press the “\[**SHIFT**] and \[**user**]” keys at the same time, the following operation will be performed. When multiple guns are selected, all of the selected guns will operate in the same way.

    |                  **Servo gun**                 |
    | :--------------------------------------: |
    | <img src="../_assets/image_13_eng.PNG"></img> |



The servo gun has the following characteristics during the manual closing and squeezing operations.

* The servo gun automatically stops at the wide opening position, the narrow opening position, and the position where the squeezing force reaches the set value.
* The moving speed is the speed inputted in 『**2: Maximum speed during step forward/backward**』 in 『**Condition setting**.』 ![](<../_assets/image_48_eng.PNG>)
* If the set squeezing force is small, the servo gun will not move even when it is operated. Considering it, set a sufficient squeezing force (R211: Squeezing force setting).
* When it comes to multiple guns, if there is a difference in the moving distance between two guns, the gun that reaches first will stop while the other gun will stop after moving as much as the remaining distance.

<p align="center">
 <img src="../_assets/image_53_eng.PNG"></img>
 <em><p align="center">Figure 3.9 Spot gun manual operation</p></em>
</p>
# 4. Work teaching

# 4.1 Gun search

Gun search is a function to measure the consumption amount of an electrode. Use this function when you need to re-measure the consumption amount of the electrode after polishing it through tip dressing or after replacing the existing tip with a new one. If  the gun type is servo gun or equalizerless gun, the gun automatically compensates the squeezing position as much as the consumption amount when executing the spot command, which makes it essential to manage the consumption amount and shows that the accuracy of the consumption amount affects the welding quality.

 The types of gun search provided by our company and their simple characteristics are as follows.

*   **gunsea**

    This is the gun search function for a servo gun and is executed with one squeezing operation.

     The total consumption amount of the moving and fixed electrodes is measured and distributed according to the designated ratio.

    This function is used if the consumption ratio between the moving electrode and fixed electrode is the same or fixed.
*   **gunsea 2**

    This is the gun search function for a servo gun and is executed with one squeezing operation and one moving operation.

    The total consumption amount of the moving and fixed electrodes is measured (one squeezing operation) and then the moving electrode consumption amount is measured separately.

    This function is used if the consumption ratio between the moving electrode and fixed electrode is not fixed.
*   **igunsea**

    In the same way as gun search  2, this is the gun search function for a servo gun and executed with one squeezing operation and one moving operation. However, the moving electrode consumption amount is measured using a sensor.

    The total consumption amount of the moving and fixed electrodes is measured (one sequeezing operation) and then the moving electrode consumption amount is measured (one moving operation) separately.

    This function is used if the consumption ratio between the moving electrode and fixed electrode is not fixed.
*   **egunsea**

    This is the gun search function for an equalizerless gun and, in the same way as the igunsea function, the consumption amount is measured by receiving a sensor signal.

</br>
The gun search state can be checked from the /Monitoring/Spot section.
# 4.1.1 Execution sequence

<p align="center">
 <img src="../../_assets/image_23_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.1 Gun search execution sequence of the servo gun</p></em>
</p># 4.1.2 Commands related to gun search
---
(1) gunsea

    This is a statement to be used for executing gun search 1 when the gun type is servo gun or executing gun search 2 by using the squeezing force.

```
gunsea gun=<gun number>,sea=<search number>,pre=<squeezing force>,spd=<search speed>,mgun=<numbers of multiple guns>,mpre=<squeezing force for multiple guns>
```

|   **Item**   | <p align="center">   **Content**   </p>| 
|:--------: | ----------------------------------------------------------------- |
|   **Gun number**  | Designates the gun number to search.                |
|  **Search number**  | Designates the gun search 1 operation or gun search operation 2.                 |
|   **Squeezing force**  | Designates the command squeezing force for detection of squeezing force matching.            |
|  **Search speed**  | <p>Designates the operation speed of the gun's axis for the search operation.</p><p>The search speed is based on safe speed and the recommended speed is 10 mm/s.</p>         |
|  **Numbers of multiple guns** | Designates the numbers for multiple guns when executing gun search for multiple servo guns at the same time.                                                   |
| **Squeezing force for multiple guns** | <p>Designates the squeezing force when required to apply a different squeezing force for each servo gun when executing gun search for multiple servo guns at the same time</p><p>If it is not designated, the squeezing force of the default gun will apply.</p> |

{% hint style="info" %}
[Use example]

A case of executing gun search 1 for the servo guns 5 and 6 with the equalizing force 100 kgf and 200 kgf respectively

→ ```gunsea gun=5,sea=1,pre=100,mgun=6,mpre=200```

{% endhint %}

---
(2) igunsea

    This is a statement to be used for executing gun search 2 based on the input signal when the gun type is servo gun.

```
igunsea gun=<gun number>,spd=<search speed>,di=<input signal>
```

|  **Item**  |   <p align="center">   **Content**   </p>  |
| :------: | ---------------------------------------------------------------------- |
| **Gun number** | Designates the gun number to search                                                              |
| **Search speed** | <p>Designates the operation speed of the gun's axis for the search operation.</p><p>The search speed is based on safe speed and the recommended speed is 10mm/s.</p>    
| **Input signal** | Designates the input signal number for the reception of the phottube output.                                               |

</br>

---
(2) egunsea

    This is used when the gun type is equalizerless gun.

```
egunsea gun=<gun number>,spd=<search speed>,dist=<search distance>,di=<input signal>
```

|  **Item**  |  <p align="center">   **Content**   </p>   |
| :------: | ---------------------------------------------------------------------- |
| **Gun number** |  Designates the gun number to search                                                            |
| **Search speed** | <p>Designates the operation speed of the gun's axis for the search operation.</p><p>The search speed is based on safe speed and the recommended speed is 10 mm/s.</p>    
| **Input signal** | Designates the input signal number for reception of the phot tube output.         # 4.1.3 Gun search reference position record

The consumption amount of an electrode is measured based on an unconsumed new tip. Therefore, the process of registering the reference position with a new tip is absolutely necessary at least once in the beginning, and this is called gun search reference position record.

{% hint style="info" %}
[Caution]
**The gun search reference position must be recorded at least once before the execution of gun search**
{% endhint %}

 When it comes to the method of recording a gun search reference position, new tips should be attached first and then the recording should be executed according to the following procedures.


<p align="center">
 <img src="../../_assets/image_51_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.2 Use environment setting screen</p></em>
</p>


>1. Set 『**2: Gun search reference position record**』 to <**Valid**>.
>2. Execute the created gun search program. In the spot monitoring screen, the state of the gun search will be initialized to “**Incomplete**”.
>3. Set 『**2: Gun search reference position record**』 to <**Invalid**>. After that, the amount of variation compared to the reference position will be calculated as a consumption amount by using the gun search program.
# 4.1.4 Gun search operation by gun type

# 4.1.4.1 Servo gun

The gun search function of the servo gun is initially set in a way that the total electrode consumption amount reflects 50% of each of the fixed electrode consumption amount and moving electrode consumption amount. Therefore, the electrode consumption amount can be calculated by using only gun search 1. If you want to calculate the consumption amounts of the fixed and moving electrodes respectively, please refer to the description of gun search 2.

{% hint style="info" %}
\[Caution\]  
If the set value of『**Moving electrode consumption amount/Total consumption amount (%)**』 is “0”, the gun search 2 operation must be performed. If it is not “0”, the total consumption amount will be distributed according to the set ratio through the gun search 1 operation.
{% endhint %}

(1) Gun search 1

    Measures the total electrode consumption amount by making the moving electrode squeeze the fixed electrode.

<p align="center">
 <img src="../../../_assets/image_47_eng.PNG"></img>
 <img src="../../../_assets/image_7_eng.PNG" width="55%"></img>
 <em><p align="center">Firgure 4.3 Gun search 1</p></em>
</p>


>1. The servo gun moves to the record position of the step. 
>2. The fixed electrode is squeezed with the moving electrode until the set squeeze force is reached.
>3.  When the squeezing force matching is detected, the total electrode consumption amount is measured and the opening operation is executed.  
>    Total electrode consumption amount = Squeezing force matching detection position  - gun search 1 reference position
>4. The servo gun opens up to the record position of the step.
>5. In an environment where only gun search 1 is operating, the measured total electrode consumption amount is distributed according to the ratio between the moving electrode and fixed electrode as shown in the figure below. (default is 50 : 50.)

<p align="center">
  <img src="../../../_assets/image_70_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.4 Calculation of the electrode consumption amount through gun search 1</p></em>
</p>


(2) Gun search 2

Measures the moving electrode consumption amount. The measurement can be performed by using a squeezing force or an external signal.

*   **By using a squeezing force**

    Measures the moving electrode consumption amount by making the moving electrode squeeze the calibration jig.

<p align="center">
 <img src="../../../_assets/image_29_eng.PNG"></img>
 <img src="../../../_assets/image_4_eng.PNG" width="55%"></img>
 <em><p align="center">Figure 4.5 Gun search by using a squeezing force</p></em>
</p>

>1. Movement to the record position of the step occurs.
>2. The calibration jig is squeezed with the moving electrode through searching unitil the set squeezing force is reached.
>3.  When the squeezing force matching is detected, the moving electrode consumption amount is detected and the opening operation is executed.   
>    **Moving electrode consumption amount = Squeezing force matching detection position - reference position for gun search 2 that uses the squeezing force**  
>    **Fixed electrode consumption amount = total consumption amount detected by gun search 1 – moving electrode consumption amount**
>4. When the opening is completed, the consumption amounts of the moving and fixed electrodes are updated. 

*   **By using an external signal**

    When the moving electrode moves to the position where the sensor is located and then the input from the sensor is detected, the moving electrode consumption amount is measured.


<p align="center">
 <img src="../../../_assets/image_79_eng.PNG"></img>
 <img src="../../../_assets/image_73_eng.PNG" width="55%"></img>
 <em><p align="center">Figure 4.6 Gun search 2 that uses an external signal input</p></em>
</p>

>1. Movement to the record position of the step occurs.
>2. The moving electrode approaches at the search speed and switches the phototube contact signal.
>3.  When a signal is detected by the photo tube, the moving electrode consumption amount is detected and the opening operation is executed.  
 >   **Moving electrode consumption amount = External signal detection position - reference position for gun search 2 that uses the external signal**  
 >   **Fixed electrode consumption amount = total consumption amount detected by gun search 1 - moving electrode consumption amount**  
>4. When the opening is completed, the consumption amounts of the moving and fixed electrodes are updated.
# 4.1.4.2 Equalizerless gun

As an equalizerless gun only manages the consumption amount on the fixed electrode, so the gun search function here measures the fixed electrode consumption amount.


<p align=center>
 <img src="../../../_assets/image_64_eng.PNG"></img>
 <img src="../../../_assets/image_34_eng.PNG" width="55%"></img>
 <em><p align="center">Figure 4.7 Gun search of an equalizerless gun</p></em>
</p>


>1. Movement to the record position of the step occurs.
>2. The fixed electrode approaches at the search speed and switches the phototube contact signal.
>3.  When a signal is detected by the photo tube, the fixed electrode consumption amount is measured and the opening operation is executed.  
 >   **Fixed electrode consumption amount = sensor detection position - gun search record position**  
>4. When the opening is completed, the fixed electrode consumption amount is updated.
# 4.2 Spot welding

While the fixed and moving electrodes are squeezing, the current flows from the welder, allowing the spot welding to be performed.
# 4.2.1 Spot statement

)If the spot welding stops and restarts while spot welding is not completed, the spot welding step will be executed again. If the \[**GUN**] LED is turned on while the step is being recorded with the \[**Record**] key, the Spot statement will be recorded along with the Move statement. (one-touch recording method.)

 When recording the welding step, if you make the fixed electrode contact the panel through a jogging operation and then record the Spot statement in one-touch method, while squeezing the panel through a manual squeezing operation, the panel thickness will be set. Once the panel thickness is set, if you make the fixed electrode contact the panel through a jogging operation and then record the Spot statement in one-touch method without a manual squeezing operation, the recording will take place by taking into consideration the position for which the panel thickness and the consumption amount are compensated.

While the gun type is servo gun, if the Spot statement exists during \[**Position modification**], the position will be automatically modified to a position for which the electrode consumption amount is compensated.

</br>

**spot** gun=<gun number>,cnd=<condition number>,seq=<sequence number>,mgun=<numbers of multiple guns>,mcnd=<conditions of multiple guns>,mseq=<sequences of multiple guns>


<center>

|   **Item**    | 　    <p align=center>           **Content**        </p>    |
| :-----------: |------------------------------------------- |
|    **Gun number**    | Designates the welding gun number                                |
|    **Condition number**   | Designates the welding condition                        |
|   **Sequence number**  | Designates the welding sequence                     |
|   **Numbers of multiple guns**  | Designates the numbers of multiple guns when performing welding simultaneously with multiple guns    |
|  **Condition numbers of multiple guns** | To be designated when welding is performed simultaneously with multiple guns with individually different welding condition for each gun </br>If they are not designated, the welding condition of the default gun will apply.  |
| **Sequence numbers of multiple guns** | To be designated when welding is performed simultaneously with multiple guns with invidually different welding sequence for each gun </br> If they are not designated, the welding sequence of the default gun will apply. |

</center>

</br>

{% hint style="info" %}
\[Example of use\]  
- When performing spot welding using the servo guns 5 and 6 while applying welding conditions 7 and 8 respectively and welding sequences 9 and 10 respectively.

  ```spot gun=5,cnd=7,seq=9,mgun=6,mcnd=8,mseq=10```

{% endhint %}# 4.2.2 Welding sequence by gun type

The controller executes the spot statement in the program to make the welding work take place and the playback of the spot welding function may vary depending on gun type.
# 4.2.2.1 Servo gun

If the gun type is servo gun, the spot welding function is played back as shown in the figure below.

<p align="center">
 <img src="../../../_assets/image_66_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.8 Playback of servo gun spot welding</p></em>
</p>


>1. At the N-1 step position, the moving and fixed electrodes move to the positions away from the record positions as much as the ‘moving electrode clearance’ and ‘fixed electrode clearance’, respectively.
>2. With the robot equalizing operation, the fixed electrode moves to the record position of the step, and the moving electrode moves to the record position of the step by shifting as much as the consumption amount.
>3. The moving electrode performs the squeezing operation with the set squeezing force. When the squeezing force is matched, the welding execution signal is outputted together with the welding condition signal at the position.
>4. When the welding completion signal (WI) is inputted, the moving and fixed electrodes open as much as the individual clearances.
>5. Movement to the next step occurs.
# 4.2.2.2 Equalizerless gun

If the gun type is equalizerless gun, the spot welding function is played back as shown in the figure below.

<p align="center">
 <img src="../../../_assets/image_5_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.9 Playback of spot welding by ann equalizerless gun</p></em>
</p>

>1. At the N-1 step position, the fixed electrode moves to the position away from the record position as much as the ‘fixed electrode clearance.’
>2. With the robot equalizing operation, the fixed electrode moves to the recordd position of the step, and the pneumatic presssure makes the moving electrode squeeze the panel.
>3. When the squeezing force is matched, the welding execution signal is outputted together with the welding condition signal at the position.
>4. When the welding completion signal (WI) is inputted, the fixed electrode moves to the position away from the record position as much as the ‘fixed electrode clearance’ and the moving electrode moves to a position where pneumatic pressure is not supplied.
>5. Movement to the next step occurs.
# 4.2.2.3 Equalizer-fitted gun

If the gun type is equalizer-fitted gun, the spot welding function is played back as shown in the figure below.

<p align="center">
 <img src="../../../_assets/image_82_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.10 Playback of spot welding by an equalizer-fitted gun</p></em>
</p>

>1.At the N-1 step position, movement to the record position of the step occurs.
>2. The welding execution signal is outputted together with the welding condition signal. The equalizing facility makes the fixed electrode squeeze the panel and the pneumatic pressure makes the moving electrode squeeze the panel.
>3. When the welding completion signal (WI) is inputted, the fixed electrode moves to a position where the equalizing facility does not operate and the moving electrode moves to a position where pneumatic pressure is not supplied.
>4. Movement to the next step occurs.# 4.3 Servo gun trip dressing

# 4.3.1 Condition setting

The tip dressing condition for the servo gun can be set in 『**Setting**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 →『**4: Welding data (condition, sequence)**』 → 『**4: Servo gun tip dressing condition**.』 Refer to the relevant menus.
# 4.3.2 Type of operation

To perform a tip dressing operation using the servo tip dressing condition, the welding sequence number in the Spot statement must be designated as 64 as shown below.


<p align="center">
 <img src="../../_assets/image_77_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.11 Servo gun tip dressing operation</p></em>
</p>

>1. At the N-1 step position, the moving electrode moves to the position away from the record position as much as the moving electrode clearance and the fixed electrode moves to the position away from the record position as much as the fixed electrode clerance.
>2. Movement to the record position of the step occurs.
>3. The moving electrode performs the squeezing operation with the squeezing force set in the welding condition. When the squeezing force is matched, the welding condition signal is outputted at the position. Whether the welding execution signal is outputted together at this time can be determined by the state of the “**Welding signal output**” setting in the tip dressing condition.
>4. When the set tip dressing time passes, the moving and fixed electrodes open as much as the clearance of each, respectively.
>5. Movement to the next step occurs.
# 4.4 Servo gun opening position recording

The recording of the spot welding step of the servo gun is usually performed according to the following procedure.

1. Check that the state is the one-touch record state. (\[GUN] key LED turned on.)
2. Contact the fixed electrode of the servo gun to the workpiece.
3. Squeeze the moving electrode to the workpiece by performing manual squeezing operation.
4. Press the \[**Record**] key to record the Spot statement together with the  step. -> Automatic registration of the panel thickness
5. Separate the moving electrode with a manual closing operation.
6. Movement to the next position occurs.

 Servo gun opening position recording is a procedure without the steps (3) and (5) above, making it possible to save a significant amount of time. For this, the controller should know the thickness of the panel to weld.
# 4.4.1 Panel thickness registration

When it comes to the servo gun opening position recording, the position of the moving electrode will be calculated by using the pre-designated panel thickness, so the panel thickness should be registered. There are two provided methods of registering the panel thickness. One is that the user inputs it manually and the other is that the panel thickness is automatically registered while the panel is squeezed.
# 4.4.1.1 Manual input method

Execute “**R220: Set the panel thickness**” to input the panel thickness.


<p align="center">
 <img src="../../../_assets/image_14_eng.PNG" ></img>
 <em><p align="center">Figure 4.12 Panel thickness input</p></em>
</p># 4.4.1.2 Auto registration method

While the “**\[GUN] LED**” is turned on, perform manual squeezing and then press the \[**Record**] key. Then the panel thickness will be automatically registered.
# 4.4.2 How to teach

(1)  In a state that the panel thickness is registered, proceed with teaching while keeping the moving electrode open and only the fixed electrode in contact with the panel.



<p align="center">
 <img src="../../_assets/image_83_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.13 Method of working when the panel thickness is the same</p></em>
</p>

</br>

(2) When the panel thickness is changed, perform teaching after registering the panel thickness again.
# 4.5 Servo tool change

The servo tool change function is used to connect and separate the robot R1 axis and welding gun if there are two or more guns to perform work in combination with the robot R1 axis. For more details, refer to the Hi6 Servo Tool Change Function Manual.
# 4.5.1 Environment setting

The environment setting for servo tool change can be progressed according to the following order.

A.   Setting the tool number and gun type corresponding to the gun number

B.   Setting the servo tool parameter
# 4.5.1.1 Setting of the tool number and gun type corresponding to the gun number

In『**Setting**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 → 『**1: Setting of the tool number and gun type corresponding to the gun number**』, set the gun type and tool number targeted for the servo tool change.

<p align="center">
 <img src="../../../_assets/image_24_eng.PNG" width="70%"></img>
 <img src="../../../_assets/image_24_1png" width="70%"></img>
 <em><p align="center">Figure 4.14 Addition of a spot gun</p></em>
</p>


The figure 4.14 shows a case in which two servo guns are set as below.

* **Gun1**: Welder 1, tool number 0, servo gun, additional axis 2 -> Required to set the servo tool parameters
* **Gun2**: Welder 1, tool number 1, servo gun, additional axis 1 -> Required to set the servo tool parameters

 In the case of s gun set as servo gun, among the targets for servo tool change, the servo tool parameters of the concerned servo gun should be set as shown in the next section.
# 4.5.1.2 Servo tool parameter setting

 In『**Setting**』 → 『**4: Application parameter**』 → 『**11: Servo tool change**』 → 『**2: Servo tool parameter setting**』, set the gun type and tool number targeted for the servo tool change.

If the gun targeted for servo tool change is a servo gun, you need to set the parameter of the servo gun you want to use because the currently set parameter for the additional axis and the parameter of the servo gun you want to use may be different. When another welding gun is used with the welding gun change function, the set parameter will replace the value of the existing parameter for the additional axis, as shown in the figure below, the same setting items as the parameter for the additional axis are used.



<p align="center">
 <img src="../../../_assets/image_67_eng.PNG" width="75%"></img>
 <em><p align="center">Figure 4.15 Application of the parameter for the additional axis during tool change</p></em>
</p>


The setting items of the parameter for the servo tool are mostly the same as the setting items of the parameter for the additional axis. You need to add the servo gun that you have set in the screen for setting the tool number and gun type corresponding to the gun number. When the OK button is clicked, the additional axis number corresponding to the gun number will be automatically set.



<p align="center">
 <img src="../../../_assets/image_88_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.16 Additional axis parameter setting screen</p></em>
</p># 4.5.2 Connection/separation commands 

In the servo tool change environment, connection/separation of the servo gun can be done in two ways as below. When the servo gun is connected, the gun number and tool number are automatically changed according to the set values, and when the servo gun is separated, the gun number and tool number are automatically changed to 0.

(1) R358

This is a function for servo gun change by using a R code, and can be used in the motor on state (the enable switch is on) in manual mode.

Operation = **R358, #1, #2, #3**

| **Parameter** |   **#1**   | **#2** |    **#3**   |
| :------: | :--------: | :----: | :---------: |
|    Meaning    |    Connection/separation   |   Axis specification  |     Gun number     |
|   Set value   | Connection=1, Separation=0 |  Servo gun=1 | The number of the gun targeted for change |

| Example of use | R358,1,1,2 (connects the servo gun G2) |
| :--: | ----------------------- |
|      | R358,1,0 (separates the servo gun)      |

(2) toolchng

This is a function for welding gun change through the execution of a work program. 

```
toolchng on/off,chng=<target for change>,di=<connection complete signal>,wtime=<connection completion wait time>,mchng1=<targe for change>,mchng2=<target for change>,mchng3=<target for change>
```

|                            **on/off**                            |       **on**       |                    Connection of the servo tool                    |                                               |
| :--------------------------------------------------------------: | :----------------: | :-----------------------------------------: | :-------------------------------------------: |
|                               ****                               |       **off**      |                    Separation of the servo tool                   |                                               |
|                            **Target for change**                            |     **G1\~G16**    |         <p>Number of the welding gun to connect/separate </p><p>Welding gun number</p>         | <mark style="color:red;">Connection/separation of the relevant additional axis</mark> |
|                         **Mechanical connection completion check signal**                        |     **1\–4096**    | <p>Number of the input signal for</p><p>mechanical connection completion</p><p>check</p> |          <p>Parameter to be ignored in off state</p><p></p>          |
|     <p><strong>Connection completion</strong></p><p><strong>wait time</strong></p>     | **<0\–5.0> (sec)** | <p>Connection completion wait time</p><p>(Limitless waiting if no parameter exists or the value is 0)</p> |          <p>Parameter to be ignored</p><p>in off state</p>          |
| <p><strong>Target for change</strong></p><p><strong>(Simultaneous connection/seperation)</strong></p> |     **G1\–G16**    |                   Number of the welding gun to connect                 |          <p>Parameter to be ignored</p><p>in off state</p>         |

Connection completion will be finalized only after the mechanical connection and the internal processing of the robot controller are completed. The connection completion wait time is the time for waiting until both of the above two processes are completed.
# 4.5.3 Connection/separation timing


<p align="center">
 <img src="../../_assets/image_10_eng.PNG" width="60%"></img>
 <em><p align="center">Figure 4.17 Connection and seperation timing chart</p></em>
</p>

*   Connection

    If the robot and servo gun are mechanically connected during the execution of the connection command (toolchng on), the connection completion signal will be inputted, the connection will be processed inside the controller, the encoder power for driving the axis of the servo gun will be inputted, and the motor on operation will be executed.
*   Separation

     The separation command will execute the processing of the separation according to the sequence opposite to that of the connection command.
# 4.5.4 Sanple program


<p align="center">
 <img src="../../_assets/image_74_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 4.18 Tool change program</p></em>
</p># 4.6 Simultaneous welding with multiple guns

In general, spot welding is performed with one welding gun at a time. The function of simultaneous welding with multiple guns is the act of welding with multiple welding guns at the same time. For this, the gun type (servo gun, equalizerless gun, or equalizer-fitted gun) should be all the same.
# 4.6.1 Manual selection of multiple guns

<p align="center">
 <img src="../../_assets/image_32_eng.PNG" width="30%"></img>
 <em><p align="center">Figure 4.19 Additional axis parameter setting screen</p></em>
</p>

The procedure for selecting G1 (master) and G2 (slave) as multiple guns through the servo tool change function is as follows.

1. Select \[**R**]+\[**358**] and then connect G1. After the connection is completed, the parameter related to the additional axis to which G1 is assigned should be set.
2. Select \[**R**]+\[**358**] and then connect G2. After the connection is completed, the parameter related to the additional axis to which G2 is assigned should be set.
3. The state of the selected gun is indicated in state flag as follows.

{% hint style="info" %}
[Note]  
* **\[R]+\[210] for changing the master gun number**
  1. Environment with a sole gun → \[R]+\[210]+\[3] → Environment with a sole gun (Example: G1 → G3)
  2. Environment with multiple guns → \[R]+\[210]+\[1] → Environment with a sole gun (Example: G1 and G3 → G1)
* **\[R]+\[214] for selecting multiple guns**
  1.  When selecting another number different from the set gun number

      A. Environment with a sole gun → \[R]+\[214]+\[3] → Environment with multiple guns (Example: G1 → G1 and G3)

      B. Environment with multiple guns → \[R]+\[214]+\[2] → Environment with multiple guns(Example: G1 and G3 → G1, G3, and G2)
  2.  When selecting the same number as the set gun number

      A. Environment with multiple guns → \[R]+\[214]+\[3] →  Environment with multiple guns(Example: G1, G3 and G2 → G1 and G2)

      B. Environment with multiple guns → \[R]+\[214]+\[2] → Environment with a sole gun (Example: G1 and G2 → G1)

      C. The master gun number does not change.
{% endhint %}

# 4.6.2 Support functions

The functions to be provided for simultaneous weldig with multiple guns is as follows.

1. Manual closing
2. Manual squeezing
3. spot statement
4. gunsea statement
# 4.7  Detection of panel thickness abnormality during the welding with servo gun

 This is a function to measure the panel thickness during the welding with a servo gun to detect any abnormality with parts and any missing of installation of materials. The function can be executed simply by adding the “thickcheck” statement. Whether the panel thickness is abnormal should be determined based on whether the measured value is within the normal range.

<p align="center">
 <img src="../_assets/image_49_eng.PNG" width="40%"></img>
 <em><p align="center">Figure 4.20 Inspection of the panel thickness with the servo gun</p></em>
</p>

* **thick**

    Designates the variable to store the measured panel thickness by squeezing the servo gun.
* **ref**

    Designates the normal panel thickness.
* **tol**

    Designates the toleranc.
* **addr(branch line)**

   Designates the method of handling when panel's abnormality is detected. If the branch line is not recorded, the situation “**E1493 Measured panel thickness exceeded the normal range**” occurs and then the robot stops and the output signal set in the “**Panel thickness abnormal**” section is turned on. If the branch line is recorded, the situation “**W0152 Measured panel thickness exceeded the normal range**” occurs and the robot continues to operate as the program jumps to the branch line. In this case, the output signal set in the “**Panel thickness abnormal**” section is turned on only for 200 ms.



{% hint style="warning" %}
[Caution]  

The following should be in place first for accurate measurement of the panel.

1. Gun search (precise management of the consumption amounts of the moving and fixed electrodes)
2. Setting of gun arm deflection amount (Setting of the gun arm deflection amount for each squeezing force)
3. Setting of panel thickness(Setting of the panel thickness for each squeezing force)
{% endhint %}
# 4.8 Handling of workpieces with the servo gun

 This is a function to transport a workpiece in small size without using a separate hanger.

<p align="center">
 <img src="../_assets/image_52_eng.PNG" width="50%"></img>
 <em><p align="center">Figure 4.21 Servo gun's handling function</p></em>
</p>

The “**svclamp**” statement can be used to hold a workpiece and perform opening operation. In the svclamp on state, the servo gun does not open.

<p align="center">
 <img src="../_assets/image_12_eng.PNG" width="50%"></img>
 <em><p align="center">Figure 4.22 svclamp command program</p></em>
</p>
# 4.9 Calculation of spots in spot welding

The following system variable stores the count of the inputs of WI during the execution of the spot welding command.

```
_spotrunno[welder number]
```

|       **Item**      | 　　　　　　　　　　**Content**      |
| :---------------: | --------------------- |
| **Welder number\[1\–4]** | Designates the welder number (totally up to four numbers) |

</br>

The above variable will be initialized to 0 when a new job program is executed after one cycle of the job program is completed, or when \[**R**]+\[**Enter**] is pressed to make a forced shifting to the first line of the job program..

```
Use example 1)
V1%=_spotrunno[1]  ‘Stores the number of WIs inputted through the welder 1 up to now into V1%

Use example 2 )
IF 10<>_spotrunno[1]	‘PRINT #0 if the number of WIs inputted throug the welder 1 up to now is not 10,“Welding count (“; _spotrunno[1];”) error !!”	‘Error message print
STOP						 	‘Stop
ENDIF
END
```

{% hint style="warning" %}
\[**Caution**]: The spot command executed in the sub task will not be calculated.
{% endhint %}

# 4.10 Consumption amount setting

The following system variable sets the gun's total consumption amount arbitrarily, or stores the total consumption amount measured through the gun search function.
.

```
_tipwear[gun number]
```

|      **Item**      | 　　　　　　　　　　**Content**       |
| :--------------: | ---------------------- |
| **Gun number\[1\–16]** | Designates the welding gun number (totally up to 16 numbers) |

If the consumption amount is arbitrarily set using the above variable, the total consumption amount will apply to the moving and fixed electrodes according to the ratio set for the moving electrode consumption amount. The value will be maintained until the execution of gun search.

```
Use example 1)
V1!=_tipwear[1]  	Sets the consumption amount of the gun 1, measured through gun search, in V1!

Use example 2)
_tipwear[2]=V1!		Sets the total consumption amount of the gun 1 in V1!
```

{% hint style="warning" %}
\[**Cautio**]: This variable can apply only to servo and equalizerless guns. In the case of the equalizerless gun, the total consumption amount equals the fixed electrode consumption amount.
{% endhint %}
# 5.  Spot welding parameters

# 5.1 Use environment setting

Sets the use environment related to spot welding to perform appropriate operation for given situations.

<p align="center">
 <img src="../_assets/image_20_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 5.1 Spot use environment setting screen</p></em>
</p>

</br>

(1)  **Servo gun spot statement execution method**
    
    During the execution of the Spot statement, if the type of the relevant gun is servo gun, it is possible to prohibit the squeezing operation from being executed and the welding signal from being outputted regardless of the welding sequence. Accordingly, this function can be usefully applied to check the teaching position. The sequence for execution of the spot welding will be as follows depending on the state of this setting. 



<center>

|Output method| <p align=center> Content </p>|  
|:---:|----------------------------------------------------|  
|Wd-On|Executes every welding sequence designated in the spot welding function. </br> Clearance position → Squeezing → Squeezing force matching inspection → Welding signal output </br> → Welding completion wait → Clearance position |
|Sq-On|Executes the welding sequence except for the signals related to welding. </br> Clerance position → Squeezing → Squeezing force matching inspection → Clerance position|
|Sq-Off|Does not perform squeezing operation, electrification signal output, WI wait, etc.</br>Clearance position|

</center>


</br>

(2)  **Gun search reference position record**

    In the case of a gun type (servo gun, equalizerless gun) for which the controller manages the tip consumption amount, the reference position should be determined first, and then the actual c35onsumption amount will be calculated based on it.
    
-   Invalid
  
      The actual consumption amount is calculated based on the determined reference position.
-   Valid
      As the reference position is to be determined to calculate the consumption amount, >>> it would be no problem to perform recording once initially while new tips are attached.


(3)  **Unit of the servo gun force**

    Selects the unit of the squeezing force for the control of the servo gun.
(4)  **Automatic adjustment of servo gun welding step record position**

    Selects whether to adjust the position of the servo gun in the Move statement recorded in consideration of the panel thickness measured while the gun is squeezed during the execution of the Spot statement. Set it to “Valid” after teaching is completed or deformation of the servo gun has occurred. After that, play back the work program once in automatic mode, then the record position will be simply adjusted based on optimal conditoins. With those features, this function can be usefully applied.

# 5.2 Welding gun parameter

If the gun type is servo gun or equalizerless gun, individual parameters can be set for each gun.

# 5.2.1 Servo gun

 If the gun type is servo gun, a screen for setting the parameters related to the servo gun will be indicated as shown below.
# 5.2.1.1 Servo gun default setting

<p align=center>
<img src="../../../../_assets/image_44_eng.PNG" width="70%"></img>
<img src="../../../../_assets/image_87_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.2 Servo gun default setting screen</p></em>
</p>

(1)  **Distance during manual opening operation (mm)**

    Designates the target position in performing wide and narrow opening operations of the servo gun by using the user key.
(2)  **Maximum electrode consumption amount (mm)**

    If the moving or fixed electrode consumption amount detected through gun search exceeds the set value, an error will be outputted and the operation will stop.
(3)  **Electrode replacement required consumption amount (mm)**

    If the moving or fixed electrode consumption amount detected by gun search exceeds the value set here, an electrode consumption alarm signal, together with a warning message, will be outputted to notify the need for replacement of the electrode. When it is set to 0.0 mm, abnormality will not be detected.
(4)  **Gun arm deflection amount/100\[Kgf]\(mm)**

    Sets the amount of gun arm deflection caused by the squeezing force to a deflection amount for 100 kgf. During the spot welding, squeezing will be performed by calculating the gun arm deflection amount not only from this set value and also from the command squeezing force.


<p align=center>
<img src="../../../../_assets/image_50_eng.PNG" ></img>
<em><p align="center">Figure 5.3 Gun arm deflection amount/100Kgf graph</p></em>
</p>

(5)  **Degree of squeezing force (%)**

    During the squeezing force matching process, squeezing force matching detection will occur if the real squeezing force reaches within the range of the accuracy of squeezing force, in comparison to the command squeezing force. If this value is set to 0, the notification 『W0110 Set in a way that squeezing force detection does not occur』 will be outputted and squeezing force matching will not be performed.
(6)  **Time for detection of abnormal squeezing force (s)**

    Sets the time from the start of squeezing to the matching of squeezing force. If squeezing force matching occurs within this time, the welding signal will be outputted immediately. If squeezing force matching does not occur, the notification 『**E1314 Exceeds the time for detection of abnormal squeezing force**』 will be outputted and stopping will occur. If the time is set to 0.0 sec, the squeezing force matching detection will continue to wait.
(7)  **Command value offset (mm)**

    When the Spot statement is executed, a squeezing force should be generated by the servo gun. For this, the moving electrode will be commanded to move to the squeezing position. The squeezing position refers to a position where the ‘command value offset’ is added to the record position in the direction of squeezing.
(8)  **Gun type**

    Selects the type (robot gun, stationary gun) of the selected servo gun. In the case of using a stationary servo gun, the user coordinate system number in which the coordinate system of the stationary gun is set in advance should be set. (it will be the robot coordinate system if the value is 0.). The user coordinate system should be set in a way that the travel direction of the fixed electrode becomes the the Z (+) direction.

<p align=center>
<img src="../../../../_assets/image_81_eng.PNG" ></img>
<em><p align="center">Figure 5.4 Stationary gun coordinate system</p></em>
</p>
 
(9)  **Moving electrode consumption amount/Total consumption amount (%)**

    When it comes to the method to measure the consumption amount of the servo gun, one is to perform the measurement only through gun search 1 and the other is to perform the measurement by using both gun search 1 and gun search 2.

    If the value is set to 0. the consumption amount will be calculated by using both gun search 1 and gun search 2. If the value is set to a value other than 0, the total consumption amount measured through gun search 1 will be distributed between the moving electrode consumption amount and fixed electrode consumption amount at the set ratio (%). 
(10)  **Real-time squeezing force control**

    Sets whether to use the real-time squeezing force control function. This is a function to perform controlling to ensure that the set squeezing force can be reached by using the actual squeezing force measured with a squeezing force gauge. If this function is set to valid, the 『 Real-time signal』 key will be activated, making it possible to set the parameter.
(11)  **Squeezing force - current table**

    A squeezing force table can be created in five levels as desired by the user by measuring the squeezing force with a squeezing force gauge. If the squeezing force is set differently for the gravity direction and anti-gravity direction, the compensation for the squeezing force will occur in line with the operating direction of the gun. 

    This squeezing force - current table sets the current values for the squeezing values in five levels. The table should be set in a way that the squeezing force - current value increases as the level goes up. The upper and lower limits inputted for the squeezing force will be used as the limiting range of the squeezing force during playback or manual operation.

<p align=center>
<img src="../../../../_assets/image_54_eng.PNG" ></img>
<img src="../../../../_assets/image_11_eng.PNG" ></img>
<em><p align="center">Figure 5.5 Gravitation direction and anti-gravitation direction</p></em>
</p># 5.2.1.1.1 Real-time squeezing force control

Real-time squeezing force control is a function to improve the accuracy of servo gun's squeezing force by using the data, measured by the squeezing force gauge, for control. For real-time squeezing force control, the squeezing force gauge should communicate with the robot controller and should be set to relevant communication specifications using the menus below.

<p align=center>
<img src="../../../../_assets/image_30_eng.PNG" width="70%"></img>
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


# 5.2.1.2 Servo gun application setting


<p align=center>
<img src="../../../_assets/image_6_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.7 Servo gun application setting</p></em>
</p>


(1)  **Gun arm deflection amount (mm)**

     Sets the gun arm deflection amount for the squeezing force set on the left. Considering that it is difficult to manually measure and fill in the values, it is recommended to use servo gun automatic setting. If you press ‘Default value calculation’, the value of 0.31 mm per 100 kgf will be set as the default value.
 
(2)  **Panel thickness compensation(mm)**

      Sets the panel thickness compensation amount for the squeezing force set on the left. Considering that it is difficult to manually measure and fill in the values, it is recommended to use servo gun automatic setting.

{% hint style="warning" %}
[**Caution**]   When it comes to ‘gun arm deflection amount compensation’ and ‘panel thickness measurement compensation’, it is difficult to manually measure and fill in the values, it is recommended to use servo gun automatic setting.

The ‘gun arm deflection amount compensation’ value is a value used instead of the ‘gun arm deflection amount/100 kgf\[mm]’ among the servo gun parameters. When the ‘gun arm deflection amount compensation’ value is set, the already set ‘gun arm deflection amount/100 kgf\[mm]’ will not be used. On the contrary, if a ‘gun arm deflection amount compensation’ value is not set, the ‘gun arm deflection amount/100 kgf\[mm] will be used.’
{% endhint %}
# 5.2.2. Equalizerless gun

If the gun type is “eqaulizerless gun”, a screen for setting the parameters related to the equalizerless gun will be indicated as shown below.


<p align=center>
<img src="../../_assets/image_42_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.8 Equalizerless gun setting</p></em>
</p>


(1)  **Maximum fixed electrode consumption amount (mm)**

    If the consumption amount measured by the egunsea statement exceeds the value set here, an error will be generated.
(2)  **Fixed electrode replacement required consumption amount (mm)**

    If the consumption amount measured by the egunsea statement exceeds the value set here, a warining will be outputted.
(3)  **Equalizing speeed (mm/s)**

    Sets the robot's equalizing speed.
(4)  **Gun type**

    Selects whether the selected equalizerless gun is a ‘robot gun’ or a ‘stationary gun’. Please refer to 『**2.3.1 Servo gun parameter**.』
(5)  **Gun arm deflection amount/100\[Kgf]\(mm)**

     Sets the deflection amount caused by the squeezing force as the deflection amount for 100 kgf. For the position of the fixed electrode for the execution of spot welding, calculate the gun arm deflection amount both from this value and the command squeezing force and then make some compensation for it and then perform squeezing. 
# 5.3 Welding data (condition, sequence)

Sets various parameters related to spot welding to perform appropriate operation in line with the work environment.



<p align=center>
<img src="../../_assets/image_59_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.9 Welding data setting</p></em>
</p>
# 5.3.1 Common data

Sets the data to be commonly applied regardless of the sequence of the spot welding.


<p align=center>
<img src="../../_assets/image_63_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.10 Common data setting</p></em>
</p>

</br>

*  The number of re-weldings

    If there is no input of WI even when the set welding completion (WI) wait time is exceeded, re-welding will be executed. the number of re-weldings can be set up to three. If there is no input of WI even re-welding is tried as many as the set number of re-weldings, an error will be generated.
# 5.3.2 Welding condition

Sets the conditions related to spot welding to perform welding in line with the work environment.

<p align=center>
<img src="../../../_assets/image_75_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.11 Welding condition setting</p></em>
</p>

(1)  **Condition number**

    Sets the welding condition quickly.
(2)  **Output data (binary)**

    Sets the data, which is to be inputted to the welder, for the welding condition number during the execution of the Spot statement.
(3)  **Initial squeezing force**

    Sets the squeezing force to squeeze the panel during the execution of the Spot statement. This will be used as the initial squeezing force during the setting of the multi-step squeezing force control.
(4)  **Multi-step squeezing force and auxiliary condition**

    This is an auxiliary condition number to manage the setting of multi-step squeezing force and pivoting. If a number is inputted, 『**Multi-step squeezing force**』 and  『**Pivoting**』 will be activated, making it possible to enter the menu.
(5)  **Moving electrode clearance**

    Sets the position where the moving electrode opens before and after the execution of the Spot statement.
(6)  **Fixed electrode clearance**

     Sets the position where the fixed electrode opens before and after the execution of the Spot statement.
# 5.3.2.1. Multi-step and auxiliary conditions

# 5.3.2.1.1 Multi-step squeezing force control

This is a function to change the squeezing force that is being applied during the spot welding with the servo gun. There are two methods to change the squeezing force. One is to change the squeezing force by creating a predetermined profile and the other is to change the squeezing force by using a signal input.

<p align=center>
<img src="../../../../_assets/image_65_eng.PNG" width="70%"></img>
<img src="../../../../_assets/image_37_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.12 Setting of multi-step squeezing force</p></em>
</p>

(1)  **Condition number**

   Indicates the condition numbers for the multi-step squeezing condition and auxiliary conditions.
(2)  **Initial squeezing force**

    Indicates the initial squeezing force set in the welding condition.
(3)  **Squeezing force change**

     Indicates the method to change the squeezing force. Creating a profile is a method in which the point of time for change and the time required for change are designated and then the squeezing force is changed in order at the relevant point of time for change. Using a signal input is a method in which the squeezing force is changed when there is a signal input from an external device.

(4)  **Handling upon change of state**

    If a state change occurs during a multi-step squeezing or while in a wait, this function makes it possible to select whether to proceed after stopping multi-step squeezing or proceed after completing multi-step squeezing.
(5)  **\<Profile creation>**

    Will be activated when profile creation is selected as the method to change the squeezing force.

 * Point of time for change: Designates the point of time for starting multi-step squeezing by dividing the spot welding steps into \[**Initial squeezing force reached**] -> \[**Welding execution output**] -> \[**Welding completion input**.] 
 * Time required for change: The squeezing force will be changed after the time required for change after the point of time for change is reached.
 * Squeezing force: The target squeezing force to change to
  
(6)  **<Signal input>**

    Will be activated when the selected method to change the squeezing force is input of a signal. The information necessary for communication with external devices needs to be inputted.

   * Communication range: Range from minimum to maximum of the assigned signal
   * Value range: Minimum and maximum values of the assigned signal
   * Squeezing force port: The number of the signal assigned for input
   * Port assignment: The number of bits assigned to the signal
   * Request for change: Port for the input signal for the request for change
   * Time of delay: For inputting the time if a delay is needed after the input of the request
   * Squeezing force: The requested squeezing force to change to. You can designate the squeezing force or receive an input signal. When the squeezing force is designated, the squeezing force for which a signal is received will be ignored.
# 5.3.2.1.2 가압 중 건 이동(피봇)

서보건 스폿 용접에서 가압 중에 건을 이동시키는 기능입니다. 설정한 이동시점에 지정한 거리, 속도, 방향으로 로봇이 이동합니다. 본 기능은 툴 좌표계를 기준으로 로봇이 이동하는 기능이기 때문에 서보건 툴 데이터, 마모량, 건 암 휨, 티칭 자세, 로봇 캘리브레이션이 성능에 영향을 줄 수 있습니다. 기능의 효과적인 적용을 위해서는 상기 요소들을 지속적으로 관리해야 합니다.

<p align=center>
<img src="../../../../_assets/image_57_eng.PNG" width="70%"></img>
<em><p align="center">그림 5.13 피봇 기능 설정</p></em>
</p>

(1)  **조건번호**
-    다단 가압 및 보조조건의 조건번호를 표시합니다.
  
(2)  **이동 시점**
-   스폿의 단계를 [**초기 가압력 도달**] → [**용접실행 출력**] → [**용접완료 입력**]으로 구분하여 이동 시작 시점을 지정

(3)  **이동 방향**
-   툴좌표계를 기준으로 건이 이동하는 방향을 선택합니다.

(4)  **이동 거리\[deg]**
-   이동할 거리를 설정합니다.

(5)  **이동 속도\[deg/s]**
-   이동할 속도를 설정합니다.

(6)  **이동 중 WI 입력 시 처리**
-   로봇 이동 중에 용접 완료가 발생한 경우 이동을 멈출 것인지, 이동을 완료 후 다음 단계로 진행할 지 선택합니다.

(7)  **이동 시작 지연 시간**
-   이동시점이 되었을 때 지연 시간 동안 대기 후 이동을 시작합니다.
# 5.3.3 Welding sequence

Sets the sequence related to the spot welding to determine the robot operation according to the work environment.


<p align=center>
<img src="../../_assets/image_1_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.14 Welding sequence setting</p></em>
</p>

(1)  **Sequence number**

    Selects the desired welding sequence quickly among the welding sequences.
(2)  **Welding signal output delay time (GWT)**

    In the case of the servo gun, this refers to the time of waiting until the welding signal is outputted after the squeezing force matching occurs

    In the case of a pneumatic gun, this refers to a time of waiting until the welding signal is outputted after the execution of the Spot statement.
(3)  **Welding signal pulse output (0=level)**

    This is to allow the welding signal to be outputted for a certain period of time. If the value is set to “0”, the welding signal continues to be outputted until the welding completion (WI) signal is inputted.
(4)  **Welding completion (WI) wait time**

    This is the time of waiting until the welding completion signal is inputted. If this value is set to “0”, waiting continues until there is an input.
(5)  **Robot wait time after welding completion (RWT)**

    In general, this the time of waiting for deposition detection after the welding completion (WI) signal is inputted. If the value is set to “0.0”, the deposition detection does not occur. When the deposition detection signal is to be used, it is recommended to use a value greater than “0.3 secs (300 msec).” However, if the value is large, the welding time will get longer and the cycle time will increase. 
# 5.3.4 Servo gun tip dressing condition

Sets various conditions for the execution of tip dressing for the servo gun

<p align="center">
 <img src="../../_assets/image_61_eng.PNG" width="70%"></img>
 <em><p align="center">Figure 5.15 Servo gun tip dressing condition setting </p></em>
</p>

</br>

(1)  **Welding signal output**

    Selects whether to output the welding signal for the tip dressing operation.
(2)  **Tip dressing time**

    Sets the time necessary for executing tip dressing. Tip dressing should be performed in the same manner by using the Spot statement. However, the welding sequence number should be set to “**64**.”
(3)  **Execution of gun search during tip dressing**

    Selects whether to execute gun search during tip dressing.
(4)  **Tip dresser thickness**

    Inputs the tip dresser thickness.
# 5.4 Input signal assignment for each welder

Assigns the signals related to spot welding, allowing the controller to monitor their state and perform necessary processing.


<p align=center>
<img src="../_assets/image_15_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.15 Input signal assignment</p></em>
</p>

(1)  **Welding completion**

    Only when this welding completion signal is inputted during the execution of spot welding, the controller executes the handling of welding completion. There are four welding completion signals in total and they are individually controllable. 
(2)  **Deposition error**

    To be used when receiving and handling the input of the gun's deposition signal.
(3)  **Welder abnormal**

    To be used to stop the operation of the robot when the signal of welder abnormal is inputted.
# 5.5 Output signal assignment for each welder

Assigns the signals related to spot welding and transfers their state to the outside.

<p align=center>
<img src="../_assets/image_45_eng.PNG" width="70%"></img>
<em><p align="center">Figure 5.17 Output signal assignment</p></em>
</p>

(1)  **Welder number**

    Selects the welder number to set. Up to four welders can be added.
(2)  **Welding condition**

    Assigns the number of the signal to output the output data corresponding to the welding condition during the execution of the Spot statement.
(3)  **Welding execution**

    To be used to output a command for welding to the welder during the execution of the Spot statement.
(4)  **Welder abnormal**

    To be used to output the inputted spot welder abnormal signal to the outside.
(5)  **Electrode consumption alarm**

    To be used to output a signal if the consumption amount detected by the gun search is larger than the electrode replacement required consumption amount.
(6) **Deposition error**

    To be used to output to the outside the state that deposition has occurred to the spot gun.
(7)  **Servo gun squeezing in progress**

    This is a signal that is turned on when squeezing starts upon the execution of the Spot statement and turned off when the opening procedure starts.
(8)  **Welding gun search in progress**

    This is a signal that is turned on when gun search starts upon the execution of the gunsea, igunsea or egunsea statement and turned off when the opening procedure starts.
    # 6. Frequently Asked Questions

*   <mark style="color:green;">**How does the servo gun axis operate when using the shift function?**</mark>

    All functions for shifting (offline, online, search, palletize) are applied only for the robot axis and the servo gun axis moves to recorded positions.
*   <mark style="color:green;">**What happens to the servo gun axis in case of coordinate conversion?**</mark>

    Only the movement elements for the robot are converted while the servo gun axis will not be converted.
*   <mark style="color:green;">**How does the operation proceed in case of the counterpart program call function?**</mark>

    Shifting occur by applying the relative position for the robot.
*   <mark style="color:green;">**What happens to the servo gun axis in case of mirror image conversion?**</mark>

    Mirror image conversion will be applied for the additional axis only when the axis specification is base and the axis configuration is linear. So, the servo gun axis will not be converted.
*   <mark style="color:green;">**How can I change the currently selected gun number?**</mark>

    You can change it by using “**R210: Spot gun number selection.** If the gun you want to change is a robot gun, the tool number will be also automatically changed by referring to the tool number corresponding to the gun number when you change the gun number. When you change a gun number by using R210 in a multi-gun environment, the environment will change to an environment of the selected sole gun.
*   <mark style="color:green;">**I want to select and manually squeeze multiple guns. How can I select multiple guns?**</mark>

    You can select multiple guns only when they are the same gun type. You can select them with “**R214: Selection of simultaneous welding guns**.” If you want to deselect a gun after selecting multiple guns, you can input the gun number you want to deselect with R214. However, you cannot deselect the first gun number (master gun). 
*   <mark style="color:green;">**How can I change the squeezing force during the servo gun squeezing process?**</mark>

    If the selected gun type is servo gun, you can change it with “**R211: Servo gun squeezing force setting.**”
*   <mark style="color:green;">**How can I arbitrarily change the moving electrode consumption amount of the servo gun?**</mark>

    If the selected gun type is servo gun, you can change it with “**R212: Servo gun moving electrode consumption amount preset.**” When gun search is performed, this value will be automatically updated.
*   <mark style="color:green;">**How can I arbitrarily change the fixed electrode consumption amount of the servo gun?**</mark>

    If the selected gun type is servo gun, you can change it with “**R213: Servo gun fixed electrode consumption amount preset.**” When gun search is performed, this value will be automatically updated.
*   <mark style="color:green;">**How can I arbitrarily change the fixed electrode consumption amount of the equalizerless gun?**</mark>

    If the selected gun type is equalizerless gun, you can change it with “**R220: Equalizerless gun fixed electrode consumption amount preset.**” When gun search is performed, this value will be automatically updated.
*   <mark style="color:green;">**I am now operating a robot in automatic mode and want to change the squeezing force in the welding condition. How can I do it?**</mark>

    With “**R215: Spot welding condition squeezing force setting,**” you can change the value of the squeezing force set in the welding condition even currently in the middle of automatic operation of the robot. 
*   <mark style="color:green;">**Can I manually change the currently selected welding condition and welding sequence numbers?**</mark>

    In the case of the welding condition, press \[**cond.sel**] and in the case of welding sequence, press\[**seq.sel**] to change to a desired number.
*   <mark style="color:green;">**Is there any shortcut key to enter the menu of『Setting』 → 『4: Application parameter』 → 『1: Spot welding』?**</mark>

    You can quickly enter the menu by placing the cursor on the spot welding related command (spot, gunsea, igunsea, and egunsea) on the initial screen of the manual mode and pressing \[**Attribute**.] 
*   <mark style="color:green;">**How can I manually change the panel thickness?**</mark>

    If the selected gun type is servo gun, you can change it with “**R220: Panel thickness setting (Sv).**”
*   <mark style="color:green;">**How can I change the record positions of the spot welding steps to normal values once?**</mark>

    You can change it simply by setting <**Valid**> for the “**Automatic adjustment of servo gun welding step record position**” item in 『**Setting**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』→ 『**2: Use environment setting**』 and then playing back the work program.
*   <mark style="color:green;">**Is it possible for any missed welding point to be detected?**</mark>

    When you initialize the number of weldings in the work program start menu and then perform weldings normally, the number of weldings will increase. Considering that you need to compare between the number of spots for completion of welding and the number of weldings performed, you need to create a program as follows.

    　　　　　　　　　　　　　　　![](<_assets/image_68_eng.PNG>)
*   <mark style="color:green;">**It seems that the working time can be shortened if tip dressing and gun search operations for a stationary servo gun is performed, independently from the handling operation. Is there any way to do this?**</mark>

    It can be simply supported if you use multi-task function. Refer to [**Multi-task Function Manual**](https://hyundai-robotics.gitbook.io/hi6-robot-controller-manual-multi-task/).

# 7\. Errors and warnings# 7.1 Error messages

|                          Code                          | 　　　　　　<p align=center> Content </p>                                    | 　　　　　　<p align=center> Measure              </p>                                                          |
| :---------------------------------------------------: | -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
|               <p>E0007 </p><p>Deposition detection</p>               | A deposition signal is inputted upon the ending of the welding sequence.                                                              | <ul><li>Check the deposition detection signal.</li><li>Remove the deposition.</li></ul>                                                                 |
|        <p>E0154 </p><p>Maximum electrode </p><p>consumption amount exceeded</p>        | The total electrode consumption amount detected by gun search exceeded the maximum electrode consumption amount (of both moving and fixed electrodes) set in the welding gun parameter.                        | <ul><li> Check the maximum electrode consumption amount in the welding gun parameter.</li><li>Replace the electrode.</li></ul>                                                   |
|       <p>E0155 </p><p>Maximum moving electrode </p><p>consumption amount exceeded</p>       | The moving electrode consumption amount detected by gun search exceeded the maximum (moving) electrode consumption amount set in the welding gun parameter.                              | <ul><li>Check the maximum (moving) electrode consumption amount in the welding gun parameter.</li><li>Replace the electrode.</li></ul>                                                |
|       <p>E0156 </p><p>Maximum fixed electrode </p><p>consumption amount exceeded</p>       | The fixed electrode consumption amount detected by gun search exceeded the maximum (fixed) electrode consumption amount set in the welding gun parameter.                              | <ul><li>Check the maximum (fixed) electrode consumption amount in the welding gun parameter.</li><li>Replace the electrode.</li></ul>                                                |
|        <p>E0171 </p><p>Gun opening time (five seconds) </p><p>exceeded</p>       | After the squeezing operation in the spot welding and gun search function was performed, the opening time exceeded five seconds.                                               | <ul><li>Check whether the gun has deposited to the welding workpiece or any interference has occurred.</li><li>Check whether deposition or interference has occurred to the gun of the moving side.</li></ul>                                |
|         <p>E1036 </p><p>Electrification wait time</p><p>exceeded</p>        | During the execution of the welding by the servo gun, the welding completion (WI) signal has not been inputted during the welding completion (WI) wait time in the welding sequence menu.                        | Check the wiring diagram of the welding completion (WI) signal and related peripheral facilities.                                                                                   |
|     <p>E1038 </p><p>Position where the electrode consumption</p><p>amount compensation cannot be performed</p>    | At the time of recording the position by performing the electrode consumption amount compensation, the robot posture was created in a way that the electrode consumption amount compensation cannot be performed.                            | Required to make sure that the robot posture does not deviate from the operation area while trying to perform compensation for as much as the detected electrode consumption amount.                                                                      |
|           <p>E1281 </p><p>The welder abnormal signal is inputted.</p>          | Occurs when the welder abnormal signal is inputted during welding.                                                           | 1) Check the welding power supply unit.                                                                                                    |
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




|  Code        | 　　　　　Content          | 　　　　　　Measure    |
|-------------| ------------- | ----------------- |
|               E0007  Deposition detection              | A deposition signal is inputted upon the ending of the welding sequence. | Check the deposition detection signal. Remove the deposition.    |# 7.2 Warning messages

|                  Code             | 　　　　　　Content                                                                  | 　　　　　　Measure                                                                                                   |
| :----------------------------------------------------: | -------------------------------------- | ---------------------------------------------------- |
|      <p>W0009 </p><p>Brake slip occurred</p><p>(the set value exceeded)</p>     | The brake slip measured during stud welding exceeded the brake deviation detection range set in the welding sequence.                  | Check the set brake deviation detection range, and, if necessary, change the value to a greater one.                                                               |
|       <p>W0105 </p><p>Electrode replacement required total consumption amount </p><p>exceeded</p>       | This warning occurs if the total consumption amount detected by gun search exceeded the electrode replacement required consumption amount (both of moving and fixed electrodes) set in the welding gun parameter.       | <ol><li>Check the set maximum electrode consumption amount.</li><li>Check whether the gun search reference position is registered normally.</li><li>Replace the electrode.</li></ol>        |
|      <p>W0106 </p><p>The moving electrode exceeded </p><p>the electrode replacement required consumption amount</p>      | This warning occurs if the moving electrode consumption amount detected by gun search exceeded the (moving) electrode replacement required consumption amount set in the welding gun parameter.             | <ol><li>Check the set (moving) electrode replacement required consumption amount. </li><li>Check whether the gun search reference position is registered normally.</li><li>Replace the electrode.</li></ol>   |
|      <p>W0107 </p><p>The fixed electrode exceeded </p><p>the electrode replacement required consumption amount</p>     | This warning occurs if the fixed electrode consumption amount detected by gun search exceeded the (fixed) electrode replacement required consumption amount set in the welding gun parameter.             | <ol><li>Check the set (fixed) electrode replacement required consumption amount. </li><li>Check whether the gun search reference position is registered normally.</li><li>Replace the electrode.</li></ol> |
| <p>W0108 </p><p>During the jog operation, </p><p>the actual squeezing force exceeded </p><p>the set value</p> | When squeezing is performed through manual operation of the axis, the actual squeezing force exceeds the set squeezing force. When this occurs, operate the servo gun axis in the opposite direction. | <ol><li>Check whether the squeezing force of the axis that will be operated is sufficiently set.</li><li>As a mechanical problem with the servo gun is anticipated, you need to contact the servo gun manufacturer for inquiry. </li></ol><p></p> |
|  <p>W0109 </p><p>Impossible to manually </p><p>operate the servo gun not </p><p>selected</p> | The servo gun you want to operate is different from the selected servo gun.                                             | When you select a servo gun, you need to perform manual jog operation. First, select the servo gun you want to operate with the R210 code and then perform the operation.                                          |
