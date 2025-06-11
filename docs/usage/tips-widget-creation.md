# Astuces pour la création de widgets

La création de widgets a déjà été abordée. Pour aider les utilisateurs à gagner en confiance dans la création de widgets, voici quelques détails pour maîtriser la création de widgets.

<a id="howto-section"></a>
## Comment choisir la visualisation de widget appropriée pour votre cas d'utilisation ?

On peut classer les widgets en 3 types différents.

### Widgets à dimension unique

Utiliser ces widgets lorsque vous souhaitez afficher des informations sur un seul type d'objet (entité ou relation).

- **Visualisations de widget : nombre, liste, liste (distribution), chronologie, donuts, radar, carte, signet, tree map.**
- Exemple de cas d'utilisation : afficher le nombre de malware sur la plateforme (widget nombre), afficher le top 10 des groupes de threat actor ciblant un pays spécifique (widget liste de distribution), etc.

### Widgets multi-dimensions

Utiliser ces widgets si vous souhaitez comparer ou obtenir des informations sur des types d'objets similaires (jusqu'à 5).

- **Visualisations de widget : ligne, aire, heatmap, barres verticales.**
- Exemple de cas d'utilisation : afficher le nombre de malware, intrusion sets, threat actor groups ajoutés au cours du dernier mois sur la plateforme (widget ligne ou aire).

!!! avertissement "Type d'objet dans le widget"
  Ces widgets doivent utiliser le même "type" d'objet pour fonctionner correctement. Il faut toujours ajouter des relations dans la vue des filtres si vous avez sélectionné une perspective "knowledge graph". Si vous avez sélectionné l'entité du knowledge graph, ajouter des "Entities" (cliquer sur `+ entities`) ne fonctionnera pas, car vous ne comptez pas les mêmes éléments.

### Widgets de répartition

Utiliser ce widget si vous souhaitez diviser votre ensemble de données en parties plus petites pour le rendre plus clair et plus utile à l'analyse.

- **Visualisation de widget : barres horizontales.**
- Exemple de cas d'utilisation : afficher la liste des malware ciblant un pays, répartis par type de malware.

![breakdown example](assets/widget-breakdown-example.png)

## Ajouter des ensembles de données à votre widget

Ajouter des ensembles de données peut servir deux objectifs : comparer des données ou décomposer une vue pour mieux comprendre la composition d'un ensemble de données spécifique.

### Cas d'utilisation 1 : comparer plusieurs ensembles de données

Comme mentionné dans la section [Comment choisir la visualisation de widget appropriée pour votre cas d'utilisation ?](#howto-section), vous pouvez ajouter des ensembles de données pour comparer différentes données. Veiller à ajouter le même type d'objets (entités ou relations) afin de pouvoir comparer les mêmes objets, en utilisant les boutons d'accès comme `+`, `+ Relationships` ou `+ Entities`.

Vous pouvez ajouter jusqu'à 5 ensembles de données différents. Le champ `Label` permet de nommer un ensemble de données, et ce label peut ensuite être affiché comme légende dans le widget en utilisant le bouton `Display legend` dans les paramètres du widget (voir la section suivante).

### Cas d'utilisation 2 : décomposer votre graphique

Comme mentionné dans la section [Comment choisir la visualisation de widget appropriée pour votre cas d'utilisation ?](#howto-section), vous pouvez ajouter des ensembles de données pour décomposer votre graphique en parties significatives plus petites. Vous trouverez ci-dessous quelques cas d'utilisation pour vous aider à comprendre comment structurer vos données.

Vous pouvez décomposer une vue soit par **entité soit par relations**, selon ce que vous souhaitez compter.

#### Décomposer par entité

**Exemple de cas d'utilisation : comprendre quels sont les pays les plus ciblés par les malware, et obtenir une répartition pour chaque pays par type de malware.**

**Procédure :**

1. Pour réaliser ce cas d'utilisation, il faut d'abord sélectionner la visualisation en barres horizontales.
2. Puis sélectionner la perspective knowledge graph.

Dans la vue des filtres :

3. Saisir ensuite votre requête principale `Source type = Malware AND Target type = Countries AND Relation type = Targets`. Ajouter un label à votre ensemble de données.
4. Ajouter **un ensemble de données entité** en utilisant le bouton d'accès `+ Entities`.
5. Ajouter les filtres suivants `Entity type = Malware AND In regards of = targets`. Ajouter un label à votre ensemble de données.

![filter view](assets/widget-breakdwon-by-entity-filter.png)

Dans la vue des paramètres :

6. Attribut (de votre relation) = entity (pour afficher les différentes valeurs d'entités)
7. Affichage du toggle source = désactivé
8. Attribut (de votre entité malware) = Malware type (puisque vous souhaitez répartir vos relations par types de malware)

![parameter view](assets/widget-breakdown-by-entity-parameter.png)

En résultat, vous obtenez une liste de pays répartis par types de malware.

![final result](assets/widget-breakdown-by-entity-final.png)

#### Décomposer par relation

**Exemple de cas d'utilisation : comprendre quels sont les malware les plus ciblants et obtenir une répartition des principales cibles par malware**

**Procédure :**

1. Pour réaliser ce cas d'utilisation, il faut d'abord sélectionner la visualisation en barres horizontales.
2. Puis sélectionner la perspective knowledge graph.

Dans la vue des filtres :

3. Saisir ensuite votre requête principale `Source type = Malware AND Relation type = Targets`. Ajouter un label à votre ensemble de données.
4. Ajouter **un ensemble de données relation** en utilisant le bouton d'accès `+ Relationships`
5. Ajouter les filtres suivants `Source type = Malware AND Relation type = targets`. Ajouter un label à votre ensemble de données.

![filter view](assets/widget-breakdown-by-relation-filter.png)

Dans la vue des paramètres :

7. Attribut (de votre relation) : entity (pour afficher les différentes valeurs d'entités)
8. Affichage du toggle source = activé
9. Attribut (de votre entité malware) = Malware type (puisque vous souhaitez répartir vos relations par types de malware)
10. Affichage du toggle source = désactivé

![paramter view](assets/widget-breakdwon-by-relation-parameter.png)

En résultat, vous obtenez une liste de malware avec la répartition de leurs principales cibles.

![final view](assets/widget-breakdown-by-relation-final.png)

## Autres cas d'utilisation

Pour voir d'autres cas d'utilisation, n'hésitez pas à consulter cet [article de blog](https://blog.filigran.io/new-octi-dashboards-the-first-graph-dashboarding-engine-for-the-stix-model-406e4eb5842a) qui vous apportera des informations complémentaires.


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.