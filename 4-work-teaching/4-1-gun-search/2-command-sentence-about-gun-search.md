### 4.1.2 Commands related to gun search


(1) gunsea

 This is a statement to be used for executing gun search 1 when the gun type is servo gun or executing gun search 2 by using the squeezing force.


```gunsea gun=<gun number>,sea=<search number>,pre=<squeezing force>,spd=<search speed>```

|   **Item**   | <p align="center">   **Content**   </p>| 
|:--------: | ----------------------------------------------------------------- |
|   **Gun number**  |  the gun number to measure the tip length (array[ ] for multi inputs)  | 
|  **Search number**  |  the gun search 1 operation or gun search operation 2             |
|   **Squeezing force**  |  the command squeezing force for detection of squeezing force matching.(array[ ] for multi inputs)       |
|  **Search speed**  |the operation speed of the gun's axis for the search operation (10 mm/s recommended)|


<br>

{% hint style="info" %}
[Use example]    

A case of executing gun search 1 for the servo guns 5 and 6 with the equalizing force 100 kgf and 200 kgf respectively

 --> ```gunsea gun=[5,6],sea=1,pre=[100,200],spd=50```

{% endhint %}

---
(2) igunsea

This is a statement to be used for executing gun search 2 based on the input signal when the gun type is servo gun.

```igunsea gun=<gun number>,spd=<search speed>,di=<input signal>```

|  **Item**  |   <p align="center">   **Content**   </p>  |
| :------: | ---------------------------------------------------------------------- |
| **Gun number** |  the gun number to search                  |
| **Search speed** | the operation speed of the gun's axis for the search operation (10 mm/s recommended)|
| **Input signal** |  the input signal address for the reception of the phottube output    |

</br>

---
(2) egunsea

This is used when the gun type is equalizerless gun.

```egunsea gun=<gun number>,spd=<search speed>,dist=<search distance>,di=<input signal>```

|  **Item**  |  <p align="center">   **Content**   </p>   |
| :------: | ---------------------------------------------------------------------- |
| **Gun number** |   the gun number to search                                                            |
| **Search speed** | the operation speed of the gun's axis for the search operation (10 mm/s recommended)  |
| **Input signal** |  the input signal address for reception of the phot tube output |     