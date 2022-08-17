# 4.10 Consumption amount setting

The following system variable sets the gun's total consumption amount arbitrarily, or stores the total consumption amount measured through the gun search function.
.

```
_tipwear[gun number]
```

|      **Item**      | 　　　　　　　　　　**Content**       |
| :--------------: | ---------------------- |
| **Gun number\[1\–16]** | Designates the welding gun number (totally up to 16 numbers) |

If the consumption amount is arbitrarily set using the above variable, the total consumption amount will apply to the moving and fixed electrodes according to the ratio set for the moving electrode consumption amount. The value will be maintained until the execution of gun search.

```
Use example 1)
V1!=_tipwear[1]  	Sets the consumption amount of the gun 1, measured through gun search, in V1!

Use example 2)
_tipwear[2]=V1!		Sets the total consumption amount of the gun 1 in V1!
```

{% hint style="warning" %}
\[**Cautio**]: This variable can apply only to servo and equalizerless guns. In the case of the equalizerless gun, the total consumption amount equals the fixed electrode consumption amount.
{% endhint %}
