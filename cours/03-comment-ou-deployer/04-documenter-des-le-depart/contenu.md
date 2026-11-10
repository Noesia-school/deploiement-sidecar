# 3.4 — Documenter dès le départ

## Intention

Appliquer les réflexions du chapitre à InterNote avec l’aide de l’agent, puis conserver les échanges, les décisions et leurs raisons pour faciliter la reprise du projet. La documentation fait partie du livrable ; lire le code ne suffit pas à retrouver le contexte des choix.

## Repères dans la vidéo

Les horodatages sont approximatifs, issus de la transcription automatique du montage final, pas d’une transcription intégralement relue. Celle-ci référence `3.4-avec-intro.mp4` (1 958,433 s), tandis que le rendu livré `3.4.mp4` dure 1 958,454 s ; les repères ne prétendent pas à un recalage image par image.

- **01:13 — Distinguer fonctionnement et raisons** : le LLM peut aider à décrire le code, mais ne connaît pas automatiquement le contexte, les échanges ni les arguments qui ont conduit aux choix.
- **02:33 — Documenter le service** : rôle de l’application, dépendances, entrées/sorties, interfaces, accès et données. À **03:02**, les runbooks sont présentés comme des procédures détaillant les interventions, sans en exécuter ici.
- **03:54 — Garder les échanges dans des PV** : date, heure, participants, lieu si pertinent, contexte, sujets discutés, accords, points ouverts et actions suivantes. Discuter un sujet n’implique pas qu’une décision ait été prise.
- **05:26 — S’aider d’outils de transcription et de compte rendu** : ils préparent la trace des échanges. À **05:55–06:47**, le formateur insiste sur la confirmation des accords par le client ; une mention unilatérale ne remplace pas cette confirmation.
- **06:51 — Introduire les ADR** : Architecture Decision Record, une fiche courte par décision, avec contexte, options, choix, raisons et conséquences. Statut, date et décideurs permettent de la situer ; limites et conditions de réexamen complètent la fiche lorsqu’elles sont connues. Le format est recommandé, pas imposé à tous les projets.
- **10:14 — Conserver l’historique** : si un fait nouveau change le choix, créer une nouvelle décision et signaler que la précédente est remplacée, éventuellement en partie, plutôt que d’effacer son raisonnement.
- **11:14 — Examiner le dépôt avant d’écrire** : dans la démonstration, le projet commence avec README et instructions aux agents. Une proposition de documentation courte pour la reprise est préparée en mode plan, puis l’écriture est autorisée.
- **13:18 — Relire et restructurer** : le document initial trop regroupé est découpé, avec un README principal menant à l’index documentaire, puis aux fiches. À **14:52**, un schéma est repris en Mermaid ; le commit est ensuite autorisé séparément.
- **16:04 — Installer le réflexe ADR** : créer une première fiche pour l’adoption du format et demander à l’agent de proposer des ADR lors des décisions structurantes. Le formateur refuse d’abord le commit pour prendre connaissance du texte.
- **17:17 — Repérer le contexte inventé** : l’agent a trop étoffé les raisons historiques de l’adoption du format. Un texte plausible ne prouve pas qu’un problème a réellement été rencontré dans le projet.
- **18:46 — Tester dans une nouvelle conversation** : envisager Docker sans rien implémenter amène l’agent à proposer une fiche au statut « Proposé ». Le formateur peut commenter les options suggérées, puis accepter la décision et autoriser son commit. Ce n’est pas encore une construction d’image.
- **21:09 — Fournir un cadrage plutôt que demander un choix sans contexte** : un PV et un document préparés pour un cas fictif InterNote décrivent usages, contraintes et questions ouvertes. Ils alimentent la proposition de déploiement, y compris l’évolution vers des pièces jointes.
- **23:09 — Challenger la première réponse** : conteneurs managés en UE, PostgreSQL managé et API externe sont proposés par l’agent, pas encore retenus comme solution finale. À **24:39–25:31**, demander le sens de PITR et RPO permet de comprendre avant de décider.
- **27:19 — Séparer les décisions après itération** : cinq ADR portent finalement SQLite, monolithe conteneurisé sur service managé, API IA économique, exploitation applicative et reprise par le prestataire, stockage objet pour les pièces jointes futures. Ces textes et une synthèse de déploiement deviennent des références à relire pour la suite.
- **30:02 — Faire vivre la documentation** : corriger les documents lorsque besoins, exigences ou fonctionnalités changent, sans effacer l’historique des décisions. La fin du chapitre annonce Docker, construction d’image et Compose ; ces manipulations ne sont pas réalisées dans cette vidéo.

