# Connecteurs d'enrichissement

L'enrichissement des données au sein de la plateforme OpenCTI s'effectue de manière transparente grâce à l'intégration de connecteurs d'enrichissement. Ces connecteurs facilitent la récupération de données supplémentaires depuis des sources ou portails externes.

### Enrichissement automatique

L'enrichissement peut être réalisé automatiquement selon deux modes distincts :

- À l'arrivée des données : Configurer le connecteur pour s'exécuter automatiquement lors de l'arrivée de nouvelles données dans OpenCTI permet un enrichissement en temps réel, complétant ainsi les données de la plateforme. Cependant, il est recommandé d'éviter l'enrichissement automatique pour les connecteurs soumis à des quotas sur des sources payantes afin de ne pas épuiser rapidement tous les quotas. De plus, cet enrichissement automatique contribue à augmenter le volume de données. À grande échelle, avec des centaines de milliers d'objets, l'espace disque occupé par ces données peut être conséquent, ce qui doit être pris en compte, notamment si l'espace disque est une contrainte. L'exécution automatique se configure au niveau du connecteur via le paramètre "auto: true|false".
- Enrichissement ciblé via les playbooks : L'enrichissement peut également être effectué de manière plus ciblée à l'aide de [playbooks](automation.md). Cette approche permet de définir une stratégie d'enrichissement personnalisée, en se concentrant sur des objets spécifiques et en optimisant la pertinence des données récupérées.

### Enrichissement manuel

Lancer manuellement le processus d'enrichissement est simple. Il suffit de localiser le bouton avec l'icône de nuage en haut à droite d'une entité.

![Enrichment button](assets/enrichment-button.png)

Cliquer sur cette icône ouvre un panneau latéral affichant la liste des connecteurs disponibles pouvant être activés pour l'objet concerné. Si aucun connecteur n'apparaît dans le panneau, cela signifie qu'aucun connecteur d'enrichissement n'est disponible pour le type d'objet sélectionné.

![Enrichment panel](assets/enrichment-panel.png)

L'activation d'un connecteur d'enrichissement déclenche un contact avec la source distante désignée, important un ensemble de données dans OpenCTI pour enrichir l'objet sélectionné. Chaque connecteur d'enrichissement fonctionne de manière unique, en se concentrant sur un ensemble spécifique de types d'objets qu'il peut enrichir et un ensemble distinct de données qu'il importe. Selon les connecteurs, ils peuvent établir des relations, ajouter des références externes ou compléter les informations de l'objet, contribuant ainsi à la richesse des informations au sein de la plateforme.

La liste des connecteurs disponibles est consultable dans notre [catalogue de connecteurs](https://www.notion.site/OpenCTI-Ecosystem-868329e9fb734fca89692b2ed6087e76). De plus, une documentation complémentaire sur les connecteurs est disponible sur [la page dédiée à la documentation](../deployment/connectors.md).

!!! note "Impact du niveau de confiance maximal"

  Le niveau de confiance maximal par utilisateur peut avoir un impact sur les connecteurs d'enrichissement, ceux-ci pouvant ne pas être en mesure de mettre à jour les données dans la plateforme. Pour comprendre ce concept et les éventuels problèmes rencontrés, consulter cette [page](reliability-confidence.md) pour plus d'informations.


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.