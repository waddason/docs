# Fusionner des objets

## Introduction

La fonctionnalité de fusion d’OpenCTI constitue un outil clé pour optimiser les données de threat intelligence, permettant de consolider plusieurs entités du même type. Ce mécanisme sert d’outil de nettoyage puissant, harmonisant la plateforme et unifiant les informations dispersées. Dans cette section, nous explorons l’importance de cette fonctionnalité, le processus de fusion des entités et les considérations stratégiques à prendre en compte.

<a id="data-streamlining-section"></a>
## Rationalisation des données

Dans le paysage en constante expansion de la threat intelligence et la multitude de noms choisis par différentes sources de données, la propreté des données est essentielle. Les doublons et les informations fragmentées entravent une analyse efficace. La fonctionnalité de fusion est une solution stratégique pour regrouper des entités liées en une unité cohérente. Au cœur du processus de fusion se trouve la sélection d’une entité principale. Cette entité principale devient l’ancre, conservant les attributs essentiels tels que le nom et la description. Les autres entités, tout en perdant certains champs comme les descriptions, sont ajoutées comme alias sous l’entité principale. Cette décision stratégique permet de préserver les données vitales tout en éliminant la redondance.

## Préservation des relations entre entités

L’une des principales caractéristiques de la fonctionnalité de fusion est sa capacité à préserver les relations. Lors de la fusion d’entités, leurs relations interconnectées ne sont pas perdues. Elles sont au contraire intégrées de manière transparente dans la nouvelle entité fusionnée. Cela garantit que le réseau complexe de relations au sein des données reste intact, favorisant une compréhension globale du paysage des menaces.

## Conclusion

La fonctionnalité de fusion d’OpenCTI contribue à améliorer la qualité des données de threat intelligence. En consolidant les entités et en centralisant les relations, OpenCTI permet aux analystes de se concentrer sur les analyses et les stratégies, sans être freinés par des silos de données ou la fragmentation. Cependant, il est essentiel de faire preuve de prudence et d’anticipation lors du processus de fusion, afin de garantir une base de connaissances robuste et rationalisée.

## Ressources supplémentaires

- **Administration :** Pour comprendre comment fusionner des entités et les points d’attention à prendre en compte, consulter la page [Merging](../administration/merging.md) dans la section Administration de la documentation.
- **Mécanisme de déduplication :** la plateforme est équipée de [processus de déduplication](deduplication.md) qui fusionnent automatiquement les données lors de leur création (manuellement ou par importation depuis différentes sources) si certaines conditions sont remplies.


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.