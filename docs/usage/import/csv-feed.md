# Flux CSV

L'ingesteur de flux CSV permet aux utilisateurs d'importer des fichiers CSV exposés via des URLs.

<a id="best-practices-section"></a>
## Bonnes pratiques

Dans OpenCTI, la section "Données > Ingestion" propose aux utilisateurs des fonctions intégrées pour l'import automatisé de données. Ces fonctions sont conçues pour des usages spécifiques et peuvent être configurées pour ingérer les données de manière transparente dans la plateforme. Nous allons ici explorer le processus de configuration des cinq fonctions intégrées : Live Streams, TAXII Feeds, TAXII Push, RSS Feeds et JSON/CSV Feeds.

Assurer un environnement sécurisé et bien organisé est primordial dans OpenCTI. Voici deux bonnes pratiques recommandées pour renforcer la sécurité, la traçabilité et la clarté organisationnelle :

1. Créer un utilisateur dédié pour chaque source : Générer un utilisateur spécifiquement pour l'import de flux, en suivant la convention `[F] Nom de la source` pour une identification claire. Assigner l'utilisateur au groupe "Connectors" afin de faciliter la gestion des utilisateurs et des droits liés à la création de données. Voir [plus d'informations ici](../../deployment/connectors.md#connector-token-section) sur cette bonne pratique.
2. Créer une Organisation dédiée pour la source : Créer une organisation portant le nom de la source de données pour une identification claire. Assigner cette organisation nouvellement créée au champ "Auteur par défaut" dans la configuration de l'import du flux si disponible.

En suivant ces bonnes pratiques, il est possible de gérer de manière indépendante les droits pour chaque source d'import grâce à des structures dédiées d'utilisateur et d'organisation. De plus, cela permet une traçabilité claire du créateur de l'entité, facilitant l'évaluation de la source, la création de tableaux de bord, le filtrage des données et d'autres tâches administratives.

## Configuration

Voici un guide étape par étape pour configurer les ingesteurs CSV :

1. URL du CSV : Fournir l'URL du fichier CSV exposé à partir duquel les éléments seront importés.
2. CSV Mappers : Choisir le CSV mapper à utiliser pour importer les données.
3. Type d'authentification (si nécessaire) : Saisir le type d'authentification.

!!! note "CSV mapper"

    La fonctionnalité de flux CSV repose sur les CSV mappers. Il est nécessaire de créer le CSV mapper approprié pour importer les données contenues dans le fichier. Voir la page dédiée au [CSV mapper](../administration/csv-mappers.md).

Options de configuration supplémentaires :

- Utilisateur responsable de la création des données : Définir l'utilisateur responsable de la création des données reçues de ce flux CSV. La bonne pratique consiste à dédier un utilisateur par source pour plus de clarté organisationnelle. Voir [la section "Bonnes pratiques" ci-dessous](../import-automated.md#best-practices-section) pour plus d'informations.
- Importer à partir de la date : Spécifier la date des données les plus anciennes à récupérer. Laisser le champ vide pour tout importer.

![Création de flux CSV : test préalable du CSV mapper](../assets/csv-feeds-creation-prior-test.png)

Dans CSV Mappers, si vous avez créé un représentant pour Marking definition, vous pouviez choisir entre 2 options :

- Laisser l'utilisateur choisir les marking definitions
- Utiliser les marking definitions par défaut de l'utilisateur

Cette configuration s'applique lors de l'utilisation d'un CSV Mapper pour un CSV Ingester. Si vous sélectionnez un CSV Mapper contenant l'option "Utiliser les marking definitions par défaut de l'utilisateur", les marking definitions par défaut de l'utilisateur choisi comme responsable de la création des données seront appliquées à toutes les données importées. Si vous sélectionnez un CSV Mapper contenant l'option "Laisser l'utilisateur choisir les marking definitions", la liste de toutes les marking definitions de l'utilisateur choisi comme responsable de la création des données vous sera présentée (et non les vôtres !)

Pour finaliser la création, cliquer sur "Vérifier" pour lancer une vérification de l'URL soumise avec le CSV mapper sélectionné. Une combinaison URL-CSV mapper valide permet d'identifier jusqu'à 50 entités.

![Création de flux CSV : test du CSV mapper](../assets/csv-feeds-creation-after-test.png)

![Création de flux CSV : liste](../assets/csv-feeds-creation-list.png)

Pour démarrer votre nouvel ingesteur, cliquer sur "Démarrer" dans le menu burger.

![Création de flux CSV : démarrer](../assets/csv-feeds-creation-start.png)

L'ingestion de flux CSV est rendue possible grâce au connector "ImportCSV". Il est donc possible de suivre la progression dans "Données > Ingestion > Connectors". L'ingestion est mise à jour régulièrement lorsque de nouvelles données sont ajoutées au flux CSV.

![Création de flux CSV : connectors](../assets/csv-feeds-connectors.png)

![Création de flux CSV : suivi](../assets/csv-feeds-importCSV-connector-tracking.png)

## Dupliquer un ingesteur de flux CSV

Si vous devez modifier une configuration précédente déjà activée, il est recommandé de dupliquer le flux CSV en utilisant l'option de duplication dans le bouton burger.

![Flux CSV dupliquer : dupliquer](../assets/csv-feeds-burger-button.png)

Comme vous le voyez, lors de la duplication du flux CSV, les champs sont pré-remplis mais il est possible de les modifier. Il est conseillé de conserver le nom avec '-copy' pour signifier l'origine du flux dupliqué.

![Formulaire de duplication de flux CSV : dupliquer](../assets/csv-feeds-duplicate.png)

Comme vu précédemment, il est nécessaire de vérifier la configuration CSV avant de valider le formulaire. Enfin, cliquer sur démarrer pour lancer le nouvel ingesteur.

![Formulaire de duplication de flux CSV : dupliquer](../assets/feeds-start-duplicate.png)


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.