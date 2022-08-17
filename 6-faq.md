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

    　　　　　　　　　　　　　　　![](<_assets/image_68_eng.png>)
*   <mark style="color:green;">**It seems that the working time can be shortened if tip dressing and gun search operations for a stationary servo gun is performed, independently from the handling operation. Is there any way to do this?**</mark>

    It can be simply supported if you use multi-task function. Refer to [**Multi-task Function Manual**](https://hyundai-robotics.gitbook.io/hi6-robot-controller-manual-multi-task/).

