# Flux RSS

La fonctionnalité des flux RSS permet aux utilisateurs d’ingérer facilement des éléments sous forme de rapports à partir de flux RSS spécifiés.

<a id="best-practices-section"></a>
## Bonnes pratiques

Dans OpenCTI, la section « Données > Ingestion » propose des fonctions intégrées pour l’importation automatisée de données. Ces fonctions sont conçues pour des usages spécifiques et peuvent être configurées pour ingérer automatiquement des données dans la plateforme. Nous allons explorer ici le processus de configuration des cinq fonctions intégrées : Live Streams, TAXII Feeds, TAXII Push, RSS Feeds et JSON/CSV Feeds.

Assurer un environnement sécurisé et bien organisé est primordial dans OpenCTI. Voici deux bonnes pratiques recommandées pour renforcer la sécurité, la traçabilité et la clarté organisationnelle :

1. Créer un utilisateur dédié pour chaque source : Générer un utilisateur spécifiquement pour l’import de flux, en suivant la convention `[F] Nom de la source` pour une identification claire. Assigner cet utilisateur au groupe « Connectors » afin de faciliter la gestion des utilisateurs et des droits liés à la création de données. Veuillez [voir ici](../../deployment/connectors.md#connector-token-section) pour plus d’informations sur cette bonne pratique.
2. Créer une Organisation dédiée pour la source : Créer une organisation portant le nom de la source de données pour une identification claire. Assigner cette organisation au champ « Auteur par défaut » dans la configuration de l’import de flux si disponible.

En suivant ces bonnes pratiques, il est possible de gérer de façon indépendante les droits pour chaque source d’import via des structures dédiées d’utilisateur et d’organisation. De plus, cela permet une traçabilité claire du créateur de l’entité, facilitant l’évaluation des sources, la création de tableaux de bord, le filtrage des données et d’autres tâches administratives.


## Configuration

Voici un guide étape par étape pour configurer les ingesteurs RSS :

1. URL du flux RSS : Indiquer l’URL du flux RSS à partir duquel les éléments seront importés.

Options de configuration supplémentaires :

- Utilisateur responsable de la création des données : Définir l’utilisateur responsable de la création des données reçues de ce flux RSS. La bonne pratique consiste à dédier un utilisateur par source pour plus de clarté organisationnelle. Veuillez [voir la section « Bonnes pratiques » ci-dessous](import-automated.md#best-practices-section) pour plus d’informations.
- Importer à partir de la date : Spécifier la date des données les plus anciennes à récupérer. Laisser le champ vide pour tout importer.
- Types de rapport par défaut : Indiquer le type de rapport à appliquer au rapport importé.
- Auteur par défaut : Indiquer l’auteur par défaut à appliquer au rapport importé. Veuillez [voir la section « Bonnes pratiques » ci-dessous](../import-automated.md#best-practices-section) pour plus d’informations.
- Définitions de marquage par défaut : Indiquer les marquages par défaut à appliquer aux rapports importés.

![RSS feed configuration](../assets/rss-feed-configuration.png)

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.