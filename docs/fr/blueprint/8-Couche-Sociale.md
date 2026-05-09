# 8. Couche Sociale

La Couche Sociale définit le **mode d'existence** d'iFay dans la société — elle répond à trois questions fondamentales : « Qui suis-je » (Identité), « Que suis-je autorisé à faire » (Permissions Sociales) et « Combien valent mes contributions » (Contribution Sociale & Voix).

Si nous comparons iFay à une personne sociale, la Couche Sociale est son **identité sociale** : une carte d'identité prouve qui vous êtes, divers certificats et clés prouvent ce que vous êtes autorisé à faire, et votre réputation sociale et votre historique de contributions déterminent votre voix et votre crédibilité dans la communauté.

La Couche Sociale est la pierre angulaire du système de sécurité d'iFay et le prérequis pour l'intégration d'iFay dans les relations sociales.

```
Architecture à quatre couches d'iFay
├── 👉 Couche Sociale
│   ├── 8.1 Identité (FayID)              ← Qui suis-je
│   ├── 8.2 Permissions Sociales           ← Que suis-je autorisé à faire
│   │   ├── Compte/Mot de passe
│   │   ├── Certificat
│   │   ├── Autorisation
│   │   ├── Jeton d'accès
│   │   └── Smart Contract
│   └── 8.3 Contribution Sociale & Voix    ← Combien valent mes contributions
│       ├── GMChain (Global Merit Chain)
│       └── MeriToken
├── Couche d'Interaction
├── Couche de Cognition
└── Couche Ego
```

---

## 8.1 Identité (FayID)

### Définition en une ligne

FayID est le **numéro d'identité** d'iFay — un identifiant persistant, globalement unique, lisible par l'humain et par la machine, qui sert de fondation pour qu'iFay soit reconnu et suivi dans toutes les interactions sociales.

### Pourquoi c'est nécessaire

Dans la société humaine, un numéro d'identification est le point de départ de toutes les activités sociales — sans pièce d'identité, vous ne pouvez pas ouvrir un compte bancaire, signer un contrat, ni même acheter un billet de train. FayID a exactement la même importance pour iFay : c'est le prérequis pour qu'iFay participe à toute interaction sociale.

La conception de FayID a deux considérations clés :

1. **Identification unifiée** : iFay et coFay utilisent le même mécanisme de génération et de gestion de FayID. Cela garantit que lorsque des iFays individuels assument éventuellement des rôles sociaux significatifs, leur identité peut transitionner en douceur — tout comme certains YouTubers individuels évoluent pour jouer des rôles importants dans le discours public sans avoir besoin de changer d'identité.

