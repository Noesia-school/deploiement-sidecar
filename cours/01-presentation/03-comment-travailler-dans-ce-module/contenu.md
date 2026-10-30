# 1.3 — Comment travailler dans ce module

## Intention

Apprendre activement : mettre en pause, éclaircir un mot, demander une explication à l’IA et confronter la réponse à une observation.

## Notions utiles

- **Harnais IA** : outil qui donne accès à l’agent et à ses capacités, notamment commandes et skills.
- **Terminal** : interface pour demander des actions ou observer un environnement à l’aide de commandes.
- **Local / distant** : la commande agit là où elle s’exécute, pas nécessairement sur l’ordinateur dont tu regardes l’écran.
- **Skill** : ensemble de consignes spécialisées que le harnais peut charger pour une tâche.
- **WSL** : environnement Linux utilisable sous Windows ; sa présence et sa maîtrise ne sont pas supposées.
- **De type Unix** : famille de systèmes partageant des repères de terminal proches, notamment macOS et Linux. Les commandes ne sont pas pour autant identiques sur tous les systèmes.

## Ce qu’on cherche à comprendre

- Le formateur utilise OpenCode dans OpenChamber ; tu peux garder ton propre harnais compatible.
- Les interfaces peuvent changer sans changer l’objectif pédagogique d’une manipulation.
- Le formateur travaille sur macOS et les serveurs du parcours utilisent Linux. macOS, Linux ou WSL permettent de garder des repères proches ; PowerShell reste possible si tu sais adapter les commandes.
- Comprendre l’objectif, les effets et les contrôles d’une commande importe plus que mémoriser toutes ses options.

## Préparer son environnement

- Sous Windows, WSL est le chemin recommandé : la ressource Circle « Installer et utiliser Linux sous Windows avec WSL » accompagne la préparation d’Ubuntu. Ses [repères et liens d’installation](../../../ressources/installer-wsl.md) sont également disponibles ici. Son installation n’est pas refaite dans cette vidéo.
- Un harnais en ligne de commande utilisé dans WSL doit être installé et lancé dans Ubuntu selon ses instructions officielles. Une installation sous Windows n’est pas automatiquement disponible sous Linux ; il n’est pas nécessaire de tout désinstaller.
- Avec une interface graphique, vérifier l’environnement auquel elle est connectée : la fenêtre ne suffit pas à savoir où les commandes s’exécutent.

## Rencontrer Sidecar

- Le formateur clone le dépôt, entre dans sa copie locale et lance OpenCode dans le terminal. Git et le harnais sont déjà installés ; les commandes figurent dans [commandes.md](commandes.md).
- La première conversation sert à découvrir le rôle du compagnon et l’aide qu’il peut apporter, sans lui demander d’exécuter des commandes.
- `AGENTS.md` porte les consignes du compagnon ; `cours/index.md` permet de retrouver les repères des vidéos. Il n’est pas nécessaire de lire tout le corpus pour poser une question.
- La démonstration montre une mémoire locale dans `MEMORY.md` : le compagnon retrouve le prénom et le démarrage du parcours lors d’un nouvel échange. Cette mémoire n’est pas l’historique complet des conversations ; ses modalités et limites sont décrites dans le README du dépôt.
- OpenChamber est ensuite présenté comme une autre interface pour OpenCode, pas comme un outil imposé. Retrouver la conversation, le dossier de travail et le terminal ; changer d’interface ne garantit pas de retrouver la même conversation.
- Le dossier de travail sert de point de départ aux chemins relatifs. Le terminal n’est pas l’IA : il permet d’agir sur un système et de lire ses réponses.

## Une explication, puis une vérification

La démarche du module est **prévoir → essayer → observer → comparer**. Faire une pause, demander une reformulation ou un exemple, puis confronter l’explication à ce qui se passe réellement. Une réponse convaincante de l’IA ne constitue pas une preuve.

La démonstration porte sur les ressources CPU et mémoire d’InterNote, déjà hébergé sur le VPS du formateur. La [commande montrée](commandes.md#observer-les-ressources-dinternote) combine SSH, Docker et yq. Elle sert à questionner une commande inconnue, pas à apprendre ces outils en détail ni à déployer l’application dans cette vidéo.

Le formateur exécute la commande dans son terminal, puis demande au compagnon d’expliquer « la commande de la vidéo 1.3 ». Il approfondit ensuite le terme JSON. L’élève peut demander une explication sans disposer de cet accès ; il n’a pas à se connecter au serveur du formateur ni à demander au compagnon d’exécuter la commande.

## Lire la commande

SSH fait exécuter Docker sur le serveur ; le pipe transmet sa sortie à yq sur le poste local. Docker relève ponctuellement les ressources des conteneurs en cours d’exécution ; yq sélectionne et renomme les champs. Une mesure ponctuelle n’établit ni une saturation ni sa cause : cette démonstration sert à comprendre une commande, pas à diagnostiquer le serveur.

## Limites

- L’autonomie ne remplace pas les explications fondamentales ni les précautions sur les gestes à risque.
- Cette fiche ne fournit ni installation WSL ni environnement déjà prêt ; clarifie ton contexte avant de pratiquer.
- Les accès et outils de la démonstration sont préparés par le formateur. Aucun accès à son serveur n’est fourni ; aucune intervention sur un système réel n’est à reproduire avec le compagnon.
