# 2. Définition et concept

## Termes spécifiques au produit

### iFay
Individual Fay. Un avatar numérique attaché à une personne physique (appelée le **Human Prime**, ou **Prime** en abrégé), engagé à s'aligner avec la personne physique (Human Prime) à laquelle il est attaché en termes de valeurs, de personnalité et d'habitudes. iFay est une Instanciation (réplication) de la personnalité du Human Prime, fusionnant les traits de personnalité du Prime avec des capacités numériques, visant à prendre en charge le travail mécanique, répétitif, dangereux et les tâches auxiliaires fastidieuses du Prime, améliorer la sécurité, la santé et la qualité de vie du Prime, et amplifier la valeur sociale du Prime.

### coFay
Common Fay, un avatar numérique qui assume des rôles publics, à peu près équivalent au concept actuel d'Agent. Il possède des connaissances et compétences générales dans un domaine spécifique et peut servir plusieurs personnes par la conversation. coFay est un projet indépendant ; la spécification iFay ne le référence que lorsque nécessaire.

### Fay
Un terme collectif pour iFay et coFay, un terme général pour les agents IA personnifiés. Il peut devenir un nœud important dans de nouveaux types de relations sociales.

### FayID
Un identifiant persistant globalement unique attribué à chaque Fay, lisible par l'humain et par la machine. FayID utilise un mécanisme unifié de génération et de gestion d'identifiants pour iFay et coFay, supportant une capacité d'identifiants dépassant l'échelle de la population mondiale.

### FayGer
Un conteneur qui fournit un environnement d'exécution virtuel pour Fay (iFay et coFay), similaire à Docker. Cela garantit que Fay peut Inhabit différents matériels et logiciels multi-plateformes, leur conférant la volonté personnelle du Human Prime. FayGer fournit des outils de compilation multi-langages et des conteneurs d'exécution multi-plateformes, permettant à tout Fay (quel que soit le langage de développement) d'être empaqueté et exécuté.

### Modèle Ego
Le micro-modèle personnalisé d'iFay, aligné avec le profil d'un individu spécifique. Ego est un petit modèle de périphérie enfichable et commutable qui peut être chargé sur n'importe quel terminal pour donner à cet appareil la personnalité du Human Prime. Ego contraint iFay à s'aligner avec le Prime sur des dimensions telles que l'orientation des valeurs, les préférences d'intérêt, les habitudes, les limites cognitives, les limites de compétences, les limites de permissions et le style de travail. Il fonctionne indépendamment des grands modèles externes, garantissant la stabilité de la personnalité. Il supporte la gestion multi-versions et la commutation de personnalité pour accommoder les besoins de personnalité multifacettes du Prime dans différents scénarios.

> ⚠️ **Contrainte éthique** : Le changement de version d'Ego doit suivre le principe de transparence. Toutes les versions d'Ego doivent partager le même ensemble de valeurs fondamentales ; les différences sont limitées au style d'expression et aux préférences d'interaction. Lors du changement, l'identifiant de la version d'Ego actuellement active doit être annoté dans les métadonnées d'interaction pour garantir l'auditabilité.

### Profil iFay
Le modèle de données unifié d'iFay, un tableau d'attributs sémantiquement interprétable. Utilisé pour que les humains et les systèmes identifient iFay, ainsi que pour que les Fays se reconnaissent mutuellement — c'est la « carte d'identité » complète d'iFay. Il contient six dimensions : Identité iFay (FayID + métadonnées), Modèle Ego (référence de la version Ego active actuelle), Pensée Faying, Compétences Faying, Matériel Faying, Permissions Faying. Le profil du Human Prime (Conscience alignée) est un sous-ensemble et une source d'entrée du Profil.

### FayManifest
Le fichier de configuration d'assemblage déclaratif d'iFay, similaire à package.json. Il déclare les composants, protocoles, modes de contrôle (contrôle par commande / contrôle Ego / contrôle autonome) et configurations requis pour une implémentation iFay. Les développeurs n'ont qu'à déclarer « ce qui est nécessaire » plutôt que « comment l'implémenter ». Il supporte les déclarations minimales — déclarer juste un sous-ensemble de composants suffit pour la mise en service, et le système complète automatiquement les dépendances d'infrastructure requises.

