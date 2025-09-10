---
layout: single
title: "MODELISME FERROVIAIRE ET SIMULATION"
permalink: /techno/
excerpt: "Technologies pour la simulation"
header:
    overlay_image: /assets/images/headerimage.jpeg
    image_description: "G1000"
    caption: "Photo Rauletus"
toc: false
toc_label: "Technologies"
toc_sticky: true
author_profile: false
sidebar:
    nav:
        - main
        - techno
---

Cette rubrique présente des solutions que j'utilise pour mes simulations.

Ces solutions se complètent et doivent donc être intelligemment assemblées sous la forme d'une architecture d'ensemble.

Les principes qui guident mes choix sont les suivants :
* fiabilité des solutions et de l'architecture d'ensemble
* respect des normes et standards techniques du marché
* bonnes performances
* simplicité de mise en oeuvre et de maintenance (à long terme)
* technologies portables (pour ne pas être verrouillé par un fournisseur)
* solutions évolutives et facilement adaptables aux nouveaux besoins
* solutions ouvertes et offrant des capacités d'interface
* coût optimisé et maîtrisé

Architecture
------------

Les principaux composants de ma solution à date sont présentés dans le schéma ci-dessous.
Je cherche à utiliser le plus possible de composants prêts à l'emploi afin de développer le minimum de choses moi-même.

![Architecture](../images/architecture_globale.jpg)

J'ai décidé de réaliser moi-même une centrale basée sur le logiciel [DCC-EX](https://dcc-ex.com) et la plateforme **Arduino**.

## Commande digitale DCC

Hardware :

J'ai réalisé une station de commande complète très simplement en assemblant :
* une carte Arduino Mega 2560
* une carte additionnelle Motor Shield
* une alimentation 18V (5A)

Cette station à une puissance suffisante pour piloter sans difficulté plusieurs locomotives et des accessoires DCC.

Software :

* ordinateur standard (PC ou Mac) :
    * connecté à la carte Arduino Mega 2560 avec un cable USB (5V et données)
* logiciel open source DCC-EX EX-CommandStation pour Arduino (C++)
* logiciel open source IDE Arduino :
    * initialisation de la carte Arduino
    * Serial Monitor pour piloter la station en utilisant l'API

Pour être compatible avec les anciens décodeurs ARNOLD, il faut utiliser le mode SPEED 28.

## Logiciel de pilotage de réseau ferroviaire

Le pilotage avec les commandes de l'API dans le Serial Monitor n'est pas conçu pour le jeu.
J'utilise principalement le logiciel open source JMRI (Java Model Railroad Interface) avec la configuration suivante :
* ordinateur standard (PC ou Mac) :
    * connecté à la carte Arduino Mega 2560 avec un cable USB (5V et données)
    * connecté au réseau local Wifi
* logiciel JMRI DecoderPro ou PanelPro
* pour la commande mobile de type "walk-around" en Wifi :
    * serveur JMRI WiThrottle
    * application mobile open source Engine Driver pour Android
    * application mobile WiThrottleLite pour iOS 

JMRI permet la gestion complète d'un réseau depuis la programmation des décodeurs DCC jusqu'au pilotage des itinéraires, en passant par les cantons, les signaux, les aiguillages, etc.
Il gère notamment ici pour mes besoins :
* une horloge accélérée
* des scripts d'automatisation tels que l'aller/retour d'une locomotive pour simuler un trafic minimum
* des interfaces natives avec DCC-EX
* des panneaux de contrôle et synoptiques du réseau animés en temps-réel
* les interfaces techniques (APIs) pour l'intégration avec d'autres logiciels
* les aiguillages pilotés en DCC
* les signaux lumineux pilotés en DCC et le cantonnement associé en mode BAL
* les itinéraires des trains et la réservation des cantons
* les mouvements de wagons

Des capteurs tels que des ILS ou des détecteurs de présence par consommation de courant (j'utilise des détecteurs 5556 de Stock87) peuvent être reliés à une carte Arduino.
Pour des réseaux qui le nécessitent, la librairie arduinoCMRI permet de réaliser un noeud C/MRI SMINI avec une carte Arduino.
Reliée au PC avec un cable USB, JMRI peut ainsi réagir à des changements d'état de boutons et détecteurs et peut comme de nombreux logiciels de cette catégorie actionner des LED et des moteurs d'aiguillage.

Simulateur / Logiciel de supervision du Jeu :

Actuellement, le programme YARS s'interface avec le logiciel de pilotage JMRI (Java Model Railroad Interface) de manière à le compléter fonctionnellement. JMRI offre l'avantage de s'interfacer lui-même avec les principales centrales DCC du marché, ainsi que les protocoles de communication standards et peut ainsi constituer une véritable plateforme d'intégration. 
De plus, il offre également à son niveau une interface et un protocole de communication permettant le pilotage des locomotives et accessoires avec divers moyens de télécommande et notamment des applications sur smartphones et tablettes.
En utilisant cette interface, j'ai développé facilement mon propre module au sein de YARS pour commander les locomotives dans les situations de jeu ou cela est utile (par exemple simuler une panne).

En complément, JMRI affiche facilement l'indispensable horloge accélérée ainsi qu'un synoptique et/ou un tableau de contrôle du réseau.
YARS disposant de son propre serveur web intégré, il peut afficher en temps-réel les informations utiles au déroulement du jeu dans un navigateur standard, sur un voire plusieurs écrans simultanément.

Consultez ces pages qui présentent davantage de détails :
* Software
* Hardware
