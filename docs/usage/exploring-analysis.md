# Analyses

Lorsque vous cliquez sur "Analyses" dans la barre latérale gauche, vous voyez tous les onglets "Analyses", visibles sur la barre supérieure à gauche. Par défaut, l'utilisateur accède directement à l'onglet "Reports", mais peut également naviguer vers les autres onglets.

Depuis la section `Analyses`, les utilisateurs peuvent accéder aux onglets suivants :

- `Reports` : Considérer les Reports comme des sortes de conteneurs permettant de détailler et structurer ce qui est contenu dans un rapport spécifique, qu'il provienne d'une source ou qu'il soit rédigé par vous-même. À voir comme une Intelligence Production dans OpenCTI.
- `Groupings` : Les Groupings sont des conteneurs, comme les Reports, mais ne représentent pas une Intelligence Production. Ils regroupent des Objects partageant un contexte explicite. Par exemple, un Grouping peut représenter un ensemble de données qui, avec le temps et une analyse suffisante, pourrait évoluer pour devenir un incident ou un rapport de menace sous forme de Report.
- `Malware Analyses` : Comme défini par la norme STIX 2.1, Malware Analyses capture les métadonnées et les résultats d'une analyse statique ou dynamique effectuée sur un échantillon ou une famille de malware.
- `Notes` : Cet onglet permet de retrouver toutes les Notes rédigées sur la plateforme, par exemple pour ajouter des connaissances non structurées d'un analyste à propos d'un Object.
- `External references` : L'intelligence n'est jamais créée ex nihilo. Les External references permettent de lier des sources ou des documents de référence à tout Object de la plateforme.

![Analyses Default page is Reports](assets/analysis-default-page.png)

## Reports

### Présentation générale

Les Reports sont l'un des composants centraux de la plateforme. C'est à partir d'un `Report` que la connaissance est extraite et intégrée dans la plateforme pour une navigation, des analyses et des exports ultérieurs. Toujours rattacher l'information à un report permet à l'utilisateur d'identifier la source de toute information présente dans la plateforme à tout moment.

Dans la documentation MITRE STIX 2.1, un `Report` est défini comme suit :

> Les Reports sont des collections de renseignements sur les menaces axées sur un ou plusieurs sujets, tels qu'une description d'un acteur de menace, d'un malware ou d'une technique d'attaque, incluant le contexte et les détails associés. Ils servent à regrouper des renseignements liés afin qu'ils puissent être publiés sous forme d'une histoire complète sur une menace cyber.

Ainsi, un objet `Report` dans OpenCTI est un ensemble d'attributs et de métadonnées définissant et décrivant un document externe à la plateforme, qui peut être un rapport de renseignement sur les menaces d'une équipe de sécurité, un article de blog, un article de presse, une vidéo, un extrait de conférence, un événement MISP, ou tout type de document et de source.

En cliquant sur l'onglet Reports en haut à gauche, vous voyez la liste de tous les Reports auxquels vous avez accès, en fonction de vos [marking definitions autorisées](../administration/users.md). Il est alors possible de rechercher et filtrer selon des attributs communs et spécifiques aux reports.

### Visualiser la connaissance dans un Report

