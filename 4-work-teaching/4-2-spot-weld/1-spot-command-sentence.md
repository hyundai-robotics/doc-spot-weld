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

{% endhint %}