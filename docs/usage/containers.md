# Containers

## Standard STIX

### Définition

Dans le [standard STIX 2.1](https://docs.oasis-open.org/cti/stix/v2.1/stix-v2.1.html), certains STIX Domain Objects (SDO) peuvent être considérés comme des "containers de connaissances", utilisant l’attribut `object_refs` pour référencer plusieurs autres objets comme références imbriquées. Dans `object_refs`, il est possible de référencer des entités et des relations.

### Exemple

```json
{
   "type": "report",
   "spec_version": "2.1",
   "id": "report--84e4d88f-44ea-4bcd-bbf3-b2c1c320bcb3",
   "created_by_ref": "identity--a463ffb3-1bd9-4d94-b02d-74e4f1658283",
   "created": "2015-12-21T19:59:11.000Z",
   "modified": "2015-12-21T19:59:11.000Z",
   "name": "The Black Vine Cyberespionage Group",
   "description": "A simple report with an indicator and campaign",
   "published": "2016-01-20T17:00:00.000Z",
   "report_types": ["campaign"],
   "object_refs": [
      "indicator--26ffb872-1dd9-446e-b6f5-d58527e5b5d2",
      "campaign--83422c77-904c-4dc1-aff5-5c38f3a2c55c",
      "relationship--f82356ae-fe6c-437c-9c24-6b64314ae68a"
   ]
}
```

Dans l’exemple précédent, nous avons une référence imbriquée vers 3 autres objets :

```json
"object_refs": [
   "indicator--26ffb872-1dd9-446e-b6f5-d58527e5b5d2",
   "campaign--83422c77-904c-4dc1-aff5-5c38f3a2c55c",
   "relationship--f82356ae-fe6c-437c-9c24-6b64314ae68a"
]
```

## Implémentation

### Types de container

Dans OpenCTI, les containers sont affichés différemment des autres entités, car ils contiennent des éléments de connaissance. Voici la liste des containers dans la plateforme :

| Type d’entité  | Standard STIX | Description                                                                                                                                                                                 |
|:---------------|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Report         | Natif         | Les reports sont des collections de renseignements sur les menaces axées sur un ou plusieurs sujets, comme la description d’un threat actor, d’un malware ou d’une technique d’attaque, incluant le contexte et les détails associés. |
| Grouping       | Natif         | Un objet Grouping affirme explicitement que les objets STIX référencés partagent un même contexte, contrairement à un STIX Bundle (qui n’apporte aucun contexte explicite).                |
| Observed Data  | Natif         | Observed Data transmet des informations sur des entités liées à la cybersécurité telles que des fichiers, systèmes et réseaux en utilisant les STIX Cyber-observable Objects (SCOs).        |
| Note           | Natif         | Une Note est destinée à transmettre un texte informatif pour fournir un contexte supplémentaire et/ou une analyse additionnelle non contenue dans les objets STIX.                         |
| Opinion        | Natif         | Une Opinion est une évaluation de la justesse des informations contenues dans un objet STIX produit par une autre entité.                                                                  |
| Case           | Extension     | Un case, qu’il s’agisse d’un Incident Response, d’une Request for Information ou d’une Request for Takedown, est utilisé pour transmettre un epic avec un ensemble de tâches.               |
| Task           | Extension     | Un task, généralement utilisé dans le contexte d’un case, est destiné à transmettre des informations sur une action à réaliser dans un délai limité.                                        |

### Comportement des containers

Dans la plateforme, il est toujours possible de visualiser la liste des entités et/ou observables référencés dans un container (`Container > Entities or Observables`), mais aussi d’ajouter / supprimer des entités du container.

![Entities](assets/entities.png)

Comme les containers peuvent aussi contenir des relations, généralement liées aux autres entités du container, il est également possible de visualiser le container sous forme de graphe (`Container > Knowledge`)

![Graph](assets/graph.png)

### Containers d’une entité ou d’une relation

Du côté de l’entité ou de la relation, il est toujours possible de retrouver tous les containers dans lesquels l’objet est contenu en utilisant le menu supérieur `Analysis` :

![Analysis](assets/analysis.png)

Dans la liste de tous les containers, il est aussi possible de filtrer les containers en fonction d’un ou plusieurs objets contenus :

![Container filters](assets/container-filters.png)

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.