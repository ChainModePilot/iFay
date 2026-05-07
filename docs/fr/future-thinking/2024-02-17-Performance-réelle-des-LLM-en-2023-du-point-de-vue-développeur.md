<!-- URL path: /2024-02-17 -->

# Performance réelle des LLM en 2023 du point de vue développeur

*17 février 2024 · Jah Guo*

Récemment, OpenAI a publié Sora, ajoutant à l'intérêt croissant pour les Modèles de Langage de Grande Taille (LLMs). En tant que chef de produit profondément impliqué dans les LLMs depuis un an, je partagerai mon expérience de travail pratique dans le contexte plus large des LLMs.

## 1. LLM est devenu le standard de la correction politique chez les géants de la tech

Après les réseaux sociaux, l'internet mobile, la blockchain et le métavers, 2023 est une fois de plus saluée comme la première année de la quatrième révolution industrielle — l'ère de l'IA. Les grandes entreprises technologiques ont découvert de nouvelles opportunités au-delà des concepts traditionnels et ont entamé une concurrence féroce. OpenAI, Microsoft, Google et Meta avancent rapidement avec des stratégies claires. Contrairement à avant, les grandes entreprises internet chinoises sont désormais prudentes et incertaines quant à leurs prochaines étapes en raison d'une puissance de calcul limitée et de scénarios d'application peu clairs.

## 2. Les patrons vivent l'amour, la peur et l'impuissance

Les patrons et les DSI sont également massivement influencés par les médias indépendants. Bien que la plupart des décideurs produit ne comprennent pas comment fonctionnent les grands modèles, ils décident tout de même de prendre une longueur d'avance dans l'implémentation des grands modèles, en interne comme en externe. Après avoir rebaptisé ChatGPT comme leur propre assistant, ils ont découvert que les informations internes de l'entreprise étaient non seulement envoyées à l'extérieur de l'entreprise, mais même à l'étranger, déclenchant ainsi des risques juridiques. Et l'interaction lente est presque inutilisable.

## 3. Les plus grands géants technologiques du monde copient ChatGPT

Depuis que ChatGPT a lancé le mode d'interaction dialogue + Prompt, les géants de la tech ont reproduit son assistant intelligent de manière presque identique. Les APIs, les applications multimodales et un store suivent. Bien que la prochaine fonctionnalité révolutionnaire d'OpenAI reste inconnue, une chose est certaine : tout le monde attend avec impatience de suivre le mouvement.

## 4. Ce pourrait être « Les habits neufs de l'empereur »

Que ce soit sur les réseaux sociaux, les forums de l'industrie ou les lancements de produits, beaucoup affirment que les grands modèles ont revitalisé leurs produits et même incubé des modèles spécifiques à l'industrie pour des milliers d'entreprises. Cependant, personne n'ose admettre que ces grands modèles dans les domaines professionnels manquent souvent de compréhension et qu'il y a de nombreuses tâches qu'ils ne peuvent pas accomplir. L'acquisition de connaissances professionnelles ou spécialisées par les grands modèles s'accompagne souvent d'un coût significatif.

## 5. Alors que les médias sont enthousiastes, les PMs, les développeurs et les experts métier sont tous déprimés

Une part significative du temps, environ 90%, est consommée par des tâches liées aux données telles que la collecte, la rédaction, le nettoyage, le formatage, le découpage, l'entraînement et l'étiquetage. Ce processus se poursuit jour après jour, semaine après semaine, mois après mois. Souvent, l'équipe de recherche en production n'est pas certaine de l'exactitude des informations. Les experts métier ne savent pas comment entraîner le modèle. Les chefs de produit réfléchissent aux moyens de faciliter la communication directe entre les experts métier et le LLM. La fin de ce processus reste floue pour tout le monde.

## 6. Rapidement devenu un nouveau point de croissance pour les plateformes cloud

Les fournisseurs traditionnels de plateformes cloud ont introduit des plateformes d'entraînement pour les LLMs basées sur le ML. Après MLOps, le concept de LLMOps a été introduit. Malgré les défis techniques et de puissance de calcul, la plateforme cloud transforme les LLMs en infrastructure de nouvelle génération. Cependant, sa conception est souvent perçue comme rudimentaire et difficile à utiliser directement par les experts métier. Il semble que les chefs de produit des services cloud n'aient pas encore pleinement compris comment les utilisateurs exploiteront les capacités des LLMs.

## 7. Transition progressive du premier plan vers l'arrière-plan, avec le métier comme cœur

Après six mois d'efforts intenses, j'ai réalisé que les grands modèles seuls ne peuvent pas tout accomplir. Construire des processus métier avec les grands modèles comme méthode principale ne parvient pas à fournir des solutions opportunes et rentables qui répondent aux besoins métier et offrent un retour sur investissement solide. De nombreux chefs de produit utilisent désormais les grands modèles hors ligne pour aider au traitement asynchrone des connaissances et des données. Pour permettre à ces modèles d'apprendre et de combiner efficacement de nouvelles formes de connaissances, nous avons donné à ce fragment de code contenant de la logique métier un nouveau nom — Agent.

## 8. L'industrie commence à définir une nouvelle forme d'applications de prochaine génération

Imaginez un avenir où les gens n'ont plus à décider quel site web ou quelle application utiliser. Au lieu de cela, ils communiquent simplement leurs intentions à l'IA, et l'IA trouve directement la réponse ou effectue une opération. Cette IA interactive pourrait représenter la prochaine génération de formes d'applications. Actuellement, de nombreux chefs de produit la conçoivent comme un chatbot, parfois appelé assistant intelligent. Cependant, il est regrettable que même avec plusieurs assistants, les utilisateurs doivent encore prendre des décisions ou effectuer des recherches.

## 9. La réglementation arrive plus tôt qu'avant

Les leaders d'opinion ont déclaré : « Si vous n'utilisez pas l'IA à l'avenir, vous serez un perdant », et ont rapidement commencé à tirer profit en proposant des cours. OpenAI a en outre montré que des millions de nouvelles « apps », ou Agents, peuvent émerger en seulement une semaine. En conséquence, une vaste quantité de données sensibles est téléchargée dans des centres de données à travers le monde, entraînant un mélange incontrôlé de valeurs contradictoires. Aucun autre type de produit n'a attiré l'attention du gouvernement aussi rapidement.

## 10. L'IA est descendue de son piédestal technologique pour devenir accessible aux gens ordinaires

L'entraînement de l'IA était autrefois le domaine exclusif des ingénieurs en algorithmes. Cependant, après le déploiement du modèle, il exige désormais une plus grande implication des experts métier et des utilisateurs dans le processus d'entraînement. Avec l'outil de génération de prompts et la plateforme d'entraînement, vous pouvez compléter l'entraînement du modèle sans aucune connaissance algorithmique. Même les modèles à petite échelle peuvent être facilement déployés sur des serveurs ou des ordinateurs personnels, de manière similaire à l'installation d'un logiciel. C'est un changement significatif qui met les ingénieurs en algorithmes sur le qui-vive.
