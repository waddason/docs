# Automatisation des Playbooks

!!! astuce "Édition Entreprise"

    L'automatisation des playbooks est disponible sous licence "OpenCTI Enterprise Edition". Veuillez lire la [page dédiée](../administration/enterprise.md) pour obtenir toutes les informations.


Les playbooks OpenCTI sont des scénarios d'automatisation flexibles, entièrement personnalisables et activables par les administrateurs de la plateforme pour enrichir, filtrer et modifier les données créées ou mises à jour dans la plateforme.

L'automatisation des playbooks est accessible dans l'interface utilisateur sous Données > Traitement > Automatisation.

!!! note "Droit requis"

    Il est nécessaire de disposer de la [capacité](../administration/users.md) "Gérer les identifiants" pour utiliser l'automatisation des playbooks, car vous pourrez manipuler des données auxquelles les utilisateurs simples n'ont pas accès.

Vous pourrez alors :

- ajouter des labels en fonction des résultats d'enrichissement pour les utiliser dans des flux de détection pilotés par la cybermenace,
- créer des rapports et des cas selon divers critères,
- déclencher des enrichissements ou des webhooks dans certaines conditions,
- modifier des attributs tels que first_seen et last_seen en fonction d'autres connaissances,
- etc.

## Philosophie des Playbooks

Considérer un playbook comme un pipeline de bundles STIX 2.1.

En commençant par un composant écoutant un flux de données, chaque composant suivant du playbook traite un bundle STIX reçu. Ces composants ont la capacité de modifier le bundle puis de transmettre le résultat modifié aux composants connectés.

Dans ce paradigme, les composants peuvent envoyer le bundle STIX 2.1 à plusieurs composants, permettant le développement de plusieurs branches dans votre playbook.

Un playbook bien conçu se termine par un composant exécutant une action basée sur les informations traitées. Par exemple, cela peut consister à écrire le bundle STIX 2.1 dans un flux de données.

!!! note "Valider l'ingestion"

    Le bundle STIX traité par le playbook ne sera pas écrit dans la plateforme sans l'indiquer explicitement via le composant approprié, c'est-à-dire "Envoyer pour ingestion".

## Créer un Playbook

Il est possible de créer autant de playbooks que nécessaire, chacun fonctionnant indépendamment. Vous pouvez donner un nom et une description à chaque playbook.

![Créer un nouveau playbook](assets/playbook_create.png)

La première étape à définir dans le playbook est votre source d'événement.
Pour cela, cliquer sur le rectangle gris au centre de l'espace de travail et sélectionner le composant d'entrée adapté à vos besoins.

![Choisir le composant d'entrée](assets/playbook_input.png)

### Écouter les événements de connaissance
Avec cette source d'événement, le playbook sera déclenché sur tout événement de connaissance (création, mise à jour ou suppression) correspondant aux filtres sélectionnés.
Notez que vous êtes limité à un sous-ensemble de filtres, disponibles pour les événements de flux contenant des objets de données STIX.

![Écoute d'un événement de création pour les IPs et noms de domaine TLP:GREEN](assets/playbook_listen.png)

### Interroger la connaissance à intervalles réguliers

Avec ce type de source d'événement, le playbook interrogera la connaissance de façon horaire / quotidienne / hebdomadaire / mensuelle, selon les filtres que vous aurez définis.

Si vous cochez l'option "Uniquement les entités modifiées depuis la dernière exécution", alors le playbook exclura à chaque exécution les entités qui n'ont pas changé depuis la dernière exécution.

![Interroger les derniers incidents](assets/playbook_query_regular.png)

### Disponible pour l'enrôlement / déclenchement manuel

Utiliser cette source d'événement pour configurer un playbook qui sera déclenché manuellement sur des entités spécifiques.
Vous pouvez configurer des filtres dans le composant afin que ce playbook soit suggéré pour certaines entités lors de l'enrôlement manuel.
Pour plus de détails sur l'enrôlement manuel, voir la section dédiée ci-dessous.

![Enrôler manuellement des incidents importants](assets/playbook_manual_source.png)

## Concevoir votre workflow

Vous disposez ensuite de choix flexibles pour les étapes suivantes afin de :

- filtrer la connaissance initiale,
- enrichir les données via des sources externes et des règles internes,
- modifier les entités et relations en appliquant des patchs,
- écrire les données, envoyer des notifications,
- etc.

... en utilisant les différents composants de playbook à votre disposition.

En cliquant sur le bouton burger d'un composant, vous pouvez le remplacer par un autre.

En cliquant sur l'icône flèche en bas à droite d'un composant, vous pouvez développer une nouvelle branche au même niveau.

En cliquant sur le bouton "+" sur un lien entre deux composants, vous pouvez insérer un composant entre les deux.

Ne pas oublier de démarrer votre playbook lorsque prêt, via l'option Démarrer du bouton burger placé près du nom de votre playbook.

## Composants des playbooks

![Liste des composants actuels](assets/playbook_components.png)

#### Journaliser les données dans la sortie standard

Écrit le bundle STIX 2.1 reçu dans les logs de la plateforme avec un niveau de log configurable, puis transmet le bundle STIX 2.1 non modifié.

#### Envoyer pour ingestion

Transmet le bundle STIX 2.1 pour qu'il soit écrit dans le flux de données. Ce composant n'a pas de sortie et doit terminer une branche de votre playbook.

#### Filtrer la connaissance

Permet de définir un filtre et de l'appliquer au bundle STIX 2.1 reçu. Le composant a 2 sorties, une pour les données correspondant au filtre et une pour le reste.

Par défaut, le filtrage s'applique aux entités ayant déclenché le playbook. Vous pouvez basculer l'option correspondante pour l'appliquer à tous les éléments du bundle (éléments pouvant résulter d'un enrichissement par exemple).

#### Enrichir via un connector

Envoie le bundle STIX 2.1 reçu au connector d'enrichissement indiqué et transmet le bundle modifié.
Les entités transmises à cette étape doivent être compatibles avec le connector d'enrichissement utilisé, sinon le playbook peut s'arrêter à cette étape. Le composant *Réduire la connaissance* peut être utilisé pour filtrer les entités incompatibles à cette étape.

#### Manipuler la connaissance

Ajoute, remplace ou supprime les attributs compatibles des entités contenues dans le bundle STIX 2.1 reçu et transmet le bundle modifié.

Par défaut, la modification s'applique aux entités ayant déclenché le playbook. Vous pouvez basculer l'option correspondante pour l'appliquer à tous les éléments du bundle (éléments pouvant résulter d'un enrichissement par exemple).

