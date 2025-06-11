# Demander à l'IA

!!! astuce "Édition Entreprise"

  Demander à l'IA est disponible sous la licence "OpenCTI Enterprise Edition".

  [Veuillez lire la page dédiée pour obtenir toutes les informations](../administration/enterprise.md)
  

## Prérequis pour utiliser Demander à l'IA

Plusieurs possibilités existent pour les clients de l'Édition Entreprise afin d'utiliser les points de terminaison IA d'OpenCTI :

- Utiliser le service Filigran AI en exploitant notre modèle IA personnalisé avec le jeton fourni par l'équipe support.
- Utiliser les points de terminaison cloud OpenAI, MistralAI ou AzureAI avec vos propres jetons.
- Déployer ou utiliser des points de terminaison IA locaux (Filigran peut vous fournir le modèle personnalisé).

[Veuillez lire la documentation de configuration](../deployment/configuration.md)

!!! info "Fonctionnalité Bêta"
  
  Demander à l'IA est une fonctionnalité bêta car nous sommes en train d'affiner nos modèles. Considérer la vérification des informations importantes.

## Fonctionnement

Même si à l'avenir, nous souhaitons exploiter l'IA pour faire du [RAG](https://blogs.nvidia.com/blog/what-is-retrieval-augmented-generation/), pour le moment nous utilisons principalement l'IA pour analyser et produire des textes ou des images, à partir des données directement envoyées dans l'invite.

Cela signifie que si vous utilisez le point de terminaison Filigran AI ou un point local, vos données ne sont jamais utilisées pour réentraîner ou adapter le modèle et tout repose sur un modèle pré-entraîné et figé. Lors de l'utilisation du bouton `Demander à l'IA` dans la plateforme, une invite est générée avec l'instruction appropriée pour générer le résultat attendu et l'utiliser dans le contexte du bouton (dans les formulaires, l'éditeur de texte enrichi, etc.).

### Modèle personnalisé Filigran

Nous hébergeons un point de terminaison IA évolutif pour tous les clients SaaS ou On-Prem de l'édition entreprise. Ce point de terminaison est basé sur MistralAI avec un modèle qui sera adapté au fil du temps pour être plus efficace lors du traitement de contenus liés à la threat intelligence.

Le modèle, encore en version bêta, sera adapté dans les prochains mois pour atteindre sa maturité à la fin de 2024. Il peut être partagé avec les clients On-Prem de l'édition entreprise sous NDA.

## Fonctionnalités de Demander à l'IA

Demander à l'IA est représenté par une icône dédiée partout où l'une de ses fonctionnalités est disponible.

![Créer un nouveau playbook](assets/askai_icon.png)

### Assistance à la rédaction de contenu pertinent

Demander à l'IA peut vous aider à rédiger un meilleur contenu textuel, par exemple un meilleur titre, nom, description et contenu détaillé des Objets.

- Corriger l'orthographe & la grammaire : essayer d'améliorer le texte du point de vue de la formulation et de la grammaire.  
- Raccourcir/allonger : essayer de raccourcir ou d'allonger le texte.
- Changer le ton : essayer de changer le ton du texte. Il est possible de sélectionner si le texte doit être rédigé pour un public Stratégique (Management, décideurs), Tactique (chefs d'équipe) ou Opérationnel (analystes CTI techniques).
- Résumer : essayer de résumer le texte sous forme de points clés.
- Expliquer : essayer d'expliquer le contexte du texte du sujet en fonction de ce qui est disponible pour le LLM.

### Assistance à l'importation de données depuis des documents

Depuis l'onglet Content d'un Container (Reports, Groupings et Cases), Demander à l'IA peut également vous aider à importer les données contenues dans les documents téléchargés dans OpenCTI pour une exploitation ultérieure.

- Générer un rapport : Générer un rapport texte basé sur le knowledge graph (entités et relations) de ce container.
- Résumer les fichiers associés : Générer un résumé des fichiers sélectionnés (ou de tous les fichiers associés à ce container).
- Essayer de convertir les fichiers sélectionnés (ou tous les fichiers associés à ce container) en un bundle STIX 2.1 que vous pourrez ensuite utiliser à votre convenance (par exemple l'importer dans la plateforme).

![Génération d'un rapport avec Demander à l'IA](assets/askai_generatereport.png)

![Exemple de contenu généré](assets/askai_generatedcontent.png)

Une courte vidéo sur la chaîne YouTube FiligranHQ présente les capacités de AskAI : https://www.youtube.com/watch?v=lsP3VVsk5ds.

<a id="nlq-section"></a>
### Assistance à la recherche d'entités spécifiques (Natural Language Query)

Un bouton Demander à l'IA est disponible dans la barre de recherche supérieure. Il permet de passer la barre de recherche en mode NLQ où il est possible de rédiger des questions ou assertions en langage naturel.
![Bouton Demander à l'IA dans la barre de recherche supérieure](assets/nlq-button.png)

Le système utilise un Large Language Model (LLM) pour générer les filtres correspondants à partir de votre question. Le modèle construit les filtres au format OpenCTI filters avec des ``filterGroups`` vides. Ainsi, les filtres sont actuellement limités à un seul niveau d'imbrication : une liste de filtres séparés par un mode and/or unique.
Le LLM construit les filtres avec :

- les clés de filtre existantes (attributs, noms d'entrée de relations et certaines clés de filtre spéciales),
- les opérateurs disponibles (equals, greater than, etc.),
- les types d'entités et de relations existants pour les valeurs possibles des filtres de type d'entité.

Le résultat des filtres NLQ est ensuite utilisé pour afficher la liste des entités correspondantes.
![Exemple de résultats avec NLQ](assets/nlq-example.png)

Si la question n'est pas comprise ou hors du contexte cyber d'OpenCTI, aucun filtre ne pourra être trouvé.
![Exemple de résultats avec NLQ sans résultat](assets/nlq-no-result.png)


!!! avertissement "Notice sur l'utilisation des jetons et les coûts"

  La fonctionnalité Natural Language Query repose sur des prompts complexes envoyés au modèle de langage pour décrire la structure des filtres et fournir des exemples. Ces requêtes complexes peuvent générer une utilisation significative de jetons.
  Lors de l'utilisation d'un point de terminaison API personnalisé (par exemple, OpenAI, Mistral, AzureAI) avec votre propre clé API, cela peut entraîner une augmentation des coûts. Il est recommandé de consulter la documentation tarifaire de votre fournisseur pour estimer précisément les coûts.    
  Pour nos clients SaaS, les requêtes sont routées via notre instance de modèle hébergée et n'entraînent pas de coûts supplémentaires.

#### Résultats NLQ impliquant une entité

Si votre question inclut un terme détecté comme représentant une entité, une recherche sera déclenchée sur plusieurs champs (nom, valeur, alias, etc.) pour la résoudre.
- Si une correspondance est trouvée, son ID sera utilisé dans les filtres générés.
  ![Exemple de résultats avec NLQ et une entité trouvée](assets/nlq-result-found-entity.png)

- Si aucune correspondance n'est trouvée, la partie des filtres impliquant l'entité sera ignorée.
  ![Exemple de résultats avec NLQ et une entité non trouvée](assets/nlq-result-not-found-entity.png)

#### Limitations actuelles du modèle NLQ

Il s'agit de la première version d'un modèle NLQ. Il est encore en développement et peut ne pas encore gérer tous les cas d'usage.

En particulier, voici quelques limitations :

- Il n'est pas possible de rechercher parmi les relations (uniquement les entités).

  Exemple : ``Lister les relations impliquant Paradise Ransomware.``

- Le modèle n'est pas encore conçu pour gérer les dates.

  Exemple : ``Lister les rapports publiés après janvier.``

- Le modèle ne peut pas filtrer sur les propriétés des entités liées (informations de second niveau).

  Exemple : ``Lister les indicateurs liés à des malwares situés en Europe.``

- Pas encore de combinaisons logiques multi-niveaux, les requêtes nécessitant des combinaisons de filtres imbriqués (par exemple, mélange des modes AND/OR entre différents filtres) ne sont pas encore prises en charge.
  
  Exemple : ``Quels sont les malwares créés par admin ou ayant le label 'test' ?`` 


## Améliorer les éléments générés par Demander à l'IA

Il faut garder à l'esprit que la qualité du texte dépend fortement des capacités du LLM associé.

C'est pourquoi chaque texte généré par Demander à l'IA est fourni dans un panneau dédié, permettant de vérifier et de corriger toute erreur que le LLM pourrait avoir commise.

> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.