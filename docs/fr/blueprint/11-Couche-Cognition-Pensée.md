# 11. Couche de Cognition — Pensée

Le sous-système de Pensée de la Couche de Cognition est le « centre de mémoire et de compréhension » d'iFay — il gère la mémoire d'iFay, acquiert des connaissances externes et maintient une compréhension profonde de vous.


---

## 11.2 Connaissances externes

## Définition en une ligne

Les Connaissances externes sont la **bibliothèque et le consultant expert** d'iFay — le Tas de données personnelles est la propre mémoire d'iFay, tandis que les Connaissances externes sont la bibliothèque qu'iFay peut consulter et les experts qu'il peut interroger. Elles donnent à iFay des connaissances au-delà des propres capacités du Human Prime.

## Pourquoi c'est nécessaire

Peu importe la qualité de votre mémoire, vous ne pouvez pas tout retenir. Quand vous rencontrez un problème que vous ne comprenez pas, que faites-vous ? Vous allez à la bibliothèque chercher, ou consultez un professionnel.

iFay fonctionne de la même manière. Le Tas de données personnelles stocke vos propres données et souvenirs, mais vos connaissances sont limitées. Le module de Connaissances externes permet à iFay de **dépasser sa propre mémoire** pour consulter des bases de connaissances externes et interroger des modèles intelligents externes — tout comme une personne entrant dans une bibliothèque ou appelant un expert.

## Sa position dans l'architecture

```
Architecture à quatre couches d'iFay
├── Couche Sociale
├── Couche d'Interaction
│   └── ...
├── Couche de Cognition          ← Les Connaissances externes sont ici
│   ├── Pensée
│   │   ├── Tas de données personnelles  ← Votre propre mémoire
│   │   ├── 👉 Connaissances externes    ← Bibliothèque et consultant expert
│   │   └── Conscience alignée           ← Compréhension de vous
│   └── Compétences
│       ├── Compétences enregistrées     ← Les sources de connaissances externes sont aussi un type de « compétence »
│       └── ...
└── Couche Ego
```

Les Connaissances externes se situent dans le **sous-système de Pensée de la Couche de Cognition**. Ce qui les rend uniques : les sources de connaissances externes sont traitées comme un **type de compétence** dans le système d'iFay. Cela signifie que l'intégration de connaissances externes suit le même flux d'enregistrement, d'autorisation et d'invocation que les autres compétences.

La relation entre les Connaissances externes et le Tas de données personnelles est comme « bibliothèque » et « carnet personnel » : après avoir fini de lire un livre emprunté à la bibliothèque, vous écrivez le contenu important dans votre carnet. De même, les informations qu'iFay acquiert des sources de connaissances externes sont intégrées dans le Tas de données personnelles, devenant partie de la propre « mémoire » d'iFay.

## Comment ça fonctionne

Le fonctionnement des Connaissances externes peut être résumé en trois mots-clés : **Connecter, Interroger, Intégrer**.

**1. Connecter — Liaison aux sources de connaissances externes**

Les sources de connaissances externes sont variées :
- **Bases de connaissances** : Bases de connaissances médicales, juridiques, encyclopédies
- **Grands modèles de langage** : GPT, Claude et autres modèles IA généraux
- **Systèmes experts** : Systèmes de raisonnement spécialisés pour des domaines spécifiques
- **Moteurs de recherche** : Informations publiques sur Internet

Ces sources de connaissances se connectent à iFay via **SSP (Protocole de partage de compétences)**. SSP est un protocole standardisé qui ouvre les services et interfaces — originalement disponibles uniquement pour des clients spécifiques — à l'ensemble du réseau.

**2. Interroger — Poser des questions comme consulter un expert**

Quand iFay a besoin de connaissances externes, il envoie une requête à la source de connaissances correspondante. Chaque résultat de requête est accompagné d'un **score de confiance** — indiquant à iFay la fiabilité de la réponse. iFay peut synthétiser les réponses de multiples sources de connaissances et sélectionner l'information la plus fiable.

**3. Intégrer — Les connaissances apprises deviennent les vôtres**

