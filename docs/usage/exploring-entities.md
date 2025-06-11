# Entités

Les objets Entités d’OpenCTI offrent un cadre complet pour modéliser différentes cibles et victimes d’attaques dans vos données de cybermenaces. Avec cinq types distincts d’objets Entité, vous pouvez représenter des secteurs, des événements, des organisations, des systèmes et des individus. Cette classification robuste permet de contextualiser efficacement les menaces, en enrichissant la profondeur et la précision de vos analyses.

En cliquant sur « Entities » dans la barre latérale gauche, il est possible d’accéder à tous les onglets « Entities », visibles dans la barre supérieure à gauche. Par défaut, l’utilisateur accède directement à l’onglet « Sectors », mais peut naviguer vers les autres onglets.

Depuis la section `Entities`, les utilisateurs peuvent accéder aux onglets suivants :

- `Sectors` : domaines d’activité.
- `Events` : événements du monde réel.
- `Organizations` : groupes avec des objectifs spécifiques tels que des entreprises ou des entités gouvernementales.
- `Systems` : technologies telles que des plateformes et des logiciels.
- `Individuals` : personnes réelles.


## Sectors

### Présentation générale

Les secteurs représentent des domaines d’activité spécifiques, définissant des secteurs tels que l’énergie, le gouvernement, la santé, la finance, etc. Utiliser les secteurs pour catégoriser les industries ciblées ou les secteurs d’intérêt, afin d’apporter un contexte précieux à l’analyse de cybermenaces dans des domaines économiques distincts.

En cliquant sur l’onglet Sectors en haut à gauche, la liste de tous les secteurs accessibles s’affiche, selon vos [marking definitions autorisées](../administration/users.md).

![Sectors list](assets/sectors_list_view.png)

### Visualiser la connaissance associée à un secteur

En cliquant sur un `Sector` dans la liste, vous accédez à son onglet Overview. Pour un secteur, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées au secteur. Différentes vues thématiques sont proposées pour visualiser facilement les entités associées, les menaces, les incidents, etc. liés au secteur. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés au secteur. Par exemple, un rapport analytique à partager avec d’autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant à des événements où un `Indicator` (IP, nom de domaine, url, etc.) est observé dans le secteur.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

![Sector overview](assets/sector_overview.png)


## Events

### Présentation générale

Les événements englobent des occurrences telles que des événements sportifs internationaux, des sommets (par exemple, G20), des procès, des conférences ou tout fait marquant du monde réel. En modélisant les événements, il est possible d’analyser les menaces associées à des occurrences spécifiques, permettant des investigations ciblées autour d’incidents de grande envergure.

En cliquant sur l’onglet Events en haut à gauche, la liste de tous les événements accessibles s’affiche, selon vos [marking definitions autorisées](../administration/users.md).

![Events list](assets/events_list_view.png)

### Visualiser la connaissance associée à un événement

En cliquant sur un `Event` dans la liste, vous accédez à son onglet Overview. Pour un événement, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées à l’événement. Différentes vues thématiques sont proposées pour visualiser facilement les entités associées, les menaces, les localisations, etc. liés à l’événement. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à l’événement. Par exemple, un rapport analytique à partager avec d’autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant à des événements où un `Indicator` (IP, nom de domaine, url, etc.) est observé lors d’une attaque contre l’événement.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).


## Organizations

### Présentation générale

Les organisations incluent des entités diverses telles que des entreprises, organismes gouvernementaux, associations, organisations à but non lucratif et autres groupes avec des objectifs spécifiques. Modéliser les organisations permet de comprendre le paysage des menaces concernant différentes entités, facilitant les investigations sur l’espionnage, les fuites de données ou d’autres activités malveillantes ciblant des groupes spécifiques.

En cliquant sur l’onglet Organizations en haut à gauche, la liste de toutes les organisations accessibles s’affiche, selon vos [marking definitions autorisées](../administration/users.md).

![Organizations list](assets/organizations_list_view.png)

### Visualiser la connaissance associée à une organisation

En cliquant sur une `Organization` dans la liste, vous accédez à son onglet Overview. Pour une organisation, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées à l’organisation. Différentes vues thématiques sont proposées pour visualiser facilement les entités associées, les menaces, les localisations, etc. liés à l’organisation. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à l’organisation. Par exemple, un rapport analytique à partager avec d’autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant à des événements où un `Indicator` (IP, nom de domaine, url, etc.) est observé dans l’organisation.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

