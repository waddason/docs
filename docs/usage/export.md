# Export manuel

## Introduction

Avec la plateforme OpenCTI, il est possible d’exporter manuellement votre contenu de renseignement dans les formats suivants :

- JSON,
- CSV,
- PDF,
- TXT.

![Generate an export panel](assets/Generate_an_export_panel.png)

## Exporter au format structuré ou document

<a id="generate-export-section"></a>
### Générer un export

Pour exporter une ou plusieurs entités, deux possibilités s’offrent à vous. D’abord, il est possible de cliquer sur le bouton « Open export panel ». La liste des exports préexistants s’ouvre, et dans le coin inférieur droit, il est possible de configurer et générer un nouvel export.

![open export panel](assets/open_export_panel.png)
Cela ouvre le panneau de configuration de l’export, où il est possible de personnaliser l’export selon quatre champs :

- format d’export souhaité (text/csv, application/pdf, application/vnd.oasis.stix+json, text/plain)
- type d’export (simple ou full),
- le niveau maximal de marking definition des éléments à inclure dans l’export (un niveau TLP, par exemple). La liste des markings maximaux disponibles est limitée par les markings autorisés de l’utilisateur et ses markings partageables maximum (plus de détails sur les maximum shareable marking definitions dans [data segregation](../administration/segregation.md)). Pour qu’un type de marking definition soit pris en compte ici, un marking definition de ce type doit être fourni. Par exemple, si TLP:GREEN est sélectionné pour ce champ, les éléments AMBER et RED seront exclus, mais aucun marking PAP ne sera pris en compte sauf si l’un d’eux est également sélectionné.
- le niveau de marking definition du fichier exporté (un niveau TLP, par exemple). Ce marking sur le fichier lui-même restreindra ensuite l’accès en fonction des niveaux de marking definition des utilisateurs. Par exemple, si un fichier possède les markings TLP:RED et INTERNAL, un utilisateur devra disposer de ces markings pour voir et accéder au fichier sur la plateforme.

![customize your export](assets/customize_your_export.png)

La seconde méthode consiste à cliquer directement sur le bouton « Generate an Export » pour exporter le contenu d’une entité dans le format souhaité. Le même panneau de configuration s’ouvre alors.

![Export entity content](assets/export_entity_content.png)

Dans les deux cas, l’export est ajouté à la liste Exported files dans l’onglet Data.
![Exported files list](assets/exported-files-list.png)

### Possibilités d’export

Toutes les entités de votre instance peuvent être exportées soit directement via Generate Export, soit indirectement via Export List aux formats .json et .csv.

### Exporter une liste d’entités

Il est possible d’exporter soit un seul élément, tel qu’un rapport, soit une collection d’éléments, comme plusieurs rapports. Ces exports peuvent contenir non seulement l’entité elle-même mais aussi des éléments liés, selon le type d’export sélectionné : « simple » ou « full ». Voir la section [Export types (simple and full)](export.md#export-type-section).

Il est également possible d’exporter une liste d’entités au sein d’un container. Pour cela, se rendre dans l’onglet entities du container. Par exemple, pour un rapport, si l’on souhaite uniquement récupérer les entités de type attack pattern et indicators afin de concevoir une stratégie de détection, aller dans l’onglet entities et sélectionner les éléments spécifiques à exporter.

![Export specific elements](assets/export_specific_elements.png)

### Exporter un template Fintel (EE uniquement)

Dans les containers, sous Enterprise Edition, il est possible de générer des fichiers html et pdf à partir d’un template donné.
Des fichiers de finished intelligence peuvent être générés via le bouton général Export ou dans la section 'Content' de votre container.
![Generate Fintel templates button](assets/fintelTemplate-generate-button.png)

Il est possible de choisir le type de fichier (html ou pdf), son nom, son marking, et les markings maximum des entités pouvant être incluses dans le fichier. En effet, un template peut inclure des listes d’entités (par exemple, les indicators contenus dans votre container) et il peut être souhaitable de restreindre les entités affichées selon leurs markings.
Le connecteur interne générant le template s’appelle 'Generate FINTEL from template'.
![Export (html) Fintel template pop-up](assets/fintelTemplates-export-html.png)

Si un template Fintel est généré en html, le fichier apparaît dans le panneau de droite et il est possible de modifier son contenu via CK Editor.
![Fintel template content edition](assets/fintelTemplate-content-edition.png)

Il est ensuite possible d’exporter le fichier html en pdf via le connecteur interne 'HTML content files to PDF' qui génère des pdf personnalisés.
![Export (pdf) Fintel template pop-up](assets/fintelTemplates-export-pdf.png)

![Fintel template pdf file](assets/fintelTemplates-pdf-file.png)

<a id="export-type-section"></a>
### Types d’export (simple et full)

Pour exporter uniquement le contenu d’une entité spécifique telle qu’un rapport, il est possible de choisir le type d’export « simple ».

Pour exporter également le contenu associé, il est possible de choisir un export « full ». Avec ce type d’export, l’entité sera exportée avec toutes les entités directement associées à l’entité centrale (premiers voisins).

![Export types](assets/export_types.png)

### Panneau de liste des exports

Une fois un export créé, il est possible de le retrouver dans le panneau de liste des exports. Il suffit de cliquer sur un export particulier pour le télécharger.

Il est également possible de générer un nouvel export directement depuis la liste des exports, comme expliqué dans la section [Générer un export](export.md#generate-export-section).

![Exports list](assets/exports_list.png)

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.