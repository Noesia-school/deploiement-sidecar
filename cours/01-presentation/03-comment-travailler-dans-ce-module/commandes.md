# 1.3 — Commandes montrées dans la vidéo

## Récupérer le compagnon

Depuis un dossier local choisi pour les projets pédagogiques, le formateur récupère le dépôt, entre dans sa copie puis lance son harnais déjà installé :

```sh
git clone https://github.com/Noesia-school/deploiement-sidecar
cd deploiement-sidecar
opencode
```

Le clonage crée un dossier local. Si une copie existe déjà, l’ouvrir sans écraser le travail présent. Le repère important est de lancer le harnais dans le dossier du compagnon ; OpenCode n’est pas imposé aux élèves.

## Observer les ressources d’InterNote

Commande montrée par le formateur sur son environnement préparé, **à étudier, pas à exécuter depuis la copie de l’élève** :

```bash
ssh internote@83.228.228.151 docker stats --no-stream --format=json | yq -pj '{"conteneur": .Name, "CPU": .CPUPerc, "Memoire": .MemUsage}'
```

Cette démonstration utilise un accès SSH déjà préparé au VPS du formateur et yq Mike Farah v4 sur son poste local. Elle observe les ressources d’une application déjà hébergée ; ce n’est ni un exercice de connexion au serveur ni un déploiement à reproduire.

Dans cette vidéo, la commande sert de support pour demander au compagnon son objectif, situer ses étapes et prévoir la nature du résultat, **sans lui demander de l’exécuter**. Le formateur confronte ensuite l’explication à son observation réelle. Aucune sortie chiffrée ni réponse du compagnon n’est préétablie ici ; l’apprentissage détaillé des outils n’est pas l’objectif de cette séquence.
