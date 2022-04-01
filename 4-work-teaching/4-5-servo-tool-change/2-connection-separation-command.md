﻿# 4.5.2 접속/분리 명령

서보툴 체인지 환경에서 서보건의 접속/분리는 아래 2가지로 수행할 수 있습니다. 서보건을 접속하면 건번호와 툴번호가 설정된 값에 따라 자동 변경되며, 서보건을 분리하면 건번호와 툴번호가 0으로 자동 변경됩니다.

### <mark style="color:green;">R358</mark>

R코드에 의한 서보건 체인지 기능으로 수동 모드의 모터 On 상태에서(Enable 스위치 On) 사용합니다.

조작 = **R358, #1, #2, #3**

| **파라미터** |   **#1**   | **#2** |    **#3**   |
| :------: | :--------: | :----: | :---------: |
|    의미    |    접속/분리   |   축사양  |     건번호     |
|   설정 값   | 접속=1, 분리=0 |  서보건=1 | 체인지할 서보건 번호 |

| 사용 예 | R358,1,1,2 (서보건 G2를 접속) |
| :--: | ----------------------- |
|      | R358,1,0 (서보건을 분리)      |

### <mark style="color:green;">toolchng</mark>

작업 프로그램 실행에 의한 용접건 체인지 기능입니다.

```
toolchng on/off,chng=<체인지 대상>,di=<접속완료 신호>,wtime=<접속완료 대기시간>,mchng1=<체인지 대상>,mchng2=<체인지 대상>,mchng3=<체인지 대상>
```

|                            **on/off**                            |       **on**       |                    서보툴 접속                   |                                               |
| :--------------------------------------------------------------: | :----------------: | :-----------------------------------------: | :-------------------------------------------: |
|                               ****                               |       **off**      |                    서보툴 분리                   |                                               |
|                            **체인지 대상**                            |     **G1\~G16**    |         <p>접속/분리할 </p><p>용접건 번호</p>         | <mark style="color:red;">해당 부가축의 접속/분리</mark> |
|                         **기계적 접속완료 확인신호**                        |     **1\~4096**    | <p>기계적인 접속완료</p><p>확인을 위한</p><p>입력신호 번호</p> |          <p>OFF시 무시되는</p><p>파라미터</p>          |
|     <p><strong>접속완료</strong></p><p><strong>대기시간</strong></p>     | **<0\~5.0> (sec)** | <p>접속완료 대기시간</p><p>(파라미터가 없거나 0이면 무한대기)</p> |          <p>OFF시 무시되는</p><p>파라미터</p>          |
| <p><strong>체인지 대상</strong></p><p><strong>(동시 접속/분리)</strong></p> |     **G1\~G16**    |                  접속할 용접건 번호                 |          <p>OFF시 무시되는</p><p>파라미터 </p>         |

접속완료는 기계적인 접속과 로봇 제어기 내부 처리가 끝나야 완료 처리가 됩니다. 접속완료 대기시간은 위 2가지 과정이 모두 완료될 때까지 대기하는 시간입니다.