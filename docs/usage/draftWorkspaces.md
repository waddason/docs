# Espaces de travail de brouillon

Les brouillons sont des outils puissants qui permettent aux analystes de créer et de manipuler des données dans un espace de travail séparé, sans impacter la base de connaissances principale de la plateforme. La plupart des fonctionnalités disponibles sur la plateforme sont également compatibles dans un brouillon.

## Création de brouillon

Les brouillons peuvent être créés de deux manières principales.

La première façon de créer un brouillon est de le créer manuellement, depuis la page Brouillons. Lorsqu'il est créé de cette manière, le brouillon sera initialisé sans aucune donnée modifiée.

![Draft creation page](assets/draftWorkspace-manual-creation.png)

La seconde façon de créer des brouillons est lors de l'importation de fichiers dans la plateforme. Selon la configuration de la plateforme et du connecteur, le téléchargement d'un fichier peut générer automatiquement un import de ce fichier. Cet import automatique peut générer un brouillon où le résultat de l'import du fichier sera disponible. Une variable a été créée pour vous permettre de choisir votre import (soit workbench, soit draft) : [Configuration](../deployment/configuration.md).

De plus, les fichiers peuvent être importés manuellement. Dans ce cas, une option est disponible pour choisir le mode de validation à utiliser. Lorsque le mode de validation brouillon est sélectionné, un brouillon sera automatiquement créé et le résultat de l'import du fichier sera disponible dans celui-ci.

Pour plus d'informations sur l'import de fichiers, consulter la page de documentation dédiée : [Import from files](import-files.md).

Pour accéder rapidement au brouillon et voir le résultat d'un import de fichier, une icône Naviguer vers le brouillon est disponible.

![Navigate to draft](assets/draftWorkspace-navigate-to-draft.png)

Sinon, un brouillon peut être ouvert en cliquant dessus dans la liste des brouillons.

![Draft list](assets/draftWorkspace-draft-list.png)

## Vue d'ensemble du brouillon

En entrant dans un brouillon, la page d'accueil affichera la vue d'ensemble des modifications contenues dans le brouillon.

![Draft overview](assets/draftWorkspace-draft-overview.png)

Cette vue d'ensemble est séparée en différents onglets : entities, observables, relationships, sightings et containers. Chaque onglet contient la liste des modifications appliquées à un élément de ce type.

### Types d'opérations

Il existe 5 types d'opérations de brouillon pouvant être appliquées aux éléments. 3 opérations sont des modifications qui impactent directement les données :

- CREATE : cela signifie que l'élément a été créé dans le brouillon et n'existe pas dans la base de connaissances principale
- UPDATE : cela signifie que l'élément existait dans la base de connaissances principale, mais a été modifié dans le brouillon
- DELETE : cela signifie que l'élément existait dans la base de connaissances principale, mais a été marqué pour suppression dans le brouillon

2 opérations sont des modifications qui n'ont pas été directement demandées sur l'élément, mais qui résultent de la modification d'éléments liés :

- UPDATE_LINKED : cela signifie que l'élément existait dans la base de connaissances principale et n'a pas été modifié directement, mais a été impacté par une modification d'une entité liée. Cela peut arriver lorsqu'une relationship est créée vers cette entité, lorsque cette entité est ajoutée dans un container, etc.
- DELETE_LINKED : cela signifie que l'élément existait dans la base de connaissances principale et n'a pas été directement marqué pour suppression, mais qu'il sera tout de même supprimé suite à la suppression d'une entité liée

### Fichiers dans un brouillon

En plus de ces listes d'entités modifiées, un onglet fichier est également disponible.

![Draft files](assets/draftWorkspace-file-tab.png)

Dans cet onglet, des fichiers supplémentaires peuvent être téléchargés et importés dans l'espace de travail du brouillon sans impacter la base de connaissances principale. Ces fichiers ne seront visibles que dans le brouillon courant.

### Actions de la barre supérieure

Dans un brouillon, la barre supérieure est modifiée pour rappeler que tout ce qui est fait dans la plateforme n'impactera que le brouillon en cours.