Les informations acquises des sources de connaissances externes ne sont pas juste « utiliser et jeter ». Les connaissances importantes sont intégrées dans le Tas de données personnelles, devenant partie de la propre mémoire d'iFay.

**Et si une source de connaissances est indisponible ?**

Le réseau pourrait se déconnecter, ou une source de connaissances pourrait être hors ligne. Dans ce cas, le module de Connaissances externes **se replie sur les connaissances en cache du Tas de données personnelles**. Pendant ce temps, iFay notifie la Couche de Cognition qu'il « utilise actuellement des connaissances en cache, qui pourraient ne pas être les plus récentes ».

## Relations avec les autres modules

| Module associé | Relation | Analogie corporelle |
|----------------|----------|---------------------|
| **Tas de données personnelles** | Les informations acquises par les Connaissances externes sont intégrées dans le Tas de données personnelles | Connaissances apprises à la bibliothèque → écrites dans votre carnet |
| **Compétences enregistrées** | Les sources de connaissances externes sont enregistrées et gérées comme un type de compétence | Une carte de bibliothèque est aussi un type de « justificatif de compétence » |
| **Conscience alignée** | La Conscience alignée aide à filtrer les connaissances externes pertinentes pour le Human Prime | Vos intérêts déterminent quels livres vous empruntez à la bibliothèque |
| **Compétences internes** | Les Compétences internes vérifient si les connaissances externes sont en conflit avec l'intention du Human Prime | Utiliser votre propre jugement pour évaluer la crédibilité des informations externes |
| **Protocole SSP** | Les sources de connaissances externes se connectent via le protocole SSP standardisé | Les règles d'emprunt unifiées de la bibliothèque |

## Histoires de scénarios

### Scénario 1 : Vous aider à comprendre un rapport de bilan de santé

Vous recevez votre rapport de bilan de santé annuel, plein d'indicateurs incompréhensibles : triglycérides 2,8 mmol/L, cholestérol LDL 3,9 mmol/L, acide urique 480 μmol/L…

Vous dites à iFay : « Aide-moi à regarder ce rapport de bilan — y a-t-il quelque chose qui devrait m'inquiéter ? »

iFay se met au travail :
1. Récupère d'abord vos données de bilan des trois dernières années du Tas de données personnelles (sa propre mémoire)
2. Puis interroge une **base de connaissances médicales** externe (la bibliothèque) : quelle est la plage normale pour chaque indicateur ? Que signifie un dépassement ?
3. Après analyse globale, vous dit :

« Vos triglycérides sont élevés (la normale devrait être en dessous de 1,7, les vôtres sont à 2,8), et votre cholestérol LDL est aussi élevé (la normale devrait être en dessous de 3,4, les vôtres sont à 3,9). Les deux indicateurs ont augmenté par rapport à l'année dernière. Combiné avec vos historiques de repas des trois derniers mois (données du Tas de données personnelles), votre fréquence de commande de plats à emporter a notablement augmenté, avec une préférence pour les aliments riches en huile et en sel. »

« Je suggère de faire attention à votre santé lipidique et d'envisager d'ajuster votre alimentation. Voulez-vous que je prenne un rendez-vous en cardiologie pour vous ? »

### Scénario 2 : Vous aider à rédiger des clauses contractuelles

Vous êtes propriétaire d'une petite entreprise qui doit signer un contrat d'approvisionnement avec un fournisseur. Vous n'êtes pas très familier avec le droit des contrats, mais vous ne voulez pas payer un avocat à chaque fois.

Vous dites à iFay : « Aide-moi à rédiger une clause de rupture pour un contrat d'approvisionnement — si le fournisseur retarde la livraison de plus de 15 jours, nous avons le droit de résilier le contrat. »

iFay se met au travail :
1. Interroge une **base de connaissances juridiques** externe : dispositions légales et formulations courantes pour les clauses de rupture de contrats d'approvisionnement
2. Référence les modèles de contrats que vous avez précédemment signés depuis le Tas de données personnelles (sa propre mémoire)
3. Synthétise un brouillon de clause de rupture incluant la terminologie juridique et les dispositions protectrices

