# Rechercher des connaissances

Dans OpenCTI, différentes fonctionnalités sont disponibles pour rechercher des connaissances sur la plateforme. Dans la plupart des cas, une recherche par mot-clé peut être affinée avec des filtres supplémentaires, par exemple sur le type d'objet, l'auteur, etc.

## Recherche globale

La recherche globale est toujours disponible dans la barre supérieure de la plateforme.

<figure markdown>
  ![Search bar](assets/search-bar.png)
</figure>

Cette recherche couvre tous les [STIX Domain Objects (SDOs)](data-model.md#stix-model-section) et [STIX Cyber Observables (SCOs)](data-model.md#stix-model-section) présents sur la plateforme. Les résultats de recherche sont triés selon le comportement suivant :

* Priorité 1 pour une correspondance exacte du mot-clé dans un attribut des objets.
* Priorité 2 pour une correspondance partielle du mot-clé dans les attributs `name`, `aliases` et `description` (recherche en texte intégral).
* Priorité 3 pour une correspondance partielle du mot-clé dans tous les autres attributs (recherche en texte intégral).

Si le résultat obtenu n'est pas celui attendu, il est toujours possible d'ajouter des filtres après la recherche initiale :

![Search filters](assets/search-filters.png)

De plus, en utilisant le bouton `Recherche avancée`, il est possible d'ajouter directement des filtres dans une recherche globale :

![Advanced search](assets/advanced-search.png)

!!! info "Filtres avancés"

    Des filtres avancés sont disponibles partout dans l'interface. Pour en savoir plus sur l'utilisation de ces filtres avec l'API ou la bibliothèque Python, [consulter la page dédiée](../reference/filters.md)

### Recherche en texte intégral dans le contenu des fichiers

!!! astuce "Édition Enterprise"

    La recherche en texte intégral dans le contenu des fichiers est disponible sous licence "OpenCTI Enterprise Edition".

    [Consulter la page dédiée pour plus d'informations](../administration/enterprise.md)

Il est possible d'étendre la recherche globale par mots-clés au contenu des documents importés sur la plateforme via l'onglet Data import, ou directement liés à une entité via son onglet Data.

Il est particulièrement utile d'activer l'option ``Full text indexing`` afin d'éviter de manquer des informations importantes qui n'auraient pas été structurées dans la plateforme. Cette situation peut survenir à cause d'une importation automatique partielle du contenu d'un document, de limitations d'un connector, ou bien sûr d'erreurs lors d'un traitement manuel.

![Files search](assets/global-search-files.png)

Pour rechercher dans les fichiers, il est nécessaire de configurer [l'indexation des fichiers](../administration/file-indexing.md).

## Recherche en masse

La fonctionnalité de recherche en masse est disponible dans la barre supérieure de la plateforme et permet de copier-coller une liste de mots-clés ou d'objets (par exemple, une liste de domaines, d'adresses IP, de vulnérabilités, etc.) à rechercher sur la plateforme :

![Bulk search](assets/bulk-search.png)

Lors d'une recherche en masse, OpenCTI recherche uniquement une correspondance exacte dans certains attributs :

* `name`
* `aliases`
* `x_opencti_aliases`
* `x_mitre_id`
* `value`
* `subject`
* `abstract`
* `hashes.MD5`
* `hashes.SHA-1`
* `hashes.SHA-256`
* `hashes.SHA-512`
* `x_opencti_additional_names`

Si un élément n'est pas trouvé, il apparaît dans la liste comme `Unknown` et sera exclu si vous choisissez d'exporter le résultat de la recherche dans un bundle JSON STIX ou dans un fichier CSV.

![Bulk search results](assets/bulk-result.png)

## Recherche contextuelle

Sur la plupart des écrans de connaissances, une barre de recherche contextuelle permet de filtrer la liste affichée :

![Contextual search](assets/contextual-search.png)

Le mot-clé utilisé ici est pris en compte si vous décidez d'exporter la vue courante dans un fichier tel qu'un bundle JSON STIX ou un fichier CSV.

## Autres barres de recherche

D'autres écrans peuvent contenir des barres de recherche pour des usages spécifiques. Par exemple, dans les vues graphiques pour filtrer les nœuds affichés sur le graphe :

![Search in graph](assets/search-graph.png)


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.