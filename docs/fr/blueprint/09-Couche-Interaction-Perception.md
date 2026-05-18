# 9. Couche d'Interaction — Perception

Le sous-système de Perception de la Couche d'Interaction représente les « sens » d'iFay — il permet à iFay de voir l'écran, de percevoir l'environnement et de lire vos intentions.


---

## 9.1 Traceur première personne

## Définition en une ligne

Le Traceur première personne est les **yeux et les oreilles** d'iFay — il permet à iFay de voir les images que vous voyez et d'entendre les sons que vous entendez, lui donnant exactement la même perspective à la première personne que vous.

## Pourquoi c'est nécessaire

Imaginez que vous avez embauché un assistant pour vous aider à remplir un formulaire web. Si cet assistant était aveugle — incapable de voir les champs de saisie, les boutons et les messages d'erreur à l'écran — comment pourrait-il vous aider ?

C'est ce que serait iFay sans le Traceur première personne.

Quand les humains utilisent des ordinateurs et des téléphones, ils comptent sur leurs yeux pour voir l'écran et leurs oreilles pour entendre les sons de notification. iFay a besoin des mêmes capacités. Le Traceur première personne est le module qui donne à iFay cette capacité — il permet à iFay de **voir l'écran comme vous**, plutôt que de lire du code comme un programmeur.

Il y a une distinction clé ici : iFay voit ce que vous **voyez à l'œil nu**, pas le code caché derrière les pages web (comme les balises HTML, les mots-clés SEO — des choses que vous ne pouvez pas voir du tout). Tout comme quand vous lisez un livre, vous voyez du texte et des images, pas les fichiers de mise en page de l'imprimerie. iFay fonctionne de la même manière — il privilégie la compréhension « visuelle » des interfaces plutôt que l'analyse de documents structurés.

## Sa position dans l'architecture

```
Architecture à quatre couches d'iFay
├── Couche Sociale
├── Couche d'Interaction          ← Le Traceur première personne est ici
│   ├── Perception (Sens)
│   │   ├── 👉 Traceur première personne   ← Regarde vers l'extérieur, voit l'écran
│   │   ├── Capteur                        ← Perçoit l'environnement
│   │   └── Conscience de soi              ← Regarde vers l'intérieur, vous lit
│   └── Action
│       ├── Opération simulée
│       ├── Invocation de compétences
│       └── Comportement autonome
├── Couche de Cognition
└── Couche Ego
```

Le Traceur première personne se situe dans le **sous-système de Perception de la Couche d'Interaction**. Si iFay était une personne, la Couche d'Interaction serait le « corps » à travers lequel iFay interagit avec le monde extérieur, et le Traceur première personne serait les **yeux et les oreilles** sur ce corps.

## Comment ça fonctionne

Le Traceur première personne fonctionne de manière intuitive — tout comme vous regardant un écran :

**1. Voir l'affichage**
iFay capture ce qui est actuellement affiché sur votre écran — texte, images, boutons, champs de saisie, pop-ups… tout ce que vous pouvez voir, iFay peut le voir aussi.

**2. Entendre les sons**
Si l'interface a des sons de notification, des annonces vocales ou de l'audio vidéo, iFay peut les capturer également.

**3. Suivi des changements en temps réel**
C'est la partie la plus importante. Quand iFay effectue une opération à l'écran (comme cliquer sur un bouton), il doit **immédiatement voir le résultat** — la page a-t-elle navigué ? Un message d'erreur est-il apparu ? L'animation de chargement tourne-t-elle encore ?

Tout comme après avoir cliqué sur un bouton « Soumettre » avec votre souris, vos yeux regardent automatiquement l'écran pour le résultat. Le Traceur première personne d'iFay fait la même chose :
- Suit les changements visuels après le mouvement du curseur
- Suit les zones nouvellement exposées après un changement de fenêtre
- Suit les mises à jour dynamiques de page (comme les données se rafraîchissant en temps réel)

**4. Coordination œil-main**
Le Traceur première personne et le module d'Opération simulée sont des « partenaires » étroitement liés — comme les yeux et les mains d'une personne. Les yeux voient où est le bouton, les mains peuvent cliquer précisément ; après avoir cliqué, les yeux vérifient le résultat. Cette boucle « voir → faire → revoir » est la capacité de coordination œil-main d'iFay.

