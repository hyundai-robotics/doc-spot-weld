﻿# 4.5.3 접속/분리 타이밍

![](<../../.gitbook/assets/image (10).png>)

*   접속

    접속명령(toolchng on)을 실행 중 로봇과 서보건이 기계적으로 접속이 되면 접속완료 신호가 입력되고 제어기 내부적으로 접속 처리 및 서보건축 구동을 위한 엔코더 전원 투입과 모터 ON 동작을 수행합니다.
*   분리

    분리명령(toolchng off)은 접속과 상반되는 시퀀스를 가지고 분리 처리를 수행합니다.