# Supprimer et restaurer des connaissances

Les connaissances peuvent être supprimées d’OpenCTI soit depuis la vue d’ensemble d’un objet, soit en utilisant les [tâches en arrière-plan](background-tasks.md).
Lorsqu’un objet est supprimé, toutes ses relations et références vers d’autres objets sont également supprimées.

L’événement de suppression est écrit dans le [flux](../reference/streaming.md), afin de déclencher des [playbooks](./automation.md) automatisés ou de synchroniser une autre plateforme.

Depuis OpenCTI 6.1, un enregistrement des objets supprimés est conservé pendant une période donnée, permettant de les restaurer à la demande. Cela n’impacte pas les événements du flux ni les autres effets secondaires de la suppression : l’objet reste _supprimé_.


## Corbeille

Une vue appelée « Corbeille » affiche toutes les opérations de suppression, qu’il s’agisse d’entités ou de relations.

![Trash](assets/trash.png)

Une opération de suppression contient non seulement l’entité ou la relation supprimée, mais aussi toutes les relations et références depuis (vers) cet objet principal vers (depuis) d’autres éléments de la plateforme.

Il est possible de trier, filtrer ou rechercher dans ce tableau en utilisant les contrôles habituels de l’interface. Les critères disponibles sont le type d’objet, leur représentation (le plus souvent, le _nom_ de l’objet), l’utilisateur ayant supprimé l’objet, la date et l’heure de la suppression, ainsi que le marquage de l’objet.

À noter que les opérations de suppression (c’est-à-dire les entrées de cette vue) héritent du marquage de l’entité principale supprimée, et suivent donc les mêmes restrictions d’accès que l’objet supprimé.

Il est possible de restaurer ou de supprimer définitivement un objet individuellement depuis la vue Corbeille, en utilisant le menu burger à la fin de la ligne.

![Trash actions](assets/trash-actions.png)

Il est également possible d’utiliser les cases à cocher au début de la ligne pour sélectionner un sous-ensemble d’objets supprimés, puis de lancer une tâche en arrière-plan pour les restaurer ou les supprimer définitivement par lot.

## Restaurer

Restaurer un élément le recrée dans la plateforme avec les mêmes informations qu’avant sa suppression.
Toutes les relations depuis ou vers cet objet, qui ont également été supprimées lors de l’opération de suppression, sont aussi restaurées.
Si l’objet possédait des fichiers joints (importés ou exportés), ceux-ci sont également restaurés.

![Trash restore confirm](assets/trash-restore-confirm.png)

## Suppression définitive

Depuis le panneau Corbeille, il est également possible de supprimer définitivement l’objet, ses relations et ses fichiers joints.

![Trash delete confirm](assets/trash-delete-confirm.png)

## Rétention de la corbeille

Les objets supprimés sont conservés dans la corbeille pendant une période fixe (7 jours par défaut), puis ils sont définitivement supprimés par le [gestionnaire de corbeille](../deployment/managers.md#trash-manager).

## Configuration

Le système de corbeille est activé par défaut mais peut être désactivé dans la [configuration](../deployment/configuration.md) de la plateforme.

La période de rétention de la corbeille peut également être configurée dans les paramètres du gestionnaire de collecte des déchets ; il est possible de définir n’importe quel nombre de jours dans le paramètre `garbage_collection_manager:deleted_retention_days`.

## Limitations

Lorsqu’il s’agit de restaurer un objet supprimé depuis la corbeille, l’implémentation actuelle présente plusieurs limitations.
Avant tout, si un objet dans la corbeille a perdu une dépendance de relation (c’est-à-dire que l’autre côté d’une relation depuis ou vers cet objet n’est plus présent dans la base de données active), il ne sera pas possible de restaurer l’objet.

![restore error: a dependency is in the trash](assets/trash-error-dependency-in-trash.png)

Dans ce cas, si la dépendance manquante se trouve également dans la corbeille, il est possible de restaurer manuellement cette dépendance en premier, puis de réessayer.

Si la dépendance manquante a été supprimée définitivement, l’objet ne pourra pas être récupéré.

![restore error: a dependency is in the trash](assets/trash-error-dependency-missing.png)

En d’autres termes :

* **pas de restauration partielle** : l’objet et _toutes_ ses relations doivent être restaurés en une seule fois
* **pas de restauration « en cascade »** : restaurer un objet ne restaure pas automatiquement tous les objets liés présents dans la corbeille

Il convient également de noter que tenter de restaurer un objet très imbriqué (par exemple une entité avec des milliers de relations) est une opération complexe qui peut prendre beaucoup de temps et mettre la plateforme sous forte charge. Cela n’est pas recommandé.

!!! avertissement "La corbeille ne remplace pas une bonne stratégie de sauvegarde de base de données"

    Le système de corbeille est conçu pour faire gagner du temps lorsqu’un utilisateur supprime par erreur des connaissances de la plateforme.
    Il n’est pas destiné à servir de système de sauvegarde complet pour votre base de données.

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.