En cliquant sur un Report, vous arrivez sur l'onglet Overview. Pour un Report, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe qui regroupe toute la connaissance structurée contenue dans le report, accessible via différentes vues (voir ci-dessous pour plus de détails). Comme décrit [ici](overview.md#knowledge-section).
- Content : un onglet permettant d'accéder au mapping de contenu, aux suggestions de mapping, et de prévisualiser, gérer et rédiger les livrables associés au Report. Par exemple, un rapport analytique à partager avec d'autres équipes, un fichier markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Entities : Un tableau contenant tous les SDO (Stix Domain Objects) présents dans le Report, avec recherche et filtres disponibles. Il indique également si le SDO a été ajouté directement ou via [inférences avec le moteur de raisonnement](inferences.md).
- Observables : Un tableau contenant tous les SCO (Stix Cyber Observable) présents dans le Report, avec recherche et filtres disponibles. Il indique également si le SCO a été ajouté directement ou via [inférences avec le moteur de raisonnement](inferences.md).
- Data : comme décrit [ici](overview.md#data-section).

Explorer et modifier la connaissance structurée contenue dans un Report peut se faire selon différentes perspectives.

#### Vue Graphique

![Graph View of a Report](assets/report-graph-view.png)

En vue Graphique, les STIX SDO sont affichés comme des nœuds de graphe et les relations comme des liens. Les nœuds sont colorés selon leur type. Les relations directes sont affichées en trait plein et les relations inférées en pointillé.
En haut à droite, une série d'icônes permet de changer le type de vue actuel. Il est aussi possible d'effectuer des actions globales sur la connaissance du Report. Deux actions principales :
- Suggestions : Cet outil propose des relations logiques à ajouter entre vos Objects pour donner plus de cohérence à votre connaissance.
- Partager avec une Organization : si une Organization principale a été définie dans les paramètres de la plateforme, il est possible de partager ici votre Report et son contenu avec les utilisateurs d'une autre Organization.

En bas, de nombreuses options permettent de manipuler le graphe :
- Plusieurs options pour façonner le graphe et appliquer des forces aux nœuds et liens
- Options de sélection multiple
- Filtres multiples, incluant un sélecteur de plage temporelle pour visualiser l'évolution de la connaissance dans le Report
- Outils de création et d'édition multiples pour modifier la connaissance contenue dans le Report

#### Vue Chronologique

![Timeline view of a Report](assets/report-timeline-view.png)

Cette vue permet de visualiser la connaissance structurée de façon chronologique. Elle est particulièrement utile lorsque le report décrit une attaque ou une campagne qui s'est déroulée sur une période, et que l'analyste a prêté attention aux dates.
La vue peut être filtrée et affiche également les relations.

#### Vue Corrélation

![Correlation view of a Report](assets/report-correlation-view.png)

La vue de corrélation est idéale pour visualiser et trouver d'autres Reports liés à votre sujet d'intérêt actuel. Ce graphe affiche tous les Reports liés aux nœuds importants contenus dans votre Report, par exemple des Objects comme Malware ou Intrusion sets.

#### Vue Matrice

![Matrix view of a Report](assets/report-matrix-view.png)

Si votre Report décrit, par exemple, une attaque, une campagne ou une compréhension d'un Intrusion set, il devrait contenir plusieurs Objects attack patterns pour structurer la connaissance sur les TTPs du Threat Actor. Ces attack patterns peuvent être affichés sous forme de matrices, par défaut la matrice MITRE ATT&CK Enterprise. Comme certaines matrices peuvent être volumineuses, il est possible de filtrer pour n'afficher que les attack patterns décrits dans le Report.

### Restreindre l'accès au report

#### Ségrégation par Organization

Si une Organization principale a été définie dans les paramètres de la plateforme, il est possible de partager votre Report et son contenu avec les utilisateurs d'une autre Organization.

![containers-organization-sharing-button.png](assets%2Fcontainers-organization-sharing-button.png)

[en savoir plus sur la ségrégation par organization](..%2Fadministration%2Forganization-segregation.md)

#### Membres autorisés

**Membres autorisés** permet de restreindre l'accès à une entité à certains utilisateurs, groupes ou organizations au sein de la plateforme.

Pour définir les membres autorisés, cliquer sur le bouton '**Gérer la restriction d'accès**'. Ce bouton est visible si vous disposez de la capacité '**Gérer les membres autorisés**'.

![containers-manage-access-restriction-button.png](assets%2Fcontainers-manage-access-restriction-button.png)

[en savoir plus sur les membres autorisés](..%2Fadministration%2Fauthorized-members.md)

## Groupings

Les Groupings sont une alternative aux Reports pour regrouper des Objects partageant un contexte sans décrire une Intelligence Production.

Dans la documentation MITRE STIX 2.1, un `Grouping` est défini comme suit :

> Un objet Grouping affirme explicitement que les objets STIX référencés partagent un contexte, contrairement à un STIX Bundle (qui n'en véhicule aucun). Un objet Grouping ne doit pas être confondu avec un produit de renseignement, qui doit être transmis via un STIX Report. Un objet Grouping peut représenter un ensemble de données qui, avec le temps et une analyse suffisante, pourrait évoluer pour devenir un incident ou un rapport de menace sous forme de STIX Report. Par exemple, un Grouping peut servir à caractériser une enquête en cours sur un événement ou incident de sécurité. Il peut aussi servir à affirmer que les objets STIX référencés sont liés à un processus d'analyse en cours, comme lorsqu'un analyste de menace collabore avec d'autres membres de sa communauté de confiance pour examiner une série de Campaigns et d'Indicators.

En cliquant sur l'onglet Groupings en haut de l'interface, vous voyez la liste de tous les Groupings auxquels vous avez accès, en fonction de vos [marking definitions autorisées](../administration/users.md). Il est alors possible de rechercher et filtrer selon des attributs communs et spécifiques aux groupings.

En cliquant sur un Grouping, vous arrivez sur son onglet Overview. Pour un Grouping, les onglets suivants sont accessibles :
- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe qui regroupe toute la connaissance structurée contenue dans le grouping, comme pour un Report, à l'exception de la vue chronologique. Comme décrit [ici](overview.md#knowledge-section).
- Content : un onglet permettant d'accéder au mapping de contenu, aux suggestions de mapping, et de prévisualiser, gérer et rédiger les livrables associés au Grouping. Par exemple, un rapport analytique à partager avec d'autres équipes, un fichier markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Entities : Un tableau contenant tous les SDO (Stix Domain Objects) présents dans le Grouping, avec recherche et filtres disponibles. Il indique également si le SDO a été ajouté directement ou via [inférences avec le moteur de raisonnement](inferences.md).
- Observables : Un tableau contenant tous les SCO (Stix Cyber Observable) présents dans le Grouping, avec recherche et filtres disponibles. Il indique également si le SDO a été ajouté directement ou via [inférences avec le moteur de raisonnement](inferences.md).
- Data : comme décrit [ici](overview.md#data-section).

### Restreindre l'accès à un Grouping

#### Ségrégation par Organization

Si une Organization principale a été définie dans les paramètres de la plateforme, il est possible de partager votre Grouping et son contenu avec les utilisateurs d'une autre Organization.

![containers-organization-sharing-button.png](assets%2Fcontainers-organization-sharing-button.png)

[en savoir plus sur la ségrégation par organization](..%2Fadministration%2Forganization-segregation.md)

#### Membres autorisés

**Membres autorisés** permet de restreindre l'accès à une entité à certains utilisateurs, groupes ou organizations au sein de la plateforme.

Pour définir les membres autorisés, cliquer sur le bouton '**Gérer la restriction d'accès**'. Ce bouton est visible si vous disposez de la capacité '**Gérer les membres autorisés**'.

![containers-manage-access-restriction-button.png](assets%2Fcontainers-manage-access-restriction-button.png)

[en savoir plus sur les membres autorisés](..%2Fadministration%2Fauthorized-members.md)

## Malware Analyses

Les Malware analyses sont une composante importante du Cyber Threat Intelligence, permettant une compréhension précise de ce que fait réellement un malware sur l'hôte, mais aussi de la façon dont il reçoit ses commandes et communique ses résultats.

Dans OpenCTI, les Malware Analyses peuvent être créées à partir de connecteurs d'enrichissement qui prennent un Observable en entrée et effectuent une analyse sur une plateforme de service en ligne pour ramener les résultats. Ainsi, les Malware Analyses peuvent être réalisées sur File, Domain et URL.

Dans la documentation MITRE STIX 2.1, un `Malware Analyses` est défini comme suit :
> Malware Analyses capture les métadonnées et les résultats d'une analyse statique ou dynamique effectuée sur un échantillon ou une famille de malware.

En cliquant sur l'onglet Malware Analyses en haut de l'interface, vous voyez la liste de toutes les Malware Analyses auxquelles vous avez accès, en fonction de vos [marking definitions autorisées](../administration/users.md). Il est alors possible de rechercher et filtrer selon des attributs communs et spécifiques aux Malware Analyses.

En cliquant sur une Malware Analyses, vous arrivez sur son onglet Overview. Les onglets suivants sont accessibles :
- Overview : Cette vue contient quelques ajouts par rapport à l'Overview commun [ici](overview.md#overview-section). Vous y trouverez des détails sur la façon dont l'analyse a été réalisée, le résultat global concernant la dangerosité de l'artefact analysé et tous les Observables découverts lors de l'analyse.
- Knowledge : Si votre Malware analysis est liée à d'autres Objects qui ne font pas partie du résultat de l'analyse, ils seront affichés ici. Comme décrit [ici](overview.md#knowledge-section).
- Content : Cet onglet spécifique permet de prévisualiser, gérer et rédiger les livrables associés à la Malware Analyses. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

![Malware Analyses Overview](assets/malwareanalysis-overview.png)

## Notes

Toute connaissance ne peut pas être structurée. Pour permettre à tout utilisateur de partager ses observations sur une connaissance spécifique, il peut créer une Note pour chaque Object et relation dans OpenCTI auxquels il a accès. Toutes les Notes sont listées dans le menu Analyses pour permettre une revue globale de cet ajout non structuré à la connaissance globale.

Dans la documentation MITRE STIX 2.1, une `Note` est définie comme suit :
> Une Note est destinée à transmettre un texte informatif pour fournir un contexte supplémentaire et/ou une analyse additionnelle non contenue dans les objets STIX, Marking Definition ou Language Content auxquels la Note se rapporte. Les Notes peuvent être créées par n'importe qui (pas seulement le créateur de l'objet d'origine).

En cliquant sur une Note, vous arrivez sur son onglet Overview. Les onglets suivants sont accessibles :
- Overview : comme décrit [ici](overview.md#overview-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

## External references

L'intelligence n'est jamais créée ex nihilo. Les External references permettent de lier des sources ou des documents de référence à tout Object de la plateforme. Toutes les external references sont listées dans le menu Analyses pour accéder directement aux sources de la connaissance structurée.

Dans la documentation MITRE STIX 2.1, une `External references` est définie comme suit :
> Les External references servent à décrire des pointeurs vers des informations représentées en dehors de STIX. Par exemple, un objet Malware peut utiliser une external reference pour indiquer un identifiant pour ce malware dans une base de données externe ou un report peut utiliser des références pour représenter des sources.

En cliquant sur une External reference, vous arrivez sur son onglet Overview. Les onglets suivants sont accessibles :
- Overview : comme décrit [ici](overview.md#overview-section).


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.