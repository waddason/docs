# Vue d'ensemble

## Introduction

Ce chapitre vise à fournir au lecteur une description pas à pas de ce qui est disponible sur la plateforme et la signification des différents onglets et entrées.

Lorsque l'utilisateur se connecte à la plateforme, la page d'accueil est le `Dashboard`. Ce `Dashboard` contient plusieurs visuels résumant les types et la quantité de données récemment importées dans la plateforme.

!!! note "Tableau de bord"
  
  Pour obtenir plus d'informations sur les composants du tableau de bord par défaut, consulter la page [Getting started](getting-started.md#dashboard-section).

Le panneau latéral gauche permet à l'utilisateur de naviguer entre différentes fenêtres et d'accéder à différentes vues et catégories de connaissances.

<figure markdown>
  ![Menu](assets/menu.png)
</figure>

## Structure

### La "hot knowledge"

La première partie de la plateforme dans le menu de gauche est dédiée à ce que nous appelons la "hot knowledge", c'est-à-dire les entités et relations ajoutées quotidiennement dans la plateforme et qui nécessitent généralement un travail ou une analyse de la part des utilisateurs.

* `Analyses` : tous les conteneurs qui véhiculent des connaissances pertinentes telles que rapports, groupements et analyses de malware.
* `Cases` : tous les types de cas comme les réponses à incident, demandes d'information, de retrait, etc.
* `Events` : tous les incidents et alertes provenant des systèmes opérationnels ainsi que les sightings.
* `Observations` : toutes les données techniques dans la plateforme telles que observables, artifacts et indicators.

### La "cold knowledge"

La seconde partie de la plateforme dans le menu de gauche est dédiée à la "cold knowledge", c'est-à-dire les entités et relations utilisées dans la hot knowledge. Vous pouvez voir cela comme "l'encyclopédie" de toutes les connaissances nécessaires pour obtenir du contexte : menaces, pays, secteurs, etc.

* `Threats` : toutes les entités de menaces, des campagnes aux threat actors, y compris les intrusion sets.
* `Arsenal` : tous les outils et malwares utilisés et/ou ciblés par les menaces, y compris les vulnérabilités.
* `Techniques` : tous les objets liés aux tactiques et techniques utilisées par les menaces (TTPs, etc.).
* `Entities` : toutes les informations contextuelles non géographiques telles que secteurs, événements, organisations, etc.
* `Locations` : toutes les informations contextuelles géographiques, des villes aux régions, y compris les positions précises.

### Masquer des catégories

Il est possible de personnaliser l'expérience sur la plateforme en masquant certaines catégories dans le menu de gauche, soit globalement, soit pour un rôle spécifique.

#### Masquer des catégories globalement

Dans `Settings > Parameters`, il est possible pour l'administrateur de la plateforme de masquer des catégories pour tous les utilisateurs.

![Masquer des catégories globalement](assets/hide-global.png)

#### Masquer des catégories dans les rôles

Dans OpenCTI, les différents rôles sont hautement personnalisables. Il est possible de définir des dashboards par défaut, des triggers, etc., mais aussi de masquer des catégories dans les rôles :

![Masquer des catégories dans les rôles](assets/hide-roles.png)

### Listes d'entités

Dans chaque catégorie de connaissance, il est possible de visualiser, trier, filtrer, modifier la liste des entités de la catégorie.
![Liste des rapports](assets/reports-list.png)

Plusieurs actions peuvent être réalisées à partir de là :

- Cliquer sur une ligne pour afficher les informations d'une entité spécifique,
- Cliquer sur le nom d'une colonne pour trier la liste selon cette colonne,

!!! note "Colonnes triables"

  Certaines colonnes sont toujours triables (comme les dates ou les noms).
  D'autres ne le sont jamais (comme les labels).

  Certaines colonnes ne sont triables que si le mapping runtime est activé, c'est-à-dire si la plateforme utilise Elastic v >= 7.12 (non compatible avec OpenSearch par exemple). C'est le cas pour les colonnes dont le contenu est calculé à la volée et non stocké en base de données : author, creator, observable value, markings, kill chain phases, assignee, participant, place of birth, ethnicity.
  En effet, tous ces champs ne sont pas stockés en base et nécessitent une résolution pour récupérer des informations supplémentaires utiles au tri (comme le nom du creator) à partir d'un id.

- Modifier les filtres pour afficher les entités correspondant à certains critères,
- Sélectionner des entités via les cases à cocher pour effectuer des actions spécifiques (fusionner, mettre à jour, supprimer, enrichir, partager des entités).


## Présentation d'une page type d'entité dans OpenCTI

Bien qu'OpenCTI propose de nombreuses entités et onglets, beaucoup d'entre eux partagent des similitudes, avec seulement de légères différences dues à des caractéristiques spécifiques. Ces différences peuvent concerner l'inclusion ou l'exclusion de certains champs, selon la nature de l'entité.

Dans cette partie, seul un aperçu général d'une page "type" d'OpenCTI sera détaillé. Les spécificités des différentes entités seront détaillées dans les pages correspondantes ci-dessous (Activités et Connaissance).

