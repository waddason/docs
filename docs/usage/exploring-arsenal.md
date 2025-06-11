# Arsenal

En cliquant sur "Arsenal" dans la barre latérale gauche, vous accédez à tous les onglets "Arsenal", visibles sur la barre supérieure à gauche. Par défaut, l'utilisateur accède directement à l'onglet "Malware", mais peut également naviguer vers les autres onglets.

Depuis la section `Arsenal`, les utilisateurs peuvent accéder aux onglets suivants :

- `Malware` : `Malware` désigne tout code spécifiquement conçu pour endommager, perturber ou obtenir un accès non autorisé à des systèmes informatiques, des réseaux ou des données utilisateur.
- `Channels` : Les `Channels`, dans le contexte de la cybersécurité, désignent les lieux ou moyens par lesquels les acteurs diffusent des informations. Cette catégorie est notamment utilisée dans le contexte de la FIMI (Foreign Information Manipulation Interference).
- `Tools` : Les `Tools` représentent des logiciels ou matériels légitimes installés sur un système d'exploitation, pouvant être détournés par des attaquants à des fins malveillantes (par exemple, LOLBAS).
- `Vulnerabilities` : Les `Vulnerabilities` sont des faiblesses pouvant être exploitées par des attaquants pour compromettre la sécurité, l'intégrité ou la disponibilité d'un système ou d'un réseau.


## Malware

### Présentation générale

Le malware englobe une large catégorie de codes malveillants créés, déployés et opérés par des intrusion set. Le malware peut prendre de nombreuses formes, notamment des virus, vers, chevaux de Troie, ransomwares, spywares, etc. Ces entités sont créées par des individus ou des groupes, y compris des États-nations, des groupes soutenus par des États, des entreprises ou des collectifs hacktivistes.

Utiliser le SDO `Malware` pour modéliser et suivre ces menaces de manière exhaustive, facilitant ainsi l'analyse approfondie, la réponse et la corrélation avec d'autres données de sécurité.

En cliquant sur l'onglet Malware en haut à gauche, vous voyez la liste de tous les Malware auxquels vous avez accès, conformément à vos [marking definitions autorisées](../administration/users.md). Ces malware sont affichés sous forme de **Cartes** où vous trouvez un résumé des connaissances importantes associées à chacun : description, alias, intrusion sets liés, pays et secteurs ciblés, et labels. Vous pouvez ensuite rechercher et filtrer selon des attributs communs et spécifiques aux Malware.

En haut à droite de chaque Carte, il est possible de cliquer sur l'icône étoile pour l'ajouter en favori. Cela épinglera la carte en haut de la liste. Vous pourrez également afficher facilement tous vos favoris dans vos [Tableaux de bord personnalisés](dashboards.md).

![The Malware cards](assets/malware_cards_view.png)

### Visualiser les connaissances associées à un Malware

En cliquant sur une carte `Malware`, vous arrivez sur son onglet Overview. Pour un Malware, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées au Malware. Différentes vues thématiques sont proposées pour visualiser facilement la victimologie, les threat actors et intrusion sets utilisant le Malware, etc. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés au Malware. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).


## Channels

### Présentation générale

Les `Channels` — tels que forums, sites web et plateformes de réseaux sociaux (par exemple Twitter, Telegram) — sont des moyens de diffuser des actualités, des connaissances et des messages à un large public. Bien qu'ils offrent des avantages comme la communication ouverte et la portée, ils peuvent aussi être utilisés à des fins malveillantes, telles que la diffusion de désinformation, la coordination de cyberattaques ou la promotion d'activités illégales.

Surveiller et gérer le contenu des `Channels` aide à analyser les menaces, activités et indicateurs associés à divers threat actors, campagnes et intrusion sets.

En cliquant sur l'onglet Channels en haut à gauche, vous voyez la liste de tous les Channels auxquels vous avez accès, conformément à vos [marking definitions autorisées](../administration/users.md). Ces channels sont affichés sous forme de liste où certains champs caractérisent l'entité : type de channel, labels et dates. Vous pouvez ensuite rechercher et filtrer selon des attributs communs et spécifiques aux Channels.

![Channels list](assets/channels_list_view.png)

### Visualiser les connaissances associées à un Channel

En cliquant sur un `Channel` dans la liste, vous arrivez sur son onglet Overview. Pour un Channel, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées au Channel. Différentes vues thématiques sont proposées pour visualiser facilement la victimologie, les threat actors et intrusion sets utilisant le Malware, etc. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés au Channel. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).


## Tools

### Présentation générale

Les `Tools` désignent des applications logicielles légitimes, des utilitaires en ligne de commande ou des scripts présents sur un système compromis. Ces objets permettent de modéliser et de surveiller les activités de ces outils, qui peuvent être détournés par des attaquants.

En cliquant sur l'onglet `Tools` en haut à gauche, vous voyez la liste de tous les `Tools` auxquels vous avez accès, conformément à vos [marking definitions autorisées](../administration/users.md). Ces tools sont affichés sous forme de liste où certains champs caractérisent l'entité : labels et dates. Vous pouvez ensuite rechercher et filtrer selon des attributs communs et spécifiques aux Tools.

![Tools list](assets/tools_list_view.png)

### Visualiser les connaissances associées à un Observed Data

En cliquant sur un `Tool` dans la liste, vous arrivez sur son onglet Overview. Pour un Tool, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées au Tool. Différentes vues thématiques sont proposées pour visualiser facilement les threat actors, intrusion sets et malware utilisant le Tool. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés au Tool. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).


## Vulnerabilities

### Présentation générale

Les `Vulnerabilities` représentent des faiblesses ou des défauts dans les logiciels, matériels, configurations ou systèmes pouvant être exploités par des acteurs malveillants. Cet objet aide à gérer et suivre la posture de sécurité de l'organisation en identifiant les points nécessitant une attention et une remédiation, tout en fournissant des informations sur les intrusion sets, malware et campagnes associés le cas échéant.

En cliquant sur l'onglet `Vulnerabilities` en haut à gauche, vous voyez la liste de toutes les `Vulnerabilities` auxquelles vous avez accès, conformément à vos [marking definitions autorisées](../administration/users.md). Ces vulnerabilities sont affichées sous forme de liste où certains champs caractérisent l'entité : sévérité CVSS3, labels, dates et créateurs (dans la plateforme). Vous pouvez ensuite rechercher et filtrer selon des attributs communs et spécifiques aux Vulnerabilities.

![Vulnerabilities list](assets/vulnerabilities_list_view.png)

### Visualiser les connaissances associées à un Observed Data

En cliquant sur une `Vulnerabilities` dans la liste, vous arrivez sur son onglet Overview. Pour une Vulnerability, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Knowledge : un onglet complexe regroupant toutes les connaissances structurées liées à la Vulnerability. Différentes vues thématiques sont proposées pour visualiser facilement les threat actors, intrusion sets et malware exploitant la Vulnerability. Comme décrit [ici](overview.md#knowledge-section).
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à la Vulnerability. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).


> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.