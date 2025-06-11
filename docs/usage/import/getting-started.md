# Importation automatisée

Les utilisateurs peuvent rationaliser le processus d’ingestion de données grâce à diverses fonctionnalités d’importation automatisée. Chaque méthode s’avère bénéfique dans des circonstances spécifiques.

- [Connectors](external-connectors.md) servent de passerelles pour récupérer des données depuis différentes sources et les formater pour une ingestion transparente dans OpenCTI.
- [Streams enable](internal-streams.md) le partage collaboratif d’intelligence entre instances OpenCTI, favorisant les mises à jour en temps réel et une synchronisation efficace des données.
- [TAXII Feeds](taxii-feed.md) offrent un mécanisme standardisé pour ingérer des données de cybermenaces depuis des serveurs TAXII ou d’autres instances OpenCTI.
- [TAXII Push](taxii-push.md) fournit un mécanisme standardisé pour ingérer des données d’intelligence au format STIX 2.1 en poussant les données dans des collections TAXII dédiées exposées par OpenCTI.
- [RSS Feeds](rss-feed.md) facilitent l’importation d’éléments sous forme de rapports à partir de flux RSS spécifiés, offrant un moyen simple de rester informé sur l’intelligence pertinente.
- [CSV Feeds](csv-feed.md) facilitent l’ingestion de données exposées sous forme de fichiers CSV, offrant un moyen simple d’ingérer tout flux CSV.
- [JSON Feeds](json-feed.md) facilitent l’ingestion de données exposées au format JSON, offrant un moyen simple d’ingérer tout flux JSON.

En tirant parti de ces fonctionnalités d’importation automatisée, les utilisateurs d’OpenCTI peuvent constituer une base de données de cybermenaces complète et à jour. L’adaptabilité de la plateforme et ses options de configuration conviviales garantissent des workflows d’intelligence agiles, évolutifs et adaptés aux besoins uniques de chaque organisation.

## Comportements des connectors

Le comportement de chaque connector est défini par son développement, déterminant les types de données importées et ses options de configuration. Cette flexibilité permet aux utilisateurs de personnaliser le processus d’importation selon leurs besoins spécifiques, assurant une intégration de données fluide et personnalisée.
Le niveau de granularité de configuration concernant le type de données importées varie selon chaque connector. Néanmoins, les connectors permettent aux utilisateurs de spécifier la date à partir de laquelle ils souhaitent récupérer les données. Cette capacité est particulièrement utile lors de l’activation initiale d’un connector, permettant la récupération de données historiques. Par la suite, le connector fonctionne en temps réel, important continuellement les nouvelles données depuis la source.

## Comportements d’importation Stream / Push / Feed

Un gestionnaire d’ingestion s’exécute périodiquement en arrière-plan, et pour chaque feed actif :
- récupère les nouvelles données depuis la source. Lorsque les données sont paginées, récupère la page suivante
- compose un bundle stix pour les données et l’envoie dans la file d’attente pour traitement par les workers

!!! Note sur la chronologie de l’ingestion de données depuis un Taxii feed, CSV feed, JSON feed et RSS feed.

    Selon la charge des workers, un délai peut exister entre la récupération des données depuis la source et leur visibilité sur la plateforme.

L’intervalle de périodicité est configuré avec le gestionnaire via `ingestion_manager:interval`.
Un feed peut être configuré pour planifier la récupération des données sur une période plus longue.

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.