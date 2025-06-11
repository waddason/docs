# Création de widget

La création de widgets sur le [dashboard](dashboards.md) implique un processus de configuration en quatre étapes. En naviguant à travers ces étapes, il est possible de concevoir des widgets adaptés à des besoins spécifiques.

## Configuration du widget

#### 1. Visualisation

Il est possible de choisir parmi 15 options de visualisation différentes pour mettre en avant divers aspects des données. Cela inclut des vues simples comme les compteurs et les listes, ainsi que des vues plus complexes comme les heatmaps et les arbres. La visualisation choisie influence les perspectives et paramètres disponibles, il est donc crucial d’aligner la vue avec les observations souhaitées. Quelques exemples :

- Vues Ligne et Aire : idéales pour visualiser les volumes d’activité dans le temps.
- Vues Barres horizontales : conçues pour identifier les entités principales qui satisfont le mieux les filtres appliqués (ex : principaux malware ciblant le secteur Finance).
- Vues Arbre : utiles pour comparer les volumes d’activité.
- ...

![Widget visualization](assets/widget-visualization.png)

#### 2. Perspective

Une perspective correspond à la manière dont la plateforme va compter les données à afficher dans les widgets :

- **Entities Perspective :** Se concentre sur les entités, permettant d’observer des connaissances simples selon des filtres et critères définis. Le comptage se base uniquement sur les entités.
- **Knowledge Graph Perspective :** Se concentre sur les relations, affichant des connaissances complexes issues des relations entre entités et des filtres spécifiés. Le comptage se base uniquement sur les relations.
- **Activity & History Perspective :** Se concentre sur les activités au sein de la plateforme, et non sur le contenu de la connaissance. Cette perspective est utile pour surveiller les activités des utilisateurs et connecteurs, évaluer les sources de données, etc.

![Widget perspective](assets/widget-perspective.png)

#### 3. Filtres

#### Connaissance générique

Les filtres varient selon la perspective sélectionnée et définissent l’ensemble de données utilisé dans le widget. Ils sont essentiels pour restreindre le périmètre d’analyse.

Les filtres dans les perspectives "Entities" et "Activity & History" sont similaires à ceux utilisés pour la recherche ou la création de flux sur la plateforme, tandis que la perspective "Knowledge Graph" introduit une configuration de filtre plus complexe. Ils doivent donc être détaillés davantage.

#### Filtre dans le contexte du Knowledge Graph

Deux types de filtres sont disponibles dans la perspective Knowledge Graph :

- **Filtre de requête principal**
    - **Filtres classiques (gris) :** Définissent les relations à récupérer, constituant la base sur laquelle le widget affiche les données. Rappel : les statistiques dans la perspective Knowledge Graph sont basées sur les relations.
  
- **Filtres de pré-requête**
    - Les filtres de pré-requête servent à **fournir à la requête principale** un ensemble de données spécifique. Autrement dit, au lieu d’interroger l’ensemble des données de la plateforme, il est possible de cibler un sous-ensemble répondant à certains critères. Il existe deux types de filtres de pré-requête :
        - **Filtres dynamiques sur la source (orange) :** Affinent les données en filtrant sur les entités positionnées comme source (dans la position "from") de la relation.
        - **Filtres dynamiques sur la cible (vert) :** Affinent les données en filtrant sur les entités positionnées comme cible (dans la position "to") de la relation.

!!! avertissement "Limitation de la pré-requête"

    La pré-requête est limitée à 5000 résultats. Si la pré-requête retourne plus de 5000 résultats, le widget affichera uniquement des statistiques basées sur ces 5000 résultats, ce qui peut donner une vue erronée. Pour éviter ce problème, il est conseillé de spécifier précisément les filtres de pré-requête.

**Exemple de scénario :**

Prenons un exemple : analyser les modes d’accès initiaux utilisés par les intrusion sets ciblant le secteur finance.

1. Filtres classiques : définir les relations associées à l’utilisation de attack patterns par les intrusion sets.
2. Filtres dynamiques sur la source (orange) : restreindre les données en filtrant sur les intrusion sets ciblant le secteur finance.
3. Filtres dynamiques sur la cible (vert) : restreindre les données en filtrant sur les attack patterns associés à la phase d’accès initial du kill chain.

En utilisant ces filtres avancés, il est possible de réaliser des analyses détaillées dans la perspective Knowledge Graph, permettant d’obtenir des informations essentielles sur les relations et statistiques complexes.

![Widget filters](assets/widget-filters.png)

Dans certaines vues, il est possible d’accéder à des boutons comme `+`, `+ Relationships` ou `+ Entities`. Ces boutons permettent d’incorporer différentes données dans un même widget pour une analyse comparative. Par exemple, dans une vue Ligne, l’ajout d’un second ensemble de filtres affichera deux courbes dans le widget, chacune correspondant à un ensemble de données filtré. Selon la vue, il est possible de travailler avec 1 à 5 ensembles de filtres. Le champ `Label` permet de nommer un ensemble de données, ce libellé pouvant ensuite être affiché comme légende dans le widget via le bouton `Display legend` dans les paramètres du widget (voir la section suivante).

![Widget multiple filters](assets/widget-multiple-filters.png)

#### 4. Paramètres

Les paramètres dépendent de la visualisation choisie et permettent de définir les titres des widgets, de choisir les éléments affichés à partir des données filtrées, de sélectionner la date de référence des données, ainsi que de configurer divers autres paramètres propres à chaque visualisation.

Pour la perspective "Knowledge Graph", un paramètre essentiel est le bouton `Display the source`. Cette fonctionnalité permet de choisir si le widget affiche les entités du côté source ou du côté cible des relations.

- Bouton activé ("Display the source") : le widget se concentre sur les entités positionnées comme source des relations (dans la position "from").
- Bouton désactivé ("Display the target") : le widget se concentre sur les entités positionnées comme cible des relations (dans la position "to").

Ce niveau de contrôle permet d’adapter précisément le dashboard à vos objectifs d’analyse, en offrant une perspective personnalisée selon les données et relations.

![Widget parameters](assets/widget-parameters.png)


## Connaissances préalables

Pour configurer efficacement des widgets dans OpenCTI, il est essentiel de bien comprendre la modélisation des données de la plateforme. Connaître les relations, entités et leurs attributs permet d’affiner les filtres avec précision. Voici deux exemples.

**Scénario 1 :**

Supposons que l’objectif soit de visualiser les relations entre intrusion sets et attack patterns. Dans ce cas, le type de relation pertinent reliant les intrusion sets aux attack patterns est nommé "Uses" (comme illustré dans la section "Filtres").

**Scénario 2 :**

Si l’objectif est de récupérer tous les rapports associés au secteur finance, il est important d’utiliser le filtre approprié pour le secteur finance. Au lieu de placer le secteur finance dans le filtre "Related entity", il faut l’utiliser dans le filtre "Contains". Un Report étant un objet container (comme Cases et Groupings), il **contient** des entités et n’est **pas lié à** des entités.

### Points clés de la modélisation des données

- Entités : reconnaître les [container](containers.md) (ex : Reports, Cases et Groupings) et comprendre la différence avec les entités non-container.
- Relations : identifier les types de relations reliant les entités.
- Attributs : comprendre les attributs des entités et des relations pour un filtrage efficace.

Disposer de ces connaissances préalables permet de naviguer aisément dans le processus de configuration des widgets, garantissant des visualisations précises et pertinentes selon les besoins spécifiques.


> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.