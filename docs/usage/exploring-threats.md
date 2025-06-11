# Menaces

En cliquant sur "Menaces" dans la barre latérale gauche, vous accédez à tous les onglets "Menaces", visibles en haut à gauche. Par défaut, l'utilisateur accède directement à l'onglet "Threat Actor (Group)", mais peut naviguer vers les autres onglets.

Depuis la section `Menaces`, les utilisateurs peuvent accéder aux onglets suivants :

- `Threat actors (Group)` : Threat actor (Group) représente un groupe physique d'attaquants opérant un Intrusion set, utilisant des malwares et une infrastructure d'attaque, etc.
- `Threat actors (Indvidual)` : Threat actor (Individual) représente un véritable attaquant pouvant être décrit par des attributs physiques et personnels ainsi que des motivations. Threat actor (Individual) opère un Intrusion set, utilise des malwares et une infrastructure, etc.
- `Intrusion sets` : Intrusion set est un concept important dans le domaine de la Cyber Threat Intelligence. Il s'agit d'un ensemble cohérent d'éléments techniques et non techniques correspondant à ce que fait, comment et pourquoi agit un Threat actor. Il est particulièrement utile pour associer plusieurs attaques et actions malveillantes à une menace définie, même sans information suffisante sur l'identité de l'auteur. Souvent, avec l'évolution de la compréhension de la menace, il est possible de lier un Intrusion set à un Threat actor (groupe ou individu).
- `Campaigns` : Campaign représente une série d'attaques ayant lieu sur une certaine période et/ou ciblant un sous-ensemble cohérent d'organisations/individus.

## Threat actors (Group and Individual)

### Présentation générale

Les Threat actors sont les humains qui construisent, déploient et opèrent les intrusion sets. Un Threat actor peut être un individu seul ou un groupe d'attaquants (qui peut être composé d'individus). Un groupe d'attaquants peut être un État-nation, un groupe soutenu par un État, une entreprise, un groupe de hacktivistes, etc.

Attention, les groupes d'attaquants peuvent être modélisés comme "Intrusion sets" dans certains flux, car il existe parfois une confusion dans l'industrie entre le groupe de personnes et l'intrusion set technique/opérationnel qu'ils opèrent.

![The Threat actor (Group) cards](assets/cards-threat-group.png)

En cliquant sur les onglets Threat actor (Group ou Individual) en haut à gauche, il est possible de voir la liste de tous les groupes de Threat actors ou Threat actors individuels auxquels vous avez accès, selon vos [marquages autorisés](../administration/users.md). Ces groupes ou individus sont affichés sous forme de **Cartes** où un résumé des connaissances importantes associées à chacun est présenté : description, alias, malwares utilisés, pays et industries ciblés, labels. Il est alors possible de rechercher et filtrer selon des attributs communs ou spécifiques aux Threat actors.

En haut à droite de chaque carte, cliquer sur l'icône étoile permet de la mettre en favori. Cela épinglera la carte en haut de la liste. Il sera également possible d'afficher facilement tous vos favoris dans vos [Tableaux de bord personnalisés](dashboards.md).

### Informations démographiques et biographiques

Les Threat actors individuels disposent de propriétés uniques pour représenter des informations démographiques et biographiques. Les données démographiques actuellement suivies incluent les pays de résidence, citoyennetés, date de naissance, genre, etc.

![Threat Actor (Individual) Demographics](assets/threat-actor-individual-demographics.png)

Les informations biographiques incluent la couleur des yeux et des cheveux, ainsi que la taille et le poids connus.

![Threat Actor (Individual) Biographics](assets/threat-actor-individual-biographics.png)

Un Threat actor individuel peut également être suivi comme employé par une organisation ou un groupe de Threat actors. Cette relation peut être définie dans l'onglet knowledge.

### Visualiser les connaissances associées à un Threat actor

En cliquant sur une carte Threat actor, vous accédez à son onglet Overview. Pour un Threat actor, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées au Threat actor. Différentes vues thématiques sont proposées pour visualiser facilement la victimologie, l’arsenal et les techniques utilisées par le Threat actor, etc. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés au Threat actor. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