**5. Signaler « Je ne vois pas »**
Si pour une raison quelconque (écran verrouillé, application plantée, permissions insuffisantes) le Traceur première personne ne peut pas capturer l'affichage, il ne fera pas semblant de rien — il signale honnêtement à la Couche de Cognition d'iFay : « Je ne vois pas. » La Couche de Cognition décide alors quoi faire ensuite (attendre, réessayer ou vous notifier).

## Relations avec les autres modules

| Module associé | Relation | Analogie corporelle |
|----------------|----------|---------------------|
| **Opération simulée** | Étroitement couplé, coordination œil-main | Yeux ↔ Mains |
| **Couche de Cognition** | Signale l'état de perception (normal/dégradé/échoué) | Yeux → Cerveau (« Je vois » ou « Je ne vois pas bien ») |
| **Capteur** | Tous deux dans le sous-système de Perception, mais rôles différents : le Traceur voit l'écran, le Capteur perçoit l'environnement | Yeux vs. nerfs de la peau |
| **Conscience de soi** | Tous deux dans le sous-système de Perception, mais directions différentes : le Traceur regarde vers l'extérieur, la Conscience de soi regarde vers l'intérieur | Yeux vs. intelligence émotionnelle |

## Histoires de scénarios

### Scénario 1 : Remplir un formulaire sur un site gouvernemental

Vous devez remplir un formulaire de demande sur un ancien site gouvernemental. Ce site n'a aucune adaptation IA — pas d'API, pas d'interface structurée, juste un formulaire web simple.

Le Traceur première personne d'iFay « voit » le formulaire : champ de saisie du nom, champ du numéro d'identité, un menu déroulant, une image CAPTCHA, un bouton bleu « Soumettre ». Il transmet ces informations visuelles au module d'Opération simulée, qui remplit les champs un par un, sélectionne les options, entre le CAPTCHA et clique sur soumettre — exactement comme vos mains le feraient.

Après la soumission, le Traceur première personne « regarde » immédiatement le résultat — si un message d'erreur rouge « Format du numéro d'identité incorrect » apparaît, il capture ce changement, et iFay sait qu'il doit corriger et resoumettre.

Tout au long du processus, iFay voit exactement ce que vous voyez — il n'a pas besoin de savoir à quoi ressemble le code HTML du site.

### Scénario 2 : Surveillance boursière en temps réel

Vous demandez à iFay de surveiller le graphique en temps réel d'une action. Le Traceur première personne « regarde » continuellement le graphique en chandeliers et les changements de chiffres à l'écran — le prix passe de 152,30 à 153,10, les barres de volume augmentent soudainement, l'indicateur MACD montre un croisement doré…

Le Traceur première personne suit continuellement tous ces changements en temps réel. Quand le prix atteint votre prix cible, iFay vous notifie immédiatement. Comme si vous surveilliez le marché vous-même, sauf qu'iFay ne sera pas distrait, ne sera pas fatigué, et peut « surveiller » 24h/24 sans interruption.

## Pour les développeurs

Le Traceur première personne appartient à la **Phase 1 (Simulation des opérations humaines)** comme module fondamental — l'un des premiers composants qu'iFay doit implémenter.

