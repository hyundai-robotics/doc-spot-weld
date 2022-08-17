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
 <img src="../../_assets/image%20(76)_eng.png" width="70%"></img>
 <em><p align="center">Figure 2.6 Confirmation with the user on the position of the axis origin</p></em>
</p>

{% hint style="warning" %}
[**Warning**] If the servo gun has a stopper other than a metal material such as a bumper attached at the maximum opening position of the servo gun, it may be difficult to estimate the maximum opening position. It is recommended to perform setting after removing the stopper.
{% endhint %}

The configuration and functionality of the servo gun default setting screen is as follows.

<p align="center">
 <img src="../../_assets/image%20(62)_eng.png" width="70%"></img>
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
>8. **Execution stop**: Stops the setting that is in progress.