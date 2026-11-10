# 3.3 — Choisir sans surdimensionner

## Intention

Combiner les exigences et risques de [3.1](../01-service-production-et-risques/contenu.md) avec la répartition du travail de [3.2](../02-modeles-hebergement-et-responsabilites/contenu.md) pour choisir un hébergement proportionné : suffisant aujourd’hui, compatible avec une évolution plausible et exploitable avec les compétences disponibles. Préparer la suite ne veut pas dire la construire d’avance.

## Repères dans la vidéo

Les horodatages sont approximatifs, issus de la transcription finale de la vidéo livrée le 9 novembre 2026.

- **00:52 — Poser le cas fictif** : un assistant documentaire utilisant un LLM répond à des questions sur un corpus déjà indexé. Ce n’est pas InterNote. Les questions sont ponctuelles et une interruption est tolérée dans cet exemple ; l’import de lots de PDF, avec résultat le lendemain matin, est une évolution supposée, pas une demande client confirmée.
- **02:04 — Examiner la simultanéité** : importer successivement ou en parallèle ne produit pas le même pic de travail. Une échéance au lendemain peut permettre d’étaler les traitements plutôt que de tout faire simultanément.
- **04:09 — Compter le coût d’un incident** : dans le scénario, un import de douze PDF échoue faute de mémoire. Diagnostic, essais et relance mobilisent trois heures qui ne sont plus disponibles pour d’autres travaux. Une petite économie d’infrastructure peut être compensée par du temps humain.
- **05:59 — Identifier ce qui bloque** : mémoire, CPU ou ressource externe. Agrandir le serveur ne résout pas un quota d’appels LLM atteint ; le diagnostic peut être préparé avec l’agent.
- **06:51 — Distinguer vertical et horizontal** : augmenter les ressources d’un serveur ou répartir le travail entre plusieurs serveurs. Le vertical est présenté comme souvent suffisant à cette échelle ; l’horizontal ajoute une complexité qui justifie de se faire accompagner.
- **08:15 — Réfléchir aux données partagées** : la vidéo donne l’indice lecture/écriture et invite à approfondir avec le sidecar pourquoi des écritures sur plusieurs serveurs compliquent la situation. Elle ne résout pas cet exercice.
- **08:45 — Vérifier la compatibilité de l’offre** : l’import demande un traitement de fond, qui continue sans attendre une requête du navigateur. L’offre doit permettre ce processus et les bibliothèques ou le langage nécessaires ; davantage de ressources ne lève pas toutes ces limites.
- **10:12 — Distinguer évolution et migration** : si l’offre ne permet pas le traitement, adapter l’application, déplacer les données et basculer s’ajoutent au travail de la fonctionnalité elle-même, avec des risques d’interruption, de perte ou de corruption des données.
- **11:07 — Raisonner en TCO** : Total Cost of Ownership, ou coût total de possession, incluant mise en service, entretien, exploitation, adaptations et migrations sur une période donnée. À **11:35**, un budget fictif de migration de 300 € face à 20 € d’économie mensuelle donne quinze mois ; anticiper ne signifie pas payer systématiquement plus dès le départ.
- **12:59 — Comprendre la dette technique** : réindexer les vingt PDF initiaux pour livrer vite peut être raisonnable. Avec des imports réguliers, retraiter les documents inchangés et recalculer leurs embeddings entraîne des coûts récurrents, en plus du travail nécessaire pour corriger ce raccourci.
- **14:52 — Garder des proportions utiles** : une application et sa base sur un serveur peuvent suffire à une petite échelle. Répartition du trafic, répliques, files de tâches et workers demandent coordination, surveillance et entretien dès la livraison, même si la croissance espérée n’arrive jamais.
- **16:19 — Distinguer prestation dédiée et SaaS** : pour une prestation à un client, le formateur recommande un environnement dédié, idéalement dans son compte et payé par lui. Son propre SaaS peut mutualiser l’infrastructure, avec des enjeux d’isolation et de pannes touchant plusieurs clients ; certaines instances peuvent aussi rester dédiées.
- **17:45 — Formuler une recommandation conditionnelle** : pour la petite équipe fictive sans équipe système, préférer une offre managée compatible avec le futur import et son traitement de fond. Retenir un VPS si une autre exigence le justifie ; réexaminer le choix si besoins, traitements, exigences ou coûts changent.
- **18:43 — Préparer une proposition avec l’agent** : décrire application, volumes, fréquence, simultanéité, marges de manœuvre, coûts et évolution plausible. Faire proposer capacité initiale, trajectoire et coûts ; à **20:02**, rappeler que cette proposition doit être comprise et challengée, la décision restant humaine.
- **20:25 — Mobiliser les compétences avant de s’engager** : la variante de l’assistant pour 300 personnes augmente les enjeux de charge et les conséquences d’une interruption. Ne pas signer seul un engagement critique sans avoir mobilisé un spécialiste et des personnes capables de prendre en charge les interventions.
- **21:24 — Rassembler les arbitrages** : exigences, risques, travail réel, coût total, chemin d’évolution et exploitation assurée. La conclusion annonce leur application à InterNote et la documentation des raisons dans la dernière vidéo du chapitre ; aucun hébergement d’InterNote n’est décidé ici.

