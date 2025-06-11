# Espace de travail analyste

Les espaces de travail servent de zones dédiées à la manipulation des données avant leur importation officielle dans la plateforme.

## Emplacement d’utilisation

Les espaces de travail se trouvent à différents endroits au sein de la plateforme :

### Fenêtre d’import de données et des espaces de travail analyste

Cette fenêtre regroupe tous les outils nécessaires pour importer un fichier. Les fichiers importés via cette interface seront ensuite traités par les connecteurs d’import, ce qui entraînera la création d’espaces de travail. De plus, les analystes peuvent créer manuellement un espace de travail en cliquant sur l’icône « + » en bas à droite de la fenêtre.

![Data import and workbenches panel](assets/data-import-and-workbenches.png)

### Onglets « Données » de toutes les entités

Les espaces de travail sont également accessibles via les onglets « Données » des entités, offrant un accès pratique aux données importées associées à l’entité.

![Workbench in "Data" tab](assets/workbench-in-data-tab.png)

## Fonctionnement

Les espaces de travail sont générés automatiquement lors de l’import d’un fichier via un connecteur d’import. Lorsqu’un connecteur d’import est lancé, il analyse les fichiers à la recherche d’entités reconnaissables et crée ensuite un espace de travail. Toutes les entités identifiées sont placées dans cet espace de travail pour révision par les analystes.
Alternativement, les analystes ont la possibilité de créer manuellement un espace de travail en cliquant sur l’icône « + » en bas à droite de la fenêtre « Import de données et espaces de travail analyste ».

![Overview of workbench](assets/overview-of-workbench.png)

L’espace de travail étant un espace de brouillon, les analystes l’utilisent pour examiner les propositions des connecteurs avant de les valider pour l’import. À l’intérieur de l’espace de travail, les analystes peuvent ajouter, supprimer ou modifier des entités selon les besoins spécifiques.

![Workbench data manipulation](assets/workbench-data-manipulation.png)

Une fois le contenu de l’espace de travail jugé satisfaisant, l’analyste doit lancer le processus d’ingestion en cliquant sur `Validate this workbench`. Cette action permet d’écrire les données dans la base de connaissances.

!!! note "Les espaces de travail sont des espaces de brouillon"

    Tant que l’espace de travail n’est pas validé, les données qu’il contient restent à l’état de brouillon et ne sont pas enregistrées dans la base de connaissances. Cela garantit que seules les données vérifiées et approuvées sont officiellement intégrées à la plateforme.

Pour plus d’informations sur l’import de fichiers, consulter la page de documentation [Import from files](import-files.md).

**Niveau de confiance des connaissances créées via l’espace de travail**

Le niveau de confiance des connaissances créées via l’espace de travail dépend du niveau de confiance de l’utilisateur. Veuillez consulter cette [page](reliability-confidence.md) pour plus de détails.


> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.