- **ID d'exigence** : Exigence 4 (Traceur première personne)
- **Spécification d'interface** : Interface `FirstPersonTracer` avec quatre méthodes fondamentales : `captureVisual()`, `captureAudio()`, `trackChanges()` et `getPerceptionStatus()`
- **Protocoles associés** : La Phase 1 ne dépend pas des protocoles CAP/DTP, implémentant directement via la capture d'écran au niveau OS ; à partir de la Phase 2, des informations d'interface plus profondes peuvent être obtenues via le protocole CAP
- **Tests de conformité** : iFACTS L1 (Conformité de composant unique) vérifie la capacité de capture visuelle ; L2 (Conformité d'interface) vérifie l'interface de coordination œil-main avec le module d'Opération simulée
- **Points de conception** : Privilégier la perception visuelle sur l'analyse de documents structurés ; les échecs de perception doivent être signalés à la Couche de Cognition ; former une boucle de rétroaction fermée avec le module d'Opération simulée


---

## 9.2 Capteur

## Définition en une ligne

Le Capteur est le **système nerveux** d'iFay — il permet à iFay de percevoir tous les changements dans l'environnement, de la température et la localisation au rythme cardiaque et à la lumière, tout comme les terminaisons nerveuses distribuées dans tout votre corps.

## Pourquoi c'est nécessaire

Si le Traceur première personne est les yeux et les oreilles d'iFay, alors le Capteur est l'**ensemble du réseau neural** d'iFay.

Pensez à votre corps : vous ne percevez pas le monde uniquement par les yeux et les oreilles. Votre peau ressent la température et le toucher, votre oreille interne ressent l'équilibre et l'accélération, votre corps vous dit quand vous avez faim, êtes fatigué ou avez froid. Ces sensations ne viennent pas des yeux ou des oreilles — elles viennent du système nerveux distribué dans tout votre corps.

Maintenant pensez à votre téléphone et votre montre connectée : le GPS sait où vous êtes, l'accéléromètre sait si vous marchez ou courez, le capteur de lumière sait si vous êtes à l'intérieur ou à l'extérieur, le capteur de rythme cardiaque sait à quelle vitesse votre cœur bat. Ce sont tous des « capteurs » — les terminaisons nerveuses de l'appareil.

Le module Capteur d'iFay **unifie l'accès** à tous ces capteurs à travers les appareils, donnant à iFay un système nerveux complet. Et ce système nerveux est continuellement extensible — tout nouveau type de capteur qui émerge à l'avenir peut être intégré.

## Sa position dans l'architecture

```
Architecture à quatre couches d'iFay
├── Couche Sociale
├── Couche d'Interaction          ← Le Capteur est ici
│   ├── Perception (Sens)
│   │   ├── Traceur première personne   ← Regarde vers l'extérieur, voit l'écran
│   │   ├── 👉 Capteur                  ← Perçoit l'environnement (température, localisation, mouvement…)
│   │   └── Conscience de soi           ← Regarde vers l'intérieur, vous lit
│   └── Action
│       ├── Opération simulée
│       ├── Invocation de compétences
│       └── Comportement autonome
├── Couche de Cognition
│   ├── Pensée
│   │   ├── Tas de données personnelles    ← Les données du Capteur sont finalement stockées ici
│   │   └── ...
│   └── Compétences
│       ├── Hub pilotes périphériques     ← Les interfaces matérielles du Capteur sont gérées par lui
│       └── ...
└── Couche Ego
```

Le Capteur se situe dans le **sous-système de Perception de la Couche d'Interaction**, aux côtés du Traceur première personne et de la Conscience de soi. Mais le Capteur a une caractéristique spéciale : il ne gère que l'**ajustement de sensibilité** (décider quand collecter plus de données et quand en collecter moins), tandis que les connexions matérielles réelles et le stockage de données sont gérés respectivement par le **Hub pilotes périphériques** et le **Tas de données personnelles** de la Couche de Cognition.

C'est comme votre système nerveux : les terminaisons nerveuses gèrent la perception, mais les voies de conduction des signaux (Hub de pilotes) et le stockage en mémoire (Tas de données) sont gérés par d'autres systèmes.

## Comment ça fonctionne

Le workflow du Capteur peut être résumé en trois mots-clés : **Relier, Réguler, Étendre**.

**1. Relier — Connecter les capteurs des appareils**

Votre téléphone a GPS, gyroscope, accéléromètre, capteur de lumière, baromètre… Votre montre connectée a capteur de rythme cardiaque, capteur d'oxygène sanguin, capteur de température cutanée… Votre maison intelligente a capteurs de température, capteurs d'humidité, capteurs de portes/fenêtres…

Le module Capteur agit comme un « traducteur », traduisant uniformément les données de tous ces différents appareils et types de capteurs dans un format qu'iFay peut comprendre. Il utilise **CAP (Protocole d'autorité de contrôle)** et **DTP (Protocole de tunnel de données)** pour réaliser ce pontage.

**2. Réguler — Sensibilité dynamique**

Votre système nerveux a une caractéristique intelligente : quand vous êtes concentré sur votre travail, vous sentez à peine le toucher de la chaise ; mais quand quelqu'un tapote votre épaule, vous le sentez immédiatement. C'est la régulation dynamique de sensibilité.

