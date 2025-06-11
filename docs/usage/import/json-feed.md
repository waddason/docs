# Flux JSON

L'ingesteur de flux JSON permet aux utilisateurs d'importer n'importe quelle API web JSON.

<a id="best-practices-section"></a>
## Bonnes pratiques

Dans OpenCTI, la section "Data > Ingestion" fournit aux utilisateurs des fonctions intégrées pour l'importation automatisée de données. Ces fonctions sont conçues pour des usages spécifiques et peuvent être configurées pour ingérer les données de manière transparente dans la plateforme. Nous allons explorer ici le processus de configuration des cinq fonctions intégrées : Live Streams, TAXII Feeds, TAXII Push, RSS Feeds et JSON/CSV Feeds.

Assurer un environnement sécurisé et bien organisé est primordial dans OpenCTI. Voici deux bonnes pratiques recommandées pour renforcer la sécurité, la traçabilité et la clarté organisationnelle :

1. Créer un utilisateur dédié pour chaque source : Générer un utilisateur spécifiquement pour l'import de flux, en suivant la convention `[F] Nom de la source` pour une identification claire. Assigner l'utilisateur au groupe "Connectors" afin de faciliter la gestion des utilisateurs et des permissions liées à la création de données. Veuillez [voir ici](../../deployment/connectors.md#connector-token-section) pour plus d'informations sur cette bonne pratique.
2. Créer une Organisation dédiée pour la source : Créer une organisation nommée d'après la source de données pour une identification claire. Assigner la nouvelle organisation au champ "Default author" dans la configuration d'import de flux si disponible.

En respectant ces bonnes pratiques, il est possible de gérer de façon indépendante les droits pour chaque source d'import via des structures d'utilisateur et d'organisation dédiées. De plus, cela permet une traçabilité claire du créateur de l'entité, facilitant l'évaluation de la source, la création de tableaux de bord, le filtrage des données et d'autres tâches administratives.

## Configuration

La configuration d'un flux JSON sera simple ou complexe selon les besoins de pagination.
Nous allons donc illustrer par exemple ses différentes possibilités et comment les configurer dans les deux cas.

### API simple

Voici un guide étape par étape pour configurer les ingesteurs JSON :

1. Période de planification : Comme l'API n'est pas paginée, il est recommandé de configurer une période d'interrogation plus longue.
2. URL HTTP JSON : Fournir l'URL de l'API JSON à partir de laquelle les éléments seront importés.
3. Verbe HTTP : Indiquer le type de verbe, qui sera GET par défaut.
4. Mappers JSON : Choisir le mapper JSON à utiliser pour importer les données.
5. Type d'authentification (si nécessaire) : Saisir le type d'authentification.

### API paginée

Pour une API paginée, la configuration du flux JSON est plus complexe. Il y a plus d'éléments à prendre en compte.

#### Verbe et variables

Il faut commencer par configurer le verbe à utiliser et les variables.

**GET**

Lorsque vous utilisez une API GET, dans la majorité des cas, des paramètres de requête sont utilisés pour définir les variables de pagination.
Par exemple, prenons une API où la commande GET doit spécifier le numéro de page à consommer.
Une partie de l'URI doit donc être dynamique.

```https://services.nvd.nist.gov/rest/json/cves/2.0?resultsPerPage=20&startIndex=$offset```

Dans cet exemple, le paramètre de requête page doit être associé à la pagination.

Pour cela, il faut configurer ce paramètre comme une variable, ici **${offset}**

**POST**

Lorsque vous utilisez une API POST, il faut spécifier le corps de la requête. Selon l'API, il peut s'agir de JSON ou de tout autre contenu.

Comme dans l'exemple précédent avec GET, il est possible de spécifier des variables dans la configuration du corps.

``` { "page": "$offset" }```

ou par exemple cette commande pour une requête Trino qui définit une variable $created.

```SELECT * FROM observables WHERE created_at > TIMESTAMP '$created' ORDER BY created_at ASC LIMIT 10```

#### Attributs de requête

L'attribut de requête sera la définition de la façon de configurer la variable requise.

Prenons l'exemple précédent avec l'URI GET.

```https://services.nvd.nist.gov/rest/json/cves/2.0?resultsPerPage=20&startIndex=$offset```

Pour l'URI de l'exemple GET, il faut configurer la variable **offset**.

![Panneau d'import de données et workbenches](../assets/json-feed-paginated.png)
Décrivons chaque configuration :
- Résoudre à partir de : **Data**

D'où la variable sera extraite. Il est possible de choisir entre Header et Data.

- Attribut exposé à : **Query parameter**

Comment l'attribut sera exposé lors du prochain appel HTTP. Il est possible de choisir entre Body / Query parameter et Header.

- Opération de résolution : **Count**

Appliquer une opération sur les données résolues. Il est possible de choisir entre Data et Count.

- Opération d'état : **Sum**

Comment calculer l'état pour la prochaine exécution. Il est possible de choisir entre Replace et Sum.

- Extraire depuis le chemin : **$.vulnerabilities**

Comment extraire les données du résultat.

- Nom de l'attribut cible : **offset**

Le nom de l'attribut qui contiendra la valeur et donc **à utiliser dans la requête / le corps ou les headers**

- Valeur par défaut : **0**

La valeur par défaut pour l'attribut cible.

#### En-têtes

Si votre API nécessite des en-têtes spécifiques, il suffit de les ajouter.

![En-têtes du flux JSON](../assets/json-feed-headers.png)

#### Sous-pagination

Cette option très spécifique sera utilisée dans de rares cas. Par exemple, Trino est un système qui nécessite une sous-pagination pour obtenir les données.

![Option de sous-pagination JSON](../assets/json-feed-sub.png)

#### Mapper et vérification

Avec le bon mapper configuré, il est possible de cliquer sur le bouton de vérification pour avoir un aperçu du résultat.

![Vérification du flux JSON](../assets/json-feed-verify.png)

Dans le résultat, il sera possible de voir le résultat du calcul des paramètres de requête (state) et les données mappées en STIX (objects).

L'état est un objet JSON qui représente les informations qui seront injectées dans les paramètres / le corps ou les headers pour la prochaine exécution.

Il est important de prendre le temps d'adapter la configuration pour obtenir le mapping attendu.


> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.