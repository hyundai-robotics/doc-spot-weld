# 4.1 Gun search

Gun search is a function to measure the consumption amount of an electrode. Use this function when you need to re-measure the consumption amount of the electrode after polishing it through tip dressing or after replacing the existing tip with a new one. If  the gun type is servo gun or equalizerless gun, the gun automatically compensates the squeezing position as much as the consumption amount when executing the spot command, which makes it essential to manage the consumption amount and shows that the accuracy of the consumption amount affects the welding quality.

 The types of gun search provided by our company and their simple characteristics are as follows.

*   **gunsea**

    This is the gun search function for a servo gun and is executed with one squeezing operation.

     The total consumption amount of the moving and fixed electrodes is measured and distributed according to the designated ratio.

    This function is used if the consumption ratio between the moving electrode and fixed electrode is the same or fixed.
*   **gunsea 2**

    This is the gun search function for a servo gun and is executed with one squeezing operation and one moving operation.

    The total consumption amount of the moving and fixed electrodes is measured (one squeezing operation) and then the moving electrode consumption amount is measured separately.

    This function is used if the consumption ratio between the moving electrode and fixed electrode is not fixed.
*   **igunsea**

    In the same way as gun search  2, this is the gun search function for a servo gun and executed with one squeezing operation and one moving operation. However, the moving electrode consumption amount is measured using a sensor.

    The total consumption amount of the moving and fixed electrodes is measured (one sequeezing operation) and then the moving electrode consumption amount is measured (one moving operation) separately.

    This function is used if the consumption ratio between the moving electrode and fixed electrode is not fixed.
*   **egunsea**

    This is the gun search function for an equalizerless gun and, in the same way as the igunsea function, the consumption amount is measured by receiving a sensor signal.

</br>
The gun search state can be checked from the /Monitoring/Spot section.
