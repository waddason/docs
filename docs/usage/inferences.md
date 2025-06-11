# Inférences et raisonnement

## Vue d’ensemble

La capacité d’inférences et de raisonnement d’OpenCTI est un moteur robuste qui automatise la création de relations au sein de vos données de cybermenace. Cette fonctionnalité, située au cœur d’OpenCTI, permet d’appliquer des règles logiques aux relations existantes, générant ainsi automatiquement de nouvelles connexions pertinentes.

## Comprendre les inférences et le raisonnement

Les inférences et le raisonnement servent de moteur intelligent à OpenCTI. Ils interprètent vos données de manière logique. En activant des règles prédéfinies spécifiques (il en existe une vingtaine), OpenCTI peut déduire de nouvelles relations à partir de celles déjà existantes. Par exemple, s’il existe une connexion indiquant qu’un Intrusion Set cible un pays spécifique, et une autre relation précisant que ce pays fait partie d’une région plus vaste, OpenCTI peut automatiquement en déduire que l’Intrusion Set cible également la région entière.

## Principaux avantages

- Efficacité : Réduit la charge de travail manuelle en automatisant la création de relations, ce qui permet de gagner un temps précieux pour les analystes.
- Exhaustivité : Comble les lacunes relationnelles, garantissant une base de données de cybermenace complète et interconnectée.
- Précision : Minimise les erreurs de saisie manuelle en déduisant les relations à partir d’une logique prédéfinie et fiable.

## Fonctionnement

Lorsque vous activez une règle d’inférence, OpenCTI analyse en continu vos relations existantes et applique les règles logiques définies. Ces règles sont des énoncés logiques qui définissent les conditions de création de nouvelles relations. Lorsque l’ensemble des conditions est rempli, OpenCTI crée automatiquement la relation correspondante.

Par exemple, si vous activez une règle comme suit :

SI [Entité A cible Identité B] ET [Identité B fait partie de Identité C]
ALORS [Entité A cible Identité C]

OpenCTI appliquera cette règle aux données existantes. S’il trouve un Intrusion Set (« Entité A ») ciblant un pays spécifique (« Identité B ») et que ce pays fait partie d’une région plus vaste (« Identité C »), la plateforme établira automatiquement une relation entre l’Intrusion Set et la région.

## Identifier les relations inférées

**Dans les graphes de connaissances :** Les relations inférées sont représentées par des lignes pointillées d’une couleur différente, ce qui les distingue des relations non inférées.

![Inferred_relationships_in_graph](assets/inferred-rel-in-graph.png)

**Dans les listes :** Dans une liste de relations, une icône de baguette magique à la fin de la ligne indique une relation créée par inférence.

![Inferred_relationships_in_list](assets/inferred-rel-in-list.png)

## Ressources supplémentaires

- **Administration :** Pour consulter les règles d’inférence existantes et les activer/désactiver, se référer à la page [Rules engine](../administration/reasoning.md) dans la section Administration de la documentation.
- **Playbooks :** Les [OpenCTI playbooks](automation.md) sont des scénarios d’automatisation hautement personnalisables. Cette intégration transparente permet d’automatiser davantage, rendant vos processus de cybermenace encore plus efficaces et adaptés à vos besoins spécifiques. Plus d’informations dans notre [article de blog](https://blog.filigran.io/introducing-threat-intelligence-automation-and-playbooks-in-opencti-b9e2f9483aba).


> Taduction automatique de la documentation en ligne d'OpenCTI 6.6.x le 10 juin 2025.