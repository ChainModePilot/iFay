# 13. Assemblage déclaratif FayManifest

FayManifest est le « package.json » d'iFay. Les développeurs listent simplement les composants, protocoles, modes de contrôle et configurations de pilotes requis dans un seul fichier de déclaration JSON, et l'environnement d'exécution FayGer résout automatiquement les dépendances et assemble l'instance iFay. Vous n'avez pas besoin de comprendre toute la complexité du système iFay — déclarez ce dont vous avez besoin, et le système complète le reste.

---

## Pourquoi FayManifest est nécessaire

Un des principes de conception d'iFay est **l'assemblage minimal déclaratif + l'adoption progressive**.

**Problème** : Construire un iFay complet à partir de zéro est complexe — 12 modules fondamentaux, 6 protocoles, systèmes de permissions, conformité sécuritaire, synchronisation multi-terminaux… Si chaque développeur devait comprendre et implémenter tout cela, l'écosystème iFay ne décollerait jamais.

**Solution** : Les développeurs n'ont qu'à déclarer le sous-ensemble de composants requis par leur métier, et le système complète automatiquement les dépendances d'infrastructure nécessaires.

---

## Structure du fichier FayManifest

FayManifest utilise le format JSON et contient les champs suivants :

| Champ | Type | Requis | Description |
|-------|------|--------|-------------|
| `name` | string | ✅ | Nom de l'implémentation iFay |
| `version` | string | ✅ | Numéro de version |
| `description` | string | ✅ | Description fonctionnelle |
| `vendor` | string | ✅ | Nom du développeur/fournisseur |
| `modules` | array | ✅ | Liste des modules requis ; chaque module peut spécifier des contraintes de version (`version`), une implémentation fournisseur (`provider`) et une configuration (`config`) |
| `protocols` | array | ✅ | Liste des protocoles requis ; chaque protocole peut spécifier version et configuration |
| `controlMode` | string | ✅ | Mode de contrôle : `command` / `ego` / `autonomous` |
| `drivers` | array | ❌ | Configurations de pilotes spécifiant nom, type, identifiant de package et configuration |
| `ego` | object | ❌ | Configuration du Modèle Ego spécifiant source du modèle, tags de scénario applicables et paramètres de contrainte |
| `permissions` | object | ❌ | Configuration des permissions déclarant permissions inhérentes, persistantes et méthodes d'authentification supportées |

---

## Modes de contrôle

Le champ `controlMode` dans FayManifest détermine l'approche de pilotage comportemental d'iFay — choisissez l'un des trois :

| Mode | Nom | Description |
|------|-----|-------------|
| `command` | **Contrôle par commande** | Le Human Prime pilote explicitement chaque action. iFay n'agira pas de manière autonome ; chaque opération nécessite la commande explicite du Human Prime. Adapté aux scénarios à haut risque ou aux phases initiales de construction de confiance. |
| `ego` | **Contrôle Ego** | Le Modèle Ego prend des décisions autonomes dans des limites contraintes. iFay peut juger et agir de manière autonome basé sur la personnalité et les préférences du Human Prime, mais les limites comportementales sont contraintes par le Modèle Ego. Adapté aux scénarios d'assistant quotidien. |
| `autonomous` | **Contrôle autonome** | Comportement entièrement autonome. iFay opère de manière autonome basé sur la Conscience de soi, le Comportement autonome et les Compétences internes, formant une boucle continue « action → retour → ré-action ». Adapté aux scénarios de collaboration à long terme et haute confiance. |

---

## Complétion automatique des dépendances

La conception fondamentale de FayManifest : les développeurs déclarent les composants métier, le système complète automatiquement l'infrastructure.

L'infrastructure suivante est requise dans toutes les implémentations iFay — que les développeurs les déclarent explicitement ou non, le système les ajoute automatiquement :

