# 3.2 — Comprendre les modèles d’hébergement et les responsabilités

## Intention

Comprendre qui installe, entretient et fait fonctionner les différentes couches du service selon l’hébergement. Après les exigences et les risques de [3.1](../01-service-production-et-risques/contenu.md), il s’agit de relier liberté technique, travail d’exploitation et organisation des interventions, sans désigner un modèle supérieur aux autres.

## Repères dans la vidéo

Les horodatages sont approximatifs, issus de la transcription de la vidéo finale.

- **00:28 — Une application, plusieurs environnements** : plateforme managée, VPS ou environnement du client. Le choix change la marge de manœuvre et le travail à prendre en charge.
- **01:19 — Partir des besoins d’exploitation** : mettre à jour l’application ou ajouter un moteur de recherche pose la question de qui peut intervenir et de qui s’en occupe.
- **01:57 — Comprendre le VPS** : Virtual Private Server, ou serveur privé virtuel. Dans le modèle présenté, on dispose des droits d’administration ; l’hébergeur prend en charge le socle de calcul, stockage et matériel, tandis que système, exécution et application restent à installer, configurer et entretenir.
- **03:25 — Relier liberté et entretien** : un moteur de recherche peut être installé sur le VPS alors qu’il n’est pas proposé par toutes les offres managées. La génération de PDF reposant sur un navigateur illustre aussi ce besoin de composants particuliers.
- **04:50 — Maintenir un composant** : une mise à jour peut modifier sa configuration ou le stockage de ses données. Il faut la tester, préparer une reprise, relancer si nécessaire et vérifier. Pouvoir administrer ne signifie pas que ce soit le meilleur usage de son temps.
- **06:09 — Déléguer au managé** : dans l’offre illustrée, le fournisseur prend aussi en charge le système, ses mises à jour, le socle d’exécution et les redémarrages. L’intervenant se concentre sur l’application ; ce choix reste professionnel même quand on sait administrer un serveur.
- **07:45 — Garder la responsabilité applicative** : redémarrer ne corrige pas un bug qui fait planter l’application en boucle. La correction ou le retour à une version fonctionnelle reste à organiser côté application.
- **08:15 — Déléguer un composant seulement** : conserver le VPS tout en confiant la base de données à un service managé est possible. Vérifier le périmètre couvert et ce qui reste à organiser ; cette délégation ne transfère pas automatiquement les engagements envers le client.
- **09:10 — Situer Coolify** : la capture illustre une interface qui facilite le déploiement à partir d’un dépôt Git. À **10:03**, la distinction est explicite : moins de gestes au terminal ne dispense pas d’entretenir le serveur et Coolify lui-même.
- **10:59 — Distinguer construction et exécution** : le build prépare le code et ses dépendances. Soit la plateforme reçoit le code source et construit l’application, soit elle reçoit une image OCI déjà préparée et l’exécute dans un conteneur.
- **12:09 — Comprendre le fil rouge OCI** : selon la plateforme, un mode de livraison ou les deux sont possibles. La vidéo annonce un même paquet construit avec Docker pour le managé et le VPS ; la configuration et le stockage des données restent à adapter à l’environnement.
- **12:57 — Déployer dans l’environnement du client** : il peut s’agir d’un VPS ou d’une plateforme, dans le cloud ou dans ses infrastructures. La distinction porte surtout sur l’organisation et les droits, pas sur un déplacement physique.
- **13:26 — Identifier les interlocuteurs** : préparer accès, livraison et interventions avec l’interlocuteur technique ; identifier aussi qui autorise les interventions et changements d’infrastructure. Ces rôles peuvent être tenus par une même personne ou plusieurs.
- **14:22 — Organiser un accès à une base du client** : décrire quel programme doit joindre quelle base, pour quelles opérations et avec quels droits ; faire autoriser le chemin réseau, planifier son ouverture par l’équipe technique, puis vérifier ensemble depuis l’application.
- **15:46 — Coordonner une indisponibilité** : une application sur un VPS du client n’accède plus à sa base managée externe. Dans cette situation, l’intervenant garant de l’application rassemble les informations, coordonne les acteurs, suit la résolution et tient le client informé.
- **16:30 — Comparer sans hiérarchiser** : davantage de liberté sur VPS implique davantage d’entretien ; le managé délègue une partie du socle ; l’environnement client ajoute des règles et des interlocuteurs. La conclusion annonce un approfondissement du choix par les coûts humains et d’infrastructure, sans effectuer cet arbitrage ici.

