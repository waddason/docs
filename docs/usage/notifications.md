# Notifications et alertes

Dans le paysage en constante évolution de la cybersécurité, la réactivité est cruciale. OpenCTI permet aux utilisateurs de rester informés et d’agir rapidement grâce à son système robuste de notifications et d’alertes. Cette fonctionnalité permet de créer des déclencheurs personnalisés qui surveillent activement la plateforme pour des événements spécifiques et notifient rapidement les utilisateurs lorsque ces conditions sont remplies.

Qu’il s’agisse d’utilisateurs individuels adaptant leurs préférences d’alerte ou d’administrateurs orchestrant des déclencheurs collaboratifs pour des Groupes ou des Organisations, le système de notification d’OpenCTI est un outil polyvalent pour tenir les parties prenantes de la cybersécurité informées.

Le menu principal "Notifications et déclencheurs" pour créer et gérer les notifications se trouve en haut à droite, représenté par l’icône de cloche.

![Notifications](assets/notifications.png)  

Cliquer sur la ligne "Digest with multiples notifiers" pour ouvrir un tiroir et accéder aux notifications détaillées.

![Notifications](assets/digestWithMultipleNotifiers.png)


## Déclencheurs

Dans OpenCTI, les déclencheurs servent de mécanismes personnalisés permettant aux utilisateurs de rester informés sur des événements spécifiques correspondant à leurs priorités en cybersécurité. Les utilisateurs peuvent créer et gérer des déclencheurs pour adapter leur expérience de notification. Chaque déclencheur fonctionne en écoutant activement les événements selon des filtres et types d’événements prédéfinis, et notifie rapidement les utilisateurs via les notifiers choisis lorsque les conditions sont remplies.

![Triggers](assets/triggers.png)

### Gestion des déclencheurs

**Déclencheurs utilisateur individuel :** Chaque utilisateur possède l’autonomie de créer ses propres déclencheurs, adaptés à ses préférences et responsabilités. En définissant des filtres personnalisés et en sélectionnant les notifiers préférés, les utilisateurs s’assurent de recevoir des notifications pertinentes et en temps voulu, alignées sur leurs domaines d’intérêt.

**Contrôle administratif :** Les administrateurs de la plateforme ont la capacité de créer et de gérer des déclencheurs pour les Utilisateurs, Groupes et Organisations. Cela offre un contrôle centralisé et la possibilité de configurer des déclencheurs répondant à des objectifs collectifs de cybersécurité. Les utilisateurs du Groupe ou de l’Organisation désignés bénéficieront de ces déclencheurs avec des droits d’accès en lecture seule. Ces déclencheurs doivent être créés directement sur l’Utilisateur|Groupe|Organisation avec lequel les partager dans "Paramètres > Sécurité > Utilisateurs|Groupes|Organisations".

![Restricted trigger](assets/restricted-trigger.png)

### Filtres de déclencheur

Grâce aux filtres, les utilisateurs peuvent **définir précisément les critères qui activent leurs déclencheurs**. Ce niveau de granularité garantit que les déclencheurs sont précis, réagissant uniquement aux événements les plus importants. Les utilisateurs peuvent adapter les filtres selon divers paramètres tels que les types d’objets, les markings, les sources ou d’autres détails contextuels. Il est également possible d’autoriser les notifications pour l’assignation d’une Task, d’un Case, etc.

Au-delà des filtres, un déclencheur peut être configuré pour **réagir à trois types d’événements** : création, modification et suppression.

![Trigger configuration](assets/trigger-configuration.png)

### Déclencheurs d’instance

Les déclencheurs d’instance offrent une approche ciblée de la surveillance en direct en permettant aux utilisateurs de configurer des déclencheurs spécifiques à une ou plusieurs entités. Ces déclencheurs, une fois activés, surveillent un ensemble prédéfini d’événements liés aux entités sélectionnées, garantissant une information instantanée sur les changements cruciaux.

#### Créer des déclencheurs d’instance

**Méthode 1 :** Utiliser le formulaire général de création de déclencheur

1. Aller dans la fenêtre "Notifications et déclencheurs".
2. Naviguer vers l’onglet "Déclencheurs et digests".
3. Accéder au formulaire général de création de déclencheur.
4. Activer l’option "Instance trigger".
5. Choisir les entités à surveiller.

![Instance trigger creation](assets/instance-trigger-creation.png)

**Méthode 2 :** Abonnement rapide

1. Sur la vue d’ensemble d’une entité, localiser le bouton "Instance trigger quick subscription" avec l’icône de cloche en haut à droite.
2. Cliquer sur le bouton pour créer le déclencheur d’instance.
3. (Optionnel) Cliquer à nouveau pour modifier le déclencheur d’instance créé.

