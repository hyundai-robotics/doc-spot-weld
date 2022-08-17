# 4.1.2 Commands related to gun search
---
(1) gunsea

    This is a statement to be used for executing gun search 1 when the gun type is servo gun or executing gun search 2 by using the squeezing force.

```
gunsea gun=<gun number>,sea=<search number>,pre=<squeezing force>,spd=<search speed>,mgun=<numbers of multiple guns>,mpre=<squeezing force for multiple guns>
```

|   **Item**   | <p align="center">   **Content**   </p>| 
|:--------: | ----------------------------------------------------------------- |
|   **Gun number**  | Designates the gun number to search.                |
|  **Search number**  | Designates the gun search 1 operation or gun search operation 2.                 |
|   **Squeezing force**  | Designates the command squeezing force for detection of squeezing force matching.            |
|  **Search speed**  | <p>Designates the operation speed of the gun's axis for the search operation.</p><p>The search speed is based on safe speed and the recommended speed is 10 mm/s.</p>         |
|  **Numbers of multiple guns** | Designates the numbers for multiple guns when executing gun search for multiple servo guns at the same time.                                                   |
| **Squeezing force for multiple guns** | <p>Designates the squeezing force when required to apply a different squeezing force for each servo gun when executing gun search for multiple servo guns at the same time</p><p>If it is not designated, the squeezing force of the default gun will apply.</p> |

{% hint style="info" %}
[Use example]

A case of executing gun search 1 for the servo guns 5 and 6 with the equalizing force 100 kgf and 200 kgf respectively

→ ```gunsea gun=5,sea=1,pre=100,mgun=6,mpre=200```

{% endhint %}

---
(2) igunsea

    This is a statement to be used for executing gun search 2 based on the input signal when the gun type is servo gun.

```
igunsea gun=<gun number>,spd=<search speed>,di=<input signal>
```

|  **Item**  |   <p align="center">   **Content**   </p>  |
| :------: | ---------------------------------------------------------------------- |
| **Gun number** | Designates the gun number to search                                                              |
| **Search speed** | <p>Designates the operation speed of the gun's axis for the search operation.</p><p>The search speed is based on safe speed and the recommended speed is 10mm/s.</p>    
| **Input signal** | Designates the input signal number for the reception of the phottube output.                                               |

</br>

---
(2) egunsea

    This is used when the gun type is equalizerless gun.

```
egunsea gun=<gun number>,spd=<search speed>,dist=<search distance>,di=<input signal>
```

|  **Item**  |  <p align="center">   **Content**   </p>   |
| :------: | ---------------------------------------------------------------------- |
| **Gun number** |  Designates the gun number to search                                                            |
| **Search speed** | <p>Designates the operation speed of the gun's axis for the search operation.</p><p>The search speed is based on safe speed and the recommended speed is 10 mm/s.</p>    
| **Input signal** | Designates the input signal number for reception of the phot tube output.         