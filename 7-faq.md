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
  
  Yes. In Manual Mode, place the cursor on a spot welding–related command (e.g., spot, gunsea, igunsea, or egunsea) on the initial screen, and press the `[property]` button to quickly access the corresponding menu.

* How can I manually change the panel thickness?  

  If the selected gun type is a servo gun, the panel thickness can be changed using R220: Panel Thickness Setting (Sv).

* How can I reset the recorded positions of the spot welding steps to normal values at once?  

  Set <Valid> for the item “Automatic Adjustment of Servo Gun Welding Step Record Position” under `[F2: system] - 4: Application parameter - 1: Spot welding - 2: Welding gun parameter - 1: Environment Setting`, and then play back the work program.

* Is it possible to detect any missed welding points?  
  
  Yes. When you initialize the welding count in the Work Program Start menu and then perform welding normally, the welding count will increase accordingly.
  To detect missed welding points, you must compare:
  the total number of welding spots required for completion, and the actual number of weldings performed. Refer to the chapter [ 4.9 Calculation of spots in spot welding](./4-work-teaching/4-9-spot-weld-calculation.md).


* It seems that the working time could be reduced if tip dressing and gun search operations for a stationary servo gun were performed independently from handling operations. Is there any way to achieve this?  

  Yes. This can be easily implemented by using the multi-task function.  By separating handling operations and stationary servo gun operations into different tasks, they can be executed independently and simultaneously. Please refer to the [Multi-task Function Manual](https://hrbook-hrc.web.app/#/view/doc-multi-task/en/README?cont_model=${cont_model}) for detailed instructions.