Le Capteur d'iFay fonctionne de la même manière. Il n'a pas besoin de collecter des données de tous les capteurs à précision maximale en permanence — cela gaspillerait trop de ressources. Par exemple :
- Quand vous travaillez tranquillement au bureau, le GPS n'a pas besoin de mettre à jour votre position chaque seconde
- Mais quand vous conduisez avec la navigation, le GPS a besoin de mises à jour haute fréquence
- Quand vous dormez, le capteur de rythme cardiaque peut baisser sa fréquence d'échantillonnage
- Mais quand un rythme cardiaque anormal est détecté, la fréquence d'échantillonnage augmente immédiatement

Le module Capteur **ajuste automatiquement la sensibilité de chaque capteur** en fonction du scénario et des besoins actuels.

**3. Étendre — Les capteurs futurs peuvent aussi être intégrés**

Les capteurs d'aujourd'hui sont GPS et moniteurs de rythme cardiaque ; ceux de demain pourraient être des capteurs d'ondes cérébrales, des capteurs de qualité de l'air, ou même des capteurs de reconnaissance d'émotions. La conception du module Capteur est ouverte — quand de nouveaux types de capteurs apparaissent, il suffit d'enregistrer un nouveau pilote via le Hub pilotes périphériques, et le module Capteur peut gérer sa sensibilité tandis que le Tas de données personnelles stocke ses données.

## Relations avec les autres modules

| Module associé | Relation | Analogie corporelle |
|----------------|----------|---------------------|
| **Hub pilotes périphériques** | Les interfaces matérielles réelles du Capteur sont gérées par le Hub pilotes périphériques | Terminaisons nerveuses → voies de conduction nerveuse |
| **Tas de données personnelles** | Les données collectées par les capteurs sont finalement stockées dans le Tas de données personnelles | Signaux sensoriels → stockage en mémoire |
| **Traceur première personne** | Tous deux dans le sous-système de Perception, mais rôles différents : le Traceur voit l'écran, le Capteur perçoit l'environnement physique | Yeux vs. nerfs du corps entier |
| **Conscience de soi** | Le Capteur fournit des données environnementales ; la Conscience de soi utilise ces données pour inférer l'état du Human Prime | Le système nerveux fournit des sensations → le cerveau interprète les émotions |
| **Protocoles CAP / DTP** | Le Capteur implémente le pontage de données basé sur ces deux protocoles | Protocole de transmission des signaux nerveux |

## Histoires de scénarios

### Scénario 1 : Rappel de santé intelligent

À 15h, vous êtes assis devant votre ordinateur depuis trois heures. iFay découvre via les données des capteurs de votre montre connectée :

- **Accéléromètre** : Presque aucun mouvement significatif dans les 3 dernières heures (indiquant que vous êtes resté assis tout le temps)
- **Capteur de rythme cardiaque** : Le rythme cardiaque est passé d'un normal de 72 bpm à 85 bpm (possiblement un léger inconfort dû à la position assise prolongée)
- **Capteur de température cutanée** : Température du poignet légèrement élevée

Le module Capteur agrège ces données et les transmet à la Couche de Cognition d'iFay. Après analyse globale, iFay vous rappelle doucement : « Tu es assis depuis 3 heures et ton rythme cardiaque est un peu élevé. Et si tu te levais pour t'étirer ? Le temps que je te prépare une tasse de thé suffit pour une petite marche. »

Dans ce processus, le module Capteur n'a pas « compris » ce que les données signifiaient — il a juste fidèlement collecté et transmis. La compréhension et le jugement sont le travail de la Couche de Cognition. Mais sans les données brutes fournies par le Capteur, la Couche de Cognition n'aurait rien sur quoi travailler.

### Scénario 2 : Vol autonome de drone

iFay est déployé sur un drone pour une mission de photographie aérienne. Le drone a de multiples capteurs :

- **GPS** : Fournit des informations de position et d'altitude
- **IMU (Unité de mesure inertielle)** : Fournit accélération et vitesse angulaire pour le contrôle d'attitude
- **Caméra** : Fournit des informations visuelles (gérées par le Traceur première personne)
- **Ultrasonique/LiDAR** : Fournit des informations de distance aux obstacles
- **Baromètre** : Fournit des données d'altitude précises
- **Capteur de vitesse du vent** : Fournit des informations sur la force du vent actuelle

