# 4.8 使用伺服枪处理工件

这是一个在不使用单独挂架的情况下运输小型工件的功能。

<p align="center">
 <img src="../_assets/image_52_eng_.PNG" width="50%"></img>
 <em><p align="center">图 4.21 伺服枪的处理功能</p></em>
</p>

<br>

```svclamp on/off gun=<gun number>,cnd=<condition number>```




|   **项目**    |        **内容**       |
| :--------: |:---------: |
|    **开/关**    |  开: 夹紧, 关: 释放 |
|    **枪编号**    |  焊接枪编号 (数组 [ ] 用于多枪) |
|    **条件编号**   |  焊接条件 |


<br>



`svclamp` 语句可用于夹持工件并执行打开操作。在 svclamp 打开状态下，伺服枪不会打开。

<br>

```python

S10   move L, ...                    # 移动到夹持位置
      svclamp on, gun=1, cnd=1       # 使用伺服枪夹持工件
S11   move L, ...                    # 机器人移动
S12   move L, ...                    # 机器人移动
S13   move L, ...                    # 移动到释放位置
      svclamp off, gun=1, cnd=1      # 释放工件 
S12   move L, ...                    # 机器人移动

```