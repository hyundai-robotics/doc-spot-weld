﻿# 4.1.2 건서치 관련 명령문

### <mark style="color:green;">gunsea</mark>

건타입이 서보건인 경우 건서치1 수행 시 또는 가압력 이용 건서치2 수행 시 사용되는 명령문입니다.

```
gunsea gun=<건번호>,sea=<서치번호>,pre=<가압력>,spd=<서치속도>,mgun=<멀티건번호>,mpre=<멀티건가압력>
```

|   **항목**   |                                      **내           용**                                     |
| :--------: | ------------------------------------------------------------------------------------------ |
|   **건번호**  | 서치 할 건번호를 지정                                                                               |
|  **서치번호**  | 건서치1 동작 또는 건서치2 동작을 지정                                                                     |
|   **가압력**  | 가압 일치를 검출하기 위한 지령 가압력을 지정                                                                  |
|  **서치속도**  | <p>서치동작 시 건축의 동작속도를 지정</p><p>서치속도는 안전속도를 기준으로 하며 권장속도는 10mm/s 입니다.</p>                     |
|  **멀티건번호** | 멀티 서보건에 대해 동시에 건서치를 수행하고자 할 때 멀티건 번호를 지정                                                   |
| **멀티건가압력** | <p>멀티 서보건에 대해 동시에 건서치를 수행하고자 할 때 각 건에 가압력을 달리할 필요가 있을 때 지정</p><p>지정되지 않으면 기본건의 가압력이 적용</p> |

{% hint style="info" %}
사용 예)

서보건 5,6을 동시에, 가압력은 각각 100, 200kgf로 건서치 1을 수행하는 경우

\=> gunsea gun=5,sea=1,pre=100,mgun=6,mpre=200
{% endhint %}

### <mark style="color:green;">igunsea</mark>

건타입이 서보건인 경우 입력신호에 의한 건서치2 수행시 사용되는 명령문입니다.

```
igunsea gun=<건번호>,spd=<서치속도>,di=<입력신호>
```

|  **항목**  |                                      **내           용**                 |
| :------: | ---------------------------------------------------------------------- |
|  **건번호** | 서치할 건번호를 지정                                                            |
| **서치속도** | <p>서치동작 시 건축의 동작속도를 지정</p><p>서치속도는 안전속도를 기준으로 하며 권장속도는 10mm/s 입니다.</p> |
| **입력신호** | 광전관 출력을 전달받을 입력신호 번호를 지정                                               |

### <mark style="color:green;">egunsea</mark>

건타입이 Eqless건인 경우 사용합니다.

```
egunsea gun=<건번호>,spd=<서치속도>,dist=<서치거리>,di=<입력신호>
```

|  **항목**  |                                      **내           용**                 |
| :------: | ---------------------------------------------------------------------- |
|  **건번호** | 서치할 건번호를 지정                                                            |
| **서치속도** | <p>서치동작 시 건축의 동작속도를 지정</p><p>서치속도는 안전속도를 기준으로 하며 권장속도는 10mm/s 입니다.</p> |
| **서치거리** | 서치동작 시 건축의 동작거리를 지정                                                    |
| **입력신호** | 광전관 출력을 전달받을 입력신호 번호를 지정                                               |