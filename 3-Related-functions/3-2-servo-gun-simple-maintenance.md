﻿# 3.2 서보건 간편 보수

서보건 고장수리 후, 재가동을 위한 일련의 설정을 하나의 창에서 간편하게 수행할 수 있도록 지원합니다. 초기 화면에서 \[**CTRL**]+\[**GUN**]키를 누르면 간편보수를 위한 대화상자가 출력됩니다.

![](<../.gitbook/assets/image (26).png>)

*   **시리얼 엔코더 리셋**

    서보건 모터에 부착된 시리얼 엔코더에 대해서 “**엔코더 리셋**” 또는 “**에러 해제**” 동작을 수행합니다. 변경된 설정이 적용되려면 반드시 전원을 재투입하여야 합니다. “엔코더 리셋”수행후에는 엔코더 정보가 초기화되므로 엔코더 옵셋 설정, 축 원점 설정, 건서치 기준위치 기록을 새롭게 수행하여야 합니다.
*   **엔코더 옵셋**

    서보건 축의 엔코더 원점을 설정합니다. 서보건 축의 엔코더 원점은 수동으로 브레이크를해제하여 이동전극이 최대로 개방된 위치에서 설정합니다.
*   **축 원점**

    서보건 축의 축 원점을 설정합니다. 서보건 축의 축 원점은 마모가 없는 새 전극을 장착한 후, 전극이 서로 맞닿는 위치에서 설정합니다.
*   **건서치 실행**

    현재 위치에서 서보건 축만 동작하여 gunsea 명령을 수행합니다.
*   **용접 실행**

    현재 위치에서 서보건 축만 동작하여 spot 명령을 수행합니다.