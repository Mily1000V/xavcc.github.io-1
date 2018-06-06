---
title: "Petite histoire d'un robot sous-marin open source en Bretagne"
layout: post
date: 2018-06-06 12:48
image: /assets/images/openrov_4.jpg
headerImage: true
tag:
- Bretagne
- Communs
- Sciences
- Concarneau
category: blog
author: XavierCoadic
description: de 2015 à 2018
---

En 2015, je recontrais Emmanuel Poisson Quinton à Concarneau, notamment pour le préparation du [Bretgane lab tour](https://xavcc.gitbooks.io/vivre-ensemble-faire-ensemble/content/) d'octobre 2015. Emmanuel travail à Explore, fond de dotation aux explorateurs et exploratrices de solutions scoiétales et environnementales céé par rolan Jourdain.

<iframe width="560" height="315" src="https://videos.lescommuns.org/videos/embed/68cf450f-ca5e-4fe3-abe1-7992f3a0f439" frameborder="0" allowfullscreen></iframe>

De cette rencontre sont nés de nombreux moments extraordinaires autour des océans, des sciences marines participatives ouvertes et des prototypes, qui aujourd'hui encore, me donne des raisons d'expérer dans les praiques collaboratives pour résoudre des problèmes majeurs. 

Voici l'histoire de l'un de ces prototypes.

## [#OceanisOpen] Tests et amélioration de l'OpenROV d'Explore

> _Par Emmanuel Poisson Quinton et Xavier Coadic_

OpenROV est le nom d'un projet en cours de développement, diffusion et large utilisation d'un petit véhicule télécommandé subaquatique léger (« ROV »). Il est conçu en « open-source » et « matériel libre »  et distribué sous licence libre (CC BY-SA 3.0). 
Facilement transportable, ce robot est destiné à permettre l'exploration sous-marine à vocation scientifique, éducationnelle et de découverte partagée du monde subaquatique (« crowd-source exploration »), à des prix abordables. « ROV » signifie en anglais « remotely operated vehicle ».

![](/assets/images/openrov_0.png)


L'OpenROV est également un outil d'appui au projet PolarROV : 

*   PolarROV Robot sous marin polaire open source
*   Répertoire Bitbucket : [bitbucket.org/polarrov/polarrov/wiki/Home](https://bitbucket.org/polarrov/polarrov/wiki/Home)


Tutoriels de montage et d'utilisation de l'OpenROV : 

*  <http://openrov.dozuki.com/c/OpenROV_v2.7_%28Kit_Assembly%29_-_English>
*   <http://openrov.dozuki.com/Guide/OpenROV+Operators+Manual/80>

Nous utilisons l'OpenROV pour comprendre les potentiels et les limites de la robotique sous-marine : 

*   Conditions d'utilisation
*   Fiabilité
*   Systèmes d'étanchéité
*   Qualité de l'image vidéo
*   Contrôles

![](/assets/images/openrov_1.jpg)

<figcaption class="caption">Vue mutli-faces de l'openROV d'Explore</figcaption>

## Premiers Tests en 2016 à Cocarneau 

### Flottabilité: 

Test en piscine en eau douce des commandes de navigation, test de stabilité et flottabilité, vérification  de l'étanchéité des compartiments. 

* En eau douce l'OpenROV est en flottabilité légèrement négative

```
Selon la différence entre la poussée d'Archimède PA et le poids réel Pr, on distingue les corps de flottabilité :

    positive (PA > Pr) : l'objet remonte ;
    nulle (PA = Pr) : l'objet flotte entre deux eaux ;
    négative (PA < Pr) : l'objet coule
```

### Etanchéité : 

Problème d'étanchéité sur le compartiment avant caméra/carte de commande/phare. Certainement lié aux système de pressurisation latéraux. Cela occasionne également de la bulle à l'intérieur du compartiment et gène la vision de la caméra. 

*   Problème d'étanchéité sur le compartiment central et le tube batterie babord

    * -> Mettre des joints caoutchoucs supplémentaires

![](/assets/images/openrov_2.jpg)

<figcaption class="caption">Vue latérale du compartiment principal et vue des caissonns batteries du ROV</figcaption>

### Solutions envisageables :

*   Sur les systèmes de pressurisation latéraux, ajouter un joint caoutchouc rond en face extérieure sur le système de piston à seringue
*   Sur ballaste batterie 

### Solutions réalisées:

*   étanchéification des systèmes de pressurisation latéraux avec de la résine epoxy
*   renforcement des couches d'étanchéité des tubes batterie avec résine epoxy sur les zones percées
*   une couche supplémentaire de ....? sur les joints du tube caméra/cartes et sur les joints des tubes batteries.

### Contrôle : 

Il faut prévoir de changer le câble de commande pilotage torsadé par un double câble non torsadé.

Monter un système de inspiré des auto tamponneuses pour placer le câble de commande pilotage d' au dessus du chassis du Rov afin d'éviter  un accident câble + hélices lors des manœuvres de recul. 

![](/assets/images/blablacar.jpg)


*   Renforts métalliques
*   Nouvel ombilic
*   Système de protection batterie ion-lithium

### Tests du samedi 16 avril 2016

En mer, derriére la station de biologie marine

![](/assets/images/openrov_4.jpg)

<figcaption class="caption"<Session test du ROV et pilotage llors d'une journée de formations aux élèves ingénieurs de l'ICAM depuis la station de biologie marine de Concarneau</figcaption>

![](/assets/images/openrov_5.jpg)


### En mer depuis la berge rocheuse

Points positifs: 

*   Le ROV est étanche
*   Le câble de commande n'approche plus les hélices moteur suite au dispositif de queue arrière semi-rigide

![](/assets/images/openrov_6.jpg)

> Colson grande taille (50 cm) pris dans l'ossature plexi du ROV. Le cable de commande est enroulé autour du Colson puis entouré au scotch électricien sur toute la longueur du colson. Cela permet d'éviter que le câble de commande vienne se prendre dans les hélices lors de manœuvre de recul par exemple.

![](/assets/images/opnrov_7.jpg)

Utilisation d'un petit colson pour tendre le câble de commande à la sortie du ROV pour éviter le contact avec les hélices en rotation.

![](/assets/images/openrov_8.jpg)


Axes d'améliorations: 

*   La puissance de propulsion est trop faible pour utiliser le ROV en Mer en l'état actuel
*   Des bulles se forment dans le caisson caméra et carte de programmation 

![](assets/images/openrov_9.jpg)

*   Imaginer un câble de  travail de force pour récupérer le ROV en cas de problème sans avoir à tirer sur le câble de commande
*   Faire flotter légèrement le câble de commande pour éviter l'emmêlement avec des obstacles? 

### Au port depuis le ponton

![](/assets/images/openrov_8_1.JPG)

<figcaption class="caption"> Depuis le port de Concarneau avec les élèves ingiéneurs de l'ICAM - Crédit Gérald Mannaerts -licence CC BY SA</figcaption>

*   Le câble de commande se prend dans un simple algue, le ROV et se retourne et devient impossible à manœuvrer
*   Après déconnexion du pad de pilotage  pour transport et reconnexion sur le port pour second test, les commandes sur le logiciel de pilotage sont déréglées.
*   Lors de l'ordre de la marche arrière, seule l'hélice gauche du ROV tourne. Le ROV pivote donc autant qu'il recul. 
*   Une gaffe est un outil utile pour récupérer le ROV ou le câble de commande en cas d'emmâlement 

## 17 et 18 juin 2016 - Lab Bro Pondi - Pontivy, semaine de la Fabrication numérique

[Lab Bro Pondi](http://labbropondi.fr/)  à Pontivy, dpt.56
 

Suite problème de connexion ethernet et webcache :

- [OpenROV](https://github.com/OpenROV)/**[openrov-cockpit](https://github.com/OpenROV/openrov-cockpit)** 

- <https://github.com/OpenROV/openrov-software/tree/master/developer_guide>

- [connection to use correct property of window.location](https://github.com/OpenROV/openrov-cockpit/pull/2/commits/2d53383fd0925c4524c5708098411f56609ba0b3)  : Cockpit

*   Vérification de la connectic RJ45 on topside interface board
*   Vérification de la conductivité de la carte interface avec multimètre 
  
 
 ![](/assets/images/openrov_10.jpg)
 
 <figcaption class="caption">Citoyennes et citoyens rassemblées pour apprendre la fabrication numérique sur l'OpenROV</figcaption>

## 5 aout 2016 - Indiecamp Camp kerbors (22)

[Documentation de ce qui a été fait](https://lebiome.github.io/#LeBiome/camps/blob/master/indie_camp_kerbors_2016/reparation_openrov.md) 

<iframe width="560" height="315" src="https://videos.lescommuns.org/videos/embed/3d4b8af7-32f5-4e9d-b9d9-ac8b9c4f3927" frameborder="0" allowfullscreen></iframe>

## Avril 2017 - déconstruction et nouvel horizon biomimétique

Dans le but d'améliorer grandement les qualités du ROV et ses possibilité
![](/assets/images/openrov_11.jpg)

<figcaption class="caption">L'open ROV mis en pièces à Concarneau</figcaption>


### Démarrage de pistes d'amélioration

Orientation prise de copier des propriétées de formes de l'espadon pour résourdre le sproblème de puissance et d'énergie, faciliter l'intégration de nouveau matériel dans le cockpit.

* Carénage 
![](/assets/images/openrov_12.jpg)

![](/assets/images/openrov_13.jpeg)

![](/assets/images/openrov_14.jpeg)

* [Hydrodynamic Characteristics of the Sailfish (Istiophorus platypterus) and Swordfish (Xiphias gladius) in Gliding Postures at Their Cruise Speeds](http://journals.plos.org/plosone/article?id=10.1371/journal.pone.0081323) 

## Aujourd'hui ?

Ocean is Open est intégré au programme [la mer en commun](https://www.monprojetpourlaplanete.gouv.fr/projects/plan-climat/collect/depot-des-projets/proposals/la-mer-en-commun) avec d'autres prototypes comme les filets à faire soi-même pour la surveillance sceintifique des planctons, les cartographies marines d'échouages des déchets, un drone en carton à faire soi-même, Etc.

### Nouveaux rendez-vous en 2018

+ Hackathon Ocean Space City Interfaces à Rennes, [6 - 11 Juin 2018](https://openagenda.com/biomehacklab/events/hackathon-open-source-circular-economy-days-rennes?lang=fr)
+ Le somment mondial des FabLabs, session Auray (56) écologie et océan, [juillet 2018](http://distributed.fab14.org/fab14-ecology-2/).
