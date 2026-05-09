# 10. Couche d'Interaction — Action

Le sous-système d'Action de la Couche d'Interaction représente les « effecteurs » d'iFay — il permet à iFay d'opérer des interfaces, d'invoquer des services et d'agir de manière proactive.


---

## 10.1 Opération simulée

## Définition en une ligne

L'Opération simulée est les **mains** d'iFay — elle peut cliquer, glisser, défiler et taper comme un humain, opérant n'importe quelle interface logicielle existante sans que le logiciel ait besoin de modifications spécifiques à l'IA.

## Pourquoi c'est nécessaire

Imaginez que vous avez embauché un nouvel assistant et voulez qu'il gère diverses tâches sur votre ordinateur et téléphone. Mais le problème est : les logiciels que vous utilisez — sites bancaires, systèmes d'assurance, plateformes de services gouvernementaux — sont tous conçus pour les humains, et aucun ne fournit une « entrée réservée à l'IA ».

Que faire ? L'approche la plus directe : **faire opérer ces applications logicielles par l'assistant exactement comme vous le feriez**. Voir un bouton, cliquer dessus. Voir un formulaire, le remplir. Voir une page, la défiler.

C'est la signification de l'Opération simulée. Elle permet à iFay de vous aider à accomplir des choses **tout de suite**, sans attendre que chaque logiciel au monde soit reconçu pour l'IA.

Mais l'Opération simulée est fondamentalement différente des « scripts d'automatisation » traditionnels (comme le RPA). Le RPA est comme un acteur qui ne peut que réciter des répliques mémorisées — il suit un script pré-écrit étape par étape, et se bloque si l'interface change légèrement. L'Opération simulée d'iFay est **guidée par la perception** : elle « voit » l'écran via le Traceur première personne, comprend l'état actuel de l'interface, puis décide quoi faire ensuite. Tout comme un vrai utilisateur humain — même si un site web est redesigné, vous pouvez intuitivement trouver le nouvel emplacement du bouton.

## Sa position dans l'architecture

```
Architecture à quatre couches d'iFay
├── Couche Sociale
├── Couche d'Interaction          ← L'Opération simulée est ici
│   ├── Perception (Sens)
│   │   ├── Traceur première personne   ← Yeux : voit ce qui est à l'écran
│   │   ├── Capteur                     ← Système nerveux : perçoit l'environnement
│   │   └── Conscience de soi           ← Cœur : lit votre intention
│   └── Action
│       ├── 👉 Opération simulée ← Mains : cliquer, glisser, taper
│       ├── Invocation de compétences  ← Bouche : « appelle » directement les services
│       └── Comportement autonome      ← Volonté : décide quand agir
├── Couche de Cognition
└── Couche Ego
```

L'Opération simulée se situe dans le **sous-système d'Action de la Couche d'Interaction**, l'une des trois façons dont iFay interagit avec le monde extérieur. Sa relation avec le Traceur première personne est la plus étroite — le Traceur est les « yeux », l'Opération simulée est les « mains », et ensemble ils réalisent la **coordination œil-main**.

## Comment ça fonctionne

Le workflow fondamental peut être résumé en trois mots-clés : **Percevoir, Opérer, Retour**.

**1. Percevoir — Regarder d'abord, agir ensuite**

Avant d'effectuer toute opération, iFay « voit » d'abord l'interface actuelle via le Traceur première personne. Il n'analyse pas le code HTML de la page — il **voit ce qui est affiché à l'écran** comme un humain : où sont les boutons, où sont les champs de saisie, où sont les menus déroulants.

**2. Opérer — Interagir comme un humain**

iFay supporte toutes les opérations que les humains peuvent effectuer sur les interfaces :
- **Cliquer** : Clic gauche sur les boutons, clic droit pour ouvrir les menus
- **Glisser** : Glisser des fichiers, redimensionner des fenêtres
- **Défiler** : Défiler les pages vers le haut et le bas pour voir plus de contenu
- **Taper** : Entrer du texte dans les champs de saisie
- **Gestes de bord** : Glisser depuis les bords de l'écran pour invoquer des barres latérales
- **Gestes multi-doigts** : Zoom à deux doigts, changement d'application à trois doigts

**3. Retour — Vérifier les résultats après chaque action**

Après chaque opération, iFay « regarde » à nouveau l'interface via le Traceur première personne pour confirmer si l'opération a réussi. Si un bouton a été cliqué mais la page n'a pas changé, iFay réalise « ce bouton n'a peut-être pas répondu » et essaie une autre approche.

