# Tableaux de bord personnalisés

OpenCTI propose une fonctionnalité de tableau de bord entièrement adaptable et personnalisable. La flexibilité du tableau de bord d’OpenCTI garantit une visualisation des données adaptée et pertinente, favorisant une compréhension approfondie des connaissances, des relations et des activités de la plateforme.

## Page de liste des tableaux de bord personnalisés

Depuis le menu de gauche, il est possible de choisir l’option tableaux de bord personnalisés pour voir tous les tableaux de bord que vous avez créés, ainsi que ceux auxquels vous avez accès (par exemple, « peut voir », « peut modifier » ou « peut gérer »).

![List of custom dashboards](assets/list_custom_dashboards.png)

**Panneau d’actions**

Il est possible de réaliser des actions sur un tableau de bord à l’aide du bouton situé à la fin de chaque ligne :

- voir les tableaux de bord publics associés
- mettre à jour
- supprimer
- dupliquer
- exporter

**Suppression massive**

Il est possible d’effectuer des opérations de suppression massive à l’aide de la case à cocher :

- Sélectionner un à un les tableaux de bord personnalisés à supprimer
- Sélectionner tous les tableaux de bord personnalisés affichés sur la page à supprimer

## Aperçu du tableau de bord

Vous avez la possibilité d’adapter l’agencement des [widgets](widgets.md) sur votre tableau de bord, afin d’optimiser l’organisation et l’efficacité du flux de travail. Les widgets peuvent être placés intuitivement pour mettre en avant les informations clés. De plus, il est possible de redimensionner les widgets depuis le coin inférieur droit en fonction de l’importance de l’information, permettant ainsi une adaptation aux besoins analytiques spécifiques. Cette flexibilité technique garantit une expérience utilisateur fluide et visuellement optimisée.

Par ailleurs, la bannière supérieure du tableau de bord offre une fonctionnalité pratique pour configurer la période temporelle des données affichées. Cela peut être réalisé en sélectionnant une période relative, telle que « 7 derniers jours », ou en spécifiant des dates fixes de « Début » et de « Fin », permettant aux utilisateurs de contrôler précisément la portée temporelle des informations affichées.

![Dashboard overview](assets/dashboard-overview.png)

<a id="access-control-section"></a>
## Contrôle d’accès

Dans OpenCTI, la création de tableaux de bord personnalisés s’accompagne d’un système de contrôle d’accès flexible, permettant aux utilisateurs d’adapter la visibilité et les droits selon leurs besoins collaboratifs.

Lorsqu’un utilisateur crée un tableau de bord personnalisé, celui-ci n’est visible que par son créateur par défaut. À ce stade, le créateur détient les droits d’accès administrateur. Cependant, il peut étendre l’accès et les droits à d’autres utilisateurs via le bouton « Gérer l’accès », représenté par une icône de cadenas, situé en haut à droite de la page du tableau de bord.

![Manage access button](assets/manage-access-button.png)

**Niveaux d’accès :**

- Voir : Accès à la visualisation du tableau de bord.
- Modifier : Voir + Permission de modifier et mettre à jour le tableau de bord et ses widgets.
- Gérer : Modifier + Possibilité de supprimer le tableau de bord et de contrôler l’accès et les droits des utilisateurs.

Il est essentiel de souligner qu’au moins un utilisateur doit conserver l’accès administrateur afin d’assurer la gestion continue du tableau de bord.

![Manage access dialog](assets/manage-access-dialog.png) 

!!! note "Restriction d’accès aux connaissances"

  Les restrictions d’accès aux données de la plateforme s’appliquent également aux tableaux de bord. Les données affichées dans les widgets dépendent des droits d’accès de l’utilisateur sur la plateforme. Ainsi, un utilisateur administrateur ne verra pas les mêmes résultats dans les widgets qu’un utilisateur avec un accès limité, tel que la visualisation des seules données TLP:CLEAR (en supposant que la plateforme contienne des données au-delà de TLP:CLEAR).


## Partager les configurations de tableaux de bord et de widgets

OpenCTI propose des fonctionnalités d’export, d’import et de duplication des configurations de tableaux de bord et de widgets, facilitant le transfert des configurations personnalisées entre différentes instances ou utilisateurs.

### Exporter

Les tableaux de bord peuvent être exportés depuis la liste des tableaux de bord personnalisés ou depuis la vue du tableau de bord.

