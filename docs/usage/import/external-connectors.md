# Connecteurs

Les connecteurs dans OpenCTI servent de passerelles dynamiques, facilitant l'importation de données depuis une grande variété de sources et de systèmes. Chaque connecteur est conçu pour gérer des types et structures de données spécifiques à la source, permettant à OpenCTI d'ingérer efficacement les données.

## Comportement des connecteurs

Le comportement de chaque connecteur est défini par son développement, déterminant les types de données qu'il importe et ses options de configuration. Cette flexibilité permet aux utilisateurs de personnaliser le processus d'importation selon leurs besoins, assurant une intégration de données fluide et adaptée.

Le niveau de granularité de configuration concernant le type de données importées varie selon chaque connecteur. Néanmoins, les connecteurs permettent aux utilisateurs de spécifier la date à partir de laquelle ils souhaitent récupérer les données. Cette fonctionnalité est particulièrement utile lors de l'activation initiale d'un connecteur, permettant la récupération de données historiques. Par la suite, le connecteur fonctionne en temps réel, important continuellement les nouvelles données de la source.

### Réinitialiser l'état du connecteur

Réinitialiser l'état du connecteur permet de redémarrer le processus d'ingestion depuis le tout début.
De plus, la réinitialisation de l'état du connecteur purge la file RabbitMQ pour ce connecteur spécifique.

Cependant, cette action nécessite la capacité "Gérer l'état du connecteur" (plus de détails sur les capacités : [Liste des capacités](../administration/users.md#list-of-capabilities)). Sans cette capacité spécifique, il ne sera pas possible de réinitialiser l'état du connecteur.

Lorsque l'action est effectuée, un message s'affiche pour confirmer la réinitialisation et vous informer du nombre de messages qui seront purgés.

![Fenêtre contextuelle de message de réinitialisation](../assets/reset-state-msg.png)

Purger une file de messages est nécessaire pour supprimer les messages accumulés qui peuvent être obsolètes ou redondants. Cela permet d'éviter de retraiter des messages déjà ingérés.

En purgeant la file, vous vous assurez que le connecteur démarre sur une base propre, ne traitant que les nouvelles données.

### Écosystème des connecteurs

L'écosystème des connecteurs d'OpenCTI couvre un large éventail de sources, renforçant la capacité de la plateforme à intégrer des données issues de divers contextes, allant des fournisseurs de threat intelligence aux bases de données spécialisées. La liste des connecteurs disponibles est accessible dans notre [catalogue de connecteurs](https://www.notion.site/OpenCTI-Ecosystem-868329e9fb734fca89692b2ed6087e76). Les connecteurs sont classés en trois types : import connecteurs (le sujet ici), [enrichment connecteurs](enrichment.md), et stream consumers. Une documentation supplémentaire sur les connecteurs est disponible sur [la page dédiée](../deployment/connecteurs.md).

En résumé, les imports automatisés via les connecteurs offrent aux utilisateurs d'OpenCTI un mécanisme d'ingestion de données évolutif, efficace et personnalisable, garantissant que la plateforme reste enrichie avec les renseignements les plus récents et pertinents.

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.