Cette boucle « opérer → observer → ajuster » est la différence fondamentale entre l'Opération simulée et les scripts RPA. Le RPA est un aveugle tâtant un éléphant — exécutant des scripts sans se soucier des résultats. iFay travaille les yeux ouverts — voyant, pensant et ajustant à chaque étape.

**Et les interfaces inconnues ?**

Quand iFay rencontre une interface qu'il n'a jamais vue, il **explore** comme un humain : essaie de cliquer sur un bouton pour voir ce qui se passe, survole la souris sur une icône pour vérifier s'il y a un texte d'info-bulle, défile la page pour voir ce qu'il y a en dessous. Par cette exploration, iFay comprend progressivement la structure et les fonctionnalités de l'interface.

## Relations avec les autres modules

| Module associé | Relation | Analogie corporelle |
|----------------|----------|---------------------|
| **Traceur première personne** | Les « yeux » de l'Opération simulée — perçoit l'état de l'interface avant et après chaque opération | Mains ↔ Yeux (coordination œil-main) |
| **Invocation de compétences** | Tous deux dans le sous-système d'Action, mais approches différentes : l'Opération simulée travaille via les interfaces, l'Invocation de compétences appelle les APIs directement | Opérer à la main vs. passer un coup de fil |
| **Comportement autonome** | Le Comportement autonome décide « quand agir », l'Opération simulée gère « comment agir » | La volonté décide l'action → les mains exécutent |
| **Modèle Ego** | Ego contraint le style comportemental de l'Opération simulée (ex. vitesse d'opération, niveau de prudence) | La personnalité influence la façon de faire les choses |
| **Gestion des identifiants** | L'Opération simulée a besoin d'identifiants de la Gestion des identifiants pour se connecter | Les mains prennent les clés pour ouvrir les portes |

## Histoires de scénarios

### Scénario 1 : Remplir un formulaire complexe de réclamation d'assurance

Vous avez eu un petit accident de voiture et devez remplir une réclamation sur le site web obsolète de la compagnie d'assurance. Le site a probablement été conçu il y a une décennie — le formulaire a plus de 30 champs répartis sur 5 pages, avec divers menus déroulants et sélecteurs de date.

Vous dites à iFay : « Aide-moi à remplir la réclamation d'assurance auto — celle de mercredi dernier après-midi à l'intersection de la rue Zhongshan et de la rue Jianshe. »

iFay se met au travail :
1. « Voit » la page de connexion du site de l'assurance via le Traceur première personne, se connecte avec vos identifiants délégués
2. Trouve l'entrée « Demande de réclamation » et clique dessus
3. Voit le formulaire de la première page : date de l'accident, lieu, type… iFay extrait les informations de votre description et du Tas de données personnelles, remplissant chaque champ
4. Rencontre un bouton « Télécharger les photos de l'accident » — iFay clique dessus, trouve vos photos de la scène dans le sélecteur de fichiers et les télécharge
5. À la troisième page, découvre un menu déroulant avec des options différentes de celles attendues (le site a peut-être été mis à jour) — iFay ne se bloque pas ; au lieu de cela, il lit attentivement le texte de chaque option et sélectionne la meilleure correspondance
6. Sur la page de confirmation finale, iFay vérifie chaque élément rempli, confirme que tout est correct et clique sur « Soumettre »

Tout au long du processus, iFay n'exécute pas un script pré-écrit — il travaille comme un assistant compétent, **regardant l'écran, comprenant le contenu, portant des jugements**. Même si ce site est redesigné demain, iFay peut toujours accomplir la tâche — parce qu'il opère en « voyant », pas en « mémorisant ».

### Scénario 2 : Commander un repas sur téléphone, s'adapter aux mises à jour de l'app

Vous dites : « Commande-moi la même chose que la dernière fois sur Meituan — le riz au poulet braisé, livraison au bureau. »

iFay ouvre l'application Meituan mais trouve que l'interface est différente — l'app vient d'être mise à jour, la disposition de la page d'accueil a changé, et la barre de recherche a bougé.

