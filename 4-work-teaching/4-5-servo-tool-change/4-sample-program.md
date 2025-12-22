# 4.5.4 Sample program


<br>

```python

S10   move L, ...                    # Move to servo tool disengagement position
      toolchng off,tg=G1,is=di1      # Execute servo tool disengagement (current connection state)
                                     # Servo tool disengagement output (dedicated output)
      do11=1                         # ATC cam open output
      wait di11                      # Check ATC cam open completion signal
S11   move L, ...                    # Robot movement
S12   move L, ...                    # Robot movement
S13   move L, ...                    # Robot movement
S14   move L, ...                    # Move to servo tool connection position
      wait di12                      # Check connection-ready signal
      do11=0                         # ATC cam close output
      toolchng on,tg=G1,is=di1       # Execute mechanical connection
                                     # Servo tool connection processing
S15   move L, ...                    # Robot movement

```