# Tableaux de bord publics

OpenCTI propose un moyen simple de partager une visualisation d’un tableau de bord personnalisé avec n’importe qui, même avec des personnes extérieures à la plateforme. Nous appelons ces visualisations : tableaux de bord publics.

Les tableaux de bord publics sont une capture instantanée d’un tableau de bord personnalisé à un moment donné. De cette façon, il est possible de partager une version d’un tableau de bord personnalisé, puis de modifier ce tableau de bord sans se soucier de l’impact sur les tableaux de bord publics déjà créés.

À l’inverse, si vous souhaitez que votre tableau de bord public soit mis à jour avec la dernière version du tableau de bord personnalisé associé, il suffit de recréer un tableau de bord public en utilisant le même nom que celui à mettre à jour.

> Pour pouvoir partager des tableaux de bord personnalisés, il est nécessaire de disposer de la capacité [Gérer le partage et l’ingestion de données](../administration/users.md).

## Page de liste des tableaux de bord publics

Depuis le menu de gauche, il est possible de choisir l’option tableau de bord public pour voir tous les tableaux de bord publics créés, ainsi que ceux auxquels vous avez accès (par exemple, « peut voir », « peut modifier » ou « peut gérer »).

![List of public dashboards](assets/list_public_dashboards.png)

**Panneau d’actions**

Il est possible de réaliser des actions sur un tableau de bord public à l’aide du bouton situé à la fin de chaque ligne :

- accéder au tableau de bord d’origine
- désactiver le lien public
- copier le lien public
- supprimer

**Suppression massive**

Il est possible d’effectuer des opérations de suppression massive à l’aide de la case à cocher :

- **Sélectionner chaque** tableau de bord public individuellement à supprimer
- **Tout sélectionner** les tableaux de bord publics affichés sur la page à supprimer

![Select all](assets/select_all_public.png)


## Créer un tableau de bord public

Il est possible de créer un tableau de bord public soit depuis la liste des tableaux de bord publics, soit depuis le tableau de bord personnalisé d’origine.

- Dans la page de liste de vos tableaux de bord personnalisés, un bouton permet d’ouvrir un panneau pour créer le tableau de bord public associé à ce tableau de bord personnalisé.

![Create a public dashboard button](assets/create_public_dashboard.png)

- En haut à droite de la page de liste des tableaux de bord publics, un bouton « Créer un tableau de bord public » est disponible.

![Share dashboard button](assets/create_public_dashboard_from_public_list.png)

- En haut à droite de la page de votre tableau de bord personnalisé, un bouton permet également d’ouvrir ce même panneau.

![Share dashboard button](assets/share-dashboard-button.png)

Dans ce panneau, deux parties sont présentes :
- En haut, un formulaire permettant de créer des tableaux de bord publics,
- En dessous, la liste des tableaux de bord publics déjà créés.

![Share dashboard panel](assets/share-public-dashboard-panel.png)

### Formulaire de création d’un nouveau tableau de bord public

Si le tableau de bord public est créé depuis la liste des tableaux de bord publics, il faut d’abord sélectionner le tableau de bord personnalisé associé.

![Select custom dashboard name](assets/select-custom-dashboard.png)

Il est nécessaire de spécifier un nom pour le tableau de bord public. Ce nom sera affiché sur la page du tableau de bord. Le nom est également utilisé pour générer un identifiant pour le tableau de bord public, qui sera utilisé dans l’URL d’accès au tableau de bord.

L’identifiant est généré comme suit : remplacer tous les espaces par le symbole `-` et supprimer les caractères spéciaux. Cet identifiant doit également être unique sur la plateforme car il est utilisé dans l’URL d’accès au tableau de bord.

![Share dashboard name](assets/share-dashboard-name.png)

Il est ensuite possible de choisir si le tableau de bord public est activé ou non. Un tableau de bord désactivé signifie qu’il n’est pas accessible via l’URL personnalisée. Il reste cependant possible de le gérer depuis ce panneau.

![Share dashboard enable](assets/share-dashboard-enable.png)

Enfin, il convient de choisir le niveau maximal de marking definitions pour les données à afficher dans le tableau de bord public. Par exemple, en choisissant `TLP:AMBER`, les données récupérées par les widgets du tableau de bord public seront au maximum AMBER, les données avec la marking definition RED ne seront pas récupérées.

À noter également que la liste des marking definitions affichée dépend de vos droits d’accès actuels sur la plateforme **et des marking definitions partageables maximales** définies dans vos groupes.

!!! note "Définir les markings partageables maximaux dans les groupes"

    En tant qu’administrateur de la plateforme, il est possible de définir, pour chaque groupe et pour chaque type de marking definition, les [markings maximaux partageables](../administration/segregation.md) à travers le Tableau de bord public, indépendamment de la définition choisie par les utilisateurs dans leur tableau de bord public.

![Share dashboard markings](assets/share-dashboard-markings.png)

### Liste des tableaux de bord publics dans le panneau

Une fois le tableau de bord public créé, il apparaît dans la liste sous le formulaire.

![Share dashboard list](assets/share-dashboard-list.png)

Dans cette liste, chaque élément représente un tableau de bord public créé. Pour chacun, il est possible de voir son nom, le chemin de l’URL, les marking definitions maximales, la date de création, le statut (activé ou non) et quelques actions.

Les actions possibles sont : copier le lien du tableau de bord public, désactiver ou activer le tableau de bord, et supprimer le tableau de bord.

Pour partager un tableau de bord public, il suffit de copier le lien et de transmettre l’URL à la personne souhaitée. Le tableau de bord sera visible même si la personne n’est pas connectée à OpenCTI.

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.