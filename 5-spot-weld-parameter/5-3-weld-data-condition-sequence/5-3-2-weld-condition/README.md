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