<figure markdown>
  ![Menu supérieur d'une entité](assets/top-menu.png)
</figure>


<a id="overview-section"></a>
### Vue d'ensemble

Dans l'onglet `Overview` de l'entité, vous trouverez toutes les propriétés de l'entité ainsi que les activités récentes.

Tout d'abord, vous trouverez la section `Details`, où sont affichées toutes les propriétés spécifiques au type d'entité consulté, exemple ci-dessous avec un malware :

![Détails](assets/details.png)

Ainsi, dans la section `Basic information`, sont affichées toutes les propriétés communes à tous les objets dans OpenCTI, telles que la marking definition, l'auteur, les labels (tags), etc.

![Informations de base](assets/basic.png)

Sous ces deux sections, vous trouverez les dernières modifications dans la base de connaissances liées à l'entité :

- `Latest created relationships` : affiche les dernières relations créées <u>depuis</u> ou <u>vers</u> cette entité. Par exemple, les derniers Indicators of Compromise et le Threat Actor associé à un malware.
- `latest containers about the object` : affiche tous les Cases et Analyses contenant cette entité. Par exemple, les derniers rapports concernant un malware.
- `External references` : affiche toutes les sources externes associées à l'entité. Vous trouverez souvent ici des liens vers des rapports ou pages web externes d'où proviennent les informations de l'entité.
- `History` : affiche les dernières modifications chronologiques de l'entité et de ses relations survenues dans la plateforme, afin de retracer toute altération.

![Dernières relations et conteneurs](assets/latest_additions.png)
![Références et historique](assets/ref_and_history.png)

Enfin, toutes les Notes rédigées par les utilisateurs de la plateforme concernant cette entité sont affichées afin d'accéder à des commentaires d'analyse non structurés.


<a id="knowledge-section"></a>
### Connaissance

Dans l'onglet `Knowledge`, qui est la partie centrale de l'entité, vous trouverez toutes les connaissances liées à l'entité courante. L'onglet `Knowledge` est différent pour les Analyses (`Report`, `Groupings`) et les Cases (`Incident response`, `Request for Information`, `Request for Takedown`) par rapport aux autres types d'entités.

- L'onglet `Knowledge` de ces entités (qui représentent des Analyses ou Cases pouvant contenir une collection d'objets) est l'endroit pour intégrer et lier des entités. Pour plus d'informations sur l'intégration d'informations dans OpenCTI via l'onglet knowledge d'un rapport, se référer à la partie [Manual creation](manual-creation.md).
- Les onglets `Knowledge` des autres entités (qui n'ont pas vocation à contenir une collection d'objets) rassemblent toutes les entités qui ont été à un moment liées à l'entité consultée. Par exemple, comme illustré dans la capture suivante, l'onglet `Knowledge` de l'Intrusion set APT29 donne accès à la liste de toutes les entités attribuées à APT29, toutes les victimes ciblées par l'intrusion set, toutes ses campagnes, TTPs, malwares, etc. Pour que des entités apparaissent dans ces onglets sous `Knowledge`, elles doivent avoir été liées directement à l'entité ou avoir été calculées par le moteur d'inférence.
- Lors de la consultation d'une entité `Incident`, `Infrastructure`, `Threat Actor (group)`, `Threat Actor (individual)`, `Intrusion Set`,  `Malware`, `Channel` ou `Tool` dans OpenCTI, il est possible de consulter son modèle `Diamond` auto-rempli depuis l'onglet `Knowledge`. Le modèle `Diamond` illustre les relations existant entre l'entité consultée et d'autres entités dans OpenCTI et les cartographie automatiquement dans l'un des quatre quadrants pertinents : Adversary (ex : Threat Actors), Infrastructure (ex : Observables), Victimology (ex : Sectors) et Capabilities (ex : Attack Patterns). Chaque quadrant du Diamond est interactif et peut être cliqué pour naviguer vers une liste complète (ou seulement un sous-ensemble) de ses entités associées.

![L'onglet Knowledge de l'Intrusion Set](assets/apt41_knowledge_view.png)


#### Focus sur les Indicators et Observables

La section `Indicators` et `Observables` propose 3 modes d'affichage :
- La `entities view`, qui affiche les indicators/observables liés à l'entité.
- La `relationship view`, qui affiche les différentes relations entre les indicators/observables liés à l'entité et l'entité elle-même.
- La `contextual view`, qui affiche les indicators/observables contenus dans les cases et analyses contenant l'entité.

![Les vues Focus sur Indicators et Observables dans Knowledge](assets/knowledge_focus_indicators_observable_views.png)


<a id="content-section"></a>
### Contenu

L'onglet `Content` est disponible pour toutes les entités. Il permet de téléverser et créer des documents de résultats liés au contenu de l'entité courante (en PDF, texte, HTML ou fichiers markdown). Cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à l'entité. Par exemple, un rapport analytique à partager avec d'autres équipes, un fichier markdown pour alimenter un wiki collaboratif, etc.