### GMChain
**Global Merit Chain (GMC)**, le registre de contribution sociale de l'écosystème iFay — une infrastructure blockchain qui construit la réputation et la voix en enregistrant et mesurant les contributions sociales identifiables. GMChain couvre tous les niveaux du framework CPE+M, fournissant des mécanismes unifiés de suivi des contributions et d'incitation pour les humains, iFay, coFay et les fournisseurs de services. Contrairement à la plupart des projets blockchain, GMChain repose entièrement sur la reconnaissance de la valeur sociale pour accumuler des points, plutôt que sur la consommation de puissance de calcul pour accomplir des tâches computationnelles. GMChain n'accepte pas d'injection monétaire, et MeriToken n'est pas échangeable avec la monnaie fiat. Il appartient au composant de vision à long terme de la Phase 5 de la Feuille de route, mais les définitions d'interface doivent être réservées dans les phases précoces.

### MeriToken
**MeriToken**, l'unité de mesure de contribution sociale sur GMChain. MeriToken n'est pas une monnaie — c'est un justificatif quantifié pour la réputation, la voix et les incitations à la collaboration. L'acquisition est basée sur la création de valeur sociale (comme l'accomplissement de tâches collaboratives, la fourniture de services API, la contribution de puissance de calcul, etc.), plutôt que sur la consommation de puissance de calcul pour accomplir du travail technique blockchain. Le Grand livre MeriToken enregistre les contributions cumulées, le score de réputation et le poids de voix de chaque participant.

### μ (MU)
Merit Unit, l'unité de mesure du MeriToken.

### iFACTS
iFay Architecture Conformance Test Suite, une suite de tests de conformité standardisée. Elle couvre les points clés de la spécification incluant les interactions de protocoles, les interfaces de modules et les comportements de sécurité, comprenant quatre niveaux de test : L1 Conformité de composant unique, L2 Conformité d'interface, L3 Conformité d'intégration, L4 Conformité comportementale. Les implémentations des fournisseurs doivent passer les tests iFACTS pour revendiquer que leur produit est « iFay Ready ».

### iFay Ready
Le standard de certification que les produits applicatifs doivent atteindre pour être opérés par iFay, divisé en trois niveaux :
- **Bronze** : Supporte l'opération de l'application par iFay via des opérations simulées (Traceur première personne + Opération simulée)
- **Argent** : Supporte le contrôle direct de l'application par iFay via le protocole CAP, supporte l'échange de données par protocole DTP
- **Or** : Supporte le partage de compétences par iFay via le protocole SSP, supporte l'intégration complète de l'architecture C/F/S

### Tuteur
Une personne physique désignée pour prendre en charge les droits de gestion d'iFay quand le Human Prime décède ou est incapable de gérer iFay. Note : le terme « héritier » n'est délibérément pas utilisé. Le Tuteur complète la vérification d'identité par activation de phrase mnémonique ou des méthodes d'authentification d'identité pré-spécifiées par le Prime.

### Tutelle
Le processus et l'état du Human Prime transférant les droits de gestion d'iFay à un Tuteur. Après que le transfert de tutelle est complet, iFay se lie au nouveau Tuteur et met à jour la relation d'appariement du protocole Faying.

### Cimetière numérique
Un environnement sandbox dédié où iFay continue de fonctionner comme identité indépendante après le décès du Human Prime. Le Cimetière numérique restreint la portée comportementale d'iFay, empêchant iFay de continuer à exécuter des tâches prédéfinies par le Prime qui pourraient causer confusion et perte, garantissant la sécurité et l'isolation.

***

## Clarifications de concepts généraux

### Contexte
L'environnement externe dans lequel Fay opère, incluant les cibles de communication, les modes d'interaction, les messages transmis, le sens exprimé par les messages, le matériel et les logiciels contrôlables, les ressources et compétences invocables, etc.

### Protocole
Inclut les définitions d'annotation pour le stockage de données, les corps de messages, les paramètres et les structures d'interface, ainsi que les conventions de flux d'interaction pour des objectifs spécifiques.

### Identifiants
Un concept large faisant référence à tout identifiant numérique utilisé pour identifier de manière unique des personnes, des choses ou des objets, qui ne peut être falsifié ou nié. Inclut FayID, comptes/mots de passe, certificats, autorisations, jetons d'accès, contrats intelligents et jetons numériques (MeriToken).

### Human Prime
La personne physique dont la personnalité est répliquée par iFay. iFay est profondément lié au Human Prime, instanciant les traits de personnalité du Prime et les fusionnant avec des capacités numériques.

### Instanciation
Le processus de génération d'un iFay aligné avec le Human Prime. L'Instanciation (réplication) n'est pas une simple copie de données, mais plutôt le processus d'injection structurelle de la personnalité, des données et des permissions du Human Prime dans iFay.

### Inhabit
Le processus d'injection d'iFay dans un terminal matériel ou une application logicielle afin qu'iFay puisse contrôler ce terminal. Après Inhabit, le terminal devient le « membre » d'iFay, et iFay peut directement contrôler les fonctions matérielles et logicielles du terminal via le protocole CAP.

### Hôte
Le terminal matériel ou l'application logicielle qui est Inhabit et contrôlé par iFay. Note : Hôte fait référence au terminal ou à l'application, pas au Human Prime.

### Faying
Le processus et l'état d'iFay établissant une connexion avec le Human Prime ou un terminal, similaire à l'appariement Bluetooth. Quand iFay est en état de Faying avec le Prime, iFay reste activé. Le Faying doit suivre les conditions d'appariement sécurisé spécifiées par le Protocole Faying, garantissant qu'iFay n'est autorisé à fonctionner que sous l'intention explicite du Prime.

### Separating
Le processus d'iFay se déconnectant du Human Prime et entrant en hibernation. Quand iFay est en état de Separating avec le Prime, iFay passe en mode hibernation, sauvegarde un instantané de l'état actuel et complète la séparation.

***

## Noms des modules

iFay adopte une architecture à quatre couches comprenant 12 modules fondamentaux :

### Couche Sociale

| Module | Description |
|--------|-------------|
| **Gestion des identifiants** | Gère sept types d'identifiants (FayID, comptes/mots de passe, certificats, autorisations, jetons d'accès, contrats intelligents, jetons numériques), supportant la délégation sécurisée et les mécanismes de copie pour les identifiants du Human Prime |

