# Techniques

En cliquant sur "Techniques" dans la barre latérale gauche, vous accédez à tous les onglets "Techniques", visibles sur la barre supérieure à gauche. Par défaut, l'utilisateur accède directement à l'onglet "Attack pattern", mais peut également naviguer vers les autres onglets.

Depuis la section `Techniques`, les utilisateurs peuvent accéder aux onglets suivants :

- `Attack pattern` : attaques utilisées par les threat actors pour mener leurs attaques. Par défaut, OpenCTI est fourni avec les attack patterns des matrices MITRE ATT&CK (pour CTI) et DISARM (pour FIMI).
- `Narratives` : dans OpenCTI, les narratives utilisées par les threat actors peuvent être représentées et liées à d'autres objets. Les narratives sont principalement utilisées dans le contexte des campagnes de désinformation où il est important de tracer quelles narratives ont été et sont encore utilisées par les threat actors.
- `Courses of action` : un Course of Action est une action entreprise soit pour prévenir une attaque, soit pour répondre à une attaque en cours. Il peut décrire des réponses techniques et automatisables (application de correctifs, reconfiguration de firewalls) mais aussi des actions de plus haut niveau comme la formation des employés ou des changements de politique. Par exemple, un course of action pour atténuer une vulnérabilité pourrait décrire l'application du correctif qui la corrige.
- `Data sources` : les data sources représentent les différents sujets/thèmes d'information pouvant être collectés par des capteurs/logs. Les data sources incluent également les data components,
- `Data components` : les data components identifient des propriétés/valeurs spécifiques d'une data source pertinentes pour détecter une technique ou sous-technique ATT&CK donnée.

## Attack pattern

### Présentation générale

Attack patterns utilisés par les threat actors pour mener leurs attaques. Par défaut, OpenCTI est fourni avec les attack patterns des matrices MITRE ATT&CK et CAPEC (pour CTI) et de la matrice DISARM (pour FIMI).

Dans la documentation MITRE STIX 2.1, un `Attack pattern` est défini comme suit :

> Les Attack Patterns sont un type de TTP qui décrivent les façons dont les adversaires tentent de compromettre des cibles. Les Attack Patterns servent à catégoriser les attaques, à généraliser des attaques spécifiques selon les patterns qu'elles suivent, et à fournir des informations détaillées sur la manière dont les attaques sont réalisées. Un exemple d'attack pattern est le "spear phishing" : un type d'attaque courant où un attaquant envoie un e-mail soigneusement conçu à une cible dans le but de la faire cliquer sur un lien ou ouvrir une pièce jointe pour délivrer un malware. Les Attack Patterns peuvent aussi être plus spécifiques ; le spear phishing tel que pratiqué par un threat actor particulier (par exemple, il peut généralement prétendre que la cible a gagné un concours) peut aussi être un Attack Pattern.

En cliquant sur l'onglet Attack pattern en haut à gauche, vous accédez à la liste de tous les attack patterns auxquels vous avez accès, en fonction de vos [allowed marking definitions](../administration/users.md). Vous pouvez ensuite rechercher et filtrer selon certains attributs communs et spécifiques des attack patterns.

### Visualiser la connaissance associée à un Attack pattern

En cliquant sur un Attack pattern, vous arrivez sur son onglet Overview. Pour un Attack pattern, les onglets suivants sont accessibles :

- Overview : l'overview d'un Attack pattern est un peu différente de celle décrite [ici](overview.md). Le bloc "Details" est plus structuré et contient des informations sur :

   - parent ou subtechniques (comme dans les matrices MITRE ATT&CK),
   - phases du kill chain associées
   - Plateforme sur laquelle l'Attack pattern est utilisable,
   - permission requise pour l'appliquer
   - Technique de détection associée
   - Courses of action pour atténuer l'Attack pattern
   - Data components dans lesquels trouver des données pour détecter l'utilisation de l'Attack pattern
- Knowledge : un onglet complexe qui regroupe toute la connaissance structurée liée à l'Attack pattern. Différentes vues thématiques sont proposées pour visualiser facilement les Threat Actors et Intrusion Sets utilisant ces techniques, les incidents liés, etc.
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à l'Attack pattern. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md).
- Data : comme décrit [ici](overview.md).
- History : comme décrit [ici](overview.md).

