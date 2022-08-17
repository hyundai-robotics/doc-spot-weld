# 2.4.1 Automatic setting

Progress the automatic setting of the application setting of the servo gun by pressing the 『**All automatic setting**』 key. In the case of ‘**all automatic setting**’, the moving electrode of the servo gun moves automatically. In addition, the set values are affected by the squeezing force, so the following conditions must be satisfied.

* Moving and fixed electrodes with new tipes attached
* No worker around the servo gun
* No workpiece between the moving electrode and fixed electrode
* Manual mode
* Motor on
* Completion of the servo gun's default setting (step 1) 


In the case of ‘**all automatic setting**’, the following procedures will proceed automatically.

1. Gun search
   * Gun search will be performed while servo gun squeezing occurs two times.
   * First time: ‘Gun search reference position record’ valid
   * Second time: ‘Gun search reference position record’ invalid 
2. Gun arm deflection amount compensation
   * Gun arm deflection amount compensation will be performed while servo gun squeezing occurs five times.
3. Panel thickness measurement compensation  
   * Gun arm deflection amount compensation will be performed while servo gun squeezing occurs five times.

{% hint style="info" %}
\[**Caution**] The gun search that can be performed through ‘**automatic setting**’ is only for gun search 1. When using other gun searches other than gun search 1, you should refer to “[**4.1** **Gun search**](../../4-work-teaching/4-1-gun-search/)” of “[**4.** **Work teaching**](../../4-work-teaching/).”
{% endhint %}

&#x20;In the case of ‘all automatic setting’, the ‘gun arm deflection amount compensation’ and ‘panel thickness measurement compensation’ will be performed at the same time, so the servo gun performs squeezing only five times. For execution of ‘gun search’, the squeezing force and gun search speed should be designated. If you press the『Gun search condition setting』key in the aformentioned ‘Application setting’ screen, the squeezing force and moving speed that will be used during gun search can be set as shown in the figure below.


<p align="center">
 <img src="../../_assets/image_22_eng.png" width=70%></img>
 <em><p align="center">Figure 2.16 Gun search condition setting screen</p></em>
</p>

{% hint style="info" %}
\[**Caution**] In the case of ‘**gun arm deflection compensation**’ and ‘**panel thickness measurement compensation**’, it is difficult to manually measure and fill in the values, so it is recommended to use automatic setting.

The ‘gun arm deflection amount compensation’ value is a value used instead of the ‘gun arm deflection amount/100 kgf\[mm]’ among the servo gun parameters. When the ‘gun arm deflection amount compensation’ value is set, the already set ‘gun arm deflection amount/100 kgf\[mm]’ will not be used. On the contrary, if a ‘gun arm deflection amount compensation’ value is not set, the ‘gun arm deflection amount/100 kgf\[mm] will be used.’
{% endhint %}

The configuration and functionality of the servo gun application setting screen is as follows.

<p align="center">
 <img src="../../_assets/image_55_eng.png" width=70%></img>
 <em><p align="center">Figure 2.17 Servo gun applicaiton setting screen</p></em>
</p>

>1. **Status**: Shows the current setting status of the servo gun (before setting, complete or changed).
>2. **Individual automatic setting**: Supports the function of automatically setting the checked items only, not all. Pressing the 『**Selected item automatic setting**』 key will allow automatic setting to be performed only for the checked items.
>3. **Manual setting**: To move to the screen for setting the relevant items
>     *   Gun arm deflection amount compensation  
>       To automatically move to the screen of 『**Setting**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 → 『**3: Welding gun parameter**』
>     *   Panel thickness measurement compensation  
>         To automatically move to the screen of 『**Setting**』 → 『**4: Application parameter**』 → 『**1: Spot welding**』 → 『**3: >Welding gun parameter**』
>4. **Guide**: Indicates the current status of settings or the cause and measure in case of occurrence of an error.
>5. **Monitoring**: Indicates the current status of settings and the position of the servo gun, the feedback current, the set values, etc.
>6. **All automatic setting**: Commands the execution of all automatic setting of all items.
>7. **Selected item automatic setting**: Automatically sets only the items that are designated as the items of individual automatic setting.
>8. **Execution stop**: Stops the setting that is in progress.
>9. **Gun search condition setting**: Sets the speed and squeeze force for gun search.