iFay présente le brouillon : « Voici une clause de rupture rédigée sur la base des dispositions pertinentes du droit des contrats. J'ai référencé des modèles standards de la base de connaissances juridiques et incorporé le style de votre précédent contrat avec la société XX. Souhaitez-vous faire des ajustements ? »

En même temps, iFay vous rappelle : « Ceci est un brouillon généré à partir de la base de connaissances juridiques. Je recommande de le faire réviser par un avocat professionnel avant la signature formelle. »

## Pour les développeurs

Les Connaissances externes appartiennent à la **Phase 3 (iFay comme interface vers le monde virtuel)** comme module fondamental.

- **ID d'exigence** : Exigence 12 (Intégration des Connaissances externes)
- **Spécification d'interface** : Interface `ExternalKnowledge` avec trois méthodes fondamentales : `query()` (interroger les connaissances externes), `registerSource()` (enregistrer une source de connaissances), et `fallbackToCache()` (se replier sur le cache)
- **Types de sources de connaissances** : `knowledge_base`, `llm` (Grand modèle de langage), `expert_system`, `search_engine`
- **Protocole associé** : SSP (Protocole de partage de compétences) pour l'intégration standardisée des sources de connaissances externes
- **Modules associés** : Tas de données personnelles (`PersonalDataHeap`) intègre les connaissances externes, Compétences enregistrées (`RegisteredSkillManager`) gère l'enregistrement des sources de connaissances, Compétences internes (`InternalSkill`) vérifie les conflits de connaissances
- **Stratégie de repli** : Quand les sources de connaissances externes sont indisponibles, se replie automatiquement sur les connaissances en cache du Tas de données personnelles et notifie la Couche de Cognition
- **Tests de conformité** : iFACTS L1 valide les capacités de requête de connaissances et de repli sur cache, L2 valide l'interface d'intégration de connaissances avec le Tas de données personnelles, L3 valide la chaîne complète « requête de connaissances → intégration → cache → repli »


---

## 11.3 Conscience alignée

## Définition en une ligne

La Conscience alignée est la **compréhension complète de vous** par iFay — si le Modèle Ego est la « personnalité » d'iFay, la Conscience alignée est la cognition profonde d'iFay de vous en tant que personne — vos valeurs, préférences, habitudes et limites. C'est la base de tout le comportement d'iFay.

## Pourquoi c'est nécessaire

Imaginez que vous avez un assistant qui est avec vous depuis dix ans. La raison pour laquelle cet assistant fonctionne si bien n'est pas grâce à des compétences techniques supérieures, mais parce qu'il **vous connaît si bien** :

- Il sait que vous n'aimez pas les réunions avant 10h
- Il sait que vous êtes allergique aux cacahuètes et les évite automatiquement en commandant de la nourriture
- Il sait que vous préférez les décisions basées sur les données, donc les rapports incluent toujours des graphiques
- Il sait que vous êtes actuellement au régime, donc il ne recommandera pas proactivement des desserts

La Conscience alignée est la version d'iFay de cette « compréhension complète » de vous. Elle maintient un **profil complet** vous concernant — pas de simples tags (« homme, 30 ans, programmeur »), mais une compréhension multidimensionnelle, continuellement mise à jour et profondément ancrée.

Pourquoi est-ce important ? Parce que chaque action d'iFay a besoin d'une « base » pour juger : cela devrait-il être fait ? Comment devrait-ce être fait ? Jusqu'à quel point ? Cette base est le profil du Human Prime fourni par la Conscience alignée.

## Sa position dans l'architecture

```
Architecture à quatre couches d'iFay
├── Couche Sociale
├── Couche d'Interaction
│   ├── Sens
│   │   └── Conscience de soi         ← Vous observe en temps réel → met à jour la Conscience alignée
│   └── Action
│       └── ...
├── Couche de Cognition          ← La Conscience alignée est ici
│   ├── Pensée
│   │   ├── Tas de données personnelles  ← Explore les données d'ici pour vous comprendre
│   │   ├── Connaissances externes
│   │   └── 👉 Conscience alignée        ← Compréhension complète de vous
│   └── Compétences
│       └── Compétences internes         ← Utilise la Conscience alignée pour contraindre le comportement
└── Couche Ego
    └── Modèle Ego                       ← La Conscience alignée est une entrée pour Ego
```

