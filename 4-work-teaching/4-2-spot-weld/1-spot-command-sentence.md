### 4.2.1 Spot statement

Spot命令执行点焊所需的一系列操作，包括枪压、焊接待机和打开。

<br>

### Description
  - 支持伺服枪、EQ枪、无EQ枪和EQ刹车枪。
  - 对于多枪配置，参数以数组格式输入。
  - 如果在点焊过程完成之前停止系统，然后重新启动，则点焊步骤将再次执行。
  - 使用`[Record]`键记录步骤时，如果`[GUN]`键的LED灯亮起，则`点 (spot)`命令将与`移动 (move)`命令一起记录（一键录制方式）。
  - 记录焊接步骤时：
     - 使用手动操作将固定电极与面板接触。
     - 使用手动压制将压力施加到面板上。
     - 然后使用一键录制方式记录Spot命令。  
       -> 面板厚度将自动设定。
  - 设置面板厚度后，使用手动操作将固定电极与面板接触。然后，使用一键录制方式记录`点 (spot)`命令，而无需执行手动压制。  
-> 记录的位置将自动反映面板厚度和电极磨损的补偿。
  - 当枪类型设置为伺服枪时，如果在`[POS.MOD]`期间存在`点 (spot)`命令，则位置将自动校正，以包括电极磨损的补偿。

<br>


### Grammar
```python
spot gun=<gun number>,cnd=<condition number>,seq=<sequence number>,pre=<pressure>,out=<output data>
```

<br>

### Parameters

<center>

|   Item    |       Content      | Note |
| :--------: |:---------: |:---------: |
|    Gun number    |  焊枪编号 | mandatory |
|    Condition number   |  焊接条件 |mandatory |
|  Sequence number  |  焊接顺序 |mandatory |
|  Pressure value  |  压力值  |optional |
|  Output data  | 以12位格式传输的输出值 |optional |

</center>

<br>

{% hint style="info" %}

\[Example of use\]  
- 所有`点 (spot)`命令的参数可以在使用多个枪时以数组格式 [ ] 输入。

{% endhint %}

{% hint style="info" %}
\[Example of use\]  
- 在使用伺服枪5和6进行点焊的情况下，焊接条件为7和8，焊接顺序为9和10，焊接压力分别为100 kgf和200 kgf。

  ```python
  spot gun=[5,6],cnd=[7,8],seq=[9,10],pre=[100,200]
  ```

{% endhint %}