#### Container wrapper

Modifie le bundle STIX 2.1 reçu pour inclure les entités dans un container du type configuré.
Par défaut, l'encapsulation s'applique aux entités ayant déclenché le playbook. Vous pouvez basculer l'option correspondante pour l'appliquer à tous les éléments du bundle (éléments pouvant résulter d'un enrichissement par exemple).

#### Partager avec des organisations

Partage chaque entité du bundle STIX 2.1 reçu avec les organisations configurées. Votre plateforme doit avoir une organisation principale déclarée dans Paramètres/Paramètres.

#### Appliquer une règle prédéfinie

Applique une règle d'automatisation complexe intégrée. Ce type de règle peut impacter les performances. Les règles actuelles sont :

- Extension du calcul First/Last seen à partir de la date de publication du rapport : renseigne les dates first seen et last seen des entités contenues dans le rapport à partir de sa date de publication,
- Résoudre les indicateurs à partir des observables (ajouter dans le bundle) : récupère tous les indicateurs liés aux observables du bundle depuis la base de données,
- Résoudre les observables sur lesquels un indicator est basé (ajouter dans le bundle) : récupère tous les observables liés à l'indicator du bundle depuis la base de données,
- Résoudre les références de container (ajouter dans le bundle) : ajoute au bundle toutes les relations et entités que le container contient (si l'entité ayant déclenché le playbook n'est pas un container, la sortie de ce composant sera vide),
- Résoudre les relations et entités voisines (ajouter dans le bundle) : ajoute au bundle toutes les relations de l'entité ayant déclenché le playbook, ainsi que toutes les entités à l'extrémité de ces relations, c'est-à-dire les "premiers voisins" (si l'entité est un container, la sortie de ce composant sera vide).


#### Envoyer au notifier

Génère une notification à chaque fois qu'un bundle STIX 2.1 est reçu.

#### Promouvoir un observable en indicator

Génère un indicator à partir des observables contenus dans le bundle STIX 2.1 reçu.

Par défaut, cela s'applique aux entités ayant déclenché le playbook. Vous pouvez basculer l'option correspondante pour l'appliquer à tous les observables du bundle (par exemple, des observables pouvant résulter d'une règle prédéfinie).

Vous pouvez également ajouter tous les indicators et relations générés par ce composant dans l'entité ayant déclenché le playbook, si cette entité est un container.

#### Extraire les observables d'un indicator

Extrait les observables à partir des indicators contenus dans le bundle STIX 2.1 reçu.

Par défaut, cela s'applique aux entités ayant déclenché le playbook. Vous pouvez basculer l'option correspondante pour l'appliquer à tous les indicators du bundle (par exemple, des indicators pouvant résulter d'un enrichissement).

Vous pouvez également ajouter tous les observables et relations générés par ce composant dans l'entité ayant déclenché le playbook, si cette entité est un container.

#### Réduire la connaissance

Filtre toutes les entités à l'étape courante qui ne correspondent pas aux conditions de filtre de l'étape. Si l'entité d'origine ayant déclenché le playbook est un container, comme un rapport ou un cas, alors le container lui-même ne peut pas être filtré et sera transmis aux étapes suivantes.

## Enrôler manuellement une entité dans un playbook

Il est possible d'enrôler individuellement des entités dans des playbooks via l'action "Enrôler dans un playbook" depuis la vue de détail de l'entité.

![Enrôler une entité dans un playbook](assets/playbook_enroll_entity.png)

Cela ouvrira un tiroir où vous pourrez choisir le playbook à déclencher sur cette entité.

![Enrôler une entité dans un playbook](assets/playbook_enroll_select.png)

Dans cette liste, vous trouverez :

* les playbooks actifs ayant défini une source d'événement "Disponible pour l'enrôlement / déclenchement manuel"
* les playbooks actifs avec une source d'événement "Écouter les événements de connaissance" dont les filtres correspondent à l'entité

## Surveiller l'activité des playbooks

En haut à droite de l'interface, il est possible d'accéder à la trace d'exécution de votre playbook et de consulter les données brutes après chaque étape de l'exécution du playbook.

![Suivi des étapes](assets/playbook_traces.png)

> Traduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.