## Notions à retenir

### Dimensionner le travail réel, pas seulement compter les utilisateurs

La charge dépend des opérations et de ce qui se passe **en même temps**. Un import et des questions simultanées peuvent demander plus de ressources que les mêmes opérations étalées. La possibilité d’attendre jusqu’au lendemain change les options ; le nombre de tâches parallèles ne donne pas à lui seul une mesure exacte de CPU ou de mémoire.

L’incident mémoire et ses trois heures de diagnostic sont un **scénario pédagogique**, pas un résultat observé sur InterNote ni une durée de dépannage standard. Identifier la ressource limitante précède la décision de payer une instance plus grosse.

Le **scaling vertical** augmente la capacité d’un serveur ; le **scaling horizontal** ajoute des serveurs qui se partagent le travail. Le premier est plus simple dans le cas présenté, mais reste limité par les capacités et coûts disponibles. Le second peut devenir intéressant à plus grande échelle, avec davantage de travail de coordination : aucun seuil tarifaire universel ni architecture distribuée à construire ne sont enseignés ici.

### Préserver un chemin d’évolution sans tout construire

Un **traitement de fond** poursuit un travail indépendamment d’une requête du navigateur. L’offre doit le permettre, pas seulement offrir assez de mémoire. Sinon, externaliser le traitement ou changer d’offre, voire de technologie, peut devenir nécessaire.

Le **TCO** compare les coûts sur un même horizon, au-delà de l’abonnement. Dans l’hypothèse de la vidéo, **300 € / 20 € par mois = 15 mois** d’économies pour égaler le budget de migration. Si le besoin arrive dans deux ou trois mois, le bilan n’est pas le même que s’il arrive bien plus tard. Ce calcul illustratif n’est ni un devis ni une garantie de rentabilité ; le temps humain et les risques de bascule comptent aussi.

La **dette technique** désigne ici les coûts futurs d’un raccourci. Réindexer tout un petit corpus peut faire gagner du temps à la livraison ; conserver ce choix avec des imports fréquents ajoute des retraitements et des embeddings facturés. Le rattrapage consiste dans cet exemple à détecter ce qui est nouveau pour ne plus retraiter inutilement les documents déjà indexés. Cette dette est distincte du temps perdu dans l’incident mémoire.

### Choisir le périmètre client et l’exploitation qu’on peut assurer

Pour une **prestation dédiée**, l’environnement propre au client évite de lui faire partager les ressources et incidents d’autres clients ; son compte et son paiement direct évitent aussi d’avancer puis de refacturer l’hébergement. Les **voisins bruyants** sont les usages d’un client qui perturbent les ressources disponibles pour un autre.

Pour un **SaaS**, service proposé à plusieurs clients, mutualiser peut être pertinent, mais demande de traiter l’isolation des données et l’impact collectif des pannes. Une instance dédiée à certains clients reste possible. Qui porte l’infrastructure, quels clients la partagent et qui l’exploite sont des choix distincts.

La préférence pour le **managé** concerne le besoin fictif décrit et reste subordonnée à la compatibilité de l’offre. Ce n’est ni une obligation pour tous les projets ni une décision pour InterNote. De même, les 300 personnes de la variante ne constituent pas un seuil automatique imposant une technologie : l’enjeu est de pouvoir tenir les engagements avec les compétences et les intervenants nécessaires. L’agent aide à préparer et comparer ; il ne remplace pas les personnes qui s’engagent à intervenir.

## Pour approfondir avec le sidecar

Reprends la question à **08:15** : plusieurs serveurs lisent les mêmes données, puis plusieurs cherchent à les modifier. Imagine deux personnes qui modifient en même temps la même fiche : quelles difficultés nouvelles vois-tu ? Propose d’abord ton raisonnement ; le sidecar peut ensuite t’aider à l’explorer. C’est un approfondissement volontairement laissé ouvert par la vidéo, pas un mécanisme distribué déjà expliqué.

Pour discuter une proposition de ton agent, repars des besoins du cas, des ressources supposées limitantes, de la compatibilité des traitements futurs et du coût total. Les hypothèses sont à examiner, pas à prendre pour des mesures. La vidéo ne réalise ni test de charge, ni dimensionnement chiffré vCPU/RAM, ni déploiement ; elle ne fournit pas de commande à reproduire.
