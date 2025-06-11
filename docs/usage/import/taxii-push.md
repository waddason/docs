# TAXII Push

L'ingesteur TAXII Push permet aux utilisateurs d'importer des objets STIX 2.1 dans OpenCTI via une collection TAXII exposée.

<a id="best-practices-section"></a>
## Bonnes pratiques

Dans OpenCTI, la section "Data > Ingestion" propose aux utilisateurs des fonctions intégrées pour l'import automatisé de données. Ces fonctions sont conçues pour des usages spécifiques et peuvent être configurées pour ingérer automatiquement des données dans la plateforme. Nous allons ici explorer le processus de configuration des cinq fonctions intégrées : Live Streams, TAXII Feeds, TAXII Push, RSS Feeds et JSON/CSV Feeds.

Assurer un environnement sécurisé et bien organisé est primordial dans OpenCTI. Voici deux bonnes pratiques recommandées pour renforcer la sécurité, la traçabilité et la clarté organisationnelle :

1. Créer un utilisateur dédié pour chaque source : Générer un utilisateur spécifiquement pour l'import de flux, en suivant la convention `[F] Nom de la source` pour une identification claire. Assigner cet utilisateur au groupe "Connectors" afin de faciliter la gestion des utilisateurs et des droits liés à la création de données. Veuillez [voir ici](../../deployment/connectors.md#connector-token-section) pour plus d'informations sur cette bonne pratique.
2. Créer une Organisation dédiée pour la source : Créer une organisation portant le nom de la source de données pour une identification claire. Assigner cette organisation nouvellement créée au champ "Default author" dans la configuration d'import de flux si disponible.

En suivant ces bonnes pratiques, il est possible de gérer de façon indépendante les droits pour chaque source d'import via des structures dédiées d'utilisateur et d'organisation. De plus, cela permet une traçabilité claire du créateur de l'entité, facilitant l'évaluation des sources, la création de tableaux de bord, le filtrage des données et d'autres tâches administratives.

## Configuration

L'ingesteur TAXII Push permet aux utilisateurs d'importer des objets STIX 2.1 dans OpenCTI via une collection TAXII exposée, conformément à la [partie “Add objects” de la spécification TAXII 2.1](https://docs.oasis-open.org/cti/taxii/v2.1/os/taxii-v2.1-os.html#_Toc31107540).
Voici un guide étape par étape pour configurer les ingesteurs TAXII Push :

1. Nom : Saisir un nom pour l'ingesteur TAXII Push.
2. Description (optionnel) : Saisir une description pour l'ingesteur TAXII Push.
3. Utilisateur responsable de la création des données : Définir l'utilisateur responsable de la création des données reçues de cet ingesteur TAXII Push. La bonne pratique consiste à dédier un utilisateur par source pour plus de clarté organisationnelle. Veuillez [voir la section "Bonnes pratiques" ci-dessous](import-automated.md#best-practices-section) pour plus d'informations.
4. Accessible pour : Saisir l'utilisateur, le groupe ou l'organisation autorisé à pousser des données dans la collection TAXII.
5. Copier le niveau de confiance vers les scores OpenCTI pour les indicators : Activer cette option pour mapper le niveau de confiance associé aux indicators STIX vers le système de scoring OpenCTI.

![TAXII Push configuration](../assets/taxii-push-configuration.png)

Après la création d'un nouvel ingesteur TAXII Push, un endpoint TAXII est généré, qui peut être utilisé pour publier des données au format STIX 2.1.
Pour démarrer votre nouvel ingesteur, cliquer sur "Start" dans le menu burger.

![TAXII Push creation: start](../assets/taxii-push-creation-start.png)

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.