# 3.1.3 State flag

Various necessary states related to spot welding will be indicate as shown in the screen below.

<p align="center">
 <img src="../../_assets/image_eng.png" width="70%"></img>
 <em><p align="center">Figure 3.6 Indication of spot welding related states</p></em>
</p>


>-  **Welding condition and welding sequence (panel thickness)**
>       - Indicates the currently selected welding condition number and welding sequence number.
>       - Indicates the currently set panel thickness. Accurate setting is required because the position of the axis of the servo gun will be automatically created based on the set panel thickness during the recording of the welding steps of the servo gun. It is also possible to perform manual setting with R220. When the recording of the welding steps is performed after the \[**manual squeezing**] operation, the setting will be automatically performed by taking into consideration the current position of the servo gun.
>-  **Tool number**
>       - Indicates the tool number corresponding to the currently selected gun number. In other words, if you change the gun number, the tool number will automatically change to the tool number set in『**Setting]: >System**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 → 『**1: Setting of the tool number and gun type corresponding to the gun number**.
>-  **Gun number**
>       - This indicates the currently selected gun number, numbers of multiple guns, and servo gun separation state (![](<../../_assets/image_39_eng.png>)). For example, if G5 and G6 are indicated, it means that stationary guns G5 and G6 are selected for simultaneous welding. In addition , there is a mark of a lock, so you can konw that the servo gun is disconnected.&#x20;
>

