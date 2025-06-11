# Gestion du cycle de vie des Indicators

## Introduction

OpenCTI applique des règles strictes pour déterminer la période pendant laquelle un indicator est effectif pour l’utilisation. Cette période est définie par les dates `valid_from` et `valid_until`. Tout au long de son cycle de vie, le `score` de l’indicator diminue selon les [règles de déclin configurées](../administration/decay-rules.md). Après expiration de l’indicator, l’objet est marqué comme `revoked` et le champ `detection` est automatiquement défini à `false`. Ce document explique comment ces dates sont calculées dans la plateforme OpenCTI et comment le score est mis à jour avec les règles de déclin.

## Définir les dates de validité

### La source de données fournit les dates

Si une source de données fournit les dates `valid_from` et `valid_until` lors de la création d’un indicator sur la plateforme, ces dates sont utilisées sans modification. Cependant, si la création est effectuée depuis l’interface utilisateur et que l’indicator est éligible à être géré par une règle de déclin, la plateforme modifiera la valeur de `valid_until` avec celle calculée par la règle de déclin.

### Règles de secours pour les dates non spécifiées

Si une source de données ne fournit pas de dates de validité, OpenCTI applique la règle de déclin correspondant à l’indicator pour déterminer ces dates.
La date `valid_until` est calculée en fonction du score de révocation de la règle de déclin : elle est fixée à l’instant précis où l’indicator atteindra ce score de révocation.
Après la date `valid_until`, l’indicator est marqué comme révoqué.

## Déclin du score

Les indicators ont un score initial à la création, soit fourni par la source de données, soit 50 par défaut.
Au fil du temps, ce score va diminuer selon les règles de déclin configurées.
Le score est mis à jour à chaque point de réaction défini pour la règle de déclin correspondant à l’indicator lors de la création.

## Exemple

Cet indicator d’URL a été associé à la règle de déclin `Built-in IP and URL`. Son score initial à la création est de 100.

![Indicator overview](./assets/indicators-lifecycle-example-overview.png)

Juste à côté du score de l’indicator, il y a un bouton `Lifecycle` qui permet d’ouvrir une boîte de dialogue pour voir les détails du cycle de vie de l’indicator.

![Indicator lifecycle](./assets/indicators-lifecycle-example-dialog.png)

## Conclusion

Comprendre comment OpenCTI calcule les périodes de validité et les scores est essentiel pour une analyse efficace de la cybermenace. Ces règles garantissent que vos indicators sont précis et à jour, fournissant une base fiable pour les données de threat intelligence.



> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.