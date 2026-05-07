# 7. Profil iFay

Le Profil iFay est la « carte d'identité » complète d'iFay — un tableau d'attributs à six dimensions sémantiquement interprétable. Il permet non seulement aux humains d'identifier un iFay, mais aussi aux systèmes de l'analyser, et plus important encore, aux Fays de se reconnaître mutuellement.

Le profil du Human Prime (Conscience alignée) est un sous-ensemble et une source d'entrée du Profil iFay. Le profil du Human Prime décrit « quel type de personne est le Human Prime », tandis que le Profil iFay décrit « quel type d'entité est cet iFay » — il inclut les traits de personnalité du Prime, mais aussi les attributs indépendants propres à iFay tels que les compétences, le matériel et les permissions.

Le profil du Human Prime est maintenu par le module [Conscience alignée](./11.3-Conscience-alignée). La dimension des compétences est gérée par les [Compétences enregistrées](./12.2-Compétences-enregistrées), la dimension matérielle par le [Hub pilotes périphériques](./12.1-Hub-pilotes-périphériques), et la dimension des permissions par la [Gestion des identifiants](./8.1-Gestion-des-identifiants).

---

## Identité iFay

L'Identité iFay se compose de FayID et de métadonnées. FayID est un identifiant persistant globalement unique, lisible par l'humain et par la machine — la base pour qu'iFay soit identifié et suivi dans tous les scénarios d'interaction.

L'Identité iFay supporte une migration d'identité fluide — quand iFay évolue d'un assistant personnel à un rôle social autonome, le FayID n'a pas besoin de changer ; l'identité continue naturellement.

---

## Modèle Ego

La dimension Ego dans le Profil enregistre la référence à la version Ego actuellement active.

Le Modèle Ego est un petit modèle de périphérie enfichable et commutable qui peut être chargé sur n'importe quel terminal pour donner à cet appareil la personnalité du Prime. iFay supporte plusieurs versions d'Ego pour accommoder la personnalité multifacettes du Human Prime — mais une seule version est active à un moment donné, empêchant la « personnalité multiple ».

Il existe deux méthodes de commutation : déclenchée manuellement par le Human Prime, ou déterminée automatiquement par iFay en fonction du contexte. Après la commutation, la référence de la version Ego active dans le Profil est mise à jour de manière synchrone.

### Scénario

> Zhang Lei est un chef de produit qui a configuré deux versions d'Ego pour son iFay : « Mode Professionnel » et « Mode Décontracté ».
>
> Les matins de semaine, iFay passe automatiquement en « Mode Professionnel » — les réponses aux e-mails sont rigoureusement formulées, les réunions sont planifiées avec l'efficacité comme priorité, et les documents d'exigences sont traités avec un accent sur la complétude logique.
>
> Les soirs de week-end, iFay détecte que Zhang Lei parcourt des recommandations de restaurants et passe automatiquement en « Mode Décontracté » — les recommandations de restaurants se concentrent davantage sur l'ambiance et les préférences gustatives, et le ton devient détendu et informel.
>
> Deux versions, même Zhang Lei.

---

## Pensée Faying

La Pensée Faying représente les actifs cognitifs d'iFay, contenant quatre sous-types :

| Sous-type | Description | Exemples |
|-----------|-------------|----------|
| **Contenu** | Actifs de contenu structurés ou non structurés | Collection de photos du Human Prime, articles écrits, musique composée, vidéos enregistrées |
| **Données** | Données personnelles | Données de suivi de santé, historiques de dépenses, habitudes d'utilisation d'applications, historique de localisation |
| **Base de connaissances** | Systèmes de connaissances organisés | Notes de domaine professionnel, bibliothèques de matériaux d'étude, résumés d'expérience de travail, rapports de recherche sectorielle |
| **Flux d'informations** | Abonnements d'informations en temps réel | Sources d'actualités suivies, flux de mises à jour sectorielles, mises à jour de réseaux sociaux, cotations boursières |

Les données de la dimension Pensée proviennent de l'initialisation et de l'accumulation continue du Tas de données personnelles, formant la base pour qu'iFay comprenne le monde et porte des jugements.

---

## Compétences Faying

Les Compétences Faying sont les capacités d'action d'iFay, contenant six types de compétences :

| Type | Description |
|------|-------------|
| **API** | Interfaces de programmation directement invocables, comme API de requête météo, API de traduction |
| **Workflow** | Processus automatisés multi-étapes, comme « générer un rapport hebdomadaire chaque lundi et l'envoyer à l'équipe » |
| **Bot** | Bots conversationnels pour des scénarios spécifiques, comme Bot de service client, Bot de rendez-vous |
| **Agent** | Agents intelligents avec prise de décision autonome, comme Agent d'analyse d'investissement |
| **APP** | Applications complètes, comme APP de gestion de calendrier, APP de suivi de santé |
| **Microservice** | Unités de service déployées indépendamment, comme service de reconnaissance d'images, service de transcription vocale |

L'enregistrement de compétences est un prérequis pour qu'iFay effectue toute action. Les compétences enregistrées complètent la pré-autorisation, garantissant qu'aucune authentification supplémentaire n'est nécessaire lors de l'exécution.

