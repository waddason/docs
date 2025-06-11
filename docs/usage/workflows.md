# Workflows et assignation

Gérer et organiser efficacement le travail au sein de la plateforme OpenCTI en tirant parti des workflows et de l’assignation. Ces fonctionnalités offrent une approche structurée pour suivre le statut des objets et attribuer des responsabilités aux utilisateurs.


## Workflows

Les workflows sont conçus pour tracer le statut des objets dans le système. Ils sont représentés par le champ « Statut de traitement » intégré à chaque objet. Par défaut, ce champ est désactivé pour la plupart des objets, mais il peut être activé via les paramètres de la plateforme. Pour plus de détails sur l’activation et la configuration des workflows, consulter la [page de documentation dédiée](../administration/entities.md#workflow-section).

Activer les workflows améliore la visibilité sur l’avancement et le statut des différents objets, offrant ainsi une vue d’ensemble pour une gestion efficace.

![Processing status](assets/processing-status.png)


## Attributs d’assignation

Certains objets, notamment les Reports, Cases et Tasks, disposent des attributs « Assignés » et « Participants ». Ces attributs permettent de désigner les personnes responsables de l’objet ainsi que celles qui y participent activement.

Les attributs peuvent être définis comme obligatoires ou avec des valeurs par défaut, ce qui simplifie le processus d’assignation. Les utilisateurs peuvent également être assignés ou désignés comme participants manuellement, contribuant ainsi à un workflow collaboratif et organisé. Pour plus de détails sur la configuration des attributs, consulter la [page de documentation dédiée](../administration/entities.md#attributes-section).

![Assignment attributes](assets/assignment-attributes.png)

Les utilisateurs peuvent rester informés des assignations via les [déclencheurs de notification](notifications.md). En configurant des déclencheurs de notification, les utilisateurs reçoivent des alertes lorsqu’un objet leur est assigné. Cela garantit une communication rapide et un engagement proactif avec les tâches ou responsabilités assignées.

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.