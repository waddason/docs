# Pivot et investigation

Dans OpenCTI, toutes les données sont structurées sous forme d’un vaste graphe de connaissances, où chaque élément est interconnecté. La fonctionnalité d’investigation offre un outil puissant pour pivoter sur n’importe quelle entité ou relation au sein de la plateforme. Le pivot permet d’explorer et d’analyser les connexions entre entités et relations, facilitant ainsi une compréhension globale des données.

Pour accéder aux investigations, naviguer vers le coin supérieur droit de la barre d’outils :

![Top menu investigation](assets/top-menu-investigation.png)

!!! note "Restriction d’accès"

    Lorsqu’une investigation est créée, elle n’est initialement visible que par son créateur, lui permettant de travailler dessus avant de décider de la partager. Le mécanisme de partage est similaire à celui des tableaux de bord. Pour plus de détails, consulter la [section Contrôle d’accès](dashboards.md#access-control-section) dans la page de documentation des tableaux de bord.


## Réaliser une investigation

### Sélectionner / rechercher une entité
Lors de la sélection (ou recherche) d’une entité, toutes les entités sélectionnées (ou correspondant à votre recherche) resteront « colorées ». Les autres entités seront superposées pour mettre en évidence votre sélection (ou recherche).
L’entité actuellement affichée dans le panneau de droite est celle avec une **ligne bleue continue** tandis que celles avec une **ligne bleue en pointillés** sont les autres entités sélectionnées mais non affichées dans le panneau de droite.
De plus, le panneau de droite affiche désormais un compteur du nombre d’entités sélectionnées pour aider à comprendre la quantité sélectionnée (ou correspondant à votre recherche).

![select entities in graph](assets/Select-entities-in-graph.png)


### Manipuler une entité

Il est possible d’ajouter toute entité existante de la plateforme à votre investigation.

![Investigation bottom right menu](assets/investigation-bottom-right-menu.png)

Après avoir ajouté une entité, il est possible de la sélectionner et de consulter ses détails dans le panneau qui apparaît à droite de l’écran.

Sur chaque nœud, une pastille avec un nombre à l’intérieur sert d’indicateur visuel du nombre d’entités qui y sont liées mais non actuellement affichées dans le graphe. Ce nombre est une approximation, c’est pourquoi il y a un « + » à côté. S’il n’y a pas de pastille affichée, cela signifie qu’il n’y a rien à étendre depuis ce nœud.

![Investigation workspace](assets/investigation-workspace.png)

### Expansion
Pour incorporer ces entités liées dans le graphe, il suffit d’étendre les nœuds. Utiliser le bouton avec un logo à 4 flèches dans le menu mentionné, ou double-cliquer directement sur l’entité. Cette action ouvre une nouvelle fenêtre où il est possible de choisir les types d’entités et de relations à étendre.

![Investigation expand entity](assets/investigation-expand-entity.png)

Par exemple, dans l’image ci-dessus, sélectionner la cible _Malware_ et la relation _Uses_ implique d’étendre dans le graphe d’investigation tous les _Malware_ liés à ce nœud par une relation de type _Uses_.

### Annuler une expansion

Étendre un graphe peut ajouter de nombreuses entités et relations, rendant la lecture difficile, voire contre-productive si cela apporte des entités et relations non utiles à l’investigation.
Pour résoudre ce problème, un bouton permet d’annuler la dernière expansion.

En cliquant sur ce bouton, l’état du graphe avant l’expansion est restauré. À noter que toutes les actions d’ajout ou de suppression effectuées depuis la dernière expansion seront perdues : autrement dit, si le graphe a été étendu, puis des entités ajoutées, en cliquant sur le bouton d’annulation, les entités ajoutées ne seront plus dans le graphe.

![Investigation rollback popup](assets/investigation-rollback-popup.png)

Il est possible d’annuler jusqu’aux 10 dernières actions d’expansion du graphe d’investigation.

### Manipuler une relation

Il est possible de créer une relation entre des entités directement dans l’investigation. Pour cela, sélectionner plusieurs entités en cliquant dessus tout en maintenant la touche shift enfoncée. Ensuite, un bouton apparaît en bas à droite pour créer une (ou plusieurs, selon le nombre d’entités sélectionnées) relation(s).

![Investigation create relationship](assets/investigation-create-relationship.png)

!!! note "Création de relation"

    Créer une relation dans le graphe d’investigation générera la relation dans votre base de connaissances.


## Valoriser une investigation


### Exporter une investigation

Les utilisateurs ont la possibilité d’exporter les investigations, offrant un moyen de partager, documenter ou archiver leurs résultats.

- Formats PDF et image : il est possible d’exporter les investigations au format PDF ou image, offrant de la flexibilité pour le partage et la documentation.
- STIX bundle : la plateforme permet d’exporter l’intégralité du contenu d’un graphe d’investigation sous forme de STIX bundle. Dans le format STIX, tous les objets du graphe d’investigation sont automatiquement agrégés dans un objet Report.

![Investigation export](assets/investigation-export.png)


### Transformer une investigation en container

Les utilisateurs peuvent collecter et consolider efficacement les résultats d’une investigation en ajoutant le contenu dans des [containers](containers.md) dédiés. Le contenu d’une investigation peut être importé dans différents types de containers, notamment :

- Grouping
- Incident Response
- Report
- Request for Information
- Request for Takedown

![investigation-turn-to-report-or-case.png](assets/investigation-turn-to-report-or-case.png)

Il est possible de choisir entre créer un nouveau container à la volée ou ajouter le contenu de l’investigation à un container existant.

![investigation-turn-to-report-or-case-dialog-new-entity.png](assets/investigation-turn-to-report-or-case-dialog-new-entity.png)

![investigation-turn-to-report-or-case-dialog-new-entity-form.png](assets/investigation-turn-to-report-or-case-dialog-new-entity-form.png)

Après avoir cliqué sur le bouton `ADD`, le navigateur sera redirigé vers l’onglet Knowledge du container où le contenu de l’investigation a été ajouté. Si le contenu a été ajouté à plusieurs containers, la redirection se fera vers le premier de la liste.

![investigation-turn-to-report-or-case-success.png](assets/investigation-turn-to-report-or-case-success.png)


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.