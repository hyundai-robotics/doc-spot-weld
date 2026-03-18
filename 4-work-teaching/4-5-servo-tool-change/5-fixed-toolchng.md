### 4.5.5 带位置可变固定电极的伺服枪更换  

当整个伺服枪被更换时，需要额外的设备，如ATC（自动换刀器）和枪架。然而，通过操作一个移动电极保持固定、仅更换固定电极的系统，则不需要额外设备，并且可以减少换装所需的时间。

为了支持此功能，必须管理每个固定电极的磨损量和软限制。因此，要求进行类似于焊接枪更换（伺服工具更换）功能的操作。因此，在使用此功能之前，用户必须先熟悉焊接枪更换（伺服工具更换）功能。

该功能与伺服枪更换功能的区别在于不执行任何机械或电气连接/断开操作。此外，由于电机和编码器信息始终保持不变，因此这些数据不会被更新。

<br>

```python

S10   move L, ...                    # Move to fixed electrode 1
      toolchng fixed,tg=G1,is=di1    # Change to fixed electrode 1
S11   move L, ...                    # Robot movement
      spot gun=1,cnd=1, seq=1        # Perform welding with gun No. 1
S12   move L, ...                    # Move to fixed electrode 2
      toolchng fixed,tg=G2,is=di1    # Change to fixed electrode 2
S13   move L, ...                    # Robot movement
      spot gun=2,cnd=2, seq=2        # Perform welding with gun No. 2

```