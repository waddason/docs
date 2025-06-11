# Signification des dates

Dans OpenCTI, les entités peuvent contenir différentes dates, chacune représentant un type d'information spécifique. Les dates disponibles varient selon les types d'entités.

## Dates

Dans OpenCTI, les dates jouent un rôle essentiel pour comprendre le contexte et l’historique des entités. Voici un aperçu des différentes dates que vous pouvez rencontrer sur la plateforme :

- « Date de création sur la plateforme » : Cette date indique le moment où l’entité a été créée dans OpenCTI. Côté API, ce timestamp correspond au champ `created_at`. Il reflète l’initiation de l’entité dans l’environnement OpenCTI.
- « Date de création originale » : Cette date reflète la date de création originale de la donnée côté source. Elle est pertinente si la source fournit cette information et si le connector chargé de l’importation la prend en compte. Si la date source n’est pas disponible ou ignorée, cette date prend par défaut la date d’importation (c’est-à-dire la « Date de création sur la plateforme »). Côté API, ce timestamp correspond au champ `created`.
- « Date de modification » : Cette date indique la dernière modification apportée à l’entité, qu’elle soit effectuée automatiquement par un connector ou manuellement par un utilisateur. Côté API, ce timestamp correspond au champ `updated_at`. Elle sert de référence pour suivre les dernières modifications de l’entité.
- Date non affichée dans l’interface graphique : Il existe une date supplémentaire qui n’est pas visible sur l’entité dans l’interface graphique. Cette date correspond au champ `modified` dans l’API. Elle reflète la date de mise à jour originale de la donnée côté source. La différence entre `modified` et `updated_at` est identique à celle entre `created` et `created_at`.

![Dates](assets/dates.png)

Comprendre ces dates est essentiel pour contextualiser les informations dans OpenCTI et garantir une vision complète de l’historique et de l’évolution des entités.

## Types de dates

### Dates techniques

Les dates techniques sont directement liées à la gestion des données dans la plateforme. Les champs API correspondant aux dates techniques sont :

- created_at : Indique la date et l’heure de création de l’entité dans la plateforme.
- updated_at : Représente la date et l’heure de la dernière mise à jour de l’entité dans la plateforme.

### Dates fonctionnelles

Les dates fonctionnelles sont significatives d’un point de vue métier, indiquant souvent des événements ou jalons spécifiques. Les champs API correspondant aux dates fonctionnelles sont :

- created : Désigne la date et l’heure de création de l’entité côté source.
- modified : Représente la date et l’heure de la dernière modification de l’entité côté source.
- start_time : Indique la date et l’heure de début associées à une relation.
- stop_time : Indique la date et l’heure de fin associées à une relation.
- first_seen : Représente la première date et heure où l’entité/l’activité a été observée.
- last_seen : Représente la date et l’heure les plus récentes où l’entité/l’activité a été observée.

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.