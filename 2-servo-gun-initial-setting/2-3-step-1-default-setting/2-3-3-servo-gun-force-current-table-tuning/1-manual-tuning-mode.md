# 2.3.3.1 Manual tuning mode

The manual tuning mode is a function to manually perform the servo gun squeezing force – current table setting. After the servo gun squeezing occurs, if the user directly inputs the measured squeezing force by using the teaching pendant, the optimal command current will be automatically calculated. This process should be repeated to increase the accuracy. The accuracy can be verified by the degree of convergence and test squeezing.

The procedure for setting the servo gun squeezing force – current table in manual mode, recommended by our company, is as follows.

<p align="center">
 <img src="../../../_assets/image_84.png" width=70%></img>
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
{% endhint %}