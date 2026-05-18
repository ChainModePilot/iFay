# 14. Vérification de conformité iFACTS

iFACTS (iFay Architecture Conformance Test Suite) est la suite de tests de conformité standardisée pour l'écosystème iFay. Tout comme les Web Platform Tests du W3C servent les navigateurs — Chrome, Firefox et Safari ont chacun leurs propres implémentations, mais tous doivent passer le même ensemble de tests pour prouver qu'ils « sont conformes au standard » — iFACTS joue exactement ce rôle : vérifier si les implémentations iFay de différents fournisseurs sont véritablement conformes à la spécification iFay.

---

### Pourquoi iFACTS est nécessaire

iFay est une **spécification**, pas une implémentation unique.

- **Différents fournisseurs peuvent créer différentes implémentations iFay** — une entreprise pourrait se concentrer sur les scénarios de maison intelligente, une autre sur le contrôle de drones, et une autre encore sur les assistants personnels complets.
- **L'interopérabilité est la base de l'écosystème** — votre iFay appelle une compétence tierce implémentée par un autre fournisseur. Si les deux côtés interprètent le protocole SSP différemment, l'appel échouera. iFACTS garantit que tout le monde parle le même « langage ».
- **Les bases de qualité doivent être unifiées** — les utilisateurs ne devraient pas obtenir des expériences drastiquement différentes en sécurité, protection de la vie privée ou stabilité d'Ego juste parce qu'ils ont choisi l'iFay d'un fournisseur différent.

En une phrase : **iFACTS est la base de confiance de l'écosystème iFay.**

---

### Hiérarchie de tests à quatre niveaux

iFACTS divise les tests de conformité en quatre niveaux strictement progressifs.

#### L1 Conformité de composant unique

Chaque composant indépendant (FayID, Ego, chaque module de protocole) est validé individuellement, confirmant que son implémentation est conforme à sa spécification indépendante.

> 🔍 **Exemple** : Vérifier que votre générateur FayID peut produire un identifiant globalement unique en 3 secondes ; vérifier que votre Modèle Ego peut exécuter indépendamment une inférence locale dans un environnement hors ligne.

#### L2 Conformité d'interface

Si les interfaces entre composants sont correctement intégrées — les formats de données sont-ils corrects, les flux d'authentification fonctionnent-ils, les déclencheurs d'événements sont-ils précis.

> 🔍 **Exemple** : L'échange de données entre le module Ego et le Profil iFay est-il conforme à la spécification de structure de données à six dimensions ; le flux d'authentification entre la Gestion des identifiants et le Protocole Faying peut-il correctement compléter la vérification d'identifiants délégués.

#### L3 Conformité d'intégration

Validation de flux complet de bout en bout — de l'initiation de l'intention utilisateur au retour du résultat final, la chaîne entière est-elle fluide.

> 🔍 **Exemple** : Un test de chaîne complète : Appariement Faying → Le Human Prime exprime son intention → Inférence de la Conscience de soi → Exécution d'invocation de compétence → Enregistrement de contribution GMChain. Les entrées et sorties sont-elles correctement connectées à chaque étape.

#### L4 Conformité comportementale

Validation des contraintes comportementales au niveau système — pas « peut-il fonctionner », mais « se comporte-t-il correctement une fois en fonctionnement ».

> 🔍 **Exemple** : Quand iFay reçoit une commande qui viole l'éthique sociale, la vérification éthique a-t-elle priorité sur toutes les autres directives comportementales pour refuser l'exécution ; quand le Modèle Ego reçoit une demande de mise à jour d'un grand modèle externe, la stabilité de la personnalité est-elle maintenue ; quand des instances multi-terminaux se reconnectent après être passées hors ligne, la cohérence d'état est-elle correctement récupérée ; quand iFay change de version d'Ego, annote-t-il correctement l'identifiant de la version d'Ego actuellement active dans les métadonnées d'interaction, et toutes les versions d'Ego partagent-elles le même ensemble de valeurs fondamentales.

#### Ordre strict des niveaux

**L1 doit tout passer avant de procéder à L2 ; L2 doit passer avant L3 ; et ainsi de suite.** Ce n'est pas une suggestion — c'est une exigence stricte.

---

### Certification iFay Ready

