# Bien démarrer

Ce guide vise à fournir une vue d'ensemble complète des fonctionnalités et des workflows d'OpenCTI. La plateforme peut être utilisée dans divers contextes pour gérer des cas d'usage de gestion des menaces, du niveau technique à un niveau plus stratégique. OpenCTI a été conçu comme un graphe de connaissances, prenant en entrée des flux de threat intelligence, des sightings & alerts, des vulnérabilités, des assets, des artifacts, etc., et générant des sorties basées sur des capacités intégrées et/ou des connectors.

Voici quelques exemples de cas d'usage :

* Base de connaissances Cyber Threat Intelligence
* Flux detection as code pour XDR, EDR, SIEMs, firewalls, proxies, etc.
* Gestion des artifacts & cas d'incident response
* Gestion des vulnérabilités
* Reporting, alerting et dashboarding sur un sous-ensemble de données

![Use Cases](assets/use-cases.png)

<a id="dashboard-section"></a>

## Tableau de bord d'accueil

La page d'accueil offre à tout visiteur de la plateforme OpenCTI une vue d'ensemble de l'activité sur la plateforme. Elle peut être remplacée par un [tableau de bord personnalisé](dashboards.md), créé par un utilisateur (ou le tableau de bord par défaut défini dans un rôle, un groupe ou une organisation).

![Dashboard](assets/dashboard.png)

### Indicateurs dans le tableau de bord

#### Chiffres

| Composant      | Description                          |
|:---------------|:-------------------------------------|
| Intrusion sets | Nombre d'intrusion sets.             |
| Malware        | Nombre de malware.                   |
| Reports        | Nombre de reports.                   |
| Indicators     | Nombre d'indicators.                 |

#### Graphiques & listes

| Composant                                   | Description                                                                                                                                         |
|:--------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
| Menaces les plus actives (3 derniers mois)  | Principales menaces actives (threat actor, intrusion set et campaign) durant les 3 derniers mois.                                                   |
| Victimes les plus ciblées (3 derniers mois) | Intensité du ciblage liée au nombre de relations `targets` pour une entité donnée (organization, sector, location, etc.) sur les 3 derniers mois.   |
| Relations créées                            | Volume de relations créées au cours des 12 derniers mois.                                                                                           |
| Malware les plus actifs (3 derniers mois)   | Principaux malware actifs durant les 3 derniers mois.                                                                                               |
| Vulnérabilités les plus actives (3 derniers mois) | Liste des vulnérabilités ayant le plus grand nombre de relations sur les 3 derniers mois.                                                    |
| Pays ciblés (3 derniers mois)               | Intensité du ciblage liée au nombre de relations `targets` pour un pays donné sur les 3 derniers mois.                                              |
| Derniers reports                            | Derniers reports ingérés dans la plateforme.                                                                                                        |
| Labels les plus actifs (3 derniers mois)    | Principaux labels attribués aux entités durant les 3 derniers mois.                                                                                 |

!!! info "Explorer la plateforme"

    Pour commencer à explorer la plateforme et comprendre comment l'information est structurée, il est recommandé de débuter par la [page de documentation d'ensemble](overview.md).


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.