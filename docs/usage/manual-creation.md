# Créations manuelles

La création manuelle de données dans OpenCTI est un processus intuitif qui se déroule dans l'ensemble de la plateforme. Cette page fournit des conseils sur deux aspects clés de la création manuelle : la création d'entités et la création de relations.

## Création d'entité

### Création simple

Pour créer une entité :

1. Naviguer vers la section de la plateforme correspondant au type d'objet à créer (par exemple Reports).
2. Cliquer sur le bouton "+" situé en bas à droite de la fenêtre.

![New report](assets/new-report.png)

3. Un formulaire apparaîtra sur le côté droit de la fenêtre. Remplir les champs spécifiques de l'entité. Certains champs sont obligatoires par défaut, et les administrateurs peuvent désigner des champs supplémentaires comme obligatoires ([Voir ici](../administration/entities.md#attributes-section) pour plus d'informations).
4. Une fois les champs souhaités remplis, cliquer sur le bouton "Create" pour lancer le processus de création de l'entité.

![Create report](assets/create-report.png)

### Création en masse

Il est également possible de créer plusieurs entités en remplissant le formulaire une seule fois.

> À noter que la création en masse n'est pas disponible pour toutes les entités pour le moment. Par exemple, il n'est pas possible de créer des Reports en masse. Nous utiliserons donc l'exemple des Malwares.

1. Naviguer vers la section de la plateforme correspondant au type d'objet à créer en masse.
2. Cliquer sur le bouton "+" situé en bas à droite de la fenêtre.

![New malware](assets/new-malware.png)

3. Cliquer sur le bouton "Create multiple entities" en haut à droite.
4. Une fenêtre modale s'ouvre avec un champ textarea. Remplir plusieurs lignes, chaque ligne correspondant à une entité à créer. Dans l'exemple ci-dessous, nous allons créer quatre malwares avec respectivement les noms : Malware #1, Malware #2, Malware #3 et Malware #4.
5. Valider les différents noms (cela ne soumettra pas encore le formulaire).

![Create malware bulk](assets/create-malware-bulk.png)

6. Les différentes valeurs saisies apparaissent dans le champ _Name_.

![Bulk input](assets/bulk-input.png)

7. Remplir les autres champs si nécessaire. Attention, pour les autres champs que _Name_, toutes les entités créées auront les mêmes valeurs. Par exemple, si un _Marking_ est défini sur TLP:GREEN, les quatre malwares auront ce marquage.

8. Soumettre le formulaire en cliquant sur le bouton "Create".

![Create malware bulk submit](assets/create-malware-bulk-submit.png)

9. Une barre de progression s'affiche pour indiquer combien d'entités ont été créées. Lorsque le processus est terminé, il est possible de la fermer.

![Create malware bulk progress bar](assets/create-malware-bulk-progressbar.png)

## Création de relation

Avant d'aborder la création de relations entre objets dans OpenCTI, il est essentiel de comprendre certains concepts fondamentaux. Voici les points clés à retenir :

- Sur plusieurs aspects, y compris les relations, il convient de différencier deux catégories d'objets : [containers](containers.md) (par exemple Reports, Groupings et Cases) et les autres. **Les containers ne sont pas liés à des objets mais les contiennent**.
- Les relations, comme toutes les autres entités, sont des objets. Elles possèdent des champs, peuvent être liées et partagent les mêmes caractéristiques que les autres entités.
- Les relations sont intrinsèquement directionnelles, comprenant une entité "from" et une entité "to". Comprendre cette directionnalité est essentiel pour une création de relation correcte.
- OpenCTI prend en charge différents types de relations, et leur utilisation dépend des types d'entités à relier. Par exemple, une relation "target" peut lier un malware à une organisation, tandis que lier un malware à un intrusion set peut nécessiter un autre type de relation.

Explorons maintenant le processus de création de relations. Pour cela, nous différencierons le cas des containers des autres.

### Pour un container

La création de relations au sein des containers dans OpenCTI est simple. Suivre ces étapes pour attacher des objets à un container :

1. Naviguer vers le container : Aller sur le container spécifique auquel ajouter un objet. Il peut s'agir d'un Report, Grouping ou Cases.
2. Accéder à l'onglet "Entities" : Dans le container, localiser et accéder à l'onglet "Entities".
3. Cliquer sur l'icône "+" : Trouver l'icône "+" située en bas à droite de la fenêtre. ![New relation with container](assets/relation-with-container.png)
4. Rechercher des entités : Une fenêtre latérale apparaît. Rechercher les entités à ajouter au container.
5. Ajouter des entités au container : Cliquer sur les entités souhaitées. Elles seront ajoutées directement au container.

### Pour les autres

Pour créer des relations n'impliquant pas un container, la méthode de création est différente. Suivre ces étapes pour créer des relations entre entités :

1. Naviguer vers l'une des entités : Aller sur l'une des entités à relier. Attention, l'entité depuis laquelle la relation est créée sera désignée comme entité "from" pour cette relation. Le choix de l'entité à partir de laquelle créer la relation doit donc être réfléchi, car il aura un impact sur le résultat.
2. Accéder à l'onglet "Knowledge" : Dans l'entité, aller dans l'onglet "Knowledge".
3. Sélectionner les catégories pertinentes : Dans la bannière de droite, naviguer vers les catégories correspondant à l'objet à lier. Les catégories disponibles dépendent du type d'entité sélectionné. Par exemple, si vous êtes sur un malware et souhaitez le lier à un sector, choisir "victimology".
4. Cliquer sur l'icône "+" : Trouver l'icône "+" située en bas à droite de la fenêtre. ![New relationhip](assets/new-relationship.png)
5. Rechercher des entités : Une fenêtre latérale apparaît. Rechercher les entités à lier.
6. Ajouter des entités et cliquer sur "Continue" : Cliquer sur les entités à lier. Plusieurs entités peuvent être sélectionnées. Puis cliquer sur "Continue" en bas à droite. ![Entities to link](assets/entities-to-link.png)
7. Remplir le formulaire de relation : Comme les relations sont des objets, un formulaire de création similaire à celui d'une entité apparaît.
8. Cliquer sur "Create" : Une fois les champs souhaités remplis, cliquer sur "create" pour lancer la création de la relation.

![Create relationship](assets/create-relationship.png)

## Méthodes supplémentaires

Bien que les méthodes précédentes soient les principales pour créer des entités et des relations, OpenCTI offre de la flexibilité, permettant de créer des objets à différents endroits de la plateforme. Voici une liste non exhaustive d'autres emplacements facilitant la création à la volée :

- Création d'entités lors de la création d'une relation : Pendant la phase "Search for entities" (voir ci-dessus) du processus de création de relation, cliquer sur l'icône "+" pour créer une nouvelle entité directement.
- Knowledge graph : Dans le knowledge graph - accessible dans l'onglet knowledge des containers ou dans la [fonctionnalité d'investigation](pivoting.md) - il est possible de créer facilement des entités ou des relations.
- À l'intérieur d'un workbench : [Le workbench](workbench.md) constitue un autre espace interactif où il est possible de créer efficacement des entités et des relations.

Ces méthodes complémentaires offrent flexibilité et praticité, permettant d'adapter le flux de travail à différents contextes dans la plateforme OpenCTI. En explorant la plateforme, les utilisateurs découvriront naturellement d'autres moyens de créer des entités et des relations.

!!! note "Niveau de confiance maximal"

Lors de la création de connaissances dans la plateforme, le niveau de confiance maximal des utilisateurs est utilisé. Veuillez consulter cette [page](reliability-confidence.md) pour comprendre ce concept et son impact sur la création de connaissances.


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.