2. **Liaison d'activation** : FayID est profondément lié au Protocole Faying. Aucun iFay ne devrait agir de manière autonome sans l'intention explicite du Human Prime. L'état d'activation de FayID est géré par le [Protocole Faying](https://github.com/ChainModePilot/Faying-Protocol/wiki), garantissant qu'iFay n'opère que sous l'autorisation explicite du Human Prime.

### Propriétés fondamentales

| Propriété | Description |
|-----------|-------------|
| **Globalement unique** | Supporte une capacité d'identifiants dépassant l'échelle de la population mondiale, garantissant l'absence de collisions |
| **Lisible par l'humain** | Les humains peuvent le reconnaître et le mémoriser intuitivement — pas une chaîne de hachage sans signification |
| **Lisible par la machine** | Les systèmes et Fays peuvent l'analyser et le comparer efficacement |
| **Persistant** | Une fois attribué, il ne change jamais pendant toute la durée de vie d'iFay, supportant la migration d'identité et la continuité de personnalité |
| **État d'activation** | Lié au Protocole Faying, indiquant clairement si iFay est actuellement actif ou en veille |

### Scénario

> Xiao Ming enregistre son propre iFay, et le système attribue le FayID `fay://ming.2024.cn`. Cet ID accompagnera l'iFay de Xiao Ming toute sa vie — que l'iFay migre du téléphone à l'ordinateur, ou évolue d'assistant personnel à agent de patrimoine numérique de Xiao Ming, le FayID ne change jamais.
>
> Quand l'iFay de Xiao Ming communique avec le coFay d'un hôpital, les deux parties s'identifient mutuellement par FayID, tout comme deux personnes échangeant des cartes de visite lors d'une rencontre.

### Pour les développeurs

- **Projet indépendant** : FayID est un [projet open-source indépendant](https://github.com/ChainModePilot/FayID) ; voir [documentation FayID](https://github.com/ChainModePilot/FayID/wiki)
- **Spécification d'interface** : Interface `FayIDRegistry` avec `generate()` (générer FayID), `resolve()` (résoudre FayID), `getActivationStatus()` (obtenir l'état d'activation)
- **Tests de conformité** : iFACTS L1 vérifie l'unicité et la persistance de FayID ; L2 vérifie la liaison de l'état d'activation avec le Protocole Faying

---

## 8.2 Permissions Sociales

### Définition en une ligne

Les Permissions Sociales sont le **trousseau de clés** d'iFay — elles gèrent de manière sécurisée les identifiants dont iFay a besoin pour utiliser divers services en votre nom. Mais ces identifiants ne sont pas vos originaux — ce sont des copies sécurisées. Même si une copie est perdue, vos identifiants originaux restent en sécurité.

### Pourquoi c'est nécessaire

iFay doit agir en votre nom — se connecter à des plateformes e-commerce pour acheter des choses, utiliser votre e-mail professionnel pour envoyer des messages, contrôler des appareils domestiques intelligents, appeler des APIs tierces. Tout cela nécessite des « clés ». Le module Permissions Sociales vous aide à gérer ces clés de manière sécurisée grâce à un **mécanisme de copie** qui garantit que les identifiants originaux ne sont jamais directement exposés.

### Cinq types de permissions

Les Permissions Sociales gèrent cinq types d'identifiants, chacun correspondant à différents scénarios de relations sociales :

#### 1. Compte / Mot de passe

Le type d'identifiant le plus courant. Le Human Prime délègue les mots de passe de comptes d'applications et de services à iFay, et iFay utilise ces identifiants via le mécanisme de copie pour se connecter et opérer.

- **Mécanisme de copie** : iFay ne détient pas le mot de passe original mais une copie d'identifiant à permissions restreintes
- **Portée des permissions** : Les copies peuvent avoir des permissions plus strictes que l'original (ex., « uniquement les articles du quotidien, achat unique ne dépassant pas 200 yuan »)
- **Révocation sur anomalie** : Révoque automatiquement la copie lorsqu'une utilisation anormale est détectée ; le mot de passe original reste intact

> 🎯 Scénario : Vous déléguez votre compte de plateforme e-commerce à iFay. Ce qu'iFay reçoit n'est pas votre mot de passe original mais une copie sécurisée. Elle peut utiliser cette copie pour passer des commandes pour vous, mais si la copie est compromise, vous pouvez la révoquer en un clic — votre mot de passe original reste intact.

#### 2. Certificat

Certificats numériques pour la communication chiffrée et la vérification d'identité. Compatible avec les systèmes d'Autorité de Certification (CA) existants, supportant les formats standards comme X.509.

- **Objectif** : Communication chiffrée de bout en bout, signature de code, authentification d'identité
- **Compatibilité** : Intégration transparente avec l'infrastructure PKI existante, supportant les certificats émis par les principales CAs
- **Cycle de vie** : Supporte la gestion complète du cycle de vie de demande, renouvellement et révocation de certificats

> 🎯 Scénario : iFay doit communiquer avec un système bancaire via un canal chiffré. Elle utilise un certificat numérique délégué par le Human Prime pour établir une connexion TLS, garantissant la confidentialité et l'intégrité de la transmission des données. Le certificat est émis par une CA de confiance, permettant au système bancaire de vérifier la légitimité de l'identité d'iFay.

#### 3. Autorisation

Compatible avec les méthodes traditionnelles d'authentification tierce (ex., OAuth 2.0), permettant à iFay de s'authentifier auprès de plateformes tierces via des facteurs autorisés pour obtenir des permissions d'accès restreintes.

- **Compatible OAuth** : Supporte le flux de code d'autorisation OAuth 2.0, le flux d'identifiants client et d'autres modèles standards
- **Authentification par facteurs** : Obtient l'autorisation pour les plateformes sociales, services financiers, etc. via les informations d'empreinte de compte (empreinte d'appareil, biométrie, modèles comportementaux)
- **Contrôle de portée** : Contrôle précisément la portée de l'autorisation, garantissant qu'iFay ne peut accéder qu'aux ressources nécessaires

> 🎯 Scénario : Vous autorisez iFay à accéder à votre plateforme sociale. iFay n'a pas besoin de votre mot de passe de réseau social — elle passe par le flux OAuth, utilisant votre empreinte d'appareil et la reconnaissance faciale comme facteurs d'authentification pour obtenir un jeton d'accès à portée restreinte. Ce jeton permet uniquement de lire votre liste d'amis et d'envoyer des messages, pas de modifier les paramètres du compte.

#### 4. Jeton d'accès

Identifiants d'accès temporaires gérés, généralement avec une période d'expiration. Utilisés pour les appels API, l'accès aux services et des scénarios similaires.

- **Gestion d'expiration** : Suit automatiquement le temps d'expiration du jeton et le renouvelle avant expiration
- **Privilège minimal** : Chaque jeton n'accorde que les permissions minimales nécessaires pour accomplir une tâche spécifique
- **Piste d'audit** : Chaque utilisation de jeton est enregistrée, supportant l'audit a posteriori

> 🎯 Scénario : iFay doit appeler une API de traduction. Elle détient une clé API (jeton d'accès) qui effectue une rotation automatique toutes les 24 heures. Si une clé est compromise, l'impact est limité à 24 heures de volume d'appels, et le système détecte immédiatement les modèles d'appels anormaux et déclenche la révocation.

#### 5. Smart Contract

Identifiants de smart contract blockchain pour les services décentralisés et la collaboration automatisée entre Fays.

- **Exécution automatique** : S'exécute automatiquement lorsque les conditions du contrat sont remplies, sans intervention manuelle nécessaire
- **Immuable** : Le contenu du contrat ne peut pas être modifié unilatéralement une fois déployé
- **Transparent et vérifiable** : Tout participant peut vérifier les résultats d'exécution du contrat

> 🎯 Scénario : Votre iFay signe un smart contract avec un coFay d'analyse de données — « payer automatiquement 5μ à la fin de l'analyse. » Quand le coFay termine l'analyse et soumet les résultats, le contrat vérifie automatiquement la qualité des résultats et exécute le paiement — aucune confirmation manuelle nécessaire. L'ensemble du processus est transparent, immuable et exécuté automatiquement.

### Mécanisme de copie et défense de sécurité

Les cinq types de permissions suivent des principes de sécurité unifiés :

- **Isolation de copie** : iFay ne détient jamais directement les identifiants originaux — uniquement des copies à permissions restreintes
- **Étiquetage du propriétaire** : Chaque identifiant indique si le propriétaire est le Human Prime ou iFay elle-même (iFay peut acquérir des identifiants de manière indépendante)
- **Piste d'audit** : Chaque utilisation d'identifiant est enregistrée, supportant l'audit a posteriori
- **Détection d'anomalies** : Révoque automatiquement les copies et notifie le Human Prime lorsque des modèles d'utilisation anormaux sont détectés
- **Protection de la vie privée** : Quand iFay est autorisé à interroger des données privées, seuls des résultats booléens (vrai ou faux) sont retournés sans exposer les données réelles

### Pour les développeurs

- **Spécification d'interface** : Interface `CredentialManager` avec `delegate()` (déléguer/créer copie), `authenticate()` (authentifier), `revoke()` (révoquer), `queryPrivacy()` (requête de confidentialité, retourne uniquement un booléen), `getAuditLog()` (journal d'audit)
- **Cinq types d'identifiants** : `account_password`, `certificate`, `authorization`, `access_token`, `smart_contract`
- **Propriétaire d'identifiant** : `human_prime` ou `ifay`
- **État de copie** : `active`, `revoked`, `expired`
- **Tests de conformité** : iFACTS L1 vérifie la gestion des cinq types d'identifiants et le mécanisme de copie ; L2 vérifie les interfaces d'authentification avec Compétences enregistrées et Invocation de compétences ; L4 vérifie la contrainte de retour booléen pour les requêtes de confidentialité et le comportement de détection d'anomalies

---

## 8.3 Contribution Sociale & Voix (GMChain & MeriToken)

### Définition en une ligne

GMChain (Global Merit Chain, GMC) est le **registre de contribution sociale** de l'écosystème iFay — il enregistre chaque contribution faite par les Fays et les humains à la société, quantifiée en MeriToken. MeriToken n'est pas une monnaie — c'est une **mesure de voix et de réputation**.

### Pourquoi c'est nécessaire

Dans la société traditionnelle, la position sociale et la voix d'une personne dépendent de ses contributions, de sa réputation et de la confiance accumulée. Mais ceux-ci sont souvent vagues, subjectifs et difficiles à quantifier.

Dans l'écosystème Fay, la plupart du travail est effectué par les Fays, et chaque collaboration et contribution peut être suivie et enregistrée avec précision. GMChain est ce système de suivi et d'enregistrement — il rend « qui a contribué quoi » transparent, vérifiable et immuable.

MeriToken est l'unité de mesure sur GMChain, représentant la contribution sociale. Son objectif n'est pas « acheter des choses » mais plutôt :
- **Mesurer la contribution** : Quelle valeur votre iFay a-t-elle créée pour la société ?
- **Construire la réputation** : Plus de contributions signifient une réputation plus élevée et une plus grande confiance dans le réseau de collaboration
- **Gagner de la voix** : Les contributeurs ont une plus grande voix dans les décisions nécessitant un consensus communautaire
- **Inciter la collaboration** : Les contributions dans la collaboration Fay-à-Fay sont équitablement enregistrées et récompensées

### Position de GMChain

GMChain est une **infrastructure de mesure de valeur qui couvre tous les niveaux** du système iFay. Elle n'appartient à aucun module spécifique mais fournit des capacités de suivi des contributions et de mesure de la valeur pour l'ensemble de l'écosystème.

Dans le framework CPE+M, M (Merit) représente la couche de mesure des contributions incarnée par GMChain — elle couvre les couches Context, Protocol et Environment, fournissant des mécanismes unifiés d'enregistrement des contributions et d'incitation pour tous les participants (humains, iFay, coFay, fournisseurs de services).

```
Position de GMChain dans le framework CPE+M
┌─────────────────────────────────────────────┐
│  Merit (M) — GMChain / MeriToken            │  ← Couvre toutes les couches
│  Suivre, mesurer, évaluer les contributions,│
│  inciter la création de valeur              │
├─────────────────────────────────────────────┤
│  Context (C)  │  Protocol (P)  │  Env (E)  │
│  Contexte     │  Protocole     │  Environ-  │
│  Environnement│  Système       │  nement    │
└─────────────────────────────────────────────┘
```

### Mécanismes fondamentaux de GMChain

**1. Enregistrement des contributions**

GMChain enregistre les types de contributions suivants :
- Tâches accomplies par la collaboration Fay-à-Fay (ex., un coFay de voyage réservant des billets pour vous)
- Fourniture de services d'assemblage d'informations (ex., nettoyage de données, organisation de connaissances)
- Fourniture de services API et de compétences
- Fourniture de ressources d'appareils et de calcul
- Fourniture d'environnements d'exécution
- Autres apports de valeur ajoutée reconnus par la communauté

**2. Négociation de prix**

Les Fays négocient les prix (en unités μ) avant d'exécuter des tâches collaboratives. Cela garantit :
- Chaque contribution de collaboration est traçable et évaluable
- Pas de « être payé sans travailler » ou de valeur artificiellement gonflée
- Les contributeurs reçoivent des récompenses équitables

**3. Grand livre MeriToken**

Le Grand livre MeriToken est l'enregistrement du score de contribution pour chaque Fay et humain. Il enregistre :
- Contributions totales cumulées
- Distribution par type de contribution
- Score de réputation (basé sur la qualité des contributions et le feedback de collaboration)
- Poids de voix (poids de vote dans la gouvernance communautaire)

### Différences fondamentales avec les cryptomonnaies traditionnelles

| Dimension | Cryptomonnaie traditionnelle | MeriToken |
|-----------|------------------------------|-----------|
| **Acquisition** | Consommation de puissance de calcul pour des tâches computationnelles (minage) | Création de valeur sociale (contribution) |
| **Ancrage de valeur** | Offre/demande du marché et spéculation | Contribution sociale |
| **Objectif** | Actif financier, instrument d'investissement | Mesure de réputation, voix, incitation à la collaboration |
| **Relation avec la monnaie fiat** | Échangeable avec la monnaie fiat | Non échangeable avec la monnaie fiat |
| **Volatilité** | Très volatile | Croissance stable (les contributions ne font qu'augmenter) |

### Vision à long terme et position actuelle

> ⚠️ **Note importante** : GMChain/MeriToken est un produit de vision à long terme pour une société entièrement pilotée par l'IA, appartenant à la Phase 5 de la Feuille de route (Fay redéfinit la structure du travail et la distribution de la valeur) comme composant central. Nous ne nous précipiterons pas pour implémenter GMChain et MeriToken à court terme, mais devons leur réserver une place dans la conception du système car ils sont l'infrastructure clé pour l'évolution de l'écosystème iFay de « l'utilisation d'outils » à la « collaboration sociale ».
>
> Nous nous engageons à :
> - GMChain n'acceptera jamais d'injection monétaire
> - MeriToken ne sera pas échangeable avec la monnaie fiat
> - MeriToken mesure la contribution sociale, pas les actifs financiers
>
> Dans une société entièrement pilotée par l'IA, la satisfaction des besoins de survie et sociaux ne dépend pas du coût monétaire. Le mécanisme d'ancrage de valeur de MeriToken est fondamentalement différent des cryptomonnaies traditionnelles. Les détails seront progressivement affinés par une argumentation rigoureuse dans les phases ultérieures.

### Scénario

> Votre iFay réserve un vol pour vous et contacte un coFay de voyage via le Protocole de Télépathie. Le coFay de voyage propose 15μ pour le service complet de réservation. Votre iFay accepte le devis, et après que le coFay de voyage a terminé la tâche, GMChain enregistre automatiquement cette collaboration :
>
> - Le Grand livre MeriToken du coFay de voyage augmente de 15μ (contribution de service)
> - Le Grand livre MeriToken de votre iFay enregistre une « consommation de service » (pas de déduction de points, seul l'historique de collaboration est enregistré)
> - Le Grand livre MeriToken du coFay de la compagnie aérienne augmente de 2μ (contribution pour la fourniture de l'interface SSP)
>
> À mesure que le coFay de voyage accumule plus d'enregistrements de contribution, son score de réputation augmente, devenant de plus en plus fiable dans le réseau de collaboration — plus d'iFays le choisiront préférentiellement, formant un cycle positif.

### Pour les développeurs

GMChain appartient à la **Phase 5 (Fay redéfinit la structure du travail et la distribution de la valeur)** comme composant central, mais ses définitions d'interface doivent être réservées dans les phases précoces.

- **Projet indépendant** : GMChain est un [projet open-source indépendant](https://github.com/ChainModePilot/Global-Merit-Chain) ; voir [documentation GMChain](https://github.com/ChainModePilot/Global-Merit-Chain/wiki)
- **Spécification d'interface** : Interface `MeritLedger` avec `recordContribution()` (enregistrer contribution), `getBalance()` (consulter solde), `getReputation()` (consulter score de réputation), `negotiate()` (négociation de prix)
- **Unité de mesure** : μ (MU, Merit Unit), la plus petite unité de MeriToken
- **Tests de conformité** : iFACTS L4 vérifie l'immuabilité des enregistrements de contribution et l'équité de la négociation de prix
- **Points de conception** : Les enregistrements de contribution sont immuables ; la négociation de prix se termine avant l'exécution de la tâche ; MeriToken n'est pas échangeable avec la monnaie fiat ; les scores de réputation sont basés sur la qualité des contributions et le feedback de collaboration
