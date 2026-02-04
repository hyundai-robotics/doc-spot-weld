### 4.2.1 Spot statement

If the spot welding stops and restarts while spot welding is not completed, the spot welding step will be executed again. If the \`GUN` LED is turned on while the step is being recorded with the \`Record` key, the Spot statement will be recorded along with the Move statement. (one-touch recording method.)

 When recording the welding step, if you make the fixed electrode contact the panel through a jogging operation and then record the Spot statement in one-touch method, while squeezing the panel through a manual squeezing operation, the panel thickness will be set. Once the panel thickness is set, if you make the fixed electrode contact the panel through a jogging operation and then record the Spot statement in one-touch method without a manual squeezing operation, the recording will take place by taking into consideration the position for which the panel thickness and the consumption amount are compensated.

While the gun type is servo gun, if the Spot statement exists during \`Position modification`, the position will be automatically modified to a position for which the electrode consumption amount is compensated.

</br>

```spot gun=<gun number>,cnd=<condition number>,seq=<sequence number>,pre=<pressure>,out=<output data>```


<center>

|   **Item**    | 　      **Content**       |
| :--------: |:---------: |
|    **Gun number**    |  the welding gun number |
|    **Condition number**   |  the welding condition |
|   **Sequence number**  |  the welding sequence |
|   **Pressure value**  |  the pressurization force value  |
|   **Output data**  | the output value transmitted in 12-bit format |

</center>

</br>

{% hint style="info" %}

\[Example of use\]  
- All parameters of  ```spot``` command can be entered in array format [ ] when using multiple guns.

{% endhint %}

{% hint style="info" %}
\[Example of use\]  
- When performing spot welding using servo guns 5 and 6 with welding conditions 7 and 8, welding sequences 9 and 10, and welding pressures of 100 kgf and 200 kgf, respectively.

  ```spot gun=[5,6],cnd=[7,8],seq=[9,10],pre=[100,200]```

{% endhint %}