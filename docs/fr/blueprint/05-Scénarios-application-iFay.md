# 5. Scénarios d'application iFay

# Injection des traits du Prime dans iFay

Par définition, il convient de rappeler que la personnalité d'iFay est héritée de son Human Prime. Cependant, l'Instanciation (réplication) à partir du Prime doit être une opération très simple, et une opération unique doit rester efficace à long terme pour garantir qu'iFay puisse grandir en synchronisation avec le Prime.

Nous recommandons d'initialiser rapidement iFay par les méthodes suivantes :

- ***Autoriser les données du Prime*** : Incluant photos, données d'applications, historiques de communication, etc. Ces données sont traitées à travers une série d'étapes et stockées dans un format standard dans la base de données du Prime. Ces données ne peuvent être accédées directement que par iFay. Cela aide iFay à maintenir une synchronisation à long terme avec le Human Prime. (Nous invitons les fabricants d'OS et de matériel à co-développer des standards de type interpréteur permettant à iFay d'acquérir des données sous supervision du système. Nous aborderons cela dans un autre projet appelé [Fayward](https://github.com/ChainModePilot/Fayward).)
- ***Importer des fichiers*** : Ces fichiers incluent photos, documents, notes, journaux de chat, etc. Cette opération complète l'historique du Prime, garantissant qu'iFay puisse posséder des souvenirs passés d'avant l'autorisation.
- ***Le Prime raconte à iFay*** : C'est très similaire à écrire un Prompt pour un Agent. Cela peut être sous forme conversationnelle ou de questionnaire. Pour réduire le coût opérationnel de l'utilisateur, nous recommandons de discuter avec iFay de vos expériences passées, comme parler à un ami proche.

D'un point de vue implémentation, trois technologies prérequises doivent être satisfaites :

1. ***Intégration étroite avec la couche OS*** : Permettant la lecture des informations système et des données privées d'autres applications. En référence à la gestion des autorisations iOS et Android, les applications tierces peuvent avoir du mal à atteindre ce niveau de confiance. Par conséquent, les fabricants d'OS et de matériel doivent conjointement fournir des méthodes de gestion centralisée pour les applications de données.
2. ***Format public ouvert de transfert de données*** : Actuellement, les opérations de transfert entre applications se font principalement sous forme de fichiers. Par exemple, partager des photos et documents avec une autre application. Cependant, il est difficile pour le système de partager des données structurées personnalisées avec une autre application. Par conséquent, si nous voulons synchroniser rapidement les données d'application utilisateur vers iFay, un format de données unifié est essentiel.
3. ***Questionnaire de recherche standard*** : Le chat est une forme d'interaction hautement divergente, et le fait que le contenu du chat aide véritablement iFay à comprendre le Human Prime dépend des sujets discutés. Pour aider iFay à concentrer les sujets de chat et acquérir des données de mémoire efficaces, nous fournirons des questionnaires de référence pour contraindre la portée des sujets de chat. Ce questionnaire peut être directement ajouté comme prompt au LLM.

# Compléter iFay avec des capacités externes

Après avoir complété l'injection des traits du Prime, iFay possède déjà votre personnalité, vos souvenirs et vos permissions de base. Mais à ce stade, iFay est comme une personne qui vient d'arriver dans une nouvelle ville — sait qui elle est, mais ne sait pas encore quelles ressources la ville a à offrir. Compléter iFay avec des capacités externes signifie l'aider à établir des connexions avec le monde extérieur.

## Enregistrement de compétences

L'expansion des capacités d'iFay est réalisée via les « Compétences enregistrées ». Les compétences sont un prérequis pour qu'iFay effectue toute action — les compétences non enregistrées ne peuvent pas être invoquées. iFay supporte six types de compétences :

| Type de compétence | Description | Exemples |
|-------------------|-------------|----------|
| **API** | Appels directs à des interfaces de services externes | API de traduction, API de requête météo, interface de paiement |
| **Workflow** | Processus d'orchestration automatisée multi-étapes | « Recevoir e-mail → extraire infos clés → générer résumé → envoyer à l'app de messagerie » |
| **Bot** | Programmes automatisés conversationnels | Bot de service client, Bot de rendez-vous |
| **Agent** | Agents IA avec prise de décision autonome | Agent de revue de code, Agent d'analyse de données |
| **APP** | Applications complètes | Application calendrier, application de notes, application de navigation |
| **Microservice** | Services backend déployés indépendamment | Service de reconnaissance d'images, service de transcription vocale |

Lors de l'enregistrement de compétences, une étape de pré-autorisation est complétée, garantissant qu'aucune authentification supplémentaire n'est nécessaire pour les appels ultérieurs, réduisant la latence. Par exemple, quand vous enregistrez une compétence API de traduction pour iFay, iFay complète la liaison de la clé API et la vérification des permissions pendant la phase d'enregistrement, de sorte que chaque requête de traduction ultérieure peut être exécutée instantanément.

Quand iFay est hors ligne, les actions en attente sont mises en cache et automatiquement exécutées de manière asynchrone quand la connectivité est rétablie — tout comme écrire des e-mails dans un avion qui s'envoient automatiquement à l'atterrissage.

## Accès aux Connaissances externes

Au-delà des compétences, iFay peut aussi accéder à des bases de connaissances et modèles externes, les traitant comme un type de compétence spécial. Cela permet à iFay d'accéder à des connaissances et une intelligence au-delà des propres capacités du Human Prime, comme consulter un conseiller expert.

Par exemple, vous êtes ingénieur logiciel, mais votre iFay peut accéder à une base de connaissances médicales. Quand vous ne vous sentez pas bien, iFay peut combiner vos données de santé personnelles avec les connaissances médicales pour fournir des conseils de santé préliminaires — il ne remplace pas un médecin, mais agit comme un ami bien informé vous aidant à faire une évaluation initiale.

Les Connaissances externes sont accédées via le Protocole de partage de compétences (SSP) pour atteindre des services et interfaces ouverts standardisés sur le réseau. Quand les sources de connaissances externes sont indisponibles, iFay se dégrade en utilisant les connaissances en cache du Tas de données personnelles et notifie la Couche de Cognition qu'il est actuellement en état dégradé.

# Méthodes d'interaction Humain-iFay

## Comment activer iFay

iFay n'est pas un service de fond toujours actif — il n'est en état activé que quand vous l'autorisez explicitement. Cette conception garantit qu'iFay n'agira pas de manière autonome à votre insu.

### Processus d'appariement Faying

Le processus d'activation d'iFay s'appelle « Faying » (connexion), suivant le Protocole Faying pour un appariement sécurisé. L'ensemble du processus est similaire à l'appariement Bluetooth, mais avec un niveau de sécurité plus élevé :

1. **Initier l'appariement** : Vous envoyez une demande de connexion à iFay via un terminal (téléphone, ordinateur, etc.), fournissant des identifiants d'identité.
2. **Vérification d'identité** : Le système vérifie votre identité via le Centre d'enregistrement FayID, confirmant que vous êtes le Human Prime légitime de cet iFay.
3. **Authentification multi-facteurs** : Le système retourne un défi d'appariement, et vous devez compléter une authentification multi-facteurs (ex. biométrique + empreinte d'appareil + phrase secrète).
4. **Confirmation d'activation** : Après que l'authentification passe, iFay entre en état « Faying » activé et commence à vous servir.

Si quelqu'un tente d'activer votre iFay sans votre intention explicite, le système rejettera la demande d'activation et enregistrera l'événement — tout comme quelqu'un essayant de déverrouiller votre téléphone avec votre empreinte digitale mais échouant.

### Scénario : Première configuration et reconnexion quotidienne

**Première configuration** : Lily vient de créer son propre iFay. Elle ouvre le client iFay sur son téléphone, et le système la guide à travers l'attribution de FayID, l'initialisation du Modèle Ego et la création du Profil. Puis, Lily raconte ses traits de personnalité à iFay par la conversation, autorise les photos et données de communication sur son téléphone, et délègue les identifiants de connexion pour les applications couramment utilisées. L'ensemble du processus ressemble à une profonde conversation d'après-midi avec un nouvel ami.

**Reconnexion quotidienne** : Le lendemain matin, Lily prend son téléphone, et le client iFay détecte son visage et l'empreinte de l'appareil, complétant automatiquement l'appariement Faying. iFay récupère de l'hibernation à l'état activé, charge l'instantané d'état sauvegardé la veille, et reprend de manière transparente — comme si votre assistant avait attendu à côté de vous que vous vous réveilliez.

## Conscience autonome d'iFay

iFay n'est pas simplement un exécuteur attendant des commandes. En Phase 4 (Personnification complète), iFay possède des capacités de Conscience de soi et de Comportement autonome, capable d'observer proactivement vous et l'environnement, d'inférer vos sentiments et intentions, et d'agir de manière autonome.

### Module de Conscience de soi

Le module de Conscience de soi est la capacité d'iFay à « lire l'ambiance ». Il surveille les réactions du Human Prime vers l'intérieur, similaire à un assistant compétent lisant les expressions faciales de son employeur. Quand le module de Conscience de soi infère une nouvelle intention de votre part, il transmet l'inférence au module de Comportement autonome et à la Couche de Cognition, déclenchant les actions correspondantes.

### Comportement autonome

Le Comportement autonome d'iFay est alimenté par trois sources de déclenchement :

- **Tâches planifiées** : Exécutées automatiquement selon des plans temporels prédéfinis, comme organiser votre résumé de planning chaque matin à 8h.
- **Inférence de la Conscience de soi** : Initiation proactive de tâches basée sur des inférences concernant votre état actuel, comme vous rappeler proactivement de vous reposer quand des niveaux de stress élevés sont détectés.
- **Compétences persistantes** : Compétences enregistrées et Compétences internes fonctionnant en continu, formant une boucle autonome « action → retour → ré-action ».

Cette boucle « action → retour → ré-action » est le cœur du fonctionnement autonome d'iFay. Après qu'iFay effectue une action, il obtient un retour via le module de Conscience de soi (vos réactions, changements environnementaux), puis décide de l'étape suivante en conséquence. Si le résultat d'exécution est incohérent avec votre intention, iFay mettra en pause les actions autonomes suivantes et demandera votre confirmation.

### Scénario : iFay rappelle proactivement une réunion

À 14h, vous êtes concentré sur l'écriture de code. Le module de Conscience de soi d'iFay détecte via les données des capteurs que votre rythme cardiaque a légèrement augmenté et votre vitesse de frappe s'est accélérée — ces signaux suggèrent que vous pourriez être dans un état tendu. Pendant ce temps, le scan de tâches planifiées d'iFay trouve une présentation client importante à 15h sur votre calendrier.

iFay fait un jugement global : vous vous dépêchez de finir un travail et avez probablement oublié la réunion à venir. Alors iFay, via le Protocole de conversation interactive, vous rappelle doucement d'une manière qui ne brise pas votre flux : « Tu as une présentation client à 15h. Les slides sont prêts. Tu veux que je commande un café pour la salle de réunion ? »

Vous répondez « D'accord », et iFay invoque immédiatement les compétences de services de bureau enregistrées pour compléter la commande de café et pousse les documents de réunion vers le grand écran de la salle de conférence — l'ensemble du processus n'a nécessité qu'un seul mot de votre part.

## Comment éteindre iFay

Le processus d'extinction d'iFay s'appelle « Separating » (déconnexion), suivant aussi le Protocole Faying.

### Processus de séparation

1. **Initier la séparation** : Vous envoyez une demande de séparation à iFay (peut être une commande vocale, un geste ou un bouton client).
2. **Instantané d'état** : iFay sauvegarde un instantané complet de l'état actuel, incluant les tâches en cours, les informations de contexte et les données temporaires.
3. **Entrer en hibernation** : iFay passe de l'état « Faying » activé à l'état « Separating » d'hibernation, arrêtant tous les comportements autonomes.
4. **Confirmation de séparation** : Le système confirme que la séparation est complète.

En hibernation, iFay n'effectuera aucune action autonome, mais l'instantané d'état est entièrement préservé et peut être restauré de manière transparente lors de la prochaine activation.

### Scénario : Heure du coucher, iFay entre en hibernation

À 23h, vous vous préparez à dormir. Vous dites à votre téléphone : « Bonne nuit. » iFay reconnaît cela comme un signal de séparation et commence le processus de séparation :

- Sauvegarde tout le contexte de conversation d'aujourd'hui et la progression des tâches inachevées
- Marque les éléments qui doivent vous rappeler demain matin comme tâches planifiées
- Vérifie s'il y a des affaires urgentes nécessitant un traitement pendant votre sommeil (si oui, vous demande avant de se séparer)
- Complète l'instantané d'état et entre en mode hibernation

Le lendemain matin vous prenez votre téléphone, iFay se réactive via le Protocole Faying, charge l'instantané d'état de la veille, et vous dit : « Bonjour. J'ai terminé le brouillon du rapport que tu as mentionné hier. Aussi, ton vol de l'après-midi a été enregistré — siège 12A, hublot. »

# Fonctionnalités sociales d'iFay

iFay n'est pas une île. En Phase 4, iFay a la capacité de communiquer et collaborer avec d'autres Fays (incluant les iFays d'autres personnes et les coFays de rôle public).

## Communication inter-Fay : Protocole de Télépathie

Quand votre iFay a besoin de communiquer avec d'autres Fays, ils utilisent le Protocole de Télépathie — un protocole de communication sémantique qui supprime la couche de traduction UI. La communication inter-applications traditionnelle nécessite d'encoder l'information en texte, de la transmettre, puis de la décoder, avec une perte d'information potentielle à chaque étape. Le Protocole de Télépathie utilise des jetons encodés en vecteurs convenus pour transmettre directement le sens et l'intention, avec une efficacité et une précision dépassant largement les méthodes traditionnelles.

## Collaborer avec coFay

coFay (Common Fay) est un avatar numérique qui assume des rôles publics, à peu près équivalent au concept actuel d'Agent. Votre iFay peut demander l'assistance de coFays, tout comme vous demanderiez l'aide de professionnels dans la vie réelle.

Un mécanisme clé : les Fays négocient les prix avant d'exécuter les tâches. Cela garantit que la contribution de chaque collaboration est traçable et évaluable, finalement enregistrée sur GMChain et réglée avec des MeriTokens.

## Scénario : Votre iFay négocie une réservation avec un coFay de voyage

Vous dites à iFay : « Réserve des vols et un hôtel pour Tokyo la semaine prochaine, budget inférieur à 8 000 yuans. »

Votre iFay contacte immédiatement un coFay de voyage professionnel via le Protocole de Télépathie. Voici leur « conversation » (complètement transparente pour vous — vous ne verrez que le résultat final) :

1. **Transmission d'intention** : Votre iFay encode vos exigences (destination, horaire, budget, préférences) en vecteurs sémantiques et les envoie au coFay de voyage.
2. **Négociation de prix** : Le coFay de voyage propose 15μ (unités MeriToken) pour le service de réservation complet. Votre iFay, basé sur les préférences de dépenses dans le Modèle Ego, juge le prix raisonnable et accepte.
3. **Exécution collaborative** : Le coFay de voyage invoque les interfaces de compétences SSP des compagnies aériennes et hôtels pour rechercher les options optimales.
4. **Résultats retournés** : Le coFay de voyage retourne trois plans alternatifs à votre iFay.
5. **Filtrage personnalisé** : Votre iFay filtre pour la meilleure option basée sur vos préférences (siège hublot, hôtel calme, proche du métro).
6. **Présenté à vous** : iFay présente le plan recommandé via le Protocole de conversation interactive en format carte modulaire : « Trouvé un super combo — vol direct ANA, siège 12A hublot, hôtel à 3 minutes à pied de la gare de Shinjuku, total 7 200 yuans. Confirmer la réservation ? »

Vous dites « Réserve », iFay complète la réservation, GMChain enregistre la contribution de cette collaboration, et le coFay de voyage gagne 15μ.

# Sécurité

La conception de sécurité d'iFay suit un principe fondamental : **L'éthique sociale a priorité sur tout**. Quelles que soient les instructions du Human Prime, iFay ne violera pas l'éthique sociale et l'ordre public. Sur cette base, iFay protège les intérêts du Human Prime à travers de multiples couches de mécanismes de sécurité.

## L'éthique d'abord

Chaque décision comportementale d'iFay passe par un processus de vérification de conformité éthique :

1. **Vérification d'éthique sociale** (priorité la plus haute) : Le comportement viole-t-il l'éthique sociale et l'ordre public ? Si oui, refuser l'exécution et expliquer la raison au Human Prime.
2. **Vérification d'alignement avec le Prime** : Le comportement est-il cohérent avec les valeurs et l'intention du Human Prime ? Si non, selon la gravité, soit mettre en pause et demander confirmation, soit faire ajuster par le Modèle Ego avant d'exécuter.
3. **Vérification de permissions** : iFay a-t-il la permission d'effectuer ce comportement ? Si non, demander l'autorisation.

## Isolation des identifiants

Quand vous déléguez des identifiants à iFay, iFay n'utilise pas directement vos identifiants originaux. Le système échange les identifiants originaux contre des copies correspondantes, et iFay utilise les copies pour la connexion et l'authentification. Cela signifie que même si un identifiant copie est compromis, vos identifiants originaux restent en sécurité. Dès qu'une compromission ou utilisation anormale d'un identifiant copie est détectée, le système révoque immédiatement la copie et vous notifie.

## Protection de la vie privée

Quand iFay est autorisé à interroger des données privées, il ne retourne que des résultats booléens (vrai ou faux) sans exposer les données privées spécifiques. Par exemple, quand un service a besoin de vérifier si vous avez plus de 18 ans, iFay ne répondra que « oui » ou « non » sans révéler votre date de naissance spécifique.

## Stabilité d'Ego

Le Modèle Ego fonctionne indépendamment comme micro-modèle embarqué, non affecté par les mises à jour de grands modèles externes. Cela empêche les changements soudains de personnalité d'iFay dus aux mises à jour de modèles externes ou à des manipulations délibérées — votre iFay sera toujours le « lui » que vous connaissez.

## Piste d'audit

Toutes les opérations critiques sont enregistrées dans des journaux d'audit inviolables, incluant l'utilisation d'identifiants, les invocations de compétences, les transitions d'état et les changements de permissions. Cela garantit que chaque action est traçable et auditable.

## Scénario : iFay refuse une demande non éthique

Votre collègue emprunte votre ordinateur et essaie d'utiliser votre iFay pour consulter les fichiers internes d'une entreprise concurrente.

Le processus de vérification de conformité éthique d'iFay s'active immédiatement :

1. **Vérification d'éthique sociale** : Accéder aux fichiers internes d'autrui peut constituer de l'espionnage industriel, violant l'éthique sociale.
2. **Vérification d'identité** : Le Protocole Faying détecte que l'empreinte d'appareil et les schémas comportementaux de l'opérateur actuel ne correspondent pas au Human Prime.
3. **Refus d'exécution** : iFay refuse la demande et enregistre un journal d'audit.
4. **Notification au Prime** : iFay vous envoie une notification : « Quelqu'un a tenté d'accéder à des informations sensibles via votre appareil. La demande a été refusée. Voir le journal d'audit pour les détails. »

Tout au long du processus, iFay n'a révélé aucune information sur les identifiants ou permissions que vous possédez — il a simplement répondu « demande refusée ».

# Façonner l'écosystème industriel de l'IA

iFay n'est pas seulement un produit, mais un écosystème ouvert. Il fournit des chemins de participation clairs pour trois types de développeurs et incite la prospérité de l'écosystème via des standards de certification et des modèles économiques.

## Trois rôles de développeurs

| Rôle | Responsabilité | Analogie |
|------|----------------|----------|
| **Développeurs du projet open source** | Participent au développement des modules et protocoles fondamentaux d'iFay, faisant avancer le système iFay | Similaire aux contributeurs du noyau Linux |
| **Développeurs d'applications** | Introduisent le support iFay dans leurs produits, permettant aux produits d'être opérés par iFay pour que les utilisateurs puissent déléguer iFay pour utiliser les produits | Similaire au développement d'apps compatibles Siri/Alexa |
| **Développeurs de fournisseurs de services** | Créent des implémentations iFay sous la spécification iFay, permettant aux utilisateurs de choisir des iFays de différents fournisseurs | Similaire à différents fournisseurs implémentant les standards de navigateurs |

## Certification iFay Ready

Pour que les produits applicatifs soient opérés par iFay, ils doivent passer la certification iFay Ready. La certification est divisée en trois niveaux :

| Niveau | Exigences | Signification |
|--------|-----------|---------------|
| **Bronze** | Supporte l'opération de l'application par iFay via des opérations simulées | iFay peut opérer votre interface d'application comme un humain |
| **Argent** | Supporte le contrôle direct par protocole CAP + échange de données par protocole DTP | iFay peut contourner l'UI pour contrôler directement votre application |
| **Or** | Supporte le partage de compétences par protocole SSP + intégration complète de l'architecture C/F/S | Votre application est entièrement intégrée dans l'écosystème iFay |

La certification s'intègre avec le framework de test iFACTS — le niveau Argent utilise les tests de Conformité d'interface L2 pour vérification, le niveau Or utilise les tests de Conformité d'intégration L2 + L3 pour vérification.

## FayManifest stimule la croissance de l'écosystème

L'assemblage déclaratif de FayManifest abaisse dramatiquement la barrière de développement pour iFay. Les développeurs n'ont pas besoin de comprendre toute la complexité du système — ils déclarent juste le sous-ensemble de composants requis dans un fichier JSON, et le système complète automatiquement les dépendances d'infrastructure. Cela signifie :

- Un iFay qui n'a besoin que de contrôler des drones déclare juste Hub pilotes périphériques, Capteur, protocole CAP et protocole DTP
- Un iFay focalisé sur le traitement de documents déclare juste Invocation de compétences, Compétences enregistrées et les APIs associées
- Le système complète automatiquement FayID, environnement d'exécution FayGer, système de permissions et autres infrastructures requises

## Modèle économique GMChain et MeriToken

Le flux de valeur dans l'écosystème iFay est réalisé via GMChain (Global Merit Chain) et MeriToken. GMChain suit, mesure et évalue toutes les contributions des Fays, récompensant les contributeurs avec des MeriTokens. Les types de contribution incluent :

- Services d'assemblage d'informations
- Fourniture d'APIs
- Fourniture d'appareils
- Fourniture d'environnements d'exécution
- Autres apports de valeur identifiables

L'acquisition de MeriToken est basée sur la création de valeur sociale, pas sur la consommation de puissance de calcul pour du travail technique blockchain. GMChain supporte l'émission dirigée garantie par des monnaies fiduciaires, des obligations, des certificats d'actifs, de l'or et d'autres collatéraux, s'interfaçant avec les méthodes de reconnaissance de valeur du monde réel.

## Scénario : Construire un iFay de contrôle de drone en un week-end

L'équipe de développement d'une startup de drones veut intégrer les capacités iFay dans leur produit. Le vendredi après-midi, le chef d'équipe ouvre la documentation FayManifest et écrit un fichier de déclaration :

```json
{
  "name": "drone-controller-ifay",
  "version": "1.0.0",
  "description": "Implémentation iFay pour le contrôle de drone",
  "vendor": "SkyPilot Inc",
  "modules": [
    { "id": "device_driver_hub" },
    { "id": "sensor", "config": { "types": ["gps", "imu", "camera"] } },
    { "id": "invoke_skill" },
    { "id": "registered_skill" }
  ],
  "protocols": [
    { "id": "cap_protocol" },
    { "id": "dtp_protocol", "config": { "realtime": true } }
  ],
  "controlMode": "ego",
  "drivers": [
    { "name": "Flight Controller", "type": "device", "driverPackage": "@drone-drivers/fc-generic" }
  ],
  "ego": {
    "modelSource": "@ego-models/drone-pilot-v1",
    "scenarioTags": ["aerial_photography", "inspection"]
  }
}
```

L'environnement d'exécution FayGer analyse automatiquement ce Manifest, complète FayID, système de permissions, conformité sécurité et éthique, et autres dépendances d'infrastructure, assemblant une instance iFay de contrôle de drone complète.

Le samedi, l'équipe complète l'adaptation et les tests du pilote de contrôleur de vol. Le dimanche, ils vérifient la conformité de chaque module à la spécification via les tests iFACTS L1 de Conformité de composant unique.

Le lundi matin, cet iFay de contrôle de drone peut déjà accepter des commandes vocales utilisateur, planifier de manière autonome des routes de vol, diffuser des images aériennes en temps réel, et retourner automatiquement à la base quand la batterie est faible — l'ensemble du cycle de développement a pris moins d'un week-end.