## Narratives

### Présentation générale

Dans OpenCTI, les narratives utilisées par les threat actors peuvent être représentées et liées à d'autres objets. Les narratives sont principalement utilisées dans le contexte des campagnes de désinformation où il est important de tracer quelles narratives ont été et sont encore utilisées par les threat actors.

Un exemple de Narrative peut être "Le pays A est faible et corrompu" ou "L'opération en cours vise à libérer le peuple".

Une Narrative peut être un moyen dans le cadre d'une attaque plus large ou l'objectif de l'opération, une vision à imposer.

En cliquant sur l'onglet Narrative en haut à gauche, vous accédez à la liste de toutes les Narratives auxquelles vous avez accès, en fonction de vos [allowed marking definitions](../administration/users.md). Vous pouvez ensuite rechercher et filtrer selon certains attributs communs et spécifiques des narratives.

### Visualiser la connaissance associée à une Narrative

En cliquant sur une Narrative, vous arrivez sur son onglet Overview. Pour une Narrative, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md).
- Knowledge : un onglet complexe qui regroupe toute la connaissance structurée liée aux Narratives. Différentes vues thématiques sont proposées pour visualiser facilement les Threat actors et Intrusion Set utilisant la Narrative, etc.
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés à la technique. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md).
- Data : comme décrit [ici](overview.md).
- History : comme décrit [ici](overview.md).

## Courses of action

### Présentation générale

Dans la documentation MITRE STIX 2.1, un `Course of action` est défini comme suit :

> Un Course of Action est une action entreprise soit pour prévenir une attaque, soit pour répondre à une attaque en cours. Il peut décrire des réponses techniques et automatisables (application de correctifs, reconfiguration de firewalls) mais aussi des actions de plus haut niveau comme la formation des employés ou des changements de politique. Par exemple, un course of action pour atténuer une vulnérabilité pourrait décrire l'application du correctif qui la corrige.

En cliquant sur l'onglet `Courses of action` en haut à gauche, vous accédez à la liste de tous les Courses of action auxquels vous avez accès, en fonction de vos [allowed marking definitions](../administration/users.md). Vous pouvez ensuite rechercher et filtrer selon certains attributs communs et spécifiques des courses of action.

### Visualiser la connaissance associée à un Course of action

En cliquant sur un `Course of Action`, vous arrivez sur son onglet Overview. Pour un Course of action, les onglets suivants sont accessibles :

- Overview : l'overview d'un Course of action est un peu différente de celle décrite [ici](overview.md). Dans le bloc "Details", les attack patterns atténués sont listés.
- Knowledge : un onglet complexe qui regroupe toute la connaissance structurée liée aux Narratives. Différentes vues thématiques sont proposées pour visualiser facilement les Threat actors et Intrusion Set utilisant la Narrative, etc.
- Content : cet onglet spécifique permet de prévisualiser, gérer et rédiger des livrables associés au Course of action. Par exemple, un rapport analytique à partager avec d'autres équipes, des fichiers markdown pour alimenter un wiki collaboratif, etc. Comme décrit [ici](overview.md#content-section).
- Analyses : comme décrit [ici](overview.md).
- Data : comme décrit [ici](overview.md).
- History : comme décrit [ici](overview.md).

## Data sources & Data components

### Présentation générale

Dans la documentation MITRE ATT&CK, les `Data sources` sont définies comme suit :

> Les data sources représentent les différents sujets/thèmes d'information pouvant être collectés par des capteurs/logs. Les data sources incluent également les data components, qui identifient des propriétés/valeurs spécifiques d'une data source pertinentes pour détecter une technique ou sous-technique ATT&CK donnée.

### Visualiser la connaissance associée à une Data source ou un Data component

En cliquant sur une `Data source` ou un `Data component`, vous arrivez sur son onglet Overview. Pour un Course of action, les onglets suivants sont accessibles :

- Overview : comme décrit [ici](overview.md).
- Data : comme décrit [ici](overview.md).
- History : comme décrit [ici](overview.md).


> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.