Si c'était un script RPA, il planterait et s'arrêterait. Mais iFay ne le fait pas :
1. Scanne la nouvelle disposition de la page d'accueil via le Traceur première personne, trouve que l'icône de recherche a bougé en haut à droite
2. Clique sur l'icône de recherche, tape « riz au poulet braisé »
3. Dans les résultats de recherche, identifie visuellement le restaurant où vous avez commandé la dernière fois (correspondance du nom et du logo du magasin)
4. Entre dans la page du magasin, trouve que le menu a été réarrangé — iFay défile dans le menu et trouve « Riz au poulet braisé »
5. Clique pour ajouter au panier, confirme que l'adresse de livraison est votre bureau
6. Complète la commande

iFay a démontré une **exploration adaptative** tout au long : il ne dépend pas de dispositions d'interface fixes mais comprend l'interface actuelle via la perception visuelle et ajuste de manière flexible sa stratégie d'opération. C'est la différence essentielle entre « guidé par la perception » et « guidé par le script ».

## Pour les développeurs

L'Opération simulée appartient à la **Phase 1 (Simulation des opérations humaines)** comme module fondamental.

- **ID d'exigence** : Exigence 5 (Opération simulée)
- **Spécification d'interface** : Interface `SimulatedOperation` avec trois méthodes fondamentales : `execute()`, `explore()` et `getPostActionState()`
- **Types d'opérations supportés** : `click`, `drag`, `scroll`, `gesture` (gestes de bord et multi-doigts), `type`
- **Modules associés** : Traceur première personne (`FirstPersonTracer`) fournit le retour visuel ; Gestion des identifiants (`CredentialManager`) fournit les identifiants de connexion
- **Conception fondamentale** : Guidé par la perception, pas par le script ; après chaque opération, perçoit les changements d'état via le Traceur, formant une boucle fermée « opérer → percevoir → ajuster » ; supporte l'exploration adaptative d'interfaces inconnues
- **Tests de conformité** : iFACTS L1 vérifie la capacité d'exécution pour chaque type d'opération ; L2 vérifie l'interface de coordination œil-main avec le Traceur première personne
- **Pertinence iFay Ready** : La certification Bronze exige que les applications supportent l'opération par iFay via l'Opération simulée


---

## 10.3 Comportement autonome

## Définition en une ligne

Le Comportement autonome est la **volonté autonome** d'iFay — l'Opération simulée est les mains, l'Invocation de compétences est la bouche, et le Comportement autonome est iFay décidant par lui-même « quand agir et quand parler ». Il transforme iFay d'un exécuteur passif en un acteur proactif.

## Pourquoi c'est nécessaire

Imaginez que vous avez un excellent assistant. Si cet assistant n'agit que quand vous donnez des commandes, alors vous devez encore penser à tout et donner chaque instruction vous-même — cela n'allège pas vraiment votre charge, ça change juste « le faire soi-même » en « dire à quelqu'un de le faire ».

