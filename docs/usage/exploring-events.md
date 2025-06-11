# Événements

En cliquant sur "Événements" dans la barre latérale gauche, vous accédez à tous les onglets "Événements", visibles sur la barre supérieure à gauche. Par défaut, l'utilisateur accède directement à l'onglet "Incidents", mais peut également naviguer vers les autres onglets.

Depuis la section `Events`, les utilisateurs peuvent accéder aux onglets suivants :

- `Incidents` : Dans OpenCTI, les `Incidents` correspondent à un événement négatif survenant sur un système d'information. Cela peut inclure une cyberattaque (intrusion, phishing, etc.), une alerte de sécurité consolidée générée par un SIEM ou un EDR qui doit être qualifiée, etc. Cela peut aussi faire référence à une attaque de guerre informationnelle dans le contexte de la lutte contre la désinformation.
- `Sightings` : Les `Sightings` correspondent à l'événement dans lequel un `Observable` (IP, nom de domaine, certificat, etc.) est détecté par ou au sein d'un système d'information, d'un individu ou d'une organisation. Le plus souvent, cela correspond à un événement de sécurité transmis par un SIEM ou un EDR.
- `Observed Data` : `Observed Data` a été ajouté dans OpenCTI pour se conformer au standard STIX 2.1. Il s'agit d'un pseudo-container qui contient des Observables, comme une ligne de log de pare-feu par exemple. Actuellement, il est rarement utilisé.

## Incidents

### Présentation générale

Les incidents représentent généralement des événements négatifs impactant les ressources que vous souhaitez protéger, mais les définitions locales peuvent beaucoup varier, allant d'un simple événement de sécurité envoyé par un SIEM à une attaque à grande échelle sur la chaîne d'approvisionnement impactant tout un secteur d'activité.

Dans MITRE STIX 2.1, le SDO `Incident` n'a pas encore été finalisé et fait l'objet de travaux importants dans le cadre d'une future extension STIX.

En cliquant sur l'onglet Incidents en haut à gauche, vous voyez la liste de tous les Incidents auxquels vous avez accès, conformément à vos [définitions de marquage autorisées](../administration/users.md).

![Incidents list](assets/incidents_list_view.png)

### Visualiser la connaissance associée à un Incident

En cliquant sur un `Incident` dans la liste, vous arrivez sur son onglet Vue d'ensemble. Pour un Incident, les onglets suivants sont accessibles :

- Vue d'ensemble : comme décrit [ici](overview.md#overview-section), avec la particularité d'afficher deux graphiques de distribution de ses Entités (STIX SDO) et Observables (STIX SCO) associés.
- Connaissance : un onglet complexe qui regroupe toute la connaissance structurée liée à l'Incident. Différentes vues thématiques sont proposées pour visualiser facilement la victimologie, l'arsenal, les techniques, etc. utilisées dans le contexte de l'Incident. Comme décrit [ici](overview.md#knowledge-section).
- Contenu : cet onglet spécifique permet de prévisualiser, gérer et rédiger les livrables associés à l'Incident. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md#analyses-section).
- Données : comme décrit [ici](overview.md#data-section).
- Historique : comme décrit [ici](overview.md#history-section).

![Incident overview](assets/incident_overview.png)

## Sightings

### Présentation générale

Les `Sightings` correspondent à des événements dans lesquels un `Observable` (IP, nom de domaine, url, etc.) est détecté par ou au sein d'un système d'information, d'un individu ou d'une organisation. Le plus souvent, cela correspond à un événement de sécurité transmis par un SIEM ou un EDR.

Dans OpenCTI, comme nous sommes dans un contexte de cybersécurité, les `Sightings` sont associés à des `Indicators` de compromission (IoC) et à la notion de "Vrai positif" et "Faux positif".

Il est important de noter que les Sightings sont un type de relation (et non un STIX SDO ou STIX SCO), entre un Observable et des Entités ou des Localisations.

En cliquant sur l'onglet Sightings en haut à gauche, vous voyez la liste de tous les Sightings auxquels vous avez accès, conformément à vos [définitions de marquage autorisées](../administration/users.md).

![Sightings list](assets/sightings_list.png)

### Visualiser la connaissance associée à un Sighting

En cliquant sur un `Sighting` dans la liste, vous arrivez sur son onglet Vue d'ensemble. Comme pour les autres relations dans la plateforme, la vue d'ensemble d'un Sighting affiche les métadonnées communes associées, les containers, les références externes, les notes et les entités liées par la relation.

De plus, cette vue d'ensemble affiche :
- Qualification : si le Sighting est un Vrai positif ou un Faux positif
- Compte : nombre de fois où l'événement a été observé

## Observed Data

### Présentation générale

`Observed Data` correspond à un extrait de log contenant des Observables.

Dans MITRE STIX 2.1, le SDO `Observed Data` est défini comme suit :

> Observed Data conveys information about cybersecurity related entities such as files, systems, and networks using the STIX Cyber-observable Objects (SCOs). For example, Observed Data can capture information about an IP address, a network connection, a file, or a registry key. Observed Data is not an intelligence assertion, it is simply the raw information without any context for what it means.

En cliquant sur l'onglet `Observed Data` en haut à gauche, vous voyez la liste de tous les `Observed Data` auxquels vous avez accès, conformément à vos [définitions de marquage autorisées](../administration/users.md).

### Visualiser la connaissance associée à un Observed Data

En cliquant sur un `Observed Data` dans la liste, vous arrivez sur son onglet Vue d'ensemble. Les onglets suivants sont accessibles :

- Vue d'ensemble : comme décrit [ici](overview.md#overview-section), avec la particularité d'afficher un graphique de distribution de ses Observables (STIX SCO) associés.
- Entités : une liste triable et filtrable de toutes les Entités (SDO)
- Observables : une liste triable et filtrable de tous les Observables (SCO) en relation avec l'Observed Data
- Données : comme décrit [ici](overview.md#data-section).
- Historique : comme décrit [ici](overview.md#history-section).


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.