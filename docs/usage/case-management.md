# Gestion des cas

## Pourquoi la gestion des cas ?

Compiler les données CTI en un seul endroit, les dédupliquer et les corréler pour les transformer en Intelligence est très important. **Mais au final, il faut agir sur la base de cette Intelligence**. Certaines situations nécessitent une prise en charge, comme des incidents de cybersécurité, des demandes d'information ou des demandes de retrait. Certaines actions devront alors être tracées, coordonnées et supervisées. Certaines actions incluront des retours et la livraison de contenu.

OpenCTI inclut les [Cases](exploring-cases.md) pour permettre aux organisations de gérer les situations et d'organiser le travail de leur équipe. Mieux encore, **en réalisant la gestion des cas dans OpenCTI, vous traitez vos cas avec tout le contexte et l'Intelligence nécessaires, à portée de main.**

## Comment gérer un Case dans OpenCTI ?

De multiples situations peuvent être modélisées dans OpenCTI comme un Case, qu'il s'agisse d'une Incident Response, d'une Request for Takedown ou d'une Request for Information.

![Incident Responses' list](assets/cases-list.png)

Tous les Cases peuvent contenir toutes les entités et relations nécessaires pour représenter le contexte d'Intelligence lié à la situation. Au début de votre case, vous pouvez n'avoir que quelques Observables détectés dans un système. À la fin, vous pouvez avoir des Indicators, des Threat Actor, des systèmes impactés, des attack patterns. Tous représentent vos découvertes, prêtes à être présentées et exportées sous forme de graphe, rapport PDF, chronologie, etc.

![Incident Responses' list](assets/cases-observables.png)

Certains Cases peuvent nécessiter un travail collaboratif et des Tasks spécifiques à réaliser par des personnes ayant les compétences requises. OpenCTI permet d'associer des `Tasks` à vos Cases et de les assigner à des utilisateurs de la plateforme. Comme certains types de situations peuvent nécessiter les mêmes tâches, il est également possible de pré-définir des listes de tâches à appliquer à votre case. Vous pouvez définir ces listes en accédant au panneau Settings/Taxonomies/Case templates. Il suffit ensuite de les ajouter depuis l’aperçu du Case souhaité.

Astuce : Un utilisateur peut avoir un tableau de bord personnalisé affichant toutes les tasks qui lui ont été assignées.

![Incident Responses' list](assets/case-applying-template.png)

Comme pour les autres objets dans OpenCTI, il est aussi possible d'utiliser les `Notes` pour ajouter des commentaires d'investigation et d'analyse, afin d'enrichir le contenu de votre case avec des données non structurées et de tracer tout le travail effectué.

Vous pouvez également utiliser les `Opinions` pour recueillir des retours sur la gestion du Case, ce qui aide à construire des retours d'expérience (Lessons Learned).

![Incident Responses' list](assets/case-opinion.png)

Pour tracer l’évolution de votre Case et définir des workflows de résolution spécifiques, il est possible d’utiliser le `Status` (qui peut être défini dans Settings/Taxonomies/Status templates).

À la fin de votre Case, vous voudrez certainement faire un rapport sur ce qui a été réalisé. OpenCTI permet d’exporter le contenu du Case dans un PDF simple mais personnalisable (actuellement en refonte). Mais bien sûr, votre entreprise possède ses propres modèles de documents, n’est-ce pas ? Avec OpenCTI, il est possible d’y inclure de beaux graphiques. Par exemple, une vue Matrix des attack pattern de l’attaquant ou même un affichage graphique des connexions entre les éléments.

Nous travaillons également sur une vue Timeline plus pertinente, qui pourra aussi être exportée.

## Exemple d’usage : Un observable suspect est détecté par un système de défense. Est-ce important ?

- Quotidiennement, votre SIEM et EDR sont alimentés en Indicators of Compromise depuis votre instance OpenCTI.
- Aujourd’hui, votre SIEM a détecté le nom de domaine "bad.com" correspondant à l’un d’eux. Son alerte a été transférée à OpenCTI et a créé une relation `Sighting` entre votre système "SIEM permiter A" et l’Observable "bad.com".
- Vous êtes alerté immédiatement, car vous avez activé la règle d’inférence créant un `Incident` correspondant dans cette situation, et vous avez créé une alerte basée sur le nouvel Incident qui vous envoie une `notification` par email et un message Teams (webhook).
- Dans OpenCTI, il est possible de voir clairement le lien entre le système d’alerte, l’Observable détecté et l’Indicator correspondant. Mieux encore, tout le contexte de l’Indicator est visible. Il est lié à une `campaign` de phishing notoire et récente ciblant votre `sector` d’activité. "bad.com" est clairement un élément à investiguer rapidement.
- Vous sélectionnez rapidement tout le contexte trouvé et l’ajoutez à un nouveau `Incident response` case. Vous positionnez la priorité sur High, au vu du contexte, et la sévérité sur Low, car il n’est pas encore certain qu’une interaction ait eu lieu avec "bad.com".
- Vous assignez également le case à un de vos collègues, en charge de l’investigation. Pour le guider, vous créez aussi une `Task` dans votre case afin de vérifier si une interaction réelle a eu lieu avec "bad.com".

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.