Le module Capteur unifie tous ces flux de données. Pendant un vol stable, la sensibilité de l'IMU peut être appropriément réduite ; mais quand des changements soudains de vitesse du vent sont détectés, le module Capteur augmente immédiatement la sensibilité de l'IMU et du baromètre, permettant à iFay de contrôler plus précisément l'attitude du drone et d'éviter la perte de contrôle.

## Pour les développeurs

Le module Capteur appartient à la **Phase 2 (Prise de contrôle directe du client)** comme module fondamental, dépendant des protocoles CAP et DTP.

- **ID d'exigence** : Exigence 7 (Module Capteur)
- **Spécification d'interface** : Interface `SensorModule` avec quatre méthodes fondamentales : `registerSource()`, `adjustSensitivity()`, `getDataStream()` et `getActiveStatus()`
- **Protocoles associés** : CAP (Protocole d'autorité de contrôle) pour prendre le contrôle du matériel capteur ; DTP (Protocole de tunnel de données) pour la transmission bidirectionnelle de données
- **Modules associés** : Hub pilotes périphériques (`DeviceDriverHub`) gère les interfaces matérielles réelles ; Tas de données personnelles (`PersonalDataHeap`) stocke les données des capteurs
- **Tests de conformité** : iFACTS L1 vérifie la capacité d'ajustement de sensibilité ; L2 vérifie l'intégration d'interface avec le Hub pilotes périphériques et le Tas de données personnelles
- **Points de conception** : Le module Capteur sert uniquement de régulateur de sensibilité, ne gérant pas directement les interfaces matérielles ; supporte l'ajustement dynamique de sensibilité ; les nouveaux types de capteurs sont intégrés via le Hub pilotes périphériques


---

## 9.3 Conscience de soi

## Définition en une ligne

La Conscience de soi est l'**intelligence émotionnelle** d'iFay — elle ne regarde pas l'écran ni ne perçoit l'environnement. Au lieu de cela, elle **regarde vers l'intérieur, vers vous**, inférant vos sentiments et intentions à travers vos réactions, comme un vieil ami qui excelle à lire les gens.

## Pourquoi c'est nécessaire

Le sous-système de Perception d'iFay a trois modules, chacun regardant dans une direction différente :
- **Traceur première personne** regarde vers l'extérieur — voit ce qui est à l'écran
- **Capteur** perçoit l'environnement — ressent la température, la localisation, le mouvement
- **Conscience de soi** regarde vers l'intérieur — vous observe **vous**

Pourquoi regarder vers l'intérieur ?

Imaginez deux types d'assistants. Le premier fait tout ce que vous dites, comme un distributeur automatique — vous appuyez sur un bouton, il distribue une boisson. Le second remarque que vous parlez plus vite que d'habitude aujourd'hui, que votre front est légèrement plissé, et que vous n'avez mangé que la moitié de votre déjeuner, alors il reporte proactivement votre réunion de l'après-midi d'une demi-heure, vous verse un verre d'eau chaude et met votre musique légère préférée.

Le premier est iFay sans Conscience de soi — un robot qui suit les commandes.
Le second est iFay avec Conscience de soi — un partenaire qui **vous comprend**.

La Conscience de soi fait passer iFay de « vous dites, je fais » à « vous ne dites pas, je comprends quand même ». Elle observe vos micro-expressions, les changements dans vos habitudes d'opération et vos fluctuations émotionnelles, puis infère ce dont vous pourriez avoir besoin — avant même que vous ne le réalisiez vous-même.

C'est la différence entre un distributeur automatique et un ami attentionné.

## Sa position dans l'architecture

```
Architecture à quatre couches d'iFay
├── Couche Sociale
├── Couche d'Interaction          ← La Conscience de soi est ici
│   ├── Perception (Sens)
│   │   ├── Traceur première personne   ← Regarde vers l'extérieur, voit l'écran
│   │   ├── Capteur                     ← Perçoit l'environnement
│   │   └── 👉 Conscience de soi        ← Regarde vers l'intérieur, vous lit
│   └── Action
│       ├── Opération simulée
│       ├── Invocation de compétences
│       └── Comportement autonome  ← Les inférences de la Conscience de soi déclenchent le Comportement autonome
├── Couche de Cognition
│   └── Pensée
│       └── Conscience alignée ← La Conscience de soi ajuste la Conscience alignée en temps réel
└── Couche Ego
```

La Conscience de soi se situe dans le **sous-système de Perception de la Couche d'Interaction**, le plus « introverti » des trois modules de perception. Elle ne se soucie pas de ce qui est affiché à l'écran (c'est le travail du Traceur première personne), ni de la température ambiante (c'est le travail du Capteur). Elle ne se soucie que d'une chose : **Comment allez-vous en ce moment ? Que voulez-vous ?**

Ce qui rend la Conscience de soi spéciale est que sa sortie circule dans deux directions simultanément :
1. **Vers le bas** vers le **module de Comportement autonome** — déclenchant les actions proactives d'iFay
2. **Vers l'intérieur** vers le **module de Conscience alignée** — mettant à jour la compréhension d'iFay de vous en temps réel

## Comment ça fonctionne

La Conscience de soi fonctionne comme un vieil ami qui vous connaît depuis des années vous lisant :

**1. Observer vos réactions**

La Conscience de soi surveille continuellement divers signaux pendant vos interactions avec iFay :
- Changements dans votre vitesse d'opération (soudainement plus rapide peut signifier urgence, plus lent peut signifier hésitation)
- Votre comportement de navigation (s'attarder sur un passage peut signifier intérêt, défiler rapidement peut signifier désintérêt)
- Vos expressions et votre ton (si l'appareil a une caméra et un microphone)
- Vos schémas d'acceptation ou de rejet des suggestions d'iFay
- Si vos habitudes quotidiennes montrent des anomalies

**2. Inférer votre intention**

Basée sur les signaux observés, la Conscience de soi infère votre état actuel et vos intentions possibles. Ce n'est pas de simples règles « si A alors B », mais une inférence intelligente combinant de multiples signaux.

Par exemple : vous lisez un article sur l'apprentissage automatique, la vitesse de défilement ralentit notablement à une certaine section, et vous revenez en arrière deux fois — la Conscience de soi infère que vous êtes particulièrement intéressé par ce paragraphe et pourriez vouloir approfondir.

**3. Transmettre les résultats d'inférence**

Quand la Conscience de soi infère une nouvelle intention, elle fait deux choses :

- **Dit au module de Comportement autonome** : « Le Human Prime pourrait être intéressé par ce sujet — devrions-nous proactivement chercher des matériaux connexes ? » Le module de Comportement autonome pourrait alors automatiquement rechercher des articles connexes.
- **Dit au module de Conscience alignée** : « Le Human Prime montre de l'intérêt pour le domaine de l'apprentissage automatique — mettre à jour le profil du Human Prime. » Le module de Conscience alignée ajoute alors « intéressé par l'apprentissage automatique » à votre profil personnel, rendant le comportement futur d'iFay plus aligné avec vous.

**4. Ajustement en temps réel**

La Conscience de soi n'est pas un jugement unique — elle fonctionne en continu. Elle révise constamment ses inférences basées sur vos dernières réactions. Si elle infère incorrectement (ex. vous rejetez une suggestion qu'elle a fournie basée sur une inférence), elle apprend et s'ajuste.

## Relations avec les autres modules

| Module associé | Relation | Analogie corporelle |
|----------------|----------|---------------------|
| **Comportement autonome** | Les inférences de la Conscience de soi déclenchent des actions proactives | QE → attention proactive (« Tu as l'air fatigué, laisse-moi… ») |
| **Conscience alignée** | La Conscience de soi ajuste le profil du Human Prime dans la Conscience alignée en temps réel | La compréhension de vous s'approfondit avec le temps passé ensemble |
| **Couche de Cognition** | Les résultats d'inférence sont transmis à la Couche de Cognition pour une compréhension et une prise de décision plus profondes | Intuition → pensée rationnelle |
| **Traceur première personne** | Le Traceur regarde vers l'extérieur, la Conscience de soi regarde vers l'intérieur — complémentaires | Les yeux voient le monde vs. le cœur lit les gens |
| **Capteur** | Les données environnementales du Capteur peuvent assister les inférences de la Conscience de soi | Les sensations corporelles assistent le jugement émotionnel (ex. rythme cardiaque accéléré → possiblement nerveux) |

## Histoires de scénarios

### Scénario 1 : Vous lisez un article, iFay trouve proactivement des matériaux

Un dimanche après-midi, vous parcourez un long article sur « la conception de bâtiments durables » sur votre tablette. La Conscience de soi remarque :

- Vous défilez rapidement la première moitié (pas très intéressé)
- Mais à la section « technologie d'économie d'énergie des maisons passives », votre vitesse de défilement ralentit notablement
- Vous revenez en arrière une fois pour relire un graphique
- Vous vous attardez sur cette section pendant près de deux minutes

La Conscience de soi infère : vous êtes particulièrement intéressé par le sujet de la « technologie d'économie d'énergie des maisons passives ».

Elle transmet cette inférence au module de Comportement autonome. Le module de Comportement autonome recherche proactivement plusieurs articles approfondis et un tutoriel vidéo YouTube, les plaçant discrètement dans votre liste de lecture. Quand vous finissez l'article, iFay suggère doucement : « J'ai trouvé des matériaux approfondis sur les maisons passives. Tu veux y jeter un œil ? »

Vous n'avez jamais dit « trouve-moi des matériaux », mais iFay les avait déjà préparés.

### Scénario 2 : Un assistant attentionné pendant une visioconférence

Vous êtes en visioconférence. La Conscience de soi capture les changements de micro-expressions de votre visage via la caméra :

- Premières 20 minutes : expression détendue, hochements de tête occasionnels
- Quand un collègue commence à discuter des coupes budgétaires du projet, votre front se plisse légèrement et les coins de votre bouche s'abaissent légèrement
- Votre posture passe de détendue à penchée en avant, les doigts tapotant inconsciemment le bureau

La Conscience de soi infère : vous êtes mal à l'aise avec le sujet de discussion actuel — possiblement en désaccord avec la proposition de coupe budgétaire, ou le sujet vous cause du stress.

Elle transmet cette inférence au module de Comportement autonome. Le module de Comportement autonome prépare discrètement deux choses :
1. Un rapport d'analyse budgétaire de projet que vous avez précédemment créé (au cas où vous auriez besoin de données pour contre-argumenter)
2. Un brouillon de message d'excuse poli (« Désolé, j'ai un appel urgent à prendre »), au cas où vous voudriez temporairement partir

Tout cela est préparé discrètement sans vous déranger. Ce n'est que quand vous en aurez besoin qu'iFay vous les présentera.

## Pour les développeurs

Le module de Conscience de soi appartient à la **Phase 4 (iFay + coFay Personnification complète)** comme module fondamental — la clé pour qu'iFay évolue d'« outil » à « partenaire ».

- **ID d'exigence** : Exigence 13 (Conscience de soi)
- **Spécification d'interface** : Interface `SelfAwareness` avec trois méthodes fondamentales : `inferIntent()` (inférer l'intention), `monitorHostReaction()` (surveiller les réactions du Human Prime), et `adjustAlignment()` (ajuster la Conscience alignée)
- **Modules associés** : Comportement autonome (`SelfDrivenBehavior`) reçoit les résultats d'inférence et déclenche des actions proactives ; Conscience alignée (`AlignedConsciousness`) reçoit les résultats d'inférence et met à jour le profil du Human Prime
- **Protocoles associés** : Pas de dépendance directe de protocole, mais peut exploiter le module Capteur (via CAP/DTP) pour des données auxiliaires (ex. rythme cardiaque, expressions faciales)
- **Tests de conformité** : iFACTS L1 vérifie la capacité d'inférence d'intention ; L2 vérifie les interfaces avec le Comportement autonome et la Conscience alignée ; L4 vérifie la précision d'inférence et la protection de la vie privée
- **Points de conception** : Les résultats d'inférence doivent être transmis simultanément au module de Comportement autonome et à la Couche de Cognition ; supporte l'ajustement en temps réel de la Conscience alignée ; doit apprendre et corriger à partir du retour du Human Prime quand les inférences sont erronées
