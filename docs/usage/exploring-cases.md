# Cas

En cliquant sur "Cases" dans la barre latérale gauche, vous accédez à tous les onglets "Cases", visibles en haut à gauche. Par défaut, l'utilisateur accède directement à l'onglet "Incident Responses", mais peut également naviguer vers les autres onglets.

Comme les Analyses, les `Cases` peuvent contenir d'autres objets. Ainsi, en ajoutant du contexte et les résultats de vos investigations dans le case, vous pourrez obtenir une vue d'ensemble à jour de la situation en cours, et produire plus facilement un rapport d'incident par la suite.

Depuis la section `Cases`, les utilisateurs peuvent accéder aux onglets suivants :

- `Incident Responses` : Ce type de Cases est dédié à la gestion des incidents. Un Incident Response case ne représente pas un incident, mais tout le contexte et les actions qui vont englober la réponse à un incident spécifique.
- `Request for Information` : Les équipes CTI sont souvent sollicitées pour fournir des informations et analyses approfondies sur un sujet particulier, qu'il soit lié à un incident en cours ou à une menace émergente. Les Request for Information cases permettent de stocker le contexte et les actions relatives à ce type de demande et à sa réponse.
- `Request for Takedown` : Lorsqu'une organisation est ciblée par une campagne d'attaque, une action de réponse typique peut consister à demander le Takedown d'éléments de l'infrastructure d'attaque, par exemple un nom de domaine usurpant l'organisation pour piéger ses employés, ou une adresse email utilisée pour diffuser du contenu de phishing. Comme le Takedown nécessite dans la plupart des cas de contacter des fournisseurs externes et d'être efficace rapidement, il requiert souvent des workflows spécifiques. Les Request for Takedown cases offrent un espace dédié pour gérer ces actions spécifiques.
- `Tasks` : Dans chaque case, des tâches doivent être réalisées pour le résoudre. L'onglet Tasks permet de consulter toutes les tâches créées afin de voir rapidement celles en retard, ou de visualiser toutes les tâches assignées à un utilisateur spécifique.
- `Feedbacks` : Si vous utilisez votre plateforme pour interagir avec d'autres équipes et leur fournir de la CTI Knowledge, certains utilisateurs peuvent souhaiter vous faire un retour à ce sujet. Ces feedbacks peuvent facilement être considérés comme un autre type de case à résoudre, car ils font souvent référence à des incohérences ou des lacunes dans la Knowledge.

![Cases Default page is Incident Response](assets/cases-default-landing-page.png)

## Incident Response, Request for Information & Request for Takedown

### Présentation générale

Les Incident responses, Request for Information & Request for Takedown cases sont une partie importante du système de gestion des cases dans OpenCTI. Ici, vous pouvez organiser le travail de votre équipe pour répondre à des situations de cybersécurité. Vous pouvez également donner du contexte à l'équipe et aux autres utilisateurs de la plateforme concernant la situation et les actions (à) prendre.

Pour gérer la situation, il est possible de créer des `Tasks` et de les assigner à des utilisateurs de la plateforme, soit en créant directement une Task, soit en appliquant un modèle de Case qui ajoutera une liste de tâches prédéfinies.

Pour apporter du contexte, vous pouvez utiliser votre Case comme un container (comme les Reports ou Groupings), ce qui vous permet d'y ajouter toute la Knowledge de votre plateforme. Vous pouvez également utiliser cette possibilité pour tracer votre investigation, votre Case jouant le rôle de rapport d'incident. Vous trouverez plus d'informations sur la gestion des cases [ici](case-management.md).

Les Incident Response, Request for Information & Request for Takedown ne sont pas des objets STIX 2.1.

En cliquant sur les onglets Incident Response, Request for Information & Request for Takedown en haut, vous voyez la liste de tous les Cases auxquels vous avez accès, selon vos [allowed marking definitions](../administration/users.md). Vous pouvez ensuite rechercher et filtrer selon certains attributs communs et spécifiques.

### Visualiser la Knowledge dans un Incident Response, Request for Information & Request for Takedown

En cliquant sur un Incident Response, Request for Information ou Request for Takedown, vous arrivez sur l'onglet Overview. Les onglets suivants sont accessibles :

