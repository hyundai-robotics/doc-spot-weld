# 4.5.2 Connection/separation commands 

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
