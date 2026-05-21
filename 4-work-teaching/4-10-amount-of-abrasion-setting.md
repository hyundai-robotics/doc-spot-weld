# 4.10 스폿 시스템 변수

일부 설정값은 스폿 시스템 변수를 이용하여 접근할 수 있습니다. 스폿 시스템 변수는 조건별 클리어런스 값과 건별 이동전극, 고정전극의 마모량 및 전체 마모량 값을 저장하고 있습니다. 아래 그림과 같이, 명령어 창에 변수 대입문을 이용하여 값을 수정하거나 읽어올 수 있습니다.


<p align="center">
 <img src="../_assets/image_93.png" width="70%"></img>
 <em><p align="center">그림 4.23 스폿 마모량 시스템 변수 사용예</p></em>
</p>

<br>

|분류|시스템 변수|내용|
|:--:|:--:|:--:|
|용접조건|_spotcnd[#].fixed_tip_clearance|조건번호(#)의 고정전극 클리어런스 값|
|용접조건|_spotcnd[#].moving_tip_clearance|조건번호(#)의 이동전극 클리어런스 값|
|용접건|_spotgun[#].fixed_tip_consump|건번호(#)의 고정전극 마모량|
|용접건|_spotgun[#].moving_tip_consump|건번호(#)의 이동전극 마모량|
|용접건|_spotgun[#].total_tip_consump|건번호(#)의 전체 마모량|

<br>

{% hint style="warning" %}
- 마모량 관련 시스템 변수는 서보건 및 Eqless 건에만 적용이 가능합니다.
- 임의 설정한 마모량 값은 건서치 이후 측정된 값으로 변경됩니다.
{% endhint %}