De plus, une organisation peut être observée sous l’angle « Author ». Il est possible de changer ce point de vue à droite du nom de l’entité, via le menu déroulant « Display as » (voir capture d’écran ci-dessous). Cette perspective différente est accessible dans les onglets Overview, Knowledge et Analyses. En mode « Author », les données affichées concernent la description de l’entité en tant qu’auteur dans la plateforme :

- Overview : les panneaux « Latest created relationships » et « Latest containers about the object » sont remplacés par le panneau « Latest containers authored by this entity ».
- Knowledge : un onglet présentant une vue d’ensemble des données rédigées par l’organisation (compteurs et graphe).
- Analyses : la liste de toutes les Analyses (`Report`, `Groupings`) et Cas (`Incident response`, `Request for Information`, `Request for Takedown`) pour lesquels l’organisation est l’auteur.

![Organization author view](assets/organization_author_view.png)


## Systems

### Présentation générale

Les systèmes représentent des applications logicielles, plateformes, frameworks ou outils spécifiques comme WordPress, VirtualBox, Firefox, Python, etc. Modéliser les systèmes permet de se concentrer sur les menaces liées à un logiciel ou une technologie spécifique, facilitant l’évaluation des vulnérabilités, la gestion des correctifs et la sécurisation des applications critiques.

En cliquant sur l’onglet Systems en haut à gauche, la liste de tous les systèmes accessibles s’affiche, selon vos [marking definitions autorisées](../administration/users.md).

![Systems list](assets/systems_list_view.png)

### Visualiser la connaissance associée à un système

En cliquant sur un `System` dans la liste, vous accédez à son onglet Overview. Pour un système, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées au système. Différentes vues thématiques sont proposées pour visualiser facilement les entités associées, les menaces, les incidents, etc. liés au système. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés au système. Par exemple, un rapport analytique à partager avec d’autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant à des événements où un `Indicator` (IP, nom de domaine, url, etc.) est observé dans le système.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

De plus, un système peut être observé sous l’angle « Author ». Il est possible de changer ce point de vue à droite du nom de l’entité, via le menu déroulant « Display as » (voir capture d’écran ci-dessous). Cette perspective différente est accessible dans les onglets Overview, Knowledge et Analyses. En mode « Author », les données affichées concernent la description de l’entité en tant qu’auteur dans la plateforme :

- Overview : les panneaux « Latest created relationships » et « Latest containers about the object » sont remplacés par le panneau « Latest containers authored by this entity ».
- Knowledge : un onglet présentant une vue d’ensemble des données rédigées par le système (compteurs et graphe).
- Analyses : la liste de toutes les Analyses (`Report`, `Groupings`) et Cas (`Incident response`, `Request for Information`, `Request for Takedown`) pour lesquels le système est l’auteur.


## Individuals

### Présentation générale

Les individus représentent des personnes spécifiques pertinentes pour votre analyse de cybermenaces. Cette catégorie inclut des personnes ciblées ou des figures influentes dans divers domaines. Modéliser les individus permet d’analyser les menaces visant des personnes précises, en facilitant les investigations sur le cyber-harcèlement, l’usurpation d’identité ou d’autres attaques ciblées.

En cliquant sur l’onglet Individuals en haut à gauche, la liste de tous les individus accessibles s’affiche, selon vos [marking definitions autorisées](../administration/users.md).

![Positions list](assets/positions_list_view.png)

### Visualiser la connaissance associée à un individu

En cliquant sur un `Individual` dans la liste, vous accédez à son onglet Overview. Pour un individu, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées à l’individu. Différentes vues thématiques sont proposées pour visualiser facilement les entités associées, les menaces, les localisations, etc. liés à l’individu. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à l’individu. Par exemple, un rapport analytique à partager avec d’autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant à des événements où un `Indicator` (IP, nom de domaine, url, etc.) est observé chez l’individu.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

De plus, un individu peut être observé sous l’angle « Author ». Il est possible de changer ce point de vue à droite du nom de l’entité, via le menu déroulant « Display as » (voir capture d’écran ci-dessous). Cette perspective différente est accessible dans les onglets Overview, Knowledge et Analyses. En mode « Author », les données affichées concernent la description de l’entité en tant qu’auteur dans la plateforme :

- Overview : les panneaux « Latest created relationships » et « Latest containers about the object » sont remplacés par le panneau « Latest containers authored by this entity ».
- Knowledge : un onglet présentant une vue d’ensemble des données rédigées par l’individu (compteurs et graphe).
- Analyses : la liste de toutes les Analyses (`Report`, `Groupings`) et Cas (`Incident response`, `Request for Information`, `Request for Takedown`) pour lesquels l’individu est l’auteur.


> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.