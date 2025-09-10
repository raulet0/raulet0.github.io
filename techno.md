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

![Architecture](../images/architecture_globale.jpg)

Actuellement, YARS s'interface avec le logiciel de pilotage JMRI (Java Model Railroad Interface) de manière à le compléter fonctionnellement. JMRI offre l'avantage de s'interfacer lui-même avec les principales centrales DCC du marché. 
De plus, il offre également à son niveau une interface et un protocole de communication permettant le pilotage des locomotives et accessoires avec divers moyens de télécommande et notamment des applications sur smartphones et tablettes.
En utilisant cette interface, j'ai développé facilement mon propre module au sein de YARS pour commander les locomotives dans les situations de jeu ou cela est utile.
En complément, JMRI affiche facilement l'indispensable horloge accélérée ainsi qu'un synoptique et/ou un tableau de contrôle du réseau.
YARS disposant de son propre serveur web intégré, il peut afficher en temps-réel les informations utiles au déroulement du jeu dans un navigateur standard, sur un voire plusieurs écrans simultanément.

Ces pages présentent des détails :
* Software
* Hardware


Cupidatat ea do et in excepteur in. Ad nostrud ut est esse eu duis ea sunt eiusmod. Aliquip tempor veniam sint elit fugiat. Velit incididunt laboris amet incididunt labore dolore irure velit excepteur commodo deserunt laborum. Consectetur eu fugiat veniam veniam Lorem labore magna eiusmod. Ea occaecat reprehenderit pariatur consectetur minim labore ut aliquip.