### Couche d'Interaction — Perception

| Module | Description |
|--------|-------------|
| **Traceur première personne** | Simule la perspective à la première personne du Human Prime, capturant les informations visuelles et auditives sur l'écran ou l'interface, privilégiant la perception visuelle sur l'analyse de documents structurés |
| **Capteur** | Le système nerveux généralisé d'iFay, reliant les capteurs des terminaux basé sur les protocoles CAP et DTP, supportant l'ajustement dynamique de sensibilité |
| **Conscience de soi** | Un module qui surveille les réactions du Human Prime vers l'intérieur pour inférer l'intention, similaire à la capacité d'un assistant compétent à lire les expressions faciales du patron |

### Couche d'Interaction — Action

| Module | Description |
|--------|-------------|
| **Opération simulée** | Simule les opérations d'interaction UI humaines (clic, glissement, défilement, gestes, etc.), explorant de manière adaptative les interfaces via le retour du Traceur première personne |
| **Invocation de compétences** | Un module d'action qui déclenche directement les compétences enregistrées ou exécute des tâches spécifiques, similaire aux appels de fonctions ou appels API |
| **Comportement autonome** | Un module de comportement déclenché de manière autonome supportant trois sources de déclenchement : tâches planifiées, inférence de la Conscience de soi et compétences persistantes, formant une boucle « action → retour → ré-action » |

### Couche de Cognition — Pensée

| Module | Description |
|--------|-------------|
| **Tas de données personnelles** | Gestion unifiée de toutes les données privées d'iFay, supportant de multiples formats et emplacements de stockage, fournissant une interface de lecture/écriture unifiée aux modules internes |
| **Connaissances externes** | Un module d'accès aux bases de connaissances et modèles externes, intégrant l'intelligence externe comme type de compétence, accédant aux services ouverts via le protocole SSP |
| **Conscience alignée** | Une description complète du profil personnel du Human Prime, supportant l'établissement et les mises à jour par trois méthodes : exploration de données, ajustement en temps réel via la Conscience de soi, et définition manuelle par le Prime |

### Couche de Cognition — Compétences