À quoi ressemble un vraiment bon assistant ? Il fait les choses **proactivement** :
- Prépare automatiquement votre résumé de travail hebdomadaire chaque lundi matin (**tâche planifiée**)
- Remarque que vous froncez les sourcils et soupirez, et demande proactivement si vous avez rencontré des difficultés (**agir après avoir lu l'ambiance**)
- Vous avez dit une fois « vérifie la logistique à chaque fois que je reçois une notification de livraison », et il se souvient toujours de le faire automatiquement (**exécuter continuellement des habitudes**)

C'est la signification du Comportement autonome. Il donne à iFay une « volonté autonome » — ne plus simplement attendre que vous parliez, mais juger par lui-même quand faire quoi, puis le faire proactivement.

Mais il y a un mécanisme de sécurité important : si quelque chose qu'iFay fait de manière autonome s'avère incorrect, il **met en pause et vous demande**. Comme un bon assistant qui aide proactivement mais vérifie avec vous quand il n'est pas sûr, plutôt que d'aller jusqu'au bout sur son propre jugement.

## Sa position dans l'architecture

```
Architecture à quatre couches d'iFay
├── Couche Sociale
├── Couche d'Interaction          ← Le Comportement autonome est ici
│   ├── Perception (Sens)
│   │   └── Conscience de soi    ← Infère votre intention ──┐
│   └── Action                                               │
│       ├── Opération simulée    ← Mains                     │
│       ├── Invocation de compétences ← Bouche               │
│       └── 👉 Comportement autonome ← Volonté ←─────────────┘
├── Couche de Cognition
│   └── Compétences
│       ├── Compétences enregistrées  ← Source de compétences persistantes
│       └── Compétences internes      ← Source de compétences persistantes
└── Couche Ego
```

Le Comportement autonome se situe dans le **sous-système d'Action de la Couche d'Interaction**, le plus « avancé » des trois types d'action. L'Opération simulée et l'Invocation de compétences sont « comment faire » ; le Comportement autonome est « quand faire et s'il faut faire ».

Il a une source d'entrée particulièrement importante : le module de **Conscience de soi**. La Conscience de soi est responsable de « vous lire », et le Comportement autonome est responsable d'« agir proactivement basé sur la compréhension de vous ». Leur coordination transforme iFay d'un outil « vous dites, je fais » en un partenaire « je vous comprends, je vous aide proactivement ».

## Comment ça fonctionne

Le Comportement autonome a **trois types de déclencheurs**, comme trois raisons pour lesquelles les humains font proactivement des choses :

**1. Tâches planifiées — Le faire quand le moment est venu**

Le déclencheur le plus simple, comme une alarme que vous avez réglée. Vous dites à iFay : « Génère le rapport de travail de la semaine dernière chaque lundi matin à 9h. » iFay exécutera cette tâche ponctuellement chaque lundi matin.

**2. Inférence de la Conscience de soi — Sentir que vous avez besoin de quelque chose, le faire proactivement**

Le déclencheur le plus « intelligent ». iFay observe votre état et votre environnement via le module de Conscience de soi, infère ce dont vous pourriez avoir besoin, puis agit proactivement.

Par exemple : iFay découvre via les données des capteurs de votre réfrigérateur intelligent que les ingrédients sont presque épuisés, combine cela avec vos habitudes alimentaires récentes, et commande proactivement des courses pour vous. Vous n'avez jamais dit « achète des courses », mais iFay a jugé par lui-même qu'« il est temps de réapprovisionner ».

**3. Compétences persistantes — Habitudes fonctionnant continuellement en arrière-plan**

Certaines compétences ne sont pas ponctuelles — elles fonctionnent en continu. Par exemple, vous dites à iFay « surveille cette action et alerte-moi si elle descend en dessous de 50 ». Cette tâche fonctionne continuellement en arrière-plan jusqu'à ce que la condition se déclenche.

Ces compétences persistantes proviennent de deux sources : **Compétences enregistrées** (capacités de surveillance continue de services externes) et **Compétences internes** (capacités inhérentes propres à iFay).

**La boucle Action → Retour → Ré-action**

Quel que soit le type de déclencheur, le Comportement autonome suit une boucle fondamentale :

1. **Action** : iFay exécute une tâche décidée de manière autonome
2. **Retour** : Observe les résultats d'exécution, juge s'ils répondent aux attentes
3. **Ré-action** : Si les résultats répondent aux attentes, continuer à l'étape suivante ; sinon, ajuster la stratégie ou mettre en pause pour demander

Cette boucle garantit que le comportement autonome d'iFay n'est pas « foncer tête baissée » mais se corrige continuellement.

**Soupape de sécurité : Pause et confirmation**

Quand iFay trouve que les résultats du comportement autonome sont incohérents avec votre intention, il **met en pause toutes les actions autonomes suivantes** et vous demande : « Je viens de faire XX pour toi, mais le résultat ne semble pas correct. Tu veux continuer ? » Ce mécanisme garantit que l'autonomie d'iFay ne dérape pas.

## Relations avec les autres modules

| Module associé | Relation | Analogie corporelle |
|----------------|----------|---------------------|
| **Conscience de soi** | La Conscience de soi infère l'intention du Human Prime, déclenchant le Comportement autonome | Sentiments intérieurs → motivent l'action |
| **Opération simulée** | Le Comportement autonome décide « quoi faire », l'Opération simulée gère « le faire à la main » | Volonté → mains |
| **Invocation de compétences** | Le Comportement autonome décide « quoi faire », l'Invocation gère « le faire par téléphone » | Volonté → bouche |
| **Compétences enregistrées** | Les compétences persistantes sont une source de déclenchement du Comportement autonome | Les habitudes à long terme motivent l'action |
| **Compétences internes** | Les Compétences internes sont une autre source de déclenchement | L'instinct motive l'action |
| **Conscience alignée** | La Conscience alignée fournit le profil du Human Prime, aidant le Comportement autonome à juger « devrais-je faire cela » | Connaître vos limites → détermine la portée d'action |

## Histoires de scénarios

### Scénario 1 : Auto-génération du rapport hebdomadaire chaque lundi (déclencheur tâche planifiée)

Lundi matin 8h55, vous êtes encore dans le métro. La tâche planifiée d'iFay se déclenche :

1. iFay extrait automatiquement les données de travail de la semaine dernière de votre Tas de données personnelles — e-mails, calendrier, achèvement de tâches dans les outils de gestion de projet, historiques de commits de code
2. Via l'Invocation de compétences, appelle une API de génération de documents pour organiser ces données en un rapport hebdomadaire bien structuré
3. Après génération, iFay vérifie si le contenu est raisonnable (ex. des projets importants manquent-ils ?)
4. À 9h00 pile, vous arrivez au bureau, ouvrez votre ordinateur, et trouvez qu'iFay a placé le rapport hebdomadaire sur votre bureau avec une note : « Tu as passé le plus de temps sur le Projet A la semaine dernière. Le Projet B a deux tâches en retard — tu veux que je t'aide à ajuster le plan de cette semaine ? »

Vous n'avez jamais dit « écris mon rapport hebdomadaire » — cela a été automatiquement complété par iFay selon la tâche planifiée que vous aviez précédemment définie. Et il n'a pas juste mécaniquement agrégé des données — il a proactivement offert des suggestions.

### Scénario 2 : Réapprovisionnement proactif de courses (déclencheur Conscience de soi)

Mercredi soir, iFay découvre via les données des capteurs de votre réfrigérateur intelligent : il ne reste qu'un carton de lait, 3 œufs restants, compartiment à légumes presque vide.

iFay combine les informations suivantes pour porter un jugement :
- Vos habitudes alimentaires (enregistrées dans la Conscience alignée : vous buvez du lait chaque matin, utilisez environ 12 œufs par semaine)
- Vos historiques d'achats récents (données dans le Tas de données personnelles : dernière course il y a 5 jours)
- L'heure actuelle (mercredi soir — si vous ne réapprovisionnez pas, vous pourriez manquer d'ici le week-end)