- **FayID** (Identité)
- **Environnement d'exécution FayGer** (Conteneur d'exécution)
- **Profil iFay** (Modèle de données unifié)
- **Système de permissions** (Gestion des permissions)
- **Conformité sécurité et éthique** (Contraintes comportementales)
- **Synchronisation multi-terminaux** (Synchronisation d'état)
- **Protocole Faying** (Appariement sécurisé, requis pour tout iFay)

De plus, si le Manifest déclare une configuration `ego`, le système ajoute automatiquement le module `ego_model`.

---

## Exemple complet : iFay de contrôle de drone

Voici une déclaration FayManifest pour un iFay de contrôle de drone :

```json
{
  "name": "drone-controller-ifay",
  "version": "1.0.0",
  "description": "Implémentation iFay pour le contrôle de drone",
  "vendor": "DroneAI Corp",

  "modules": [
    { "id": "device_driver_hub", "version": "^1.0.0" },
    { "id": "sensor", "config": { "types": ["gps", "imu", "camera", "lidar"] } },
    { "id": "invoke_skill", "version": "^1.0.0" },
    { "id": "registered_skill", "config": { "preload": ["flight_control", "obstacle_avoidance"] } }
  ],

  "protocols": [
    { "id": "cap_protocol", "config": { "targets": ["flight_controller", "gimbal", "camera"] } },
    { "id": "dtp_protocol", "config": { "bandwidth": "high", "realtime": true } }
  ],

  "controlMode": "ego",

  "drivers": [
    {
      "name": "DJI Flight Controller",
      "type": "device",
      "driverPackage": "@drone-drivers/dji-fc",
      "config": { "model": "A3", "firmwareVersion": "^3.0.0" }
    },
    {
      "name": "Gimbal Controller",
      "type": "device",
      "driverPackage": "@drone-drivers/gimbal-generic"
    }
  ],

  "ego": {
    "modelSource": "@ego-models/drone-pilot-v1",
    "scenarioTags": ["aerial_photography", "inspection", "mapping"],
    "constraints": {
      "skillBoundaries": {
        "allowed": ["flight", "camera", "navigation"],
        "restricted": ["financial", "social"]
      }
    }
  },

  "permissions": {
    "inherent": ["device_control", "sensor_read"],
    "persistent": ["flight_plan_execute"],
    "authMethods": ["device_fingerprint"]
  }
}
```

Le Manifest ci-dessus ne déclare que 4 modules et 2 protocoles, mais le système complète automatiquement l'infrastructure suivante : FayID, Environnement d'exécution FayGer, Profil iFay, Système de permissions, Conformité sécurité et éthique, Synchronisation multi-terminaux, Modèle Ego et Protocole Faying.

---

## Intégration avec iFACTS

iFACTS (iFay Architecture Conformance Test Suite) détermine quels tests de conformité une implémentation doit passer basé sur le contenu déclaré du FayManifest.

Après résolution des dépendances, le système détermine la phase iFay (Resolved Stage) correspondant au Manifest. L'exemple de contrôle de drone ci-dessus déclare Hub pilotes périphériques, Capteur, protocoles CAP et DTP, correspondant à la Phase 2 (Prise de contrôle directe du client), et doit donc passer tous les tests de conformité pour les Phases 1 et 2.

---

## Configuration minimale de composants par phase

Chaque phase a son Ensemble Minimal de Composants :

| Phase | Nouveaux modules | Nouveaux protocoles |
|-------|-----------------|---------------------|
| **Phase 1** : Simulation des opérations humaines | FayID, Gestion des identifiants, Traceur première personne, Opération simulée, Modèle Ego | Protocole Faying, Protocole de conversation interactive |
| **Phase 2** : Prise de contrôle directe du client | Capteur, Hub pilotes périphériques, Compétences enregistrées, Invocation de compétences, Tas de données personnelles | Protocole CAP, Protocole DTP |
| **Phase 3** : Interface vers le monde virtuel | Connaissances externes | Protocole SSP |
| **Phase 4** : Personnification complète | Conscience de soi, Comportement autonome, Compétences internes, Conscience alignée | Protocole de Télépathie |
| **Phase 5** : Distribution de la valeur | GMChain, MeriToken | — |

> **Infrastructure transversale** (requise pour toutes les phases) : Environnement d'exécution FayGer, Profil iFay, Système de permissions, Conformité sécurité et éthique, Synchronisation multi-terminaux. Ces composants n'appartiennent à aucune phase spécifique mais sont requis dans chaque phase.

---

### Documents associés

- [iFACTS](./14-iFACTS) — Tests de conformité
- [Feuille de route](./4-Feuille-de-route) — Configuration par phase
- [Hub pilotes périphériques](./12.1-Hub-pilotes-périphériques) — Configuration des pilotes
