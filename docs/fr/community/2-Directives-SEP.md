# 2. Directives SEP

## Qu'est-ce qu'un SEP

Un SEP (Specification Enhancement Proposal) est le processus formel de proposition pour les modifications de la spécification iFay. Toute modification substantielle de la spécification iFay — qu'il s'agisse de l'ajout d'un nouveau module, de la modification du comportement d'un protocole ou de l'ajustement du modèle de données iFay Profile — doit passer par le processus SEP.

## Pourquoi les SEPs sont nécessaires

iFay est un écosystème de standards ouverts avec des implémentations multi-fournisseurs, et chaque modification de la spécification peut potentiellement affecter tous les implémenteurs. Le processus SEP garantit que l'évolution de la spécification est ordonnée, transparente et traçable, donnant à toutes les parties prenantes la possibilité de participer à la discussion et à la révision.

## Cycle de vie du SEP

Un SEP passe par les étapes suivantes, de la proposition à l'implémentation finale :

### 1. Draft (Brouillon)

Le proposant crée un Issue SEP sur GitHub en utilisant le modèle standard, décrivant la motivation, la solution proposée et l'impact. Un SEP à l'étape Draft peut être incomplet, mais doit contenir suffisamment d'informations pour que la communauté comprenne l'intention de la proposition.

### 2. Discussion

Le SEP entre dans une période de discussion publique d'au moins **14 jours**. Pendant cette période :

- Les membres de la communauté et les groupes de travail concernés discutent de la proposition
- Le proposant révise et affine la proposition en fonction des retours
- Les mainteneurs des sous-projets concernés évaluent l'impact de la proposition sur leurs domaines respectifs

### 3. Review (Révision)

Après la fin de la période de discussion, les Core Maintainers procèdent à une révision formelle du SEP. Pendant la révision, le proposant peut être invité à apporter des révisions ou des ajouts supplémentaires, tels que :

- L'ajout d'une analyse de compatibilité ascendante
- La réalisation d'une évaluation de l'impact sur les tests iFACTS
- La fourniture d'une analyse comparative des approches alternatives

### 4. Accepted / Rejected (Accepté / Rejeté)

Les Core Maintainers décident du résultat final du SEP par vote :

- **Accepted (Accepté)** : Le SEP est approuvé et passe à l'étape d'implémentation
- **Rejected (Rejeté)** : Le SEP est rejeté, avec les raisons documentées. Le proposant peut réviser et soumettre à nouveau en fonction des retours

### 5. Implemented (Implémenté)

Un SEP accepté entre dans l'étape d'implémentation. Le travail d'implémentation peut être effectué par le proposant ou d'autres contributeurs. Pendant l'implémentation :

- Les documents de spécification concernés doivent être mis à jour
- Le code de référence doit être implémenté (le cas échéant)
- Les cas de test iFACTS doivent être écrits ou mis à jour

### 6. Final

Après que l'implémentation est terminée et a passé la révision, le SEP entre dans son état final. À ce stade :

- Les documents de spécification ont été mis à jour
- La suite de tests iFACTS a été mise à jour en conséquence
- La documentation et les guides associés ont été mis à jour

## Modèle de SEP

Lors de la soumission d'un SEP, veuillez inclure les éléments suivants :

- **Titre** : Une description concise de la proposition
- **Motivation** : Pourquoi ce changement est-il nécessaire ? Quel problème résout-il ?
- **Conception détaillée** : Détails techniques et plan d'implémentation de la proposition
- **Compatibilité ascendante** : Analyse de l'impact sur les spécifications et implémentations existantes
- **Impact sur iFACTS** : Quels tests de conformité doivent être ajoutés ou modifiés
- **Alternatives** : Autres approches envisagées et leurs avantages et inconvénients comparatifs

## Qui peut soumettre un SEP

Toute personne peut soumettre un SEP. Que vous soyez Core Maintainer, mainteneur, contributeur ou utilisateur de l'écosystème iFay, si vous estimez que la spécification nécessite une amélioration, vous êtes invité à soumettre une proposition.

## Notes spéciales

Les SEPs impliquant des modifications de protocole nécessitent une attention particulière : étant donné que chaque protocole iFay (Faying, Telepathy, ICP, CAP, DTP, SSP) correspond à un sous-projet indépendant, les mainteneurs des protocoles concernés doivent participer à la révision. Par exemple, un SEP qui modifie le comportement du Control Authority Protocol (CAP) nécessite que les mainteneurs du groupe de travail WG-Protocols évaluent son impact sur les modules associés tels que le Device Driver Hub et l'environnement d'exécution FayGer.