---

## Matériel Faying

Le matériel est les « membres » d'iFay. iFay est une entité de personnalité et de cognition ; le matériel est son véhicule pour interagir avec le monde physique.

### Trois sous-types de matériel

| Sous-type | Description | Exemples |
|-----------|-------------|----------|
| **Appareil** | Terminaux matériels | Téléphone, ordinateur, montre connectée, drone, appareils de maison intelligente |
| **Stockage** | Ressources de stockage de données | Stockage cloud, disque dur local, NAS, base de données vectorielle |
| **Calcul** | Ressources de calcul | GPU, nœuds de calcul cloud, appareils de calcul en périphérie |

### Mécanisme de découverte matérielle

Quand iFay migre vers un nouvel environnement, le terminal est responsable de scanner le matériel compatible Faying dans l'environnement actuel — similaire à la façon dont le Bluetooth ou le WiFi scanne les appareils à proximité. iFay lui-même n'effectue pas directement le scan matériel ; au lieu de cela, il effectue une correspondance de capacités basée sur les résultats du scan.

Il y a une distinction clé ici :

- **Quel matériel iFay peut opérer** dépend de ses capacités cognitives (compétences enregistrées, compétences internes)
- **À quel matériel iFay peut se connecter** dépend des appareils réellement disponibles dans l'environnement actuel

### Scénario

> Imaginez une personne qui sait jouer au badminton entrant dans une salle de sport.
>
> « Savoir jouer au badminton » est sa **compétence** — c'est sa propre capacité qu'elle emporte partout. Mais pouvoir réellement jouer dépend de si la salle a des **raquettes** — c'est le matériel fourni par l'environnement.
>
> iFay fonctionne de la même manière. Il pourrait avoir la compétence de contrôler un drone (a enregistré une API de contrôle de vol), mais s'il n'y a pas de drone connectable dans l'environnement actuel, cette compétence ne peut pas être exercée. Inversement, même s'il y a une imprimante 3D dans l'environnement, si iFay n'a pas enregistré la compétence d'opération correspondante, il ne peut que « voir » l'appareil mais pas l'utiliser.

---

## Permissions Faying

Les permissions sont les « relations » d'iFay — elles définissent les limites de confiance entre iFay et le monde extérieur.

### Trois cycles de vie des permissions

| Cycle de vie | Description | Exemples |
|--------------|-------------|----------|
| **Inhérente** | Permissions possédées dès la création | Accès au calendrier du Human Prime, lecture des paramètres de préférences du Prime |
| **Persistante** | Permissions valides à long terme | Accès lecture/écriture à l'e-mail du Prime, accès à l'intranet d'entreprise |
| **Éphémère** | Demandée quand nécessaire, libérée après utilisation | Accès unique aux dossiers médicaux, droits d'appel API temporaires |

### Méthodes d'authentification extensibles

Les méthodes d'authentification d'iFay sont extensibles, supportant SSO, OAuth, Empreinte et d'autres méthodes. « Empreinte » ici est un terme collectif couvrant tout identifiant reconnaissable par identité — reconnaissance faciale, empreinte vocale, empreinte d'appareil, etc. Différents types d'empreintes ont différents niveaux de confiance : la reconnaissance faciale peut avoir une confiance plus élevée que l'empreinte d'appareil, tandis que les combinaisons multi-facteurs ont une confiance plus élevée que les facteurs uniques.

### Scénario

> L'iFay de Wang Fang a trois permissions avec différents cycles de vie :
>
> **Inhérente** : Quand iFay a été créé, il a automatiquement obtenu l'accès au calendrier de Wang Fang — c'est une capacité de base de chaque iFay, ne nécessitant aucune demande supplémentaire.
>
> **Persistante** : Wang Fang a autorisé iFay à gérer son e-mail professionnel à long terme. iFay peut lire les e-mails, rédiger des réponses et gérer les étiquettes — cette permission reste valide jusqu'à ce que Wang Fang la révoque activement.
>
> **Éphémère** : Wang Fang a besoin de consulter le rapport d'examen physique de l'année dernière. Elle demande à iFay de récupérer les dossiers du système hospitalier. iFay demande temporairement une permission d'accès unique aux données médicales, et après avoir obtenu le rapport, la permission est automatiquement libérée — la prochaine fois qu'elle sera nécessaire, une nouvelle demande sera requise.

---

## Visibilité du Profil

La visibilité du Profil est une préoccupation de la couche applicative, déterminée par les scénarios d'application spécifiques et les méthodes d'interaction.

Le même Profil iFay affiche différentes dimensions dans différents scénarios : lors de la collaboration inter-Fay, l'autre partie peut n'avoir besoin de voir que les dimensions compétences et permissions ; dans l'interface de gestion du Human Prime, les six dimensions sont entièrement visibles ; dans les scénarios sociaux publics, seules l'identité et les informations partielles de compétences peuvent être montrées.

Le Profil lui-même ne définit pas « qui peut voir quoi » — cette décision est laissée à l'application utilisant le Profil.
