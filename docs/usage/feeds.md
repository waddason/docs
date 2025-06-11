# Flux natifs

OpenCTI propose des mécanismes polyvalents pour le partage de données via ses flux intégrés, notamment les flux en direct (Live streams), les collections TAXII et les flux CSV.

## Configuration des flux

Les flux sont configurés dans la fenêtre "Données > Partage de données". La configuration de tous les types de flux est uniforme et repose sur les paramètres suivants :

- Configuration des filtres : le flux peut avoir des filtres spécifiques pour ne publier qu'un sous-ensemble des connaissances globales de la plateforme. Toutes les données répondant aux critères définis par les filtres du flux de l'utilisateur seront partagées (par exemple, types spécifiques d'entités, labels, définitions de marquage, etc.).
- Contrôle d'accès : un flux peut être public, c'est-à-dire accessible sans authentification, ou restreint. Par défaut, il est accessible à tout utilisateur disposant de la capacité "Accès au partage de données", mais il est possible d'augmenter les restrictions en limitant l'accès à un utilisateur, un groupe ou une organisation spécifique.

![Feed access restriction](assets/feed-access-restriction.png)

En configurant soigneusement les filtres et les contrôles d'accès, il est possible d'adapter le comportement des flux en direct, des collections TAXII et des flux CSV à vos besoins spécifiques de partage de données.

<a id="live-stream-section"></a>
## Flux en direct (Live streams)

### Introduction

Les flux en direct, une fonctionnalité exclusive d'OpenCTI, augmentent la capacité de partage de données en temps réel en servant des bundles STIX 2.1 sous forme de collections TAXII avec des capacités avancées. Ce qui les distingue, c'est leur nature dynamique, incluant la création, la mise à jour et la suppression de données. Contrairement à TAXII, les flux en direct résolvent de manière exhaustive les relations et dépendances, assurant un échange d'informations plus nuancé et interconnecté. Ceci est particulièrement bénéfique dans les scénarios où le partage implique des entités avec des relations complexes, fournissant un contexte enrichi pour les données partagées.

Dans les scénarios de partage de données entre deux plateformes OpenCTI, les flux en direct sont le mécanisme privilégié. Ces flux fonctionnent comme des collections TAXII mais sont nettement améliorés, prenant en charge :

* les événements de création, mise à jour et suppression selon les paramètres,
* la mise en cache des entités créées dans les 5 dernières minutes,
* la résolution des relations et dépendances même hors des filtres,
* la possibilité d'être publics (sans authentification).

![Live stream](assets/live-stream.png)

!!! avertissement "Résolution des relations et dépendances"

  Les dépendances et relations des entités partagées via les flux en direct, telles que déterminées par les filtres spécifiés, sont automatiquement partagées même au-delà de ces filtres. Cela signifie que des données interconnectées, qui ne répondent pas directement aux critères des filtres, sont tout de même incluses dans le flux en direct. Cependant, les mécanismes de ségrégation des données d'OpenCTI sont toujours appliqués. Ils permettent de restreindre l'accès aux données partagées en fonction de critères tels que les marquages ou l'organisation. Il est impératif de configurer et de gérer soigneusement ces contrôles d'accès pour garantir qu'aucune donnée confidentielle ne soit partagée.

### Scénario illustratif

Pour mieux comprendre le fonctionnement des flux en direct, voici quelques exemples, du plus simple au plus complexe.

Étant donné un flux en direct avec les filtres *Type d'entité : Indicator* `ET` *Label : detection*. Voyons ce qui se passe avec un indicator ayant :

* Définition de marquage : `TLP:GREEN`
* Auteur `Crowdstrike`
* Relation `indicates` vers le malware `Emotet`

| Action                          | Résultat dans le flux (avec `Eviter la résolution des dépendances=true`)   | Résultat dans le flux (avec `Eviter la résolution des dépendances=false`)                                                                    |
|:--------------------------------|:----------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------|
| 1. Créer un indicator           | Rien                                                                         | Rien                                                                                                                                        |
| 2. Ajouter le label `detection` | Créer `TLP:GREEN`, créer `CrowdStrike`, créer l'indicator                   | Créer `TLP:GREEN`, créer `CrowdStrike`, créer le malware `Emotet`, créer l'indicator, créer la relation `indicates`                         |
| 3. Retirer le label `detection` | Supprimer l'indicator                                                        | Supprimer l'indicator et la relation                                                                                                         |
| 4. Ajouter le label `detection` | Créer l'indicator                                                            | Créer l'indicator, créer la relation `indicates`                                                                                             |
| 5. Supprimer l'indicator        | Supprimer l'indicator                                                        | Supprimer l'indicator et la relation                                                                                                         |

Pour plus de détails sur la consommation de ces flux en direct, consulter [la page dédiée](import-automated.md).


## Collections TAXII

OpenCTI dispose d'un point de terminaison TAXII intégré qui fournit des bundles STIX 2.1 valides. Pour en savoir plus sur la norme TAXII, [lire l'introduction officielle](https://oasis-open.github.io/cti-documentation/taxii/intro.html).

Dans OpenCTI, il est possible de créer autant de collections TAXII 2.1 que nécessaire.

![TAXII Collection](assets/taxii-collection.png)

Après la création d'une nouvelle collection, tout système disposant d'un jeton d'accès approprié peut consommer la collection en utilisant différents types d'authentification (basic, bearer, etc.).

Comme pour l'utilisation de l'API GraphQL, les collections TAXII 2.1 disposent d'un système classique de pagination qui doit être géré côté consommateur. Il est également important de comprendre que les dépendances d'éléments (IDs imbriqués) à l'intérieur de la collection ne sont pas toujours contenues/résolues dans le bundle, la cohérence devant donc être gérée côté client.

<a id="csv-feeds-section"></a>
## Flux CSV

### Introduction

Le flux CSV permet la génération automatique d'un fichier CSV, accessible via une URL.
Le fichier CSV est régénéré et mis à jour à des intervalles définis par l'utilisateur, offrant ainsi de la flexibilité.
Les entrées du fichier correspondent aux informations qui correspondent aux filtres appliqués et qui ont été créées ou modifiées sur la plateforme pendant l'intervalle de temps (entre la dernière génération du CSV et la nouvelle).

![CSV feed](assets/csv-feed.png)

### Rolling Time & Base Attribute

La valeur *Rolling Time* (exprimée en minutes) détermine la période sur laquelle OpenCTI doit rechercher les données correspondant à vos filtres depuis le dernier fetch. La valeur *Base Attribute* détermine si OpenCTI doit rechercher les données <ins>créées</ins> pendant la période *Rolling Time*, ou les données <ins>mises à jour</ins> pendant cette période.

### Duplication
Pour configurer facilement un nouveau flux CSV, il est possible de partir d'une configuration de flux existante et de la dupliquer.
L'action "dupliquer" est accessible depuis le menu burger du flux.

![CSV feed duplication button](assets/feeds-duplicate.png)

Lors de la duplication du flux CSV, tous les champs sont copiés dans le formulaire de création et peuvent être modifiés.
Le nouveau flux porte le suffixe "-copy" dans son nom.

![CSV feed duplication form](assets/feeds-duplication-form.png)


### Limite de taille du CSV

Les données CSV générées à partir d'un flux CSV ont une limite de 5 000 entrées par défaut.
Si plus de 5 000 entités sont récupérées par la plateforme, seules les 5 000 plus récentes seront partagées dans le fichier.
  
Il est possible de modifier cette limite en définissant la variable d'environnement correspondante :

```
DATA_SHARING__MAX_CSV_FEED_RESULT=10000
```

Ou dans le fichier de configuration de la plateforme :

```
"data_sharing": {
  "max_csv_feed_result": 10000
},
```

!!! avertissement "Considérations de performance"

  Modifier la limite de taille peut entraîner une dégradation des performances selon votre plateforme et la configuration de votre flux CSV.
  Tester correctement votre installation et aligner ce nombre avec la capacité de votre plateforme pour éviter tout problème.

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.