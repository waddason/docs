# Références et objets imbriqués

## Standard STIX

### Définition

Dans le [standard STIX 2.1](https://docs.oasis-open.org/cti/stix/v2.1/stix-v2.1.html), les objets peuvent :

1. Faire référence à d'autres objets directement dans leurs `attributes`, en référant un ou plusieurs IDs.
2. Avoir d'autres objets directement intégrés dans l'entité.

### Exemple

```json
{
   "type": "intrusion-set",
   "spec_version": "2.1",
   "id": "intrusion-set--4e78f46f-a023-4e5f-bc24-71b3ca22ec29",
   "created_by_ref": "identity--f431f809-377b-45e0-aa1c-6a4751cae5ff", // référence imbriquée vers une identity
   "object_marking_refs": ["marking-definition--34098fce-860f-48ae-8e50-ebd3cc5e41da"], // référence imbriquée vers plusieurs marking definitions
   "external_references": [
      {
         "source_name": "veris",
         "external_id": "0001AA7F-C601-424A-B2B8-BE6C9F5164E7",
         "url": "https://github.com/vz-risk/VCDB/blob/125307638178efddd3ecfe2c267ea434667a4eea/data/json/validated/0001AA7F-C601-424A-B2B8-BE6C9F5164E7.json",    
      }
   ],
   "created": "2016-04-06T20:03:48.000Z",
   "modified": "2016-04-06T20:03:48.000Z",
   "name": "Bobcat Breakin",
   "description": "Incidents usually feature a shared TTP of a bobcat being released within the building containing network access...",
   "aliases": ["Zookeeper"],
   "goals": ["acquisition-theft", "harassment", "damage"]
}
```

Dans l'exemple précédent, il y a 2 références imbriquées vers d'autres objets dans :

```json
"created_by_ref": "identity--f431f809-377b-45e0-aa1c-6a4751cae5ff", // référence imbriquée vers une identity
"object_marking_refs": ["marking-definition--34098fce-860f-48ae-8e50-ebd3cc5e41da"], // référence imbriquée vers plusieurs marking definitions
```

Mais il y a aussi un objet imbriqué dans l'entité (une `External Reference`) :

```json
"external_references": [
   {
      "source_name": "veris",
      "external_id": "0001AA7F-C601-424A-B2B8-BE6C9F5164E7",
      "url": "https://github.com/vz-risk/VCDB/blob/125307638178efddd3ecfe2c267ea434667a4eea/data/json/validated/0001AA7F-C601-424A-B2B8-BE6C9F5164E7.json",    
   }
]
```

## Implémentation

### Modélisation

Dans OpenCTI, toutes les références et objets imbriqués sont modélisés comme des relations, afin de permettre de pivoter plus facilement sur les labels, external references, kill chain phases, marking definitions, etc.

![Investigation](assets/investigation.png)

### Import & export

Lors de l'import et de l'export de données vers/depuis OpenCTI, la traduction entre références et objets imbriqués et des nœuds et arêtes complets est automatisée et donc transparente pour les utilisateurs. Voici un exemple avec l'objet du graphe ci-dessus :

```json
{
   "id": "file--b6be3f04-e50f-5220-af3a-86c2ca66b719",
   "spec_version": "2.1",
   "x_opencti_description": "...",
   "x_opencti_score": 50,
   "hashes": {
       "MD5": "b502233b34256285140676109dcadde7"
   },
   "labels": [
       "cookiecutter",
       "clouddata-networks-1"
   ],
   "external_references": [
       {
           "source_name": "Sekoia.io",
           "url": "https://app.sekoia.io/intelligence/objects/indicator--3e6d61b4-d5f0-48e0-b934-fdbe0d87ab0c"
       }
   ],
   "x_opencti_id": "8a3d108f-908c-4833-8ff4-4d6fc996ce39",
   "type": "file",
   "created_by_ref": "identity--b5b8f9fc-d8bf-5f85-974e-66a7d6f8d4cb",
   "object_marking_refs": [
       "marking-definition--613f2e26-407d-48c7-9eca-b8e91df99dc9"
   ]
}
```

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.