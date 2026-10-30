# Installer et utiliser Linux sous Windows avec WSL

Cette ressource accompagne la vidéo consacrée à WSL : conserver son bureau Windows tout en travaillant dans Ubuntu, avec l’Explorateur et VS Code. Docker constitue un complément facultatif à partir de **30:27**.

## Les repères essentiels
- **Linux** : le noyau autour duquel une distribution rassemble les outils du système. La vidéo choisit **Ubuntu**.
- **WSL 2** : permet de faire fonctionner un environnement Linux à côté de Windows, avec des intégrations entre les deux.
- **Terminal** : fenêtre d’interaction. **Shell** : interprète les commandes, par exemple PowerShell sous Windows ou Bash dans Ubuntu. **Programme** : outil lancé par une commande, comme `ls`.
- Utiliser un environnement local Linux rapproche les outils de ceux du serveur visé ; cela ne garantit pas à lui seul la réussite du déploiement.

## Parcours de la vidéo

### 11:17 — Préparer puis installer WSL

Prévoir une version compatible de Windows, la virtualisation disponible et les droits administrateur. Enregistrer son travail avant le redémarrage ; sur un poste géré par une organisation, demander l’installation au service informatique si nécessaire.

Dans **PowerShell ouvert en administrateur**, la vidéo lance :

```powershell
wsl --install
```

Cette commande installe WSL. Redémarrer quand Windows le demande. Dans la séquence filmée, l’installation d’Ubuntu est ensuite poursuivie depuis le terminal Windows :

```powershell
wsl --list --online
wsl --install Ubuntu
```

La première commande liste les distributions proposées ; la seconde demande Ubuntu. Selon l’état de la machine, Ubuntu peut déjà avoir été installé par la commande initiale : ne pas recommencer une installation déjà terminée.

Au premier lancement d’Ubuntu, créer l’utilisateur Linux et son mot de passe, distincts du compte Windows. **Aucun caractère ne s’affiche pendant la saisie du mot de passe : c’est normal.**

### 17:57 — Distinguer les systèmes de fichiers

Pour un projet utilisé par des outils Linux, conserver ses fichiers dans l’espace Linux, par exemple sous `/home/<utilisateur>` (abrégé `~`). `/mnt/c` donne accès au disque C: de Windows depuis Linux ; traverser ce pont peut avoir un coût de performance ou des différences de comportement.

Les gestes montrés dans **Ubuntu** :

```sh
ls
touch test.txt
cat test.txt
pwd
explorer.exe .
```

- `ls` liste le dossier courant ; `touch test.txt` crée un fichier vide s’il n’existe pas.
- Dans la démonstration, le fichier est modifié avec le Bloc-notes ; `cat test.txt` permet ensuite d’en lire le contenu depuis Linux.
- `pwd` affiche le chemin du dossier courant ; il aide à distinguer `/mnt/c/...` de `/home/...`.
- `explorer.exe .` ouvre le dossier courant dans l’Explorateur Windows. Le point désigne ce dossier.

Après installation, relancer Windows Terminal si le profil Ubuntu n’apparaît pas encore. Avoir WSL installé ne signifie pas que l’onglet actuellement ouvert est un shell Linux.

### 22:37 — Travailler avec VS Code

Installer VS Code **sur Windows**, puis son extension officielle **WSL** de Microsoft. Utiliser **Connect to WSL**, ouvrir un dossier Linux et vérifier l’indication de connexion à Ubuntu/WSL dans le coin inférieur gauche. Le premier démarrage installe les éléments nécessaires côté Linux et peut être plus long.

Depuis Ubuntu, une fois placé dans le dossier du projet :

```sh
code .
```

Cette commande ouvre VS Code pour travailler sur le dossier courant avec l’intégration WSL.

Vers **26:24**, le formateur utilise Claude Code déjà installé sous Windows pour l’aider à installer ses outils côté Linux. La transcription ne fournit pas le détail complet des commandes exécutées par l’agent : il n’y a donc pas de script d’installation à recopier ici. Le point utile est de distinguer les outils disponibles sous Windows de ceux disponibles dans Ubuntu, puis de vérifier où l’éditeur et l’agent travaillent.

### 30:27 — Complément facultatif : Docker Desktop

Il est possible de s’arrêter avant cette section. Pour suivre le complément, Docker Desktop est installé et lancé **sur Windows**. Dans ses réglages, choisir le moteur WSL 2 si nécessaire, puis activer l’intégration WSL pour Ubuntu et appliquer les changements.

Dans **Ubuntu** :

```sh
docker version
```

La démonstration vérifie la présence des informations **Client** et **Server**, avec Docker Desktop côté serveur. Ce contrôle porte sur l’accès au moteur Docker depuis Ubuntu, pas sur une application déjà déployée.

## Liens fournis pour l’installation
- [Installer WSL — Microsoft](https://learn.microsoft.com/en-us/windows/wsl/install)
- [Télécharger VS Code](https://code.visualstudio.com/download)
- [Installer Docker Desktop sur Windows](https://docs.docker.com/desktop/setup/install/windows-install/)