La `Content mapping view` et la `Suggested mapping view` sont disponibles pour un sous-ensemble d'entités : `Report`, `Grouping`, `Incident`, `Incident response`, `Request for Information`, et `Request for Takedown`.


![L'onglet Content d'un Malware](assets/entity-content-tab.png)

#### Content mapping view

![Content mapping view d'un Case](assets/case-content-mapping.png)

La `Content mapping view` affiche le contenu mappable de votre container à gauche (Description et Content), et les objets contenus dans le container à droite.

Cette vue permet d'associer du contenu lisible à des objets existants ou nouveaux en sélectionnant du texte à gauche. Mapper un objet l'ajoutera à votre container, et l'objet sera alors affiché à droite.
Il est possible de supprimer tous les mappings ajoutés en cliquant sur le bouton `Clear mappings`. Cette action ne supprimera que le mapping : les objets resteront contenus dans votre container.

Cela permet d'ajouter rapidement de la connaissance structurée dans votre Case avant de la compléter avec des relations et des détails, et en fait un excellent endroit pour visualiser le continuum entre connaissance non structurée et structurée.

#### Suggested mapping view

![Suggested mapping view d'un Report](assets/suggested-mapping.png)

La `Suggested mapping view` affiche le contenu mappable de votre container à gauche (Description et Content), et la suggestion de mapping d'entités à droite.

Cette vue permet d'obtenir une liste de suggestions d'objets existants basée sur votre contenu mappable en cliquant sur `Suggest new mapping`. 
Pour pouvoir obtenir une suggestion, il faut avoir au moins un analysis connector de type `INTERNAL_ANALYSIS` configuré. 
Une fois la suggestion calculée par le connector, elle sera disponible à droite.
Il est alors possible de supprimer les suggestions non pertinentes, puis de cliquer sur le bouton `Validate` pour ajouter les objets mappés à votre container.

Cela permet de remplir rapidement votre Container avec les données nécessaires, sans avoir à mapper manuellement chaque objet lié.

<a id="analyses-section"></a>
### Analyses

L'onglet `Analyses` contient la liste de toutes les Analyses (`Report`, `Groupings`) et Cases (`Incident response`, `Request for Information`, `Request for Takedown`) dans lesquelles l'entité a été identifiée.

![Exemple de liste de rapports dans lesquels le pattern d'attaque "data obfuscation" a été identifié.](assets/entity_analysis-tab.png)

Par défaut, cet onglet affiche la liste, mais il est aussi possible d'afficher le contenu de toutes les Analyses listées sous forme de graphe, permettant d'explorer toutes leurs connaissances et d'avoir un aperçu du contexte autour de l'entité.

![Vue graphe de toutes les connaissances contenues dans les analyses listées](assets/analyses-graphview.png)


<a id="data-section"></a>
### Données

L'onglet `Data` contient les documents associés à l'objet et qui ont été soit :

- Téléversés sur la plateforme : par exemple le document PDF contenant le texte du rapport
- Générés depuis la plateforme pour être téléchargés : un fichier JSON ou CSV contenant des informations sur l'objet et généré par l'utilisateur.
- associés à une référence externe

[Analyst Workbench](workbench.md) peut également être créé à partir d'ici. Il contiendra l'entité par défaut.

![L'onglet Data d'un Threat Actor](assets/entity-data-tab.png)

De plus, l'onglet `Data` des `Threat actors (group)`, `Threat actors (individual)`, `Intrusions sets`, `Organizations`, `Individuals` dispose d'un panneau supplémentaire :

- Pictures Management : permet de gérer les photos de profil attachées à l'entité.

![Panneau de gestion des photos de profil](assets/profile_pictures_panel.png)
![Photos de profil d'un Threat Actor](assets/profile_pictures_of_TA.png)


<a id="history-section"></a>
### Historique

L'onglet `History` affiche l'historique des modifications de l'entité, mise à jour des attributs, création de relations, ...

En raison du volume d'informations, l'historique est écrit dans un index spécifique qui consomme le flux redis pour reconstruire l'historique pour l'interface.
![Onglet History d'un Malware](assets/history.png)


### Onglets moins fréquents

- L'onglet `Observables` (pour Reports et Observed data) : un tableau contenant tous les SCO (Stix Cyber Observable) contenus dans le Report ou l'Observed data, avec recherche et filtres disponibles. Il affiche également si le SCO a été ajouté directement ou via [inférences avec le reasoning engine](inferences.md)
- l'onglet `Entities` (pour Reports et Observed data) : un tableau contenant tous les SDO (Stix Domain Objects) contenus dans le Report ou l'Observed data, avec recherche et filtres disponibles. Il affiche également si le SDO a été ajouté directement ou via [inférences avec le reasoning engine](inferences.md)
- Observables :
- l'onglet `Sightings` (pour Indicators et Observables) : un tableau contenant toutes les relations `Sightings` correspondant à des événements où des `Indicators` (IP, nom de domaine, URL, etc.) sont détectés par ou dans un système d'information, un individu ou une organisation. Le plus souvent, cela correspond à un événement de sécurité transmis par un SIEM ou un EDR.



> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.