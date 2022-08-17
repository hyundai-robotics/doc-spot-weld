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