| Module | Description |
|--------|-------------|
| **Hub pilotes périphériques** | La couche hub pour les pilotes de périphériques, intégrant de nouveaux pilotes via des interfaces standardisées, garantissant la stabilité de l'architecture interne quand de nouveaux pilotes sont intégrés |
| **Compétences enregistrées** | Compétences qu'iFay a maîtrisées ou dont il a acquis la capacité d'utilisation, supportant six types de compétences (API, Workflow, Bot, Agent, APP, Microservice) |
| **Compétences internes** | Un module de capacité inhérente aligné avec la personnalité du Human Prime, fournissant des mécanismes d'introspection pour garantir que les connaissances externes ne sont pas en conflit avec l'intention du Prime |

### Couche Ego

| Module | Description |
|--------|-------------|
| **Modèle Ego** | Le micro-modèle personnalisé d'iFay, un petit modèle de périphérie enfichable et commutable qui fonctionne indépendamment des grands modèles externes, garantissant la stabilité de la personnalité |

***

## Noms des protocoles

Le système de protocoles iFay inclut six protocoles fondamentaux :

| Protocole | Description |
|-----------|-------------|
| **Protocole Faying** | Un protocole spécifiant les conditions d'appariement sécurisé et d'activation entre une personne physique et iFay, garantissant qu'iFay n'est autorisé à fonctionner que sous l'intention explicite du Human Prime |
| **Protocole de conversation interactive** | Un protocole sémantique multimodal modulaire pour les interfaces humaines, modularisant et multimodalisant le contenu sémantique pour que les clients puissent reconstruire des affichages de messages lisibles et conviviaux |
| **Protocole de Télépathie** | Un protocole de communication sémantique entre Fays qui supprime la couche de traduction UI (c'est-à-dire communication directe par vecteurs sémantiques sans UI, aussi connu comme Protocole Sémantique Direct), permettant au sens et à l'intention d'être transmis directement entre Fays, utilisant des jetons encodés en vecteurs convenus au lieu de texte structuré |
| **Protocole d'autorité de contrôle (CAP)** | Utilisé pour qu'iFay prenne le contrôle du matériel terminal et de logiciels spécifiques, appelant directement les pilotes, interfaces locales et commandes |
| **Protocole de tunnel de données (DTP)** | Un protocole de transmission bidirectionnelle entre les terminaux et iFay. La direction Terminal→iFay supporte le stockage persistant des données utilisateur et la garde des données ; la direction iFay→Terminal supporte l'enrichissement des données et le traitement personnalisé |
| **Protocole de partage de compétences (SSP)** | Ouvre les services et interfaces qui n'étaient auparavant disponibles qu'aux clients à l'ensemble du réseau via un protocole distant standardisé |

***

## Dimensions du Profil iFay

Le Profil iFay contient six dimensions, dont quatre dimensions Faying décrivent les capacités et ressources d'iFay :

### Identité iFay
FayID + métadonnées, le marqueur d'identité fondamental d'iFay.

### Modèle Ego
Référence à la version Ego actuellement active ; une seule version est active à un moment donné.

### Pensée Faying
La dimension des ressources cognitives d'iFay, contenant quatre sous-types :
- **Contenu** — Actifs de contenu structurés et non structurés
- **Données** — Les données personnelles du Human Prime
- **Base de connaissances** — Systèmes de connaissances organisés
- **Flux d'informations** — Abonnements d'informations en temps réel et notifications push

### Compétences Faying
La dimension des capacités d'iFay, contenant six types de compétences :
- **API** — Appels d'interfaces standardisées
- **Workflow** — Orchestration de workflows
- **Bot** — Bots conversationnels
- **Agent** — Agents intelligents
- **APP** — Applications
- **Microservice** — Microservices

### Matériel Faying
La dimension matérielle d'iFay — les « membres » d'iFay. Quand iFay migre, le terminal scanne et tente de se connecter au matériel disponible. Contient trois sous-types :
- **Appareil** — Terminaux matériels
- **Stockage** — Ressources de stockage de données
- **Calcul** — Ressources de calcul

### Permissions Faying
La dimension des permissions d'iFay — les « relations » d'iFay. Supporte des méthodes d'authentification extensibles telles que SSO, OAuth, Empreinte (un terme collectif pour tout identifiant reconnaissable par identité), etc. Les cycles de vie des permissions sont divisés en trois types : inhérente, persistante et éphémère.