## Notions à retenir

### Trois traces différentes, complémentaires

La **documentation technique** décrit le service et son fonctionnement. Un **runbook** explique comment mener une intervention ; l’avoir rédigé ne démontre pas que la procédure a été testée.

Un **PV**, ou procès-verbal/compte rendu, garde la trace d’un échange : ce qui a été discuté, les accords effectivement confirmés et les suites encore ouvertes. Une transcription est une matière première, pas automatiquement un compte rendu validé.

Un **ADR** conserve une décision et son raisonnement : problème, options envisagées, choix, raisons, conséquences, statut et acteurs. Une proposition n’est pas une décision acceptée. Les options que l’agent ajoute peuvent servir à discuter, mais ne doivent pas être présentées d’emblée comme des échanges qui ont réellement eu lieu.

### Relire l’agent, pas seulement lui faire produire du texte

L’agent peut proposer la structure, rédiger et dessiner un schéma ; l’humain doit fournir le contexte absent du code et vérifier ce qui est affirmé. La démonstration montre un contexte inventé, une restructuration de la documentation et une autorisation de commit distincte de la rédaction. Elle ne dispense pas de relire les documents avant qu’ils servent de référence aux conversations suivantes.

Une décision acceptée peut devenir caduque : conserver son texte historique, relier la nouvelle décision et mettre à jour le statut évite de réécrire le passé. Cela reste compatible avec une documentation technique vivante, corrigée quand le fonctionnement change.

### Confirmer les accords sans promettre une exonération

Le repère pratique de l’aparté juridique est de **faire confirmer explicitement les accords** et de distinguer ce qui reste à valider. Ne pas transformer la formulation orale sur la « valeur légale » d’un PV en règle juridique universelle, ni la confirmation en transfert automatique de responsabilité : contrat et obligations applicables restent déterminants. Cela complète la distinction entre délégation et transfert abordée en [3.1](../01-service-production-et-risques/contenu.md).

### Le cadrage InterNote est un scénario pédagogique

Le PV et le cadrage sont préparés pour un **cas fictif**, pas pour attester d’un accord client réel. La vidéo cite notamment 15 utilisateurs, 5 personnes actives, un accès 24 h/24, une interruption visée d’une heure et une perte maximale de deux heures de données récentes. Ce sont des besoins à expliciter, pas des garanties démontrées par la rédaction des ADR.

**PITR**, Point-in-Time Recovery, désigne une restauration à un instant donné. **RPO**, Recovery Point Objective, désigne la perte maximale acceptable de données récentes, généralement exprimée en durée ; ce n’est pas le temps de réparation. Ces termes sont expliqués à la demande, pas enseignés ici sous forme de procédure de sauvegarde/restauration.

La proposition initiale de PostgreSQL/PITR n’est pas le résultat final : après discussion, la synthèse retient SQLite et répartit les autres choix en fiches distinctes. Le stockage objet concerne des pièces jointes futures. Ces orientations ne prouvent ni sélection d’un fournisseur, ni fonctionnalité déjà implémentée, ni capacité de reprise testée. Le choix managé pour InterNote dans ce scénario ne transforme pas non plus le cas documentaire fictif de [3.3](../03-choisir-sans-surdimensionner/contenu.md) en décision client réelle.

## Pour reprendre la pratique

Sur un projet d’exercice sans données sensibles, regarde d’abord la documentation existante. Choisis un seul point à clarifier avec l’agent : est-ce un fait lisible dans le code, un contexte que tu dois lui fournir ou une proposition encore à discuter ? Relis le résultat avant de le traiter comme une référence.

Tu peux aussi reprendre la proposition Docker à **18:46** et repérer ce qui distingue « envisager », « proposer », « accepter » et « implémenter ». La vidéo illustre leur séparation ; elle ne fournit pas une commande ni un déploiement à reproduire. Les formulations exactes des prompts ne sont pas intégralement données par la transcription : ne pas les reconstruire comme des citations du formateur. Ne partage ni secrets, ni enregistrements ou documents clients sensibles pour cet exercice.