## Notions à retenir

### Héberger, c’est aussi répartir le travail après la mise en ligne

Dans le **VPS présenté**, l’hébergeur fournit le socle infrastructurel. Le système d’exploitation, ses mises à jour, le socle d’exécution — principalement Docker dans le parcours annoncé —, les redémarrages, l’application et ses dépendances restent du côté de l’intervenant qui l’administre. Installer un composant supplémentaire apporte de la liberté, mais aussi du travail de maintenance et de vérification.

Dans le **managé présenté**, davantage de couches sont exploitées par le fournisseur. Cela délègue du travail à des professionnels, pas seulement un clic de publication. Le périmètre dépend de l’offre : il faut savoir ce qu’elle prend en charge. L’application et ses erreurs ne disparaissent pas de ses propres responsabilités parce que la plateforme sait la redémarrer.

Le choix n’est pas forcément tout ou rien : une **base managée à côté d’une application sur VPS** permet de déléguer ce composant délicat. Il faut encore vérifier la prestation, les engagements et le travail restant, sans supposer que sauvegardes et restauration sont déjà organisées. Leur mise en pratique n’est pas développée dans cette vidéo.

### Un outil d’administration ne remplace pas un exploitant

**Coolify** facilite des gestes de déploiement et peut réduire les manipulations au terminal. Installé sur son serveur, il laisse ce serveur et l’outil lui-même à entretenir : simplifier l’interface n’équivaut pas à confier l’exploitation à un fournisseur managé. La vidéo montre une capture explicative, pas une installation ni un exercice Coolify. Le formateur annonce une pratique au terminal pour le chapitre VPS afin de comprendre les opérations sous-jacentes.

### Qui construit n’est pas la même question que qui exploite

La **construction**, ou **build**, prépare l’application et ses dépendances avant l’exécution. On peut livrer du code source que la plateforme construit, ou une **image OCI**, un paquet applicatif déjà préparé qu’elle exécutera dans un conteneur. Les possibilités dépendent de la plateforme ; « managé » ne signifie pas nécessairement « livraison de code source ».

Le paquet commun annoncé dans le cours permet de garder un même fil rouge entre managé et VPS, voire environnement client. Cela ne rend pas identiques la configuration ni la manière de stocker les données. La fabrication de l’image et les déploiements sont annoncés pour les chapitres suivants, pas réalisés ici.

### Chez le client, organiser les droits et les interventions

Un environnement client peut reposer sur les mêmes modèles techniques, mais les droits disponibles et les décisions ne sont pas nécessairement entre les mains de l’intervenant. Il faut distinguer **l’interlocuteur technique**, avec qui préparer l’intervention, de **la personne qui l’autorise** ; ce sont des rôles, pas obligatoirement deux postes séparés.

L’exemple de connexion à une base montre l’importance d’une demande précise et d’une vérification commune : besoin applicatif, droits nécessaires, autorisation, planification, ouverture par l’équipe concernée, puis contrôle depuis l’application. La connexion n’est pas présentée comme effectivement ouverte pendant la vidéo.

Même quand les tâches sont réparties, la **coordination** reste nécessaire. Dans le cas du VPS du client et de la base externe, chercher à qui attribuer la panne ne suffit pas à rétablir le service. L’intervenant chargé de l’application organise les échanges et le suivi et informe le client ; cela ne lui donne pas automatiquement les droits d’agir sur les systèmes des autres acteurs.

## Pour reprendre la réflexion

Reprends la situation à **15:46** : le VPS appartient au compte du client et son équipe le gère ; la base dépend d’un fournisseur managé externe. Avant de relire la discussion, distingue qui exploite chaque composant et qui rassemble les informations et suit la résolution. Répartir les tâches ne suffit pas si personne ne coordonne l’ensemble.

Cette vidéo explique des modèles et des situations d’organisation, sans commande ni intervention sur un système à reproduire.