## Intrusion Sets

Un intrusion set est un ensemble cohérent d'éléments techniques tels que "tactiques, techniques et procédures" (TTP), outils, malwares et infrastructures utilisés par un Threat actor contre une ou plusieurs victimes partageant généralement certaines caractéristiques (secteur d'activité, pays ou région) pour atteindre un objectif similaire, quel que soit la victime. L'intrusion set peut être déployé une ou plusieurs fois et peut évoluer dans le temps.
Plusieurs intrusion sets peuvent être liés à un Threat actor. Toutes les entités décrites ci-dessous peuvent être liées à un intrusion set. Il existe de nombreux débats dans la communauté Threat Intelligence sur la façon de définir un intrusion set et de distinguer plusieurs intrusion sets en fonction de :

- leurs différences
- leurs évolutions
- la possible réutilisation
- les attaques de type "false flag"

Comme OpenCTI est très personnalisable, chaque organisation ou individu peut utiliser ces catégories comme il le souhaite. Il est également possible d'utiliser le flux d'importation pour le choix des catégories.

![Intrusion set Cards](assets/instrusion-set-cards.png)

En cliquant sur l'onglet Intrusion set en haut à gauche, il est possible de voir la liste de tous les intrusion sets auxquels vous avez accès, selon vos [marquages autorisés](../administration/users.md). Ces intrusion sets sont affichés sous forme de **Cartes** où un résumé des connaissances importantes associées à chacun est présenté : description, alias, malwares utilisés, pays et industries ciblés, labels. Il est alors possible de rechercher et filtrer selon des attributs communs ou spécifiques à l'Intrusion set.

En haut à droite de chaque carte, cliquer sur l'icône étoile permet de la mettre en favori. Cela épinglera la carte en haut de la liste. Il sera également possible d'afficher facilement tous vos favoris dans vos [Tableaux de bord personnalisés](dashboards.md).

### Visualiser les connaissances associées à un Intrusion set

En cliquant sur une carte Intrusion set, vous accédez à son onglet Overview. Les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées à l'Intrusion Set. Différentes vues thématiques sont proposées pour visualiser facilement la victimologie, l’arsenal et les techniques utilisées par l'Intrusion Set, etc. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à l'Intrusion set. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

## Campaigns

Une campaign peut être définie comme "une série d'activités ou d'attaques malveillantes (parfois appelées 'vague d'attaques') ayant lieu sur une période limitée, contre un groupe défini de victimes, associée à un intrusion set similaire et caractérisée par l'utilisation d'un ou plusieurs malwares identiques envers les différentes victimes et des TTPs communs".
Cependant, une campaign est un élément d'investigation et peut ne pas être largement reconnue. Ainsi, un fournisseur peut définir une série d'attaques comme une campaign et un autre comme un intrusion set.
Les campaigns peuvent être attribuées à un Intrusion set.

![Campaigns cards](assets/campaigns-cards.png)

En cliquant sur l'onglet Campaign en haut à gauche, il est possible de voir la liste de toutes les campaigns auxquelles vous avez accès, selon vos [marquages autorisés](../administration/users.md). Ces campaigns sont affichées sous forme de **Cartes** où un résumé des connaissances importantes associées à chacune est présenté : description, alias, malwares utilisés, pays et industries ciblés, labels. Il est alors possible de rechercher et filtrer selon des attributs communs ou spécifiques aux Campaigns.

En haut à droite de chaque carte, cliquer sur l'icône étoile permet de la mettre en favori. Cela épinglera la carte en haut de la liste. Il sera également possible d'afficher facilement tous vos favoris dans vos [Tableaux de bord personnalisés](dashboards.md).

### Visualiser les connaissances associées à une Campaign

En cliquant sur une carte Campaign, vous accédez à son onglet Overview. Les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées à la Campaign. Différentes vues thématiques sont proposées pour visualiser facilement la victimologie, l’arsenal et les techniques utilisées dans le contexte de la Campaign. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à la Campaign. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).


> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.