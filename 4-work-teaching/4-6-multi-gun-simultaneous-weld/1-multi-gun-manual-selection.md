### 4.6.1 Manual selection of multiple guns

<p align="center">
 <img src="../../_assets/image_32_eng_.PNG" width="60%"></img>
 <em><p align="center">Figure 4.19 Screen with multi-gun applied</p></em>
</p>

The procedure for selecting G1 (master) and G2 (slave) as multiple guns through the servo tool change function is as follows.

1. Select `R358` and then connect G1. After the connection is completed, the parameter related to the additional axis to which G1 is assigned should be set.
2. Select `R358` and then connect G2. After the connection is completed, the parameter related to the additional axis to which G2 is assigned should be set.
3. The state of the selected gun is indicated in state flag as follows.

<br>

{% hint style="info" %}
* `R210` for changing the master gun number
  - Environment with a single gun → `R210 + 3` → Environment with a single gun (Example: G1 → G3)
  - Environment with multiple guns → `R210 + 1` → Environment with a single gun (Example: G1 and G3 → G1)
* `R214` for selecting multiple guns
  -  When selecting another number different from the set gun number

      A. Environment with a single gun → `R214 + 3` → Environment with multiple guns (Example: G1 → G1 and G3)

      B. Environment with multiple guns → `R214 + 2` → Environment with multiple guns(Example: G1 and G3 → G1, G3, and G2)
  -  When selecting the same number as the set gun number

      A. Environment with multiple guns → `R214 + 3` →  Environment with multiple guns(Example: G1, G3 and G2 → G1 and G2)

      B. Environment with multiple guns → `R214 + 1` → Environment with a single gun (Example: G1 and G2 → G1)

      C. The master gun number (G1) does not change.  
{% endhint %}

