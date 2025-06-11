# Flux internes

Les flux Live Streams permettent aux utilisateurs de consommer des données provenant d'une autre plateforme OpenCTI, favorisant ainsi le partage collaboratif de renseignements.

<a id="best-practices-section"></a>
## Bonnes pratiques

Dans OpenCTI, la section "Data > Ingestion" offre aux utilisateurs des fonctions intégrées pour l'importation automatisée de données. Ces fonctions sont conçues pour des usages spécifiques et peuvent être configurées afin d'ingérer les données de manière transparente dans la plateforme. Nous allons ici explorer le processus de configuration des cinq fonctions intégrées : Live Streams, TAXII Feeds, TAXII Push, RSS Feeds et CSV/JSON Feeds.

Assurer un environnement sécurisé et bien organisé est primordial dans OpenCTI. Voici deux bonnes pratiques recommandées pour renforcer la sécurité, la traçabilité et la clarté organisationnelle :

1. Créer un utilisateur dédié pour chaque source : Générer un utilisateur spécifiquement pour l'import de flux, en suivant la convention `[F] Nom de la source` pour une identification claire. Assigner cet utilisateur au groupe "Connectors" afin de faciliter la gestion des utilisateurs et des droits liés à la création de données. Veuillez [voir ici](../../deployment/connectors.md#connector-token-section) pour plus d'informations sur cette bonne pratique.
2. Créer une Organisation dédiée pour la source : Créer une organisation portant le nom de la source de données pour une identification claire. Assigner la nouvelle organisation au champ "Default author" dans la configuration de l'import de flux si disponible.

En respectant ces bonnes pratiques, il est possible de garantir l'indépendance dans la gestion des droits pour chaque source d'import via des structures d'utilisateur et d'organisation dédiées. De plus, cela permet une traçabilité claire du créateur de l'entité, facilitant l'évaluation des sources, la création de tableaux de bord, le filtrage des données et d'autres tâches administratives.

## Configuration

Les flux Live Streams permettent aux utilisateurs de consommer des données provenant d'une autre plateforme OpenCTI, favorisant ainsi le partage collaboratif de renseignements. Voici un guide étape par étape pour configurer le synchroniseur de Live streams :

1. URL OpenCTI distante : Indiquer l'URL de la plateforme OpenCTI distante (par exemple, `https://[domain]`; ne pas inclure le chemin).
2. Jeton OpenCTI distant : Fournir le jeton utilisateur. Un administrateur de la plateforme distante doit fournir ce jeton, et l'utilisateur associé doit disposer du privilège "Access data sharing".
3. Après avoir renseigné l'URL et le jeton utilisateur, valider la configuration.
4. Une fois validée, sélectionner un flux live auquel vous avez accès.

![Live stream configuration](../assets/live-stream-configuration.png)

Options de configuration supplémentaires :

- Utilisateur responsable de la création des données : Définir l'utilisateur responsable de la création des données reçues depuis ce flux. La bonne pratique consiste à dédier un utilisateur par source pour une meilleure clarté organisationnelle. Veuillez [voir la section "Bonnes pratiques" ci-dessous](import-automated.md#best-practices-section) pour plus d'informations.
- Démarrer la synchronisation : Spécifier la date des données les plus anciennes à récupérer. Laisser le champ vide pour tout importer.
- Prendre en compte les suppressions : Activer cette option pour supprimer les données de votre plateforme si elles ont été supprimées sur le flux source. (Remarque : les données ne seront pas supprimées si une autre source les a déjà importées.)
- Vérifier le certificat SSL : Vérifier la validité du certificat du domaine hébergeant la plateforme distante.
- Éviter la résolution des dépendances : Importer uniquement les entités sans leurs relations. Par exemple, si le flux partage un malware, toutes les relations du malware seront récupérées par défaut. Cette option permet de choisir de ne pas les récupérer.
- Utiliser la synchronisation parfaite : Cette option est spécifiquement destinée à la synchronisation de deux plateformes. Si une entité importée existe déjà sur la plateforme, celle provenant du flux l'écrasera.

![Live stream additional configuration](../assets/live-stream-additional-configuration.png)

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.