La Conscience alignée se situe dans le **sous-système de Pensée de la Couche de Cognition**, mais son influence rayonne dans toute l'architecture iFay. Elle descend pour explorer les données du **Tas de données personnelles** afin de construire votre profil, et monte pour fournir des bases de contrainte comportementale au **Modèle Ego** et aux **Compétences internes**.

## Comment ça fonctionne

Le profil du Human Prime maintenu par la Conscience alignée contient de multiples dimensions : **orientation des valeurs, préférences d'intérêt, schémas d'habitudes, limites cognitives, limites de compétences, limites de permissions et style de travail**.

Ce profil est établi et mis à jour par **trois méthodes** :

**1. Exploration de données — Vous comprendre à partir de vos données**

La Conscience alignée explore les schémas comportementaux du Tas de données personnelles. Par exemple :
- Analyser vos commandes de nourriture de l'année passée, découvrir que vous n'avez pas commandé de plats de viande dans les trois derniers mois → inférer que vous êtes peut-être devenu végétarien
- Analyser vos données de calendrier, découvrir que vous ne planifiez jamais de réunions de travail le week-end → inférer que vous valorisez l'équilibre travail-vie

Cette méthode est **passive et continue** — iFay n'a pas besoin de vous demander ; il vous comprend progressivement en observant vos données.

**2. Ajustement en temps réel — Vous lire à partir de vos réactions**

Le module de Conscience de soi observe vos réactions en temps réel et transmet les observations à la Conscience alignée. Par exemple :
- iFay a recommandé une chanson, et vous l'avez immédiatement sautée → la Conscience alignée met à jour : vous n'aimez pas ce style de musique
- iFay a écrit un e-mail pour vous, et vous avez fortement révisé la formulation → la Conscience alignée met à jour : votre style d'e-mail est plus formel que ce qu'iFay attendait

Cette méthode est **active et immédiate** — iFay apprend de chacune de vos réactions, affinant continuellement sa compréhension de vous.

**3. Définition manuelle — Vous dites directement à iFay**

Certaines préférences et limites vous pouvez les dire directement à iFay :
- « Je ne veux pas que tu planifies de réunions avant 10h »
- « Je suis allergique aux cacahuètes — garde ça en tête quand tu commandes de la nourriture pour moi »
- « Utilise un ton formel pour les e-mails de travail, décontracté c'est bien pour les messages personnels »

Cette méthode est **explicite et immédiate** — ce que vous dites, iFay l'enregistre, pas d'inférence nécessaire.

Les trois méthodes se complètent : l'exploration de données fournit les tendances à long terme, l'ajustement en temps réel capture les changements immédiats, et la définition manuelle fixe des limites explicites.

## Relations avec les autres modules

| Module associé | Relation | Analogie corporelle |
|----------------|----------|---------------------|
| **Tas de données personnelles** | La Conscience alignée explore les données du Tas pour construire le profil du Human Prime | Résumer « quel type de personne je suis » à partir des souvenirs |
| **Conscience de soi** | La Conscience de soi observe les réactions du Human Prime en temps réel et les transmet à la Conscience alignée pour mise à jour du profil | Lire les expressions faciales → mettre à jour la compréhension de vous |
| **Modèle Ego** | La Conscience alignée fournit le profil du Human Prime au Modèle Ego comme entrée pour les contraintes de personnalité | Compréhension de vous → façonne la personnalité d'iFay |
| **Compétences internes** | La Conscience alignée fournit des bases de contrainte comportementale aux Compétences internes | Compréhension de vous → détermine ce qui peut et ne peut pas être fait |
| **Comportement autonome** | La Conscience alignée aide le Comportement autonome à juger « devrais-je proactivement faire cela » | Connaître vos limites → détermine la portée d'action |

## Histoires de scénarios

### Scénario 1 : Découvrir que vous êtes devenu végétarien à partir des données de commandes

Au cours des trois derniers mois, la fonction d'exploration de données de la Conscience alignée d'iFay a analysé vos historiques de commandes dans le Tas de données personnelles :

