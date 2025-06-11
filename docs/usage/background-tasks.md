# Tâches en arrière-plan

Trois types de tâches sont effectuées en arrière-plan :

- tâches de règles,
- tâches de knowledge,
- tâches utilisateur.

Les tâches de règles peuvent être consultées et activées dans Paramètres > Personnalisation > Rules engine.
Les tâches de knowledge et les tâches utilisateur peuvent être consultées et gérées dans Données > Tâches en arrière-plan. Le périmètre de chaque tâche est indiqué.

![Background_tasks](assets/background-tasks.png)

## Tâches de règles

Si une tâche de règle est activée, elle entraîne l’analyse de l’ensemble des données de la plateforme et la création d’entités ou de relations si une configuration correspond aux règles de la tâche. Les données créées sont appelées « inferred data ». À chaque événement sur la plateforme, le rules engine vérifie si les inferred data doivent être mises à jour, créées ou supprimées.

## Tâches de knowledge

Les tâches de knowledge sont des tâches en arrière-plan qui mettent à jour ou suppriment des entités et correspondent à des opérations de masse sur ces données. Pour en créer une, sélectionner des entités via les cases à cocher dans une liste d’entités, puis choisir l’action à effectuer via la barre d’outils.

### Droits

- Pour créer une tâche de knowledge, l’utilisateur doit avoir la capacité Update Knowledge (ou la capacité de supprimer la knowledge si l’action de la tâche est une suppression).
- Pour voir une tâche de knowledge dans la section Tâches en arrière-plan, l’utilisateur doit être le créateur de la tâche ou avoir la capacité KNOWLEDGE.
- Pour supprimer une tâche de knowledge depuis la section Tâches en arrière-plan, l’utilisateur doit être le créateur de la tâche ou avoir la capacité KNOWLEDGE_UPDATE.

## Tâches utilisateur

Les tâches utilisateur sont des tâches en arrière-plan qui mettent à jour ou suppriment des notifications. Cela peut être fait depuis la section Notifications, en sélectionnant plusieurs notifications via les cases à cocher, puis en choisissant une action via la barre d’outils.

### Droits

- Un utilisateur peut créer une tâche utilisateur uniquement sur ses propres notifications.
- Pour voir ou supprimer une tâche utilisateur, l’utilisateur doit être le créateur de la tâche ou avoir la capacité SET_ACCESS.

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.