# Observations

En cliquant sur "Observations" dans la barre latérale gauche, vous accédez à tous les onglets "Observations", visibles sur la barre supérieure à gauche. Par défaut, l'utilisateur accède directement à l'onglet "Observables", mais peut également naviguer vers les autres onglets.

Depuis la section `Observations`, les utilisateurs peuvent accéder aux onglets suivants :

- `Observables` : Un `Observable` représente un objet immuable. Les Observables peuvent couvrir un large éventail d'entités telles que des adresses IPv4, des noms de domaine, des adresses email, etc.
- `Artefacts` : Dans OpenCTI, un `Artefact` est un Observable particulier. Il peut contenir un fichier, tel qu'un échantillon de malware.
- `Indicators` : Un `Indicator` est un objet de détection. Il est défini par un motif de recherche, qui peut être exprimé dans différents formats tels que STIX, Sigma, YARA, entre autres.
- `Infrastructures` : Une `Infrastructure` décrit tout système, service logiciel et toute ressource physique ou virtuelle associée destinée à soutenir un objectif (par exemple, serveurs C2 utilisés lors d'une attaque, dispositifs ou serveurs faisant partie de la défense, serveurs de bases de données ciblés par une attaque, etc.).


## Observables

### Présentation générale

Un Observable est une entité distincte de l'Indicator dans OpenCTI et représente un objet immuable. Les Observables peuvent couvrir un large éventail d'entités telles que des adresses IPv4, des noms de domaine, des adresses email, etc. Il est important de noter que les Observables n'impliquent pas nécessairement une intention malveillante ; ils peuvent inclure des éléments légitimes comme des adresses IP ou des domaines associés à une organisation. De plus, ils servent de points de données bruts sans le contexte de détection supplémentaire présent dans les Indicators.

En cliquant sur l'onglet Observables en haut à gauche, vous voyez la liste de tous les Observables auxquels vous avez accès, en fonction de vos [définitions de marquage autorisées](../administration/users.md).

![Observables list](assets/observables-list-view.png)

### Visualiser la connaissance associée à un Observable

En cliquant sur un `Observable` dans la liste, vous arrivez sur son onglet Overview. Pour un Observable, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section), avec la particularité d'afficher les Indicators composés avec l'Observable.
- Knowledge : un onglet listant toutes ses relations et [objets imbriqués](nested.md).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à l'Observation. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant aux événements où l'`Observable` (IP, nom de domaine, url, etc.) a été observé.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

![Observable overview](assets/observable_overview.png)


## Artefacts

### Présentation générale

Un Artefact est un Observable particulier. Il peut contenir un fichier, tel qu'un échantillon de malware. Les fichiers peuvent être téléchargés ou téléversés dans des archives chiffrées, offrant une couche de sécurité supplémentaire contre la manipulation potentielle de charges malveillantes.

En cliquant sur l'onglet Artefacts en haut à gauche, vous voyez la liste de tous les Artefacts auxquels vous avez accès, en fonction de vos [définitions de marquage autorisées](../administration/users.md).

![Artefacts list](assets/artefacts-list-view.png)

### Visualiser la connaissance associée à un Artefact

En cliquant sur un `Artefact` dans la liste, vous arrivez sur son onglet Overview. Pour un Artefact, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section), avec la particularité de pouvoir télécharger le fichier attaché.
- Knowledge : un onglet listant toutes ses relations et [objets imbriqués](nested.md).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à l'Artefact. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant aux événements où l'`Artefact` a été observé.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

![Artefact overview](assets/artefact_overview.png)


## Indicators

### Présentation générale

Un Indicator est un objet de détection. Il est défini par un motif de recherche, qui peut être exprimé dans différents formats tels que STIX, Sigma, YARA, entre autres. Ce motif sert de clé pour identifier des menaces potentielles dans les données. De plus, un Indicator inclut des informations supplémentaires qui enrichissent son contexte de détection. Ces informations comprennent :

- Dates de validité : Les Indicators sont accompagnés d'une période de validité, spécifiant la durée de leur pertinence, modélisée par les champs `Valid from` et `Valid until`.
- Champs actionnables : Liés aux dates de validité, les champs `Revoked` et `Detection` peuvent être utilisés pour trier les Indicators à des fins de détection.
- Kill chain phase : Ils indiquent la phase dans la cyber kill chain où ils sont applicables, offrant des informations sur la progression d'une menace potentielle.
- Types : Les Indicators sont catégorisés selon leur nature, facilitant la classification et l'analyse.

En cliquant sur l'onglet Indicators en haut à gauche, vous voyez la liste de tous les Indicators auxquels vous avez accès, en fonction de vos [définitions de marquage autorisées](../administration/users.md).

![Indicators list](assets/indicators-list-view.png)

### Visualiser la connaissance associée à un Indicator

En cliquant sur un `Indicator` dans la liste, vous arrivez sur son onglet Overview. Pour un Indicator, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section), avec la particularité d'afficher les Observables sur lesquels il est basé.
- Knowledge : un onglet listant toutes ses relations.
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à l'Indicator. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant aux événements où l'`Indicator` a été observé.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

![Indicator overview](assets/indicator_overview.png)


## Infrastructures

### Présentation générale

Une Infrastructure désigne un ensemble de ressources, outils, systèmes ou services utilisés par une menace pour mener ses activités. Elle représente le cadre ou le système de support sous-jacent qui facilite les opérations malveillantes, comme les serveurs de commande et contrôle (C2) lors d'une attaque. À noter, comme pour les Observables, une Infrastructure n'implique pas nécessairement une intention malveillante. Elle peut aussi représenter des ressources légitimes affiliées à une organisation (par exemple, des dispositifs ou serveurs faisant partie de la défense, des serveurs de bases de données ciblés par une attaque, etc.).

En cliquant sur l'onglet Infrastructures en haut à gauche, vous voyez la liste de toutes les Infrastructures auxquelles vous avez accès, en fonction de vos [définitions de marquage autorisées](../administration/users.md).

![Infrastructures list](assets/infrastructures-list-view.png)

### Visualiser la connaissance associée à une Infrastructure

En cliquant sur une `Infrastructure` dans la liste, vous arrivez sur son onglet Overview. Pour une Infrastructure, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section), avec la particularité d'afficher des graphiques de distribution de ses Observables associés (STIX SCO).
- Knowledge : un onglet complexe qui regroupe toute la connaissance structurée liée à l'Infrastructure. Différentes vues thématiques sont proposées pour visualiser facilement les menaces, l'arsenal, les observations, etc. liés à l'Infrastructure. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à l'Infrastructure. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.