- Il y a trois mois : 70% de vos commandes incluaient des plats de viande
- Il y a deux mois : le ratio de plats de viande est tombé à 30%, avec des options végétariennes apparaissant fréquemment
- Le mois dernier : vous n'avez commandé aucun plat de viande, et vous avez suivi plusieurs blogueurs végétariens sur les réseaux sociaux

La Conscience alignée synthétise ces données et met à jour votre profil : **la préférence alimentaire est passée d'omnivore à végétarien**.

Cette mise à jour affecte immédiatement le comportement d'iFay :
- Quand vous dites « commande-moi à manger », iFay ne recommande que des restaurants végétariens
- Quand iFay planifie un voyage pour vous, il marque spécifiquement les restaurants végétariens près de la destination
- Quand un ami vous invite à dîner, iFay vous rappelle « ce restaurant a des options végétariennes limitées — voulez-vous suggérer un autre endroit ? »

Vous n'avez jamais explicitement dit à iFay « je suis végétarien maintenant », mais iFay a découvert ce changement par l'exploration de données par lui-même et a automatiquement ajusté tous les comportements associés.

### Scénario 2 : Vous dites directement à iFay une règle

Un matin, vous êtes réveillé par une réunion à 8h. Quelque peu agacé, vous dites à iFay : « À partir de maintenant, ne planifie aucune réunion pour moi avant 10h. »

iFay répond immédiatement : « Compris. Toutes les réunions seront planifiées après 10h à partir de maintenant. »

C'est une **définition manuelle** — vous dites directement à iFay une règle explicite. La Conscience alignée met immédiatement à jour votre profil, ajoutant cette contrainte à la dimension « schémas d'habitudes ».

L'impact de cette mise à jour est immédiat :
- Quand quelqu'un essaie de vous réserver pour une réunion à 9h demain via iFay, iFay répond : « XX n'est pas disponible avant 10h. Après 10h conviendrait-il ? »
- Quand le Comportement autonome d'iFay veut vous rappeler une tâche de travail à 8h, il vérifie la Conscience alignée, trouve la règle « pas de dérangement avant 10h », et reporte le rappel à 10h

Une simple instruction verbale, transmise via la Conscience alignée, affecte tous les comportements associés d'iFay.

## Pour les développeurs

La Conscience alignée appartient à la **Phase 4 (iFay + coFay Personnification complète)** comme module fondamental.

- **ID d'exigence** : Exigence 16 (Conscience alignée)
- **Spécification d'interface** : Interface `AlignedConsciousness` avec quatre méthodes fondamentales : `getProfile()` (obtenir le profil du Human Prime), `mineFromDataHeap()` (mise à jour par exploration de données), `adjustFromAwareness()` (ajustement en temps réel depuis la Conscience de soi), et `manualUpdate()` (définition manuelle par le Human Prime)
- **Dimensions du profil du Human Prime** : Orientation des valeurs (`values`), préférences (`preferences`), habitudes (`habits`), limites cognitives (`cognitiveBoundaries`), limites de compétences (`skillBoundaries`), limites de permissions (`permissionBoundaries`), style de travail (`workingStyle`)
- **Trois méthodes de mise à jour** : Exploration depuis le Tas de données personnelles (passive, continue), ajustement en temps réel via la Conscience de soi (active, immédiate), définition manuelle par le Human Prime (explicite, immédiate)
- **Modules associés** : Tas de données personnelles (`PersonalDataHeap`) fournit la source de données, Conscience de soi (`SelfAwareness`) fournit le retour en temps réel, Modèle Ego (`EgoModel`) et Compétences internes (`InternalSkill`) consomment les données de profil
- **Relation avec le Profil iFay** : Le profil du Human Prime (`HostProfile`) est un sous-ensemble et une source d'entrée du Profil iFay. Le Profil est la « carte d'identité » complète d'iFay ; la Conscience alignée est la portion « compréhension du Human Prime » en son sein
- **Tests de conformité** : iFACTS L1 valide les trois méthodes de mise à jour du profil, L2 valide les interfaces de livraison du profil avec le Modèle Ego et les Compétences internes, L4 valide l'impact réel des mises à jour de profil sur les contraintes comportementales