![Quick subscription button](assets/quick-subscription-button.png)

#### Événements surveillés par les déclencheurs d’instance

Un déclencheur d’instance défini sur une entité X surveille activement les événements suivants :

- Mise à jour/Suppression de X : Être informé lorsque l’entité sélectionnée subit des modifications ou est supprimée.
- Création/Suppression de relations : Recevoir des notifications lors de l’ajout ou de la suppression de relations vers/depuis X.
- Création/Suppression d’entités liées : Être alerté lors de la création ou suppression d’entités qui référencent X – c’est-à-dire qui contiennent X, sont partagées avec X, sont créées par X, etc.
- Ajout/Retrait de X dans une référence : Être informé lorsque X est inclus ou retiré de la référence d’autres entités – par exemple, ajout de X comme auteur d’une entité, ajout de X dans un rapport, etc.

!!! note "Notification de suppression d’entité"

    Il est important de noter que la notification de suppression d’entité peut intervenir dans deux scénarios :
        - Suppression réelle de l’entité : lorsque l’entité est effectivement supprimée de la plateforme.
        - Perte de visibilité : lorsqu’une modification de l’entité entraîne la perte de visibilité de cette entité pour l’utilisateur.


## Digest

Les digests offrent un moyen efficace de rationaliser et d’organiser vos notifications. En regroupant les notifications selon les déclencheurs sélectionnés et en spécifiant la période de livraison (quotidienne, hebdomadaire, mensuelle), vous bénéficiez de la flexibilité de recevoir des mises à jour consolidées au moment souhaité, plutôt que des notifications immédiates déclenchées par chaque événement.

### Créer des digests

1. Aller dans la fenêtre "Notifications et déclencheurs".
2. Naviguer vers l’onglet "Déclencheurs et digests".
3. Créer un nouveau digest.
4. Configurer le digest : définir les paramètres, y compris les déclencheurs à inclure et la fréquence des notifications (quotidienne, hebdomadaire, mensuelle).
5. Choisir le(s) notifier(s) : sélectionner la ou les méthodes de notification (par exemple, dans l’interface OpenCTI, par email, etc.).

![Digest configuration](assets/digest-creation.png)

### Configuration du buffering des digests

Il est possible de configurer le buffering des digests directement dans votre fichier de configuration afin de regrouper les notifications si de nombreux changements surviennent dans un court laps de temps.
La configuration du buffering est activée par défaut sur la plateforme à une minute. Vous pouvez la modifier selon vos besoins.

### Avantages des digests

- Notifications organisées : Les digests permettent d’organiser et de catégoriser les notifications, évitant ainsi une surcharge d’alertes individuelles.
- Livraison personnalisée : Choisir la fréquence de réception des digests selon vos préférences, qu’il s’agisse d’un aperçu quotidien, d’un résumé hebdomadaire ou d’un récapitulatif mensuel.
- Moins de distractions : Recevoir les notifications à un moment planifié, minimisant les interruptions et permettant de se concentrer sur les tâches critiques.

Les digests renforcent votre contrôle sur la gestion des notifications, assurant une approche plus structurée et pratique pour rester informé des événements importants.


## Notifiers

Dans OpenCTI, les notifiers servent de canaux de diffusion des notifications, permettant aux utilisateurs de rester informés des événements critiques. La plateforme propose deux notifiers intégrés, "Default mailer" pour les notifications par email et "User interface" pour les alertes dans la plateforme.

![Notifiers](assets/notifiers.png)

### Connecteurs de notifier

OpenCTI propose des connecteurs de notifier intégrés permettant aux utilisateurs de créer des notifiers personnalisés pour la notification et l’alerte d’activité. Trois connecteurs essentiels sont disponibles :

- Platform mailer connector : permet l’envoi de notifications directement dans la plateforme OpenCTI.
- Simple mailer connector : offre une approche simplifiée pour les notifications par email avec des options de configuration allégées.
- Generic webhook connector : facilite la communication via webhooks.

OpenCTI fournit deux exemples de notifiers webhook conçus pour l’intégration avec Teams.

![Custom notifiers](assets/custom-notifiers.png)

### Configuration et accès

Les notifiers sont gérables dans la fenêtre "Paramètres > Personnalisation > Notifiers" et peuvent être restreints via le contrôle d’accès basé sur les rôles (RBAC). Les administrateurs peuvent restreindre l’accès à certains Utilisateurs, Groupes ou Organisations, assurant ainsi un usage contrôlé.

Pour obtenir des conseils sur la configuration de notifiers personnalisés et consulter des instructions détaillées, se référer à la [page de documentation dédiée](../administration/notifiers.md).


> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.