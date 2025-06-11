# Flux TAXII

Les flux TAXII dans OpenCTI offrent un mécanisme robuste pour l’ingestion de collections TAXII depuis des serveurs TAXII ou d’autres instances OpenCTI.

<a id="best-practices-section"></a>
## Bonnes pratiques

Dans OpenCTI, la section « Données > Ingestion » propose aux utilisateurs des fonctions intégrées pour l’importation automatisée de données. Ces fonctions sont conçues pour des usages spécifiques et peuvent être configurées pour ingérer les données de manière transparente dans la plateforme. Nous allons ici explorer le processus de configuration des cinq fonctions intégrées : Live Streams, TAXII Feeds, TAXII Push, RSS Feeds et JSON/CSV Feeds.

Assurer un environnement sécurisé et bien organisé est primordial dans OpenCTI. Voici deux bonnes pratiques recommandées pour renforcer la sécurité, la traçabilité et la clarté organisationnelle :

1. Créer un utilisateur dédié pour chaque source : Générer un utilisateur spécifiquement pour l’import de flux, en suivant la convention `[F] Nom de la source` pour une identification claire. Assigner cet utilisateur au groupe « Connectors » afin de faciliter la gestion des utilisateurs et des droits liés à la création de données. Veuillez [consulter ici](../../deployment/connectors.md#connector-token-section) pour plus d’informations sur cette bonne pratique.
2. Créer une Organisation dédiée pour la source : Créer une organisation portant le nom de la source de données pour une identification claire. Assigner l’organisation nouvellement créée au champ « Auteur par défaut » dans la configuration de l’import du flux si disponible.

En respectant ces bonnes pratiques, il est possible de gérer de manière indépendante les droits pour chaque source d’import via des structures d’utilisateur et d’organisation dédiées. De plus, cela permet une traçabilité claire du créateur de l’entité, facilitant l’évaluation des sources, la création de tableaux de bord, le filtrage des données et d’autres tâches administratives.

## Configuration

Voici un guide étape par étape pour configurer les ingesteurs TAXII :

1. URL du serveur TAXII : Fournir l’URL racine de l’API du serveur TAXII. Pour les collections provenant d’une autre instance OpenCTI, l’URL est de la forme `https://[domaine]/taxii2/root`.
2. Collection TAXII : Saisir l’ID de la collection TAXII à ingérer. Pour les collections provenant d’une autre instance OpenCTI, l’ID suit le format `426e3acb-db50-4118-be7e-648fab67c16c`.
3. Type d’authentification (si nécessaire) : Indiquer le type d’authentification. Pour les collections non publiques provenant d’une autre instance OpenCTI, le type d’authentification est « Bearer token ». Saisir le token d’un utilisateur ayant accès à la collection (similaire au point 2 de la configuration des Live streams ci-dessus).

!!! note "URL racine de l’API TAXII"

    De nombreuses instructions de configuration TAXII fournies par les ISAC indiqueront l’URL de la collection ou du service de découverte. Dans ces cas, retirer le dernier segment du chemin de l’URL du serveur TAXII afin de l’utiliser dans OpenCTI. Par exemple, utiliser https://[domaine]/tipapi/tip21, et non https://[domaine]/tipapi/tip21/collections.

Options de configuration supplémentaires :

- Utilisateur responsable de la création des données : Définir l’utilisateur responsable de la création des données reçues de ce flux TAXII. La bonne pratique consiste à dédier un utilisateur par source pour une meilleure clarté organisationnelle. Veuillez [consulter la section « Bonnes pratiques » ci-dessous](../import-automated.md#best-practices-section) pour plus d’informations.
- Importer à partir de la date : Spécifier la date des données les plus anciennes à récupérer. Laisser le champ vide pour tout importer.

![TAXII feed configuration](../assets/taxii-feed-configuration.png)

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.