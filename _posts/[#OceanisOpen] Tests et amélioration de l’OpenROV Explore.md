# [#OceanisOpen] Tests et amélioration de l'OpenROV Explore

> _Par Emmanuel Poisson Quinton et Xavier Coadic_

![](https://i.imgur.com/J2mS2HI.png)


L'OpenROV est un outil d'appui au projet PolarROV : 

*   Pad de suivi : [PolarROV Robot sous marin polaire open source](/I1SyFbeTdeO_Kcdnx35WdeN)
*   Répertoire Bitbucket : [bitbucket.org/polarrov/polarrov/wiki/Home](https://bitbucket.org/polarrov/polarrov/wiki/Home)


Tutoriels de montage et d'utilisation de l'OpenROV : 

*   [](http://openrov.dozuki.com/c/OpenROV_v2.7_%28Kit_Assembly%29_-_English)http://openrov.dozuki.com/c/OpenROV_v2.7_%28Kit_Assembly%29_-_English
*   [](http://openrov.dozuki.com/Guide/OpenROV+Operators+Manual/80)http://openrov.dozuki.com/Guide/OpenROV+Operators+Manual/80

Nous utilisons l'OpenROV pour comprendre les potentiels et les limites de la robotique sous-marine : 

*   Conditions d'utilisation
*   Fiabilité
*   Systèmes d'étanchéité
*   Qualité de l'image vidéo
*   Contrôles

![](https://i.imgur.com/dQmVQtq.jpg)

**Flottabilité**: 

Test en piscine des commandes de navigation, test de stabilité et flottabilité, vérification  de l'�tanch�it� des compartiments. 

*   En eau douce l'OpenROV est en flottabilité légèrement négative

**Etanchéité **: 

Problème d'étanchéité sur le compartiment avant caméra/carte de commande/phare. Certainement lié aux système de pressurisation latéraux. Cela occasionne également de la bulle à l'intérieur du compartiment et gène la vision de la caméra. 

*   Problème d'étanchéité sur le compartiment central et le tube batterie babord

    * -> Mettre des joints caoutchoucs supplémentaires


![](https://i.imgur.com/L849fHE.jpg)

**Solutions envisageables :**

*   Sur les systèmes de pressurisation latéraux, ajouter un joint caoutchouc rond en face extérieure sur le système de piston à seringue
*   Sur ballaste batterie 

** Solutions réalisées:**

*   étanchéification des systèmes de pressurisation latéraux avec de la résine epoxy
*   renforcement des couches d'étanchéité des tubes batterie avec résine epoxy sur les zones percées
*   une couche supplémentaire de ....? sur les joints du tube caméra/cartes et sur les joints des tubes batteries.

**Contrôle**: 

Il faut prévoir de changer le câble de commande pilotage torsadé par un double câble non torsadé.

Monter un système de inspiré des auto tamponneuses pour placer le câble de commande pilotage d' au dessus du chassis du Rov afin d'éviter  un accident câble + hélices lors des manSuvres de recul. 
![](https://i.imgur.com/bHEY0mZ.jpg)


*   Renforts métalliques
*   Nouvel ombilic
*   Système de protection batterie ion-lithium

**Tests du samedi 16 avril 2016**

En mer, derriére la station de biologie marine

![](https://i.imgur.com/jKGvG68.jpg)



_Cession test du ROV et pilotage par les élèves ingénieurs de l'ICAM depuis la station de biologie marine de Concarneau_

![](https://i.imgur.com/K14W8AP.jpg)


**En mer depuis la berge rocheuse**

Points positifs: 

*   Le ROV est étanche
*   Le câble de commande n'approche plus les h�lices moteur suite au dispositif de queue arri�re semi rigide

![](https://i.imgur.com/kIpODSR.jpg)


Colson grande taille (50 cm) pris dans l'ossature plexi du ROV. Le cable de commande est enroul� autour du Colson puis entouré au scotch électricien sur toute la longueur du colson. Cela permet d'éviter que le c�ble de commande vienne se prendre dans les hélices lors de manSuvre de recul par exemple.

![](https://i.imgur.com/ONzcjNo.jpg)

Utilisation d'un petit colson pour tendre le c�ble de commande à la sortie du ROV pour �viter le contact avec les hélices en rotation.

![](https://i.imgur.com/8oNVzJq.jpg)


Axes d'améliorations: 

*   La puissance de propulsion est trop faible pour utiliser le ROV en Mer
*   De la bulle se forme dans le caisson caméra et carte de programmation 

![](https://i.imgur.com/3ASLbuQ.jpg)


*   Imaginer un câble de  travail de force pour récupérer le ROV en cas de problème sans avoir à tirer sur le câble de commande
*   Faire flotter légèrement le câble de commande pour éviter l'emmêlement avec des obstacles? 

**Au port depuis le ponton**

*   Le câble de commande se prend dans un simple algue, le ROV et se retourne et devient impossible à manœuvrer
*   Après déconnexion du pad de pilotage  pour transport et reconnexion sur le port pour second test, les commandes sur le logiciel de pilotage sont déréglées.
*   Lors de l'ordre de la marche arrière, seule l'hélice gauche du ROV tourne. Le ROV pivote donc autant qu'il recul. 
*   Une gaffe est un outil utile pour récupérer le ROV ou le câble de commande en cas d'emmâlement 

**17 et 18 juin 2016 - Lab Bro Pondi - semaine Fabrication numérique**

[Lab Bro Pondi](http://labbropondi.fr/)  à Pontivy, dpt.56
 

Suite problème de connexion ethernet et webcache :

- [OpenROV](https://github.com/OpenROV)/**[openrov-cockpit](https://github.com/OpenROV/openrov-cockpit)** 

- [](https://github.com/OpenROV/openrov-software/tree/master/developer_guide)https://github.com/OpenROV/openrov-software/tree/master/developer_guide

- [connection to use correct property of window.location](https://github.com/OpenROV/openrov-cockpit/pull/2/commits/2d53383fd0925c4524c5708098411f56609ba0b3)  : Cockpit

*   Vérification de la connectic RJ45 on topside interface board
*   Vérification de la conductivité de la carte interface avec multimètre 
  
 
 ![](https://i.imgur.com/syFtGNM.jpg)


**5 aout 2016 - Indiecamp Camp**

[Documentation de ce qui a été fait](https://lebiome.github.io/#LeBiome/camps/blob/master/indie_camp_kerbors_2016/reparation_openrov.md) 


<iframe width="560" height="315" src="https://videos.lescommuns.org/videos/embed/3d4b8af7-32f5-4e9d-b9d9-ac8b9c4f3927" frameborder="0" allowfullscreen></iframe>

**Avril 2017 - déconstruction **

Dans le but d'améliorer grandement les qualit�s du ROV et ses possibilité
![](https://i.imgur.com/FAEelKC.jpg)


**Démarrage de pistes d'amélioration**

* Carénage 
![](https://i.imgur.com/AP8lWWg.jpg)

![](https://i.imgur.com/Yn4ie2y.jpg)


![](https://i.imgur.com/kRckg5l.jpg)


* [Hydrodynamic Characteristics of the Sailfish (Istiophorus platypterus) and Swordfish (Xiphias gladius) in Gliding Postures at Their Cruise Speeds](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0081323) 