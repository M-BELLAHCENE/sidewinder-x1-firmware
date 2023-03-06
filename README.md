# [EN] ARTILLERY Sidewinder X1

![SidewinderTFT](https://user-images.githubusercontent.com/34917424/158008670-81473660-f0a3-4e17-90ff-7afa34f93dbd.png)
 
## Steps/mm

The default setting was 80.121 in X and Y, 399.778 in Z and 445 in E.  
The decimal values did not bring more precision and anyway the printer is calibrated by M92 in the startup GCode.  
In Z the printer is equipped with a worm screw and there is no reason to use a decimal pitch value.  
Unjustified decimals in Z lead to impossible rounding and a microstep management which is detrimental to the correct operation of the printer.  
In the firmware I changed the default settings to {80,80,400,445}.  

## Increase the precision

In the original firmware there is MIN_STEPS_PER_SEGMENT set to 6.  
As the printer is set to 80 steps per millimeter this represents a precision of about 0.075mm.  
I set this value to 1 to allow a definition of 0.0125mm.  

## Limiting temperatures

The original firmware allows to go up to 150° on the plate and 275° on the nozzle.  
I was using this possibility to print ABS (135° plate) but I noticed that the equipment could suffer because of the overheating of the electronics.  
In practice, if such high temperatures are used, the printer will behave very strangely, such as tracings that do not appear in the slicer because one of the steppers has gone to safety.  
You can also notice that the printer stops mysteriously in the middle of a layer while the material cools down.  

After this experience I decided to limit the heating of the plate to 95° and 260° on the nozzle.  

## Why no LIN_ADVANCE ?

This feature is very attractive and was supposed to improve the quality of the prints, so I tried it.  
Unfortunately my tests were not really successful.  
Maybe the 8-bit motherboard doesn't have enough computing power or maybe this version of Marlin implements it badly but I didn't succeed.  
I had activated the LIN_ADVANCE first with the K value defined in the firmware and then with K at 0 but I had tried and tried again to calibrate correctly I only found degradations on several tests.
I also tried with the deactivation of the arcs (ARC_SUPPORT G2 and G3) which allows to recover several Kb but it didn't help and it deprived the firmware of some useful features.  
After several tests I decided not to activate this feature.  
In this version ARC_SUPPORT is enabled and LIN_ADVANCE is not.  



# [FR] ARTILLERY Sidewinder X1

![SidewinderTFT](https://user-images.githubusercontent.com/34917424/158008670-81473660-f0a3-4e17-90ff-7afa34f93dbd.png)
 
## Steps/mm

Le réglage par défaut était à 80.121 en X et Y, 399.778 en Z et 445 en E.  
Les valeurs décimales n'apportaient pas plus de précision et de toute façon on calibre l'imprimante par M92 dans le GCode de démarrage.  
En Z l'imprimante est équipée d'une vis sans fin et rien ne justifie une valeur de pas à décimales.  
Des décimales injustifiées en Z mènent à des arrondis impossibles et une gestion du micropas qui nuit au bon fonctionnement de l'imprimante.  
Dans le firmware j'ai modifié les réglages par défaut à {80,80,400,445}.  

## Augmenter la précision

Dans le firmware d'origine on trouve MIN_STEPS_PER_SEGMENT défini à 6.  
Comme l'imprimante est à 80 pas par millimetre ça représente une précision de l'ordre de 0.075mm.  
J'ai ramené cette valeur à 1 pour autoriser une définition de 0.0125mm.  

## Limiter les températures

Le firmware d'origine permet d'aller jusqu'à 150° sur le plateau et 275° sur la buse.  
J'utilisais cette possibilité pour imprimer l'ABS (plateau à 135°) mais j'ai constaté que le matériel pouvait en souffrir à cause des surchauffes de l'électronique.  
En pratique si on utilise des températures aussi hautes l'imprimante aura des comportements des plus étranges comme des tracés qui n'apparaissent pas dans le slicer parce qu'un des steppers s'est mis en sécurité.  
On peut également constater que l'imprimante s'arrête mystérieusmeent au milieu d'une couche le temps que le matériel refroidisse.  

Suite à cette expérience j'ai décidé de limiter la chauffe du plateau à 95° et à 260° sur la buse.  

## Pourquoi pas de LIN_ADVANCE ?

Cette fonctionalité est très séduisante et devait améliorer la qualité des impressions et j'ai donc essayé.  
Malheureusement mes essais n'ont vraiment pas été couronnés de succès.  
Peut être que la carte mère 8 bits ne dispose pas d'assez de puissance de calcul ou peut être que cette version de Marlin l'implémente mal mais je n'y suis pas arrivé.  
J'avais activé le LIN_ADVANCE d'abord avec la valeur K définie dans le firmware puis avec K à 0 mais j'avais beau essayer et ré-essayer de calibrer correctement je n'ai constaté que des dégradations sur plusieurs tests.
J'ai essayé egalement avec la désactivation des arcs (ARC_SUPPORT G2 et G3) qui permet de récupérer plusieurs Kb mais ça n'a rien arrangé et ça amputait le firmware de fonctionalités qui peuvent être utiles.  
Après plusieurs tests j'ai décidé de ne pas activer cette fonctionnalité.  
Dans cette version ARC_SUPPORT est activé et LIN_ADVANCE non.  
