<img width="100%" alt="iFay Title Banner" src="./illustration/ifay-title-banner.png"/>

# 3. Principes de conception

iFay (Individual Fay) est un avatar numérique IA profondément lié à une personne physique. Ce n'est pas un outil, mais une extension de votre personnalité — fusionnant votre caractère, vos souvenirs, vos préférences et vos capacités numériques, prenant en charge votre travail mécanique, répétitif et dangereux, et amplifiant votre valeur sociale. iFay adopte le framework CPE+M (Contexte, Protocole, Environnement, Mérite), constitué d'une architecture à quatre couches — Couche Sociale, Couche d'Interaction, Couche de Cognition et Couche Ego — couvrant cinq phases évolutives allant de la simulation des opérations humaines à la redéfinition de la structure du travail et de la distribution de la valeur.

---

## Principes de conception

La conception d'iFay suit cinq principes fondamentaux qui imprègnent l'architecture et l'implémentation de l'ensemble du système :

| # | Principe | Résumé en une ligne |
|---|----------|---------------------|
| 1 | **Adoption progressive favorable à l'écosystème** | Les partenaires de l'écosystème n'ont pas besoin d'implémenter un iFay complet pour livrer un produit — un iFay qui ne contrôle que des drones n'a besoin de satisfaire que le sous-ensemble requis de composants pour être mis en service. |
| 2 | **Assemblage minimal déclaratif** | Définir les composants, protocoles et configurations requis via un seul fichier de déclaration FayManifest, assembler iFay comme écrire un package.json. |
| 3 | **Composition flexible** | Les composants sont faiblement couplés et mixables ; les implémentations de différents fournisseurs peuvent être librement combinées tant qu'elles respectent les contrats d'interface. |
| 4 | **Personnifié, pas instrumentalisé** | iFay n'est pas un Agent — chaque iFay a une personnalité, une mémoire et des préférences uniques, une Instanciation du Human Prime, capable de perpétuer la personnalité du Prime même après son décès. |
| 5 | **Intuition guidée par les scénarios** | Chaque module fonctionnel peut être expliqué avec un scénario de vie concret, permettant aux lecteurs d'imaginer intuitivement la vie avec iFay. |

---

## Table des matières

1. [Définition et concept](./2-Définition-et-concept)

    Fournit la définition et l'aperçu structurel d'iFay, analyse les différences fondamentales entre iFay et le concept actuel d'Agent, et les principes derrière ses caractéristiques opérationnelles.

---

