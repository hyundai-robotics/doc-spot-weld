﻿# 4.1.4.1 서보건

서보건의 건서치 기능은 총 전극 마모량을 고정전극과 이동전극이 50%씩 반영하도록 초기 설정되어 있습니다. 따라서 건서치 1만을 사용하여 마모량을 계산할 수 있습니다. 만일 고정전극과 이동전극의 마모량을 각각 계산하고자 하는 경우에는 건서치 2 설명을 참고하십시오.

{% hint style="warning" %}
『**이동전극 마모량/전체 마모량(%)**』 설정 값이 “0”이면 건서치 2 동작이 반드시 필요하며, “0”이 아니면 건서치 1 동작에 의한 전체 마모량을 설정 비율로 각각 분배합니다.
{% endhint %}

(1) 건서치 1

이동전극으로 고정전극을 가압하여 전극의 전체 마모량을 측정합니다.

```python
S1   move P,spd=60%,accu=0,tool=1           #건서치1 동작위치로 이동
     gunsea gun=1,sea=1,pre=100,spd=10      #건서치1 수행
     end
```

<p align="center">
 <img src="../../../_assets/image_7.png" width="55%"></img>
 <em><p align="center">그림 4.3 건서치 1</p></em>
</p>


>1. 스텝의 기록 위치로 이동합니다.
>2. 설정된 가압력에 도달할 때까지 이동전극으로 고정전극을 가압합니다.
>3.  가압 일치가 검지되면 전극의 전체 마모량을 측정하고 개방동작을 실행합니다.  
>    전극의 전마모량 = 가압일치 검지위치 - 건서치1 기준위치
>4. 스텝의 기록 위치까지 개방합니다.
>5. 건서치 1만 동작하는 환경에서는 아래의 그림과 같이 측정된 전체 마모량을 이동전극과 >고정전극의 비율로 마모량을 각각 분배합니다. (기본값은 50:50)

<p align="center">
  <img src="../../../_assets/image_70.png" width="70%"></img>
 <em><p align="center">그림 4.4 건서치 1에 의한 마모량 계산</p></em>
</p>


(2) 건서치 2

이동전극의 마모량을 측정합니다. 측정방법은 가압력을 이용하는 방법과 외부신호를 이용하는 방법을 사용할 수 있습니다.

*   **가압력을 이용하는 방법**

    이동전극으로 교정지그를 가압하여 이동전극의 마모량을 측정합니다.

```python
S1   move P,spd=60%,accu=0,tool=1           #건서치1 동작위치로 이동
     gunsea gun=1,sea=1,pre=100,spd=10      #건서치1 수행
S2   move P,spd=60%,accu=0,tool=1           #건서치2 동작위치로 이동
     gunsea gun=1,sea=2,pre=100,spd=10      #건서치2 수행
     end
```

<p align="center">
 <img src="../../../_assets/image_4.png" width="55%"></img>
 <em><p align="center">그림 4.5 가압력 이용 건서치 2</p></em>
</p>

>1. 스텝의 기록 위치로 이동합니다.
>2. 설정된 가압력에 도달할 때까지 이동전극으로 서치 교정지그를 가압합니다.
>3.  가압일치가 검지되면, 이동전극 마모량을 검출하고, 개방동작을 실행합니다.  
>    **이동전극 마모량 = 가압일치 검지위치 –가압력 이용 방식 건서치 2 기준위치**  
>    **고정전극 마모량 = 건서치1로 검지한 전체 마모량 – 이동전극 마모량**  
>4. 개방이 완료되면 이동전극 및 고정전극 마모량이 갱신됩니다.

*   **외부신호를 이용하는 방법**

    이동전극을 센서가 있는 위치로 이동하여 센서 입력이 감지되면 이동전극의 마모량을 측정합니다.

```python
S1   move P,spd=60%,accu=0,tool=1           #건서치1 동작위치로 이동
     gunsea gun=1,sea=1,pre=100,spd=10      #건서치1 수행
S2   move P,spd=60%,accu=0,tool=1           #i건서치 동작위치로 이동
     igunsea gun=1,spd=10,di=1              #i건서치 수행
     end
```

<p align="center">
 <img src="../../../_assets/image_73.png" width="55%"></img>
 <em><p align="center">그림 4.6 외부신호 입력 건서치 2</p></em>
</p>

>1. 스텝의 기록 위치로 이동합니다.
>2. 이동전극이 서치 속도로 접근하여 광전관 접점신호를 절환합니다.
>3.  광전관에 신호가 검지되면 이동전극 마모량을 검출하고 개방동작을 실행합니다.  
 >   **이동전극 마모량 = 외부신호 검지위치 - 외부신호 입력 방식의 건서치2 기준위치**  
 >   **고정전극 마모량 = 건서치1로 검지한 전체 마모량 - 이동전극 마모량**  
>4. 개방이 완료되면 이동전극 및 고정전극 마모량이 갱신됩니다.
