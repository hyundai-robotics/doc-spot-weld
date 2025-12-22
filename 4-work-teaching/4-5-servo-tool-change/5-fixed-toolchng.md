# 4.5.5 Servo gun change with position-variable fixed electrodes  



When the entire servo gun is replaced, additional equipment such as an ATC (Automatic Tool Changer) and a gun stand is required. However, by operating a system in which the moving electrode remains fixed and only the fixed electrode is changed, no additional equipment is necessary, and the time required for changeover can be reduced.

To support this function, wear amount and soft limits must be managed for each fixed electrode. Therefore, an operation similar to the Welding Gun Change (Servo Tool Change) function is required. Accordingly, before using this function, users must first become familiar with the Welding Gun Change (Servo Tool Change) function.

The difference between this function and the Servo Gun Change function is that no mechanical or electrical connection/disconnection operations are performed. In addition, since the motor and encoder information always remain the same, these data are not updated.

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