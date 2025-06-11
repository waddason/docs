# Modèle de données

## Introduction

La conception principale d’OpenCTI repose sur le concept de [knowledge graph](https://en.wikipedia.org/wiki/Knowledge_graph), où il existe deux types d’objets différents :

1. **Nœuds** utilisés pour décrire des `entities`, qui possèdent des `properties` ou `attributes`.
2. **Arêtes** utilisées pour décrire des `relationships`, créées entre deux nœuds `entity` et possédant également des `properties` ou `attributes`.

!!! note "Exemple"
    
    Un exemple serait que l’entity `APT28` possède une relationship `uses` vers l’entity malware `Drovorub`.

## Standard

<a id="stix-model-section"></a>
### Le modèle STIX

Pour permettre une approche unifiée dans la description des connaissances en threat intelligence ainsi que pour l’import et l’export de données, le modèle de données OpenCTI est basé sur le [standard STIX 2.1](https://docs.oasis-open.org/cti/stix/v2.1/stix-v2.1.html). Il est donc fortement recommandé de consulter le [STIX Introductory Walkthrough](https://oasis-open.github.io/cti-documentation/stix/walkthrough) ainsi que les [différents types de relationships STIX](https://oasis-open.github.io/cti-documentation/examples/visualized-sdo-relationships) pour mieux comprendre le fonctionnement d’OpenCTI.

Quelques abréviations importantes de STIX :

- **STIX Domain Objects (SDO)** : Attack Patterns, Malware, Threat Actors, etc.
- **STIX Cyber Observable (SCO)** : IP Addresses, domain names, hashes, etc.
- **STIX Relationship Object (SRO)** : Relationships, Sightings

![STIX meta model](assets/stix.png)

### Extensions

Dans certains cas, le modèle a été étendu afin de :

* Prendre en charge davantage de types de SCOs pour modéliser des systèmes d’information tels que des portefeuilles de cryptomonnaie, user agents, etc.
* Prendre en charge davantage de types de SDOs pour modéliser la désinformation et la cybercriminalité, tels que channels, events, narrative, etc.
* Prendre en charge davantage de types de SROs pour étendre les nouveaux SDOs, tels que `amplifies`, `publishes`, etc.

## Implémentation dans la plateforme

### Diagramme des types

Vous trouverez ci-dessous le diagramme de tous les types d’entities et de relationships disponibles dans OpenCTI.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Ffile%2FSrp4IQ9xAnzaS043epUZuJ%2FOpenCTI---Models%3Ftype%3Dwhiteboard%26node-id%3D0%253A1%26t%3DDeOZVWsFdJ13c05f-1" allowfullscreen></iframe>

### Attributs et propriétés

Pour obtenir une liste complète des propriétés disponibles pour un type donné d’entity ou de relationship, utiliser le schéma GraphQL playground disponible dans "Profile > Playground". Ensuite, cliquer sur le bouton Documentation à gauche. Par exemple, rechercher le mot-clé `IntrusionSet` :

![STIX meta model](assets/schema.png)

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.