iFay agit proactivement :
1. Génère une liste de courses : 2 cartons de lait, 1 boîte d'œufs, vos légumes habituels
2. Via l'Invocation de compétences, appelle l'API de l'application de livraison fraîche pour passer une commande
3. Avant de commander, iFay met en pause — parce que le total dépasse votre budget habituel d'achat unique. Il demande : « Le frigo se vide. J'ai fait une liste de courses — 186 yuans au total, un peu plus que d'habitude parce que j'ai ajouté les légumes bio que tu as mentionné vouloir essayer la semaine dernière. Je passe la commande ? »
4. Vous répondez « D'accord », iFay complète la commande

Notez l'étape « pause et confirmation » — iFay a trouvé que le montant dépassait votre budget habituel (résultat pas entièrement cohérent avec les habitudes du Human Prime), donc il n'a pas commandé directement mais a demandé d'abord. C'est le mécanisme de sécurité du Comportement autonome en action.

## Pour les développeurs

Le Comportement autonome appartient à la **Phase 4 (iFay + coFay Personnification complète)** comme module fondamental.

- **ID d'exigence** : Exigence 14 (Comportement autonome)
- **Spécification d'interface** : Interface `SelfDrivenBehavior` avec quatre méthodes fondamentales : `scheduleTask()` (tâche planifiée), `handleInference()` (gérer l'inférence de la Conscience de soi), `pauseAndConfirm()` (pause et confirmation), et `getLoopStatus()` (statut de la boucle)
- **Trois sources de déclenchement** : `scheduled` (tâche planifiée), `self_awareness` (inférence de la Conscience de soi), `registered_skill` / `internal_skill` (compétences persistantes)
- **Mécanisme fondamental** : Boucle continue action → retour → ré-action ; met en pause et demande confirmation quand les résultats d'exécution sont incohérents avec l'intention du Human Prime
- **Modules associés** : Conscience de soi (`SelfAwareness`) fournit l'inférence d'intention ; Opération simulée et Invocation de compétences gèrent l'exécution réelle ; Conscience alignée (`AlignedConsciousness`) fournit la base de contrainte comportementale
- **Tests de conformité** : iFACTS L1 vérifie la réactivité aux trois sources de déclenchement ; L2 vérifie l'interface avec le module de Conscience de soi ; L4 vérifie les contraintes de sécurité du comportement autonome (mécanisme de pause-et-confirmation)
