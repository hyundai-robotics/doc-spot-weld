# 4.9 点焊中的点的计算

内置PLC提供存储点焊点计数的功能。PLC分别存储初始化、上电、上一个周期和当前周期的焊接点数，用户可以手动重置这些值。

有关更多详细信息，请参见内置PLC手册中的「[3.4.3 S Relay - OP_TIME](https://hrbook-hrc.web.app/#/view/doc-hi6-embedded-plc/zh/3-relay/4-sw-relay/3-slot-op-time?cont_model=${cont_model})」。

<p align="center">
 <img src="../_assets/image_94_eng.PNG" width="70%"></img>
 <em><p align="center">图 4.22 点计数</p></em>
</p>

<br>

{% hint style="warning" %}
在子任务中执行的点命令将不会被计算。
{% endhint %}