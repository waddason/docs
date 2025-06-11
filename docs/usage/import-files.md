# Importer depuis des fichiers


## Mécanismes d'import

La plateforme propose un processus transparent pour l'analyse automatique des données à partir de divers formats de fichiers. Cette capacité est assurée par deux mécanismes distincts.

**Connecteurs d'import de fichiers :** Actuellement, il existe quatre connecteurs conçus pour importer des fichiers et identifier automatiquement les entités.

- `ImportFileStix` : Conçu pour gérer les fichiers structurés STIX (format json ou xml).
- `ImportFileMISP` : Conçu pour gérer les fichiers structurés MISP (format json).
- `ImportFileYARA` : Conçu pour gérer les fichiers de règles YARA (format yar).
- `ImportDocument` : Connecteur polyvalent prenant en charge une gamme de formats de fichiers, y compris pdf, texte, html et markdown.

**CSV mappers :** Le CSV mapper est une fonctionnalité dédiée pour faciliter l'import de données stockées dans des fichiers CSV. Pour plus d'informations sur l'utilisation des CSV mappers, consulter la page de documentation [CSV Mappers](../administration/csv-mappers.md).

![Connecteurs d'import manuel](assets/manual-import-connectors.png)


## Utilisation

### Emplacements

Les deux mécanismes peuvent être utilisés partout où le téléversement de fichiers est possible. Cela inclut les onglets "Données" de toutes les entités ainsi que le panneau dédié nommé "Import de données et workbenches analyste" situé dans le coin supérieur droit (logo base de données avec un petit engrenage). Importer des fichiers depuis ces deux emplacements n'est pas totalement équivalent ; se référer à la section "Gestion des relations depuis l'onglet Données d'une entité" ci-dessous pour plus de détails à ce sujet.

### Processus d'identification des entités

Pour le connecteur `ImportDocument`, le processus d'identification consiste à rechercher les entités existantes sur la plateforme et à analyser le document pour y extraire des informations pertinentes. De plus, le connecteur utilise des expressions régulières (regex) pour détecter les adresses IP et les domaines dans le document.

Concernant le connecteur `ImportFileStix` et les CSV mappers, il n'y a pas de mécanisme d'identification. Les données importées correspondront respectivement aux données définies dans le bundle STIX ou selon la configuration du CSV mapper utilisé.

### Vue d'ensemble du workflow

1. Téléverser le fichier : Aller à l'emplacement souhaité, tel que l'onglet "Données" d'une entité ou le panneau "Import de données et workbenches analyste". Ensuite, téléverser le fichier contenant les données pertinentes en cliquant sur le petit nuage avec la flèche à l'intérieur à côté de "Fichiers téléversés".
2. Identification des entités : Pour un fichier CSV, sélectionner le connecteur et le CSV mapper à utiliser en cliquant sur l'icône avec une flèche vers le haut dans un cercle. S'il ne s'agit pas d'un fichier CSV, le connecteur se lancera automatiquement. Ensuite, les connecteurs d'import de fichiers ou les CSV mappers identifieront les entités dans le document téléversé.
3. Revue et validation dans le workbench : Les entités identifiées par les connecteurs ne sont pas immédiatement intégrées dans la base de connaissances de la plateforme. Elles sont placées dans un workbench, en attente de revue et de validation par un analyste. Les workbenches fonctionnent comme des espaces de brouillon, garantissant qu'aucune donnée n'est officiellement intégrée à la plateforme tant que le workbench n'a pas été validé. Pour plus d'informations sur les workbenches, consulter la page de documentation [Workbench analyste](workbench.md).

!!! avertissement "Revue des workbenches"

    Les connecteurs d'import peuvent introduire des erreurs dans l'identification des types d'objets ou ajouter des entités "inconnues". Les workbenches ont été créés dans le but de revoir la sortie des connecteurs avant validation. Il est donc crucial d'être vigilant lors de l'examen du workbench afin d'éviter l'import de données incorrectes dans la plateforme.

![Panneau d'import global](assets/global-import-panel.png)


## Informations complémentaires

### Pas de workbench pour le CSV mapper

Il est important de noter que les CSV mappers fonctionnent différemment des autres mécanismes d'import. Contrairement aux connecteurs, les CSV mappers ne génèrent pas de workbench. Les données identifiées par les CSV mappers sont importées directement dans la plateforme sans étape intermédiaire de workbench.

### Gestion des relations depuis l'onglet "Données" d'une entité

Lors de l'import d'un document directement depuis l'onglet "Données" d'une entité, il peut y avoir une addition automatique de relations entre les objets identifiés par les connecteurs et l'entité concernée. Le processus diffère selon le type d'entité dans lequel l'import a lieu :

- Si l'entité est un container (par exemple, Report, Grouping et Cases), les objets identifiés dans le fichier importé seront liés à l'entité (après validation du workbench). Dans le contexte d'un container, l'objet est dit "contenu".
- Pour les entités qui ne sont pas des containers, un comportement distinct s'applique. Dans ce cas, les objets identifiés ne sont pas liés à l'entité, sauf pour les Observables. Les relations `Related to` entre les Observables et l'entité sont automatiquement ajoutées au workbench et créées après validation de celui-ci.


### Import de fichiers dans l'onglet Contenu

Pour élargir les possibilités d'import, les utilisateurs peuvent ajouter des fichiers dans l'onglet `Content` des [Analyses](exploring-analysis.md) ou [Cases](exploring-cases.md). Dans ce cas, le fichier est ajouté directement en tant que pièce jointe sans utiliser de mécanisme d'import.

### Prérequis de capacité utilisateur

Pour initier des imports de fichiers, les utilisateurs doivent disposer de la [capacité](../administration/users.md) requise : "Upload knowledge files." Cette capacité garantit que seuls les utilisateurs autorisés peuvent contribuer et gérer les fichiers de connaissance au sein de la plateforme OpenCTI, assurant ainsi un environnement contrôlé et sécurisé pour les téléversements de données.


!!! avertissement "Avertissement de dépréciation"

    L'utilisation du connecteur `ImportDocument` pour analyser un fichier CSV est désormais interdite car elle produit des résultats incohérents.
    Veuillez configurer et utiliser les [CSV mappers](../administration/csv-mappers.md) dédiés à votre contenu CSV spécifique pour un traitement fiable.
    Les CSV mappers peuvent être créés et configurés dans l'interface d'administration.   


> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.