Pour exporter la configuration d’un tableau de bord depuis la liste des tableaux de bord personnalisés :

1. Cliquer sur le bouton menu burger à la fin de la ligne du tableau de bord.
2. Sélectionner `Exporter`.

![Export dashboard option](assets/custom_dashboard_export.png)

Pour exporter un widget, le même mécanisme est utilisé, mais depuis le bouton menu burger situé dans le coin supérieur droit du widget.

![Export widget option](assets/export-widget-option.png)

Pour exporter la configuration d’un tableau de bord depuis la vue du tableau de bord :

1. Accéder au tableau de bord souhaité.
2. Cliquer sur le bouton `Exporter` (icône de fichier avec une flèche pointant vers le coin supérieur droit) situé en haut à droite du tableau de bord.

![Export JSON button](assets/export-json-button.png)

#### Fichier de configuration

La configuration du tableau de bord sera enregistrée sous forme de fichier JSON, avec un titre au format `[YYYYMMDD]_octi_dashboard_[dashboard title]`. Le contenu attendu du fichier de configuration est le suivant :

```JSON
{
  "openCTI_version": "5.12.0",
  "type": "dashboard",
  "configuration": {
  "name": "My dashboard title",
  "manifest": "eyJ3aWRn(...)uZmlnIjp7fX0="
  }
}
```

La configuration du widget sera enregistrée sous forme de fichier JSON, avec un titre au format `[YYYYMMDD]_octi_widget_[widget view]`. Le contenu attendu du fichier de configuration est le suivant :

```JSON
{
  "openCTI_version": "5.12.0",
  "type": "widget",
  "configuration": "eyJ0eXB(...)iOmZhbHNlfX0="
}
```

!!! warning "Filtres liés à la plateforme source"

  Lors de l’export d’une configuration de tableau de bord ou de widget, tous les filtres seront exportés tels quels. Les filtres portant sur des objets inexistants sur la plateforme de destination devront être supprimés manuellement après l’import. Les filtres à supprimer sont identifiables par leur valeur barrée « supprimer ».

![Filter to delete](assets/filter-to-delete.png)


### Importer

Les tableaux de bord peuvent être importés depuis la liste des tableaux de bord personnalisés :

1. Cliquer sur le bouton `Importer un tableau de bord` en haut à droite.
2. Sélectionner votre fichier.

![Import dashboard option](assets/import_dashboard.png)

Pour importer un widget depuis la vue d’un tableau de bord :
1- Survoler le bouton Ajouter (+) dans le coin inférieur droit.
2- Cliquer sur le bouton Importer un widget (nuage avec une flèche vers le haut).
3- Sélectionner votre fichier.

![Import widget option](assets/import_widget.png)

!!! warning "Compatibilité des configurations"

  Seuls les fichiers JSON comportant les propriétés requises seront acceptés, notamment « openCTI_version: [5.12.0 et supérieur] », « type: [dashboard|widget] » et une « configuration ». Ceci s’applique aussi bien aux configurations de tableaux de bord qu’à celles des widgets.


### Dupliquer

Les tableaux de bord peuvent être dupliqués depuis la liste des tableaux de bord personnalisés ou depuis la vue du tableau de bord.

Pour dupliquer un tableau de bord depuis la liste des tableaux de bord personnalisés :

1. Cliquer sur le bouton à la fin de la ligne du tableau de bord.
2. Sélectionner `Dupliquer`.

Pour dupliquer un widget, le même mécanisme est utilisé, mais depuis le bouton menu burger situé dans le coin supérieur droit du widget.

Pour dupliquer un tableau de bord depuis la vue du tableau de bord :

1. Accéder au tableau de bord souhaité.
2. Cliquer sur le bouton `Dupliquer le tableau de bord` (deux feuilles superposées) situé en haut à droite du tableau de bord.

![Duplicate dashboard button](assets/duplicate_dashboard_button.png)

Après duplication, un message de confirmation s’affiche brièvement, accompagné d’un lien pour accéder facilement à la nouvelle vue du tableau de bord. Néanmoins, le nouveau tableau de bord reste accessible dans la liste des tableaux de bord.

![duplicate-dashboard-success-message](assets/duplicate_custom.png)

!!! note "Accès au tableau de bord"

  L’utilisateur important ou dupliquant un tableau de bord devient le seul à y avoir accès. L’accès peut ensuite être géré comme d’habitude.

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.