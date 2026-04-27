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