![Draft context banner](assets/draftWorkspace-context-banner.png)

Cliquer sur le nom du brouillon permet de revenir rapidement à la vue d'ensemble du brouillon et de voir le récapitulatif de toutes les modifications.

Quitter un brouillon et revenir à la base de connaissances principale de la plateforme peut se faire avec le bouton Quitter le brouillon.

Approuver un brouillon et l'ingérer dans la base de connaissances principale peut se faire avec le bouton Approuver le brouillon.

Une icône et un compteur seront visibles lorsqu'il y a des processus en cours dans le brouillon (travaux d'enrichment connector, tâches en arrière-plan, etc.). Cliquer sur cette icône ouvrira la liste complète des processus en cours, avec plus de détails disponibles.

![Draft processes](assets/draftWorkspace-processes.png)

### Approbation du brouillon

Une fois que le contenu du brouillon est jugé acceptable, il peut être approuvé. Cela enverra le contenu du brouillon pour ingestion dans la base de connaissances principale. Le statut du brouillon sera également mis à jour : le brouillon ne sera plus considéré comme ouvert, mais validé.

Les brouillons peuvent être approuvés même s'il y a encore des processus en cours, mais veuillez noter que les modifications qui auraient été appliquées par ces processus seront perdues.

Selon l'opération de brouillon sur les données, le processus d'ingestion sera légèrement différent. Seules les opérations Create, Update et Delete sont envoyées pour ingestion. Les entités créées seront entièrement envoyées pour ingestion. Mais les entités mises à jour ne seront pas entièrement envoyées et upsertées : seules les mises à jour appliquées dans le brouillon seront appliquées sur la version principale. Pour les suppressions, seules les entités supprimées auront une action de suppression appliquée, et non les entités liées supprimées.

### Ségrégation des données & RBAC dans le brouillon

Étant donné que dans le brouillon vous pouvez voir votre plateforme, il est important de souligner que :

- [Capabilities](../administration/users.md) s'appliquent dans le brouillon : un utilisateur sans la capacité de créer ou de mettre à jour la connaissance ne pourra pas créer ou mettre à jour la connaissance dans le brouillon. De plus, cet utilisateur ne pourra pas non plus approuver un brouillon.
- [Confidence level](reliability-confidence.md) s'applique dans le brouillon : le niveau de confiance s'appliquera dans le brouillon, de la même manière qu'il est appliqué dans la plateforme.
- [Markings](../administration/segregation.md) s'appliquent dans le brouillon : si vous n'êtes pas autorisé à voir une donnée dans la plateforme, vous ne pourrez pas la voir non plus dans le brouillon.
- [Data segregation](../administration/organization-segregation.md) : si vous avez activé la ségrégation des données et qu'une entité ne vous a pas été partagée, lors de l'accès à un brouillon, cette entité restera inaccessible pour vous. De plus, si entre-temps cette entité vous a été partagée, elle restera cachée dans le brouillon, puisque le brouillon a été créé avant que l'accès ne vous soit accordé.

## Vue en lecture seule du brouillon

Une fois le brouillon approuvé et qu'il est désormais en statut validé, il n'est plus possible d'entrer dans ce brouillon et d'y appliquer des modifications.

Cependant, il est toujours possible de voir les modifications qui existaient lors de l'approbation du brouillon.

![Draft processes](assets/draftWorkspace-read-only-view.png)

En ouvrant un brouillon validé, la même vue d'ensemble du brouillon sera disponible pour voir tous les changements du brouillon.

De plus, la progression de l'ingestion de l'approbation du brouillon est visible en haut des listes de données.

## Fonctionnalités non disponibles dans le brouillon

Même si les brouillons essaient de fournir autant d'actions que possible dans la plateforme, certaines actions n'ont pas de sens ou n'ont pas encore été implémentées pour fonctionner en mode brouillon. Parmi elles :

- playbooks
- inference rules
- sharing to org
- apply authorized members
- downloading knowledge
- disseminate a file
- merge entities

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.