2. [Scénarios d'application iFay](./5-Scénarios-application-iFay)

    Le processus complet d'utilisation réelle d'iFay à partir de zéro : comment injecter votre personnalité, ajouter des compétences à iFay, interagir avec iFay, comment iFay socialise, et une vue panoramique de la sécurité et de l'écosystème industriel.

    - [Injection des traits du Prime dans iFay](./5-Scénarios-application-iFay#injection-des-traits-du-prime-dans-ifay)
    - [Compléter iFay avec des capacités externes](./5-Scénarios-application-iFay#compléter-ifay-avec-des-capacités-externes)
    - [Méthodes d'interaction Humain-iFay](./5-Scénarios-application-iFay#méthodes-dinteraction-humain-ifay)
        - [Comment activer iFay](./5-Scénarios-application-iFay#comment-activer-ifay)
        - [Conscience autonome d'iFay](./5-Scénarios-application-iFay#conscience-autonome-difay)
        - [Comment éteindre iFay](./5-Scénarios-application-iFay#comment-éteindre-ifay)
    - [Fonctionnalités sociales d'iFay](./5-Scénarios-application-iFay#fonctionnalités-sociales-difay)
    - [Sécurité](./5-Scénarios-application-iFay#sécurité)
    - [Façonner l'écosystème industriel de l'IA](./5-Scénarios-application-iFay#façonner-lécosystème-industriel-de-lia)

---

3. [iFay est une réplique de la personnalité humaine](./6-iFay-est-réplique-de-la-personnalité-humaine)

    iFay est attaché à une personne physique spécifique, donc les traits du Human Prime doivent être injectés dans iFay selon trois dimensions : la personnalité façonne le Modèle Ego, les données alimentent le Tas de données personnelles, et les permissions établissent la délégation d'identifiants.

    - [Personnalité du Prime](./6-iFay-est-réplique-de-la-personnalité-humaine#personnalité-du-prime)
    - [Données du Prime](./6-iFay-est-réplique-de-la-personnalité-humaine#données-du-prime)
    - [Permissions du Prime](./6-iFay-est-réplique-de-la-personnalité-humaine#permissions-du-prime)

---

4. [Profil iFay](./7-Profil-iFay)

    Le Profil iFay est la « carte d'identité » complète d'iFay — un tableau d'attributs à six dimensions sémantiquement interprétable utilisé pour que les humains identifient iFay, que les systèmes identifient iFay, et que les Fays se reconnaissent mutuellement.

    - [Identité iFay](./7-Profil-iFay#identité-ifay)
    - [Modèle Ego](./7-Profil-iFay#modèle-ego)
    - [Pensée Faying](./7-Profil-iFay#pensée-faying)
        1. [Contenu](./7-Profil-iFay#contenu)
        2. [Données](./7-Profil-iFay#données)
        3. [Base de connaissances](./7-Profil-iFay#base-de-connaissances)
        4. [Flux d'informations](./7-Profil-iFay#flux-dinformations)
    - [Compétences Faying](./7-Profil-iFay#compétences-faying)
        1. [API](./7-Profil-iFay#api)
        2. [Workflow](./7-Profil-iFay#workflow)
        3. [Bot](./7-Profil-iFay#bot)
        4. [Agent](./7-Profil-iFay#agent)
        5. [APP](./7-Profil-iFay#app)
        6. [Microservice](./7-Profil-iFay#microservice)
    - [Matériel Faying](./7-Profil-iFay#matériel-faying)
        1. [Appareil](./7-Profil-iFay#appareil)
        2. [Stockage](./7-Profil-iFay#stockage)
        3. [Calcul](./7-Profil-iFay#calcul)
    - [Permissions Faying](./7-Profil-iFay#permissions-faying)
        1. [SSO](./7-Profil-iFay#sso)
        2. [OAuth](./7-Profil-iFay#oauth)
        3. [Empreinte](./7-Profil-iFay#empreinte)

---

5. [Assemblage déclaratif FayManifest](./13-FayManifest)

    FayManifest est le « package.json » d'iFay — les développeurs n'ont qu'à lister les composants, protocoles, modes de contrôle et configurations de pilotes requis dans un seul fichier de déclaration JSON, et l'environnement d'exécution FayGer résout automatiquement les dépendances et assemble l'instance iFay. Vous pouvez construire un iFay dédié à partir de zéro en un week-end.

---

6. [Vérification de conformité iFACTS](./14-iFACTS)

    iFACTS (iFay Architecture Conformance Test Suite) est une suite de tests de conformité standardisée couvrant les points clés de la spécification incluant les interactions de protocoles, les interfaces de modules et les comportements de sécurité. Les implémentations des fournisseurs doivent passer les tests iFACTS pour revendiquer « iFay Ready », avec des tests divisés en quatre niveaux : L1 Conformité de composant unique, L2 Conformité d'interface, L3 Conformité d'intégration, L4 Conformité comportementale.

---

7. [Tutelle et continuité de la personnalité](./15-Tutelle-et-continuité-personnalité)

    iFay est le vaisseau numérique de la personnalité. Quand le Human Prime ne peut plus gérer iFay, un Tuteur peut prendre en charge les droits de gestion par des phrases mnémoniques ou une authentification d'identité pré-spécifiée ; après le décès du Human Prime, iFay peut continuer à exister comme identité indépendante dans un sandbox de Cimetière numérique — la personnalité perdure.

---

8. Études de cas

    Nous fournirons une série d'études de cas démontrant comment iFay est créé et comment les systèmes s'interfacent avec iFay.
