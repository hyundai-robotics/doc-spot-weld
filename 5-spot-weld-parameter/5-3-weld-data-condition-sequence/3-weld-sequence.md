﻿# 5.3.3 용접시퀀스

스폿용접과 관련된 시퀀스를 설정하여 작업환경에 따라 로봇의 동작을 결정합니다.

<p align="center">
 <img src="../../.gitbook/assets/image (1).png"></img>
</p>

1.  **시퀀스번호**

    용접시퀀스중 원하는 용접시퀀스를 빠르게 선택합니다.
2.  **용접신호 출력 지연시간(GWT)**

    서보건의 경우는 가압일치 후에 용접 신호를 출력할 때까지의 대기시간입니다.

    공압건의 경우는 spot 명령문 실행 후 용접 신호를 출력할 때까지의 대기시간입니다.
3.  **용접신호 펄스출력(0=레벨)**

    용접 신호를 일정시간 동안만 출력하기 위한 항목입니다. “0”으로 설정하면 용접완료(WI) 신호가 입력될 때까지 계속 출력합니다.
4.  **용접완료(WI) 대기시간**

    용접완료(WI) 신호가 입력되기까지 대기하는 시간입니다. 이 값을 “0”으로 설정하면 입력될 때까지 계속 대기합니다.
5.  **용접완료 후 로봇 대기시간 (RWT)**

    통상 용접완료(WI) 신호가 입력 후 용착 검출을 대기하는 시간입니다. “0.0”으로 설정될 경우 용착 검출을 하지 않습니다. 용착 검출 신호를 사용할 때에는 “0.3초(300 msec)” 이상의 값을 입력하기를 권장합니다. 그러나 이 값이 크면 용접시간이 길어지고 사이클타임이 증가하게 됩니다.