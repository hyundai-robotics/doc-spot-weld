﻿# 4.2.2.3 Eq건

건타입이 Eq건인 경우 스폿용접 펑션의 재생은 아래의 그림과 같이 동작합니다.

<p align="center">
 <img src="../../../_assets/image_82.png" width="60%"></img>
 <em><p align="center">그림 4.10 Eq건 스폿용접의 재생</p></em>
</p>

>1. N-1스텝의 위치에서 스텝의 기록위치로 이동합니다.
>2. 용접조건 신호와 함께 용접실행 신호를 출력합니다. 고정전극은 이퀄라이징 설비에 의해서 이동전극은 공압에 의해 판넬을 가압합니다.
>3. 용접완료 신호(WI)가 입력되면, 고정전극은 이퀄라이징 설비가 동작되지 않는 위치로 이동전극은 공압이 공급되지 않은 위치로 이동합니다.
>4. 다음 스텝으로 이동합니다.
