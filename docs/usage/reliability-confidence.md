# Fiabilité et Confiance

## Généralités

Dans le domaine de la Cyber Threat Intelligence, l’évaluation des sources d’information et de la qualité des informations est l’un des aspects les plus importants du travail. Il est primordial d’évaluer les situations en tenant compte de la fiabilité des sources et de la crédibilité des informations.

Ce concept est fondamental dans OpenCTI, et a un impact réel sur :

* le [processus de déduplication](deduplication.md) des données
* le filtrage des flux de données pour l’ingestion et le partage

### Qu’est-ce que la fiabilité d’une source ?

La fiabilité d’une source d’information mesure la confiance que l’analyste peut accorder à cette source, en se basant sur ses capacités techniques ou son historique. La source est-elle un partenaire fiable avec un long historique de partage ? Un concurrent ? Inconnue ?

La fiabilité des sources est souvent évaluée au niveau organisationnel, car cela nécessite une vue d’ensemble de tout l’historique avec cette source.

Dans le domaine du renseignement, la fiabilité est souvent notée selon le [code d’Admirauté de l’OTAN](https://fr.wikipedia.org/wiki/Code_d%27admiraut%C3%A9).

### Qu’est-ce que la confiance dans une information ?

La fiabilité d’une source est importante, mais même une source fiable peut se tromper. L’information elle-même possède une crédibilité, basée sur ce qui est connu du sujet et le niveau de corroboration par d’autres sources.

La crédibilité est souvent évaluée au niveau de l’équipe d’analystes, experts du sujet, capables de juger l’information dans son contexte.

Dans le domaine du renseignement, la confiance est souvent notée selon le [code d’Admirauté de l’OTAN](https://fr.wikipedia.org/wiki/Admiralty_code).

!!! info "Pourquoi Confiance au lieu de Crédibilité ?"

    Utiliser à la fois la Fiabilité et la Crédibilité est un cas d’usage avancé pour la plupart des équipes CTI. Cela nécessite une organisation mature et une équipe bien dotée. Pour la majorité des équipes CTI internes, un simple niveau de confiance suffit pour établir une évaluation, en particulier pour les équipes qui se concentrent sur la CTI technique.

    Ainsi, dans OpenCTI, nous avons fait le choix de fusionner la notion de Crédibilité avec le niveau de Confiance couramment utilisé par la majorité des utilisateurs. Ils ont désormais la liberté d’aller plus loin dans leur pratique et d’utiliser à la fois la Confiance et la Fiabilité dans leurs évaluations quotidiennes.


## Vocabulaire ouvert de la fiabilité

La valeur de fiabilité peut être définie pour chaque Entité de la plateforme pouvant être Auteur de Connaissance :

* `Organizations`
* `Individuals`
* `Systems`
* ainsi que `Reports`

La fiabilité sur les `Reports` permet de spécifier la fiabilité associée à l’auteur original du rapport si vous l’avez reçu via un fournisseur.

Pour toutes les Connaissances de la plateforme, la fiabilité de la source de la Connaissance (auteur) est affichée dans l’Aperçu. Ainsi, vous pouvez toujours forger votre propre évaluation de la Connaissance fournie en fonction de la fiabilité de l’auteur.

![Entity reliability and confidence](./assets/entity-reliability-confidence.png)

Il est également possible de filtrer les entités selon la fiabilité de leur auteur.

!!! astuce "Astuce"

    De cette façon, il est possible de n’alimenter votre travail qu’avec des Connaissances provenant de sources fiables.

La fiabilité est un vocabulaire ouvert qui peut être personnalisé dans Paramètres -> Taxonomies -> Vocabulaires : reliability_ov.

!!! info

    Le paramètre par défaut est l’échelle de fiabilité du code d’Admirauté de l’OTAN. Mais il est possible de définir ce qui correspond le mieux à votre organisation.

![Settings reliability](./assets/settings-reliability_ov.png)


## Échelle de confiance

Le niveau de confiance peut être défini pour :

* Analyses : `Report`, `Grouping`, `Malware analysis`, `Notes`
* Cas : `Incident Response`, `Request for Information`, `Request for Takedown`, `Feedback`
* Événements : `Incident`, `Sighting`, `Observed data`
* Observations : `Indicator`, `Infrastructure`
* Menaces : `Threat actor (Group)`, `Threat actor (Individual)`, `Intrusion Set`, `Campaign`
* Arsenal : `Malware`, `Channel`, `Tool`, `Vulnerability`

Pour toutes ces entités, le niveau de Confiance est affiché dans l’Aperçu, en même temps que la Fiabilité. Ainsi, il est possible d’évaluer rapidement la Connaissance grâce au niveau de Confiance représentant la crédibilité/qualité de l’information.

### Personnalisation de l’échelle de confiance

Le niveau de confiance est une valeur numérique comprise entre 0 et 100. Mais plusieurs « paliers » peuvent être définis et étiquetés pour fournir une échelle significative.

Le niveau de confiance peut être personnalisé pour chaque type d’entité dans Paramètres > Personnalisation > Type d’entité.

![Confidence level customization](assets/confidence-level-customization.png)

Comme une telle personnalisation peut être fastidieuse, trois modèles d’échelle de confiance sont fournis dans OpenCTI :

* Admiralty : correspondant à l’[échelle de crédibilité du code d’Admirauté](https://fr.wikipedia.org/wiki/Code_d%27admiraut%C3%A9)
* Objective : correspondant à une échelle totalement objective, visant à éliminer toute subjectivité. Avec cette échelle, la confiance dans une information est :
    * « Ne peut être jugée » : aucune donnée concernant la crédibilité de l’information
    * « Told » : l’information est connue car elle a été rapportée à la source. La source ne la vérifie pas.
    * « Induced » : l’information est le résultat d’un travail d’analyse et se base sur d’autres informations similaires supposées vraies.
    * « Deduced » : l’information est le résultat d’un travail d’analyse, et constitue une conclusion logique d’autres informations supposées vraies.
    * « Witnessed » : la source a elle-même observé la situation ou l’objet décrit.
* standard : l’échelle historique de confiance dans OpenCTI définissant un niveau de confiance Bas, Moyen et Élevé.

Il est toujours possible de modifier un modèle existant pour définir une échelle personnalisée adaptée à votre contexte.

!!! astuce "Astuce"

    Si vous utilisez le paramètre du code d’Admirauté pour la fiabilité et la Confiance, vous retrouverez l’équivalent de la notation OTAN dans l’Aperçu de vos différentes entités (A1, B2, C3, etc.)

<a id="confidence-level-section"></a>
### Niveau de confiance maximal

#### Aperçu

Il est connu que, dans les organisations, les utilisateurs n’ont pas toujours le même niveau d’expertise ou d’ancienneté. Par conséquent, certains utilisateurs spécifiques peuvent être plus « fiables » lors de la création ou de la mise à jour de connaissances que d’autres. De plus, comme les connecteurs, flux TAXII et streams sont tous liés à un utilisateur, il est important de pouvoir différencier quel connecteur, flux ou stream TAXII est plus digne de confiance qu’un autre.

C’est pourquoi nous avons introduit le concept de niveau de confiance maximal pour répondre à ce cas d’usage.

Le niveau de confiance maximal par utilisateur permet aux organisations d’affiner la gestion de leurs utilisateurs afin de garantir que les connaissances créées ou mises à jour restent aussi cohérentes que possible.

Le niveau de confiance maximal peut être défini au niveau du Groupe ou de l’Utilisateur, et peut être surchargé par type d’entité pour affiner votre politique de confiance.

#### Fonctionnement général

L’idée générale est que les utilisateurs ayant un niveau de confiance maximal inférieur au niveau de confiance d’une entité ne peuvent pas mettre à jour ou supprimer cette entité.

De plus, dans une approche conservatrice, lorsque deux niveaux de confiance sont possibles, le plus bas est toujours retenu.

Pour une compréhension détaillée du concept, consulter ce schéma :

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/embed?embed_host=share&url=https%3A%2F%2Fwww.figma.com%2Ffile%2FlVU6O39B76MJmtnzg9DbZZ%2FConfidence-Level---Documentation%3Ftype%3Dwhiteboard%26node-id%3D0%253A1%26t%3DPQWrdBF6iMGEp0bw-1" allowfullscreen></iframe>

#### Niveau de confiance effectif de l’utilisateur

La configuration du niveau de confiance utilisateur et groupe doit être vue comme :

* un niveau de confiance maximal entre 0 et 100 (optionnel pour les utilisateurs, obligatoire pour les groupes) ;
* une liste de surcharges (un niveau de confiance maximal entre 0 et 100) par type d’entité (optionnel).

Le niveau de confiance effectif de l’utilisateur résulte de cette configuration provenant de plusieurs sources (utilisateur et ses groupes).

Pour calculer cette valeur, OpenCTI utilise la stratégie suivante :

* le niveau de confiance maximal effectif est la valeur maximale trouvée parmi les groupes de l’utilisateur ;
* les surcharges effectives par type d’entité sont cumulées de tous les groupes, en prenant la valeur maximale si plusieurs surcharges sont définies sur le même type d’entité ;
* si un niveau de confiance maximal utilisateur est défini, il surcharge tout ce qui vient des groupes, y compris les surcharges par type d’entité définies au niveau groupe ;
* sinon, mais si l’utilisateur a des surcharges spécifiques par type d’entité, elles surchargent les niveaux de confiance correspondants provenant des groupes ;
* si l’utilisateur dispose de la capacité administrateur « Bypass », le niveau de confiance effectif sera toujours 100 sans surcharge, quel que soit le groupe ou la configuration utilisateur sur le niveau de confiance.

Le schéma suivant décrit les différents cas d’usage que vous pouvez adresser avec ce système.

<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://www.figma.com/board/cecHM2dDyOPoviw6qbVYK4/Effective-Confidence-Level-Computation---Documentation?node-id=0-1&t=ZSJNGb93mPAQRPVh-1" allowfullscreen></iframe>

#### Comment définir un niveau de confiance

Il est possible de définir un niveau de confiance maximal depuis l’onglet Confidences dans le panneau d’édition de votre utilisateur ou groupe.
La valeur peut être sélectionnée entre 0 et 100, ou en utilisant le sélecteur d’échelle Admiralty.

Au niveau du groupe, le niveau de confiance maximal est obligatoire, mais il est optionnel au niveau utilisateur (il faut l’activer via le bouton correspondant).

![Update Confidence Level](assets/update-confidence-level.png)

#### Comment surcharger un niveau de confiance maximal par type d’entité

Il est également possible de surcharger un niveau de confiance maximal par type d’entité, limité aux Stix Domain Objects.

![Override Max Confidence Level Per Entity](assets/user-confidence-overrides.png)

Il est possible de visualiser le niveau de confiance effectif de l’utilisateur dans la vue de détails de l’utilisateur, en survolant l’info-bulle correspondante.
Elle décrit l’origine des différentes valeurs.

![Override Confidence Tooltip](assets/override-confidence-tooltip.png)

## Utilisation dans OpenCTI

### Exemple avec le modèle code d’Admirauté

Votre organisation a reçu un rapport d’un fournisseur CTI. Au niveau de votre organisation, ce fournisseur est considéré comme fiable la plupart du temps et son niveau de fiabilité a été défini sur « B - Généralement fiable » (votre organisation utilise le code d’Admirauté).

Ce rapport concerne le paysage des menaces ransomware et a été analysé par votre analyste CTI spécialisé en cybercriminalité. Cet analyste a attribué un niveau de confiance de « 2 - Probablement vrai » à l’information.

En tant qu’analyste technique, grâce à la notation cumulée de la fiabilité et de la Confiance, vous savez désormais que les éléments techniques de ce rapport méritent probablement d’être pris en considération.

![Example with the admiralty code template](assets/example-admiralty-code.png)

### Exemple avec le modèle Objective

En tant qu’analyste CTI dans un CSIRT gouvernemental, vous construisez des Connaissances qui seront partagées sur la plateforme avec les bénéficiaires. Votre CSIRT est considéré comme une source fiable par vos bénéficiaires, même si vous jouez un rôle de relais avec d’autres sources, mais vos bénéficiaires ont besoin d’informations sur la façon dont la Connaissance a été construite/recueillie.

Pour cela, vous utilisez l’échelle de confiance « Objective » dans votre plateforme afin de fournir ces informations aux bénéficiaires. Lorsque la Connaissance est le fruit de l’enquête de votre CSIRT, soit à partir d’une réponse à incident, soit d’une investigation sur une infrastructure d’attaque, vous définissez le niveau de confiance sur « Witnessed », « Deduced » ou « Induced » (selon que vous avez observé directement les données ou que vous les avez déduites lors de votre recherche). Lorsque l’information n’a pas été vérifiée par le CSIRT mais présente un intérêt à être partagée avec les bénéficiaires, vous pouvez utiliser le niveau « Told » pour leur indiquer clairement que l’information est probablement intéressante mais n’a pas été vérifiée.

![Example with the Objective template](assets/example-objective-scale.png)


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.