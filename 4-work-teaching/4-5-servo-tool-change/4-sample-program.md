### 4.5.4 示例程序


<br>

```python

S10   move L, ...                    # 移动到伺服工具脱离位置
      toolchng off,tg=G1,is=di1      # 执行伺服工具脱离（当前连接状态）
                                     # 伺服工具脱离输出（专用输出）
      do11=1                         # ATC 凸轮打开输出
      wait di11                      # 检查 ATC 凸轮打开完成信号
S11   move L, ...                    # 机器人移动
S12   move L, ...                    # 机器人移动
S13   move L, ...                    # 机器人移动
S14   move L, ...                    # 移动到伺服工具连接位置
      wait di12                      # 检查连接准备信号
      do11=0                         # ATC 凸轮关闭输出
      toolchng on,tg=G1,is=di1       # 执行机械连接
                                     # 伺服工具连接处理
S15   move L, ...                    # 机器人移动

```