- Overview : L'Overview des Cases diffère légèrement de l'habituel (décrit [ici](overview.md#overview-section)). L'Overview des Cases affiche également la liste des tâches associées au case. Il permet aussi de mettre en avant l'Incident, le Report ou le Sighting à l'origine du case. Si d'autres cases contiennent des Observables en commun avec votre Case, ils seront affichés comme Related Cases dans l'Overview.
- Knowledge : un onglet complexe qui regroupe toute la Knowledge structurée contenue dans le Case, accessible via différentes vues (voir ci-dessous pour plus de détails). Comme décrit [ici](overview.md#knowledge-section).
- Content : un onglet pour accéder au content mapping, au suggested mapping et permet de prévisualiser, gérer et rédiger les livrables associés au Case. Par exemple, un rapport analytique à partager avec d'autres équipes, un fichier markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Entities : Un tableau contenant tous les SDO (Stix Domain Objects) contenus dans le Case, avec recherche et filtres disponibles. Il indique également si le SDO a été ajouté directement ou via [inférences avec le reasoning engine](inferences.md)
- Observables : Un tableau contenant tous les SCO (Stix Cyber Observable) contenus dans le Case, avec recherche et filtres disponibles. Il indique également si le SDO a été ajouté directement ou via [inférences avec le reasoning engine](inferences.md)
- Data : comme décrit [ici](overview.md#data-section).

Explorer et modifier la Knowledge structurée contenue dans un Case peut se faire sous différents angles.

#### Vue Graphique

![Graph View of a Case](assets/case-graph.png)

En vue Graph, les STIX SDO sont affichés comme des nœuds du graphe et les relations comme des liens. Les nœuds sont colorés selon leur type. Les relations directes sont affichées en trait plein et les relations inférées en pointillé.
En haut à droite, vous trouverez une série d'icônes. De là, il est possible de changer le type de vue actuel. Vous pouvez également effectuer des actions globales sur la Knowledge du Case. Deux d'entre elles sont à noter :

- Suggestions : Cet outil vous suggère des relations logiques à ajouter entre vos objets contenus afin de donner plus de cohérence à votre Knowledge.
- Share with an Organization : si vous avez désigné une Organisation principale dans les paramètres de la plateforme, vous pouvez ici partager votre Case et son contenu avec les utilisateurs d'une autre Organisation.
En bas, de nombreuses options permettent de manipuler le graphe :
- Plusieurs options pour façonner le graphe et appliquer des forces aux nœuds et liens
- Plusieurs options de sélection multiple
- Plusieurs filtres, dont un sélecteur de plage temporelle permettant de voir l'évolution de la Knowledge dans le Case.
- Plusieurs outils de création et d'édition pour modifier la Knowledge contenue dans le Case.

#### Vue Timeline

![Timeline view of a Case](assets/case-timeline.png)

Cette vue permet de visualiser la Knowledge structurée de façon chronologique. Elle est particulièrement utile dans le contexte d'un Case, permettant de voir la chaîne des événements, que ce soit du point de vue de l'attaque, de la défense ou les deux.
La vue peut être filtrée et afficher également les relations.

#### Vue Matrix

Si votre Case contient des attack patterns, vous pourrez les visualiser dans une vue Matrix.

### Restreindre l'accès à un Incident Response, Request for Information & Request for Takedown

#### Ségrégation par organisation

Si vous avez désigné une Organisation principale dans les paramètres de la plateforme, vous pouvez partager votre Case et son contenu avec les utilisateurs d'une autre Organisation.

![containers-organization-sharing-button.png](assets%2Fcontainers-organization-sharing-button.png)

[lire plus sur la ségrégation par organisation](..%2Fadministration%2Forganization-segregation.md)

#### Membres autorisés

**Membres autorisés** permet de restreindre l'accès à une entité à certains utilisateurs, groupes ou organisations au sein de la plateforme.

Pour définir les membres autorisés, il faut cliquer sur le bouton '**Gérer la restriction d'accès**'. Ce bouton est visible si vous disposez de la capacité '**Gérer les membres autorisés**'.

![containers-manage-access-restriction-button.png](assets%2Fcontainers-manage-access-restriction-button.png)

## Tasks

Les Tasks sont des actions à réaliser dans le contexte d'un Case (Incident Response, Request for Information, Request for Takedown). Généralement, une task est assignée à un utilisateur, mais des tâches importantes peuvent impliquer plusieurs participants.

En cliquant sur l'onglet Tasks en haut de l'interface, vous voyez la liste de toutes les Tasks auxquelles vous avez accès, selon vos [allowed marking definitions](../administration/users.md). Vous pouvez ensuite rechercher et filtrer selon certains attributs communs et spécifiques des tasks.

En cliquant sur une Task, vous arrivez sur son onglet Overview. Pour une Task, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Content : comme décrit [ici](overview.md#content-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

## Feedbacks

Lorsqu'un utilisateur remplit un formulaire de feedback depuis son menu Profil/Feedback, il sera accessible ici.

Cette fonctionnalité offre la possibilité d'échanger avec les autres utilisateurs de votre plateforme et de répondre directement à leurs préoccupations concernant celle-ci ou la Knowledge, sans avoir besoin d'un logiciel tiers.

![Feedback Overview](assets/feedback-overview.png)

En cliquant sur un Feedback, vous arrivez sur son onglet Overview. Pour un Feedback, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md#overview-section).
- Content : comme décrit [ici](overview.md#content-section).
- Data : comme décrit [ici](overview.md#data-section).
- History : comme décrit [ici](overview.md#history-section).

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.