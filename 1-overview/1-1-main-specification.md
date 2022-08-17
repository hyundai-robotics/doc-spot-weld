# 1.1 Main specifications

|       **Item**       |                          **Specification**                          |
| :----------------: | :------------------------------------------------------: |
|     Spot welding setting file     |           spotweld.json            |
|      Maximum welder count     |              4 units                 |
| Count of multiple guns for simultaneous welding</br>(the same gun type) |           4 units                   |
|            |                 16 units                   |
|       Welding condition number      |                         1 – 1024                        |
|   Output data dependent on welding condition   |                         1 – 1024                        |
|       Welding sequence number      |                   1 –  63 (64 is exclusively for tip dressing)                   |
|     Position modification (servo gun)    | SPOT command step – Consumption amount automatic compensation position</br>Other steps – Positions that do not consider the consumption amount |
|    Inspection of the tool number corresponding to the gun umber   |                     Inspection of robot guns and no inspection of stationary guns                    |
|     Welding condition signal output     |   To be outputted in sync with the output of the welding execution signal</br>Impossible to output only the welding condition signal   |