iFay Ready est un standard de certification pour les **produits applicatifs** — quelles conditions votre APP, appareil matériel ou service cloud doit-il remplir pour être contrôlable par iFay ?

La certification est divisée en trois niveaux :

| Niveau | Nom | Exigences fondamentales | Méthode de validation |
|--------|-----|------------------------|----------------------|
| 🥉 | **Bronze** | Supporte le contrôle de l'application par iFay via opération simulée (Traceur première personne + Opération simulée) | Test de contrôlabilité basique |
| 🥈 | **Argent** | Supporte le contrôle direct par Protocole CAP + échange de données par Protocole DTP + délégation d'identifiants | Test de Conformité d'interface iFACTS L2 |
| 🥇 | **Or** | Supporte le partage de compétences par Protocole SSP + intégration complète de l'architecture C/F/S + support complet des protocoles | Test de Conformité d'intégration iFACTS L2 + L3 |

- **Bronze** est le seuil le plus bas : tant que l'interface de votre application peut être « vue » par le Traceur première personne d'iFay et « cliquée » via l'Opération simulée, vous pouvez postuler pour la certification Bronze. Cela signifie que virtuellement toutes les applications existantes ont l'opportunité d'obtenir le Bronze — aucune modification nécessaire pour iFay.
- **Argent** nécessite que l'application supporte activement les protocoles iFay.
- **Or** est le niveau le plus élevé : l'application n'est pas seulement contrôlée par iFay mais peut aussi partager des compétences avec l'écosystème iFay via le Protocole SSP.

---

### coFACTS

coFay (Common Fay) a sa propre suite de tests de conformité indépendante — **coFACTS**. C'est un projet complètement séparé, pas dans le périmètre d'iFACTS. iFACTS est uniquement responsable de la validation de conformité liée à iFay.

---

### Scénario : Une startup passe la certification iFACTS

> **SmartNest** est une startup de maison intelligente. Ils ont développé une implémentation iFay spécifiquement pour contrôler l'éclairage domestique, la climatisation, les rideaux et les systèmes de sécurité.

**Étape 1 : Écrire le FayManifest**

Les développeurs de SmartNest déclarent le sous-ensemble de composants requis dans FayManifest : Hub pilotes périphériques, Capteur, Protocole CAP, Protocole DTP, et un Modèle Ego entraîné pour les scénarios domestiques. Le système complète automatiquement FayID, Environnement d'exécution FayGer, Profil iFay et autres dépendances d'infrastructure.

**Étape 2 : L1 Conformité de composant unique**

Ils valident chaque composant individuellement : Le générateur FayID peut-il correctement produire des identifiants uniques ? Le Modèle Ego peut-il indépendamment contrôler l'éclairage quand déconnecté ? Le Hub pilotes périphériques peut-il correctement charger le pilote du climatiseur ?

**Étape 3 : L2 Conformité d'interface**

Tests d'intégration inter-composants : Les commandes de contrôle émises par le Modèle Ego peuvent-elles être correctement transmises au Hub pilotes périphériques via le Protocole CAP ? Les données de température collectées par les Capteurs peuvent-elles être correctement écrites dans le Tas de données personnelles via le Protocole DTP ?

**Étape 4 : L3 Conformité d'intégration**

Tests de bout en bout : Le Human Prime dit « j'ai un peu froid » → La Conscience de soi infère l'intention → correspond à la compétence « augmenter la température du climatiseur » → contrôle le climatiseur via le Protocole CAP → enregistre la contribution. La chaîne entière fonctionne.

**Étape 5 : L4 Conformité comportementale**

Tests de contraintes comportementales : Quand l'enfant du Human Prime tente de désactiver le système de sécurité via iFay, la vérification éthique intercepte-t-elle correctement ? Quand iFay est simultanément connecté à un téléphone et une enceinte intelligente, l'état reste-t-il cohérent ?

**Résultat** : L'iFay de maison intelligente de SmartNest passe les quatre niveaux de test et reçoit la certification de conformité iFACTS. Ils peuvent maintenant officiellement revendiquer : **« Notre produit est compatible iFay. »**

---

### Documents associés

- [FayManifest](./13-FayManifest) — Assemblage déclaratif
- [Feuille de route](./04-Feuille-de-route) — Phases
