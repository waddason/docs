# Localisation

Les objets Locations d’OpenCTI offrent un cadre complet pour représenter diverses entités géographiques au sein de vos données de cybermenace. Avec cinq types distincts d’objets Location, il est possible de définir précisément des régions, pays, zones, villes et positions spécifiques. Cette classification robuste permet de contextualiser géographiquement les menaces, améliorant ainsi la profondeur et la précision de l’analyse.

En cliquant sur "Locations" dans la barre latérale gauche, il est possible d’accéder à tous les onglets "Locations", visibles en haut à gauche. Par défaut, l’utilisateur accède directement à l’onglet "Regions", mais peut naviguer vers les autres onglets.

Depuis la section `Locations`, il est possible d’accéder aux onglets suivants :

- `Regions` : très grands territoires géographiques, comme un continent.
- `Countries` : les pays du monde.
- `Areas` : zones géographiques plus ou moins étendues, souvent sans limite très définie.
- `Cities` : les villes du monde.
- `Positions` : positions très précises sur le globe.


## Regions

### Présentation générale

Les régions englobent de vastes territoires géographiques, représentant souvent des continents ou des parties significatives de continents. Exemples : EMEA (Europe, Moyen-Orient et Afrique), Asie, Europe de l’Ouest, Amérique du Nord. Utiliser les régions pour catégoriser de grandes zones géopolitiques et obtenir une vision macro des schémas de menace.

En cliquant sur l’onglet Regions en haut à gauche, la liste de toutes les régions accessibles s’affiche, selon vos [définitions de marquage autorisées](../administration/users.md).

![Regions list](assets/regions_list_view.png)

### Visualiser la connaissance associée à une région

En cliquant sur une `Region` dans la liste, l’utilisateur arrive sur l’onglet Overview. Pour une région, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section), avec la particularité de ne pas avoir de section `Details` mais une carte localisant la région.
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées à la région. Différentes vues thématiques sont proposées pour visualiser facilement les entités, menaces, incidents, etc. liés à la région. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à la région. Par exemple, un rapport analytique à partager avec d’autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant à des événements où un `Indicator` (IP, nom de domaine, url, etc.) est observé dans une région.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

![Region Overview](assets/region_overview.png)

## Countries

### Présentation générale

Les pays représentent les nations individuelles à travers le monde. Avec ce type d’objet, il est possible de spécifier des informations détaillées sur un pays particulier, permettant une localisation précise des données de cybermenace. Les pays sont des entités fondamentales dans l’analyse géopolitique, offrant une vue ciblée des activités à l’intérieur des frontières nationales.

En cliquant sur l’onglet Countries en haut à gauche, la liste de tous les pays accessibles s’affiche, selon vos [définitions de marquage autorisées](../administration/users.md).

![Countries list](assets/countries_list_view.png)

### Visualiser la connaissance associée à un pays

En cliquant sur un `Country` dans la liste, l’utilisateur arrive sur l’onglet Overview. Pour un pays, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section), avec la particularité de ne pas avoir de section `Details` mais une carte localisant le pays.
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées au pays. Différentes vues thématiques sont proposées pour visualiser facilement les entités, menaces, incidents, etc. liés au pays. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés au pays. Par exemple, un rapport analytique à partager avec d’autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant à des événements où un `Indicator` (IP, nom de domaine, url, etc.) est observé dans un pays.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

## Areas

### Présentation générale

Les zones (Areas) définissent des régions géographiques spécifiques d’intérêt, telles que le Golfe Persique, les Balkans ou le Caucase. Utiliser les zones pour identifier des espaces uniques présentant une importance géopolitique, culturelle ou stratégique. Ce type d’objet facilite l’analyse fine des menaces dans des contextes géographiques définis.

En cliquant sur l’onglet Areas en haut à gauche, la liste de toutes les zones accessibles s’affiche, selon vos [définitions de marquage autorisées](../administration/users.md).

![Areas list](assets/areas_list_view.png)

### Visualiser la connaissance associée à une zone

En cliquant sur une `Area` dans la liste, l’utilisateur arrive sur l’onglet Overview. Pour une zone, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section), avec la particularité de ne pas avoir de section `Details` mais une carte localisant la zone.
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées à la zone. Différentes vues thématiques sont proposées pour visualiser facilement les entités, menaces, incidents, etc. liés à la zone. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à la zone. Par exemple, un rapport analytique à partager avec d’autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant à des événements où un `Indicator` (IP, nom de domaine, url, etc.) est observé dans une zone.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).


## Cities

### Présentation générale

Les villes fournissent des informations détaillées sur les centres urbains du monde entier. Des grandes métropoles aux petites villes, les villes sont essentielles pour comprendre les activités de menace localisées. Ce type d’objet permet de cibler les menaces au niveau urbain, facilitant les évaluations tactiques et la planification de la réponse.

En cliquant sur l’onglet Cities en haut à gauche, la liste de toutes les villes accessibles s’affiche, selon vos [définitions de marquage autorisées](../administration/users.md).

![Cities list](assets/cities_list_view.png)

### Visualiser la connaissance associée à une ville

En cliquant sur une `City` dans la liste, l’utilisateur arrive sur l’onglet Overview. Pour une ville, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section), avec la particularité de ne pas avoir de section `Details` mais une carte localisant la ville.
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées à la ville. Différentes vues thématiques sont proposées pour visualiser facilement les entités, menaces, incidents, etc. liés à la ville. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à la ville. Par exemple, un rapport analytique à partager avec d’autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant à des événements où un `Indicator` (IP, nom de domaine, url, etc.) est observé dans une ville.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).


## Positions

### Présentation générale

Les positions représentent des points géographiques très précis, tels que des monuments, bâtiments ou lieux d’événements spécifiques. Ce type d’objet permet de définir des coordonnées exactes, facilitant la cartographie précise d’événements ou d’incidents. Les positions améliorent la granularité des données de cybermenace, permettant une analyse géospatiale fine.

En cliquant sur l’onglet Positions en haut à gauche, la liste de toutes les positions accessibles s’affiche, selon vos [définitions de marquage autorisées](../administration/users.md).

![Positions list](assets/positions_list_view.png)

### Visualiser la connaissance associée à une position

En cliquant sur une `Position` dans la liste, l’utilisateur arrive sur l’onglet Overview. Pour une position, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section), avec la particularité d’afficher une carte localisant la position.
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées à la position. Différentes vues thématiques sont proposées pour visualiser facilement les entités, menaces, incidents, etc. liés à la position. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à la position. Par exemple, un rapport analytique à partager avec d’autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Sightings : un tableau contenant toutes les relations `Sightings` correspondant à des événements où un `Indicator` (IP, nom de domaine, url, etc.) est observé à une position.
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).


> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.