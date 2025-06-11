# Déduplication

L’un des concepts fondamentaux du graphe de connaissances OpenCTI est l’ensemble des mécanismes sous-jacents mis en œuvre pour dédupliquer et consolider (aussi appelé `upserting`) avec précision les informations concernant les entités et les relations.

## Comportement lors de la création

Lorsqu’un objet est créé sur la plateforme, que ce soit manuellement par un utilisateur ou automatiquement par la chaîne de connectors / workers, la plateforme vérifie si un objet similaire existe déjà en se basant sur certaines propriétés de l’objet. Si l’objet existe déjà, il sera retourné et, dans certains cas, mis à jour.

Techniquement, OpenCTI génère des identifiants déterministes à partir des propriétés listées ci-dessous afin d’éviter les doublons (appelées "propriétés contribuant à l’ID"). Il est également important de noter qu’il existe un lien particulier entre `name` et `aliases` qui empêche d’avoir des entités avec des alias qui se chevauchent ou un alias déjà utilisé comme nom d’une autre entité.

### Entités

| Type                    | Attributs                                                    |
| :---------------------- |:------------------------------------------------------------|
| Area                    | (`name` OU `x_opencti_alias`) ET `x_opencti_location_type`   |
| Attack Pattern          | (`name` OU `alias`) ET `x_mitre_id` optionnel                |
| Campaign                | `name` OU `alias`                                            |
| Channel                 | `name` OU `alias`                                            |
| City                    | (`name` OU `x_opencti_alias`) ET `x_opencti_location_type`   |
| Country                 | (`name` OU `x_opencti_alias`) ET `x_opencti_location_type`   |
| Course Of Action        | (`name` OU `alias`) ET `x_mitre_id` optionnel                |
| Data Component          | `name` OU `alias`                                            |
| Data Source             | `name` OU `alias`                                            |
| Event                   | `name` OU `alias`                                            |
| Feedback Case           | `name` ET `created` (date)                                   |
| Grouping                | `name` ET `context`                                          |
| Incident                | `name` OU `alias`                                            |
| Incident Response Case  | `name` OU `alias`                                            |
| Indicator               | `pattern` OU `alias`                                         |
| Individual              | (`name` OU `x_opencti_alias`) ET `identity_class`            |
| Infrastructure          | `name` OU `alias`                                            |
| Intrusion Set           | `name` OU `alias`                                            |
| Language                | `name` OU `alias`                                            |
| Malware                 | `name` OU `alias`                                            |
| Malware Analysis        | `name` OU `alias`                                            |
| Narrative               | `name` OU `alias`                                            |
| Note                    | *Aucun*                                                      |
| Observed Data           | `name` OU `alias`                                            |
| Opinion                 | *Aucun*                                                      |
| Organization            | (`name` OU `x_opencti_alias`) ET `identity_class`            |
| Position                | (`name` OU `x_opencti_alias`) ET `x_opencti_location_type`   |
| Region                  | `name` OU `alias`                                            |
| Report                  | `name` ET `published` (date)                                 |
| RFI Case                | `name` ET `created` (date)                                   |
| RFT Case                | `name` ET `created` (date)                                   |
| Sector                  | (`name` OU `alias`) ET `identity_class`                      |
| Task                    | *Aucun*                                                      |
| Threat Actor            | `name` OU `alias`                                            |
| Tool                    | `name` OU `alias`                                            |
| Vulnerability           | `name` OU `alias`                                            |

!!! info "Gestion des noms et des alias"
    
    Le nom et les alias d’une entité définissent un ensemble de valeurs uniques, il n’est donc pas possible d’avoir un nom égal à un alias et inversement.

### Relations

Le processus de déduplication des relations est basé sur les critères suivants :

* Type
* Source
* Cible
* Date de début comprise entre -30 jours / +30 jours
* Date de fin comprise entre -30 jours / +30 jours

### Observables

Pour les STIX Cyber Observables, OpenCTI génère également des identifiants déterministes selon la [spécification STIX](https://docs.oasis-open.org/cti/stix/v2.1/csprd01/stix-v2.1-csprd01.html#_Toc16070607) en utilisant les "propriétés contribuant à l’ID" définies pour chaque type d’observable.

## Comportement lors de la mise à jour

Dans les cas où une entité existe déjà sur la plateforme, les créations entrantes peuvent déclencher la mise à jour des attributs de l’entité existante.
Cette logique a été mise en œuvre pour faire converger la base de connaissances vers les niveaux de confiance et de qualité les plus élevés, tant pour les entités que pour les relations.

Pour comprendre en détail comment fonctionne le mécanisme de déduplication dans le contexte du niveau de confiance maximal, consulter ce diagramme (section déduplication) :

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Ffile%2FlVU6O39B76MJmtnzg9DbZZ%2FConfidence-Level---Documentation%3Ftype%3Dwhiteboard%26node-id%3D0%253A1%26t%3DPQWrdBF6iMGEp0bw-1" allowfullscreen></iframe>

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.