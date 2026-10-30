# Commandes de référence — Observer le serveur de démonstration

Ces commandes sont reprises du deck de la vidéo 2.3 et correspondent aux gestes décrits dans la transcription. Elles servent à comprendre la démonstration, **pas à se connecter au serveur du formateur**. Aucun compte, droit d’accès ou environnement identique n’est fourni par cette fiche. Une reproduction demande son propre environnement pédagogique autorisé et préparé.

## Ouvrir la session distante

```sh
ssh internote@83.228.228.151
```

`internote` est l’utilisateur distant et `83.228.228.151` l’adresse du serveur de démonstration. SSH établit une connexion chiffrée et authentifiée. Dans la vidéo, le changement de prompt aide à voir que les commandes suivantes s’exécutent désormais sur le serveur.

## Retrouver les services du projet

Dans la session distante du formateur :

```sh
cd ~/demo
docker compose ps
```

- `cd` change de dossier ; `~` représente le dossier personnel de l’utilisateur distant.
- `docker compose ps` affiche les conteneurs du projet Compose trouvé dans ce contexte. La démonstration montre les services `app`, `db` et `proxy`.

Variante de présentation du deck, également décrite dans la vidéo :

```sh
docker compose ps | less -S
```

`|` transmet le tableau à `less` ; `-S` évite de couper les lignes longues sur plusieurs lignes. Les flèches permettent de se déplacer et `q` de quitter cette lecture.

## Suivre le journal de l’application

```sh
docker compose logs --tail=5 --follow app
```

- `logs` lit les journaux ; `--tail=5` limite l’historique initial aux cinq dernières lignes.
- `--follow` continue à afficher les nouveaux événements.
- `app` sélectionne le service applicatif de ce projet.

Dans la vidéo, l’ouverture d’une intervention produit un GET visible dans Network et une nouvelle ligne dans le journal. Comparer méthode, route, identifiant et statut ; le journal peut présenter une route générique tout en indiquant l’identifiant séparément.

`Ctrl+C` arrête le suivi des logs, pas l’application. Une ligne de journal ne prouve pas à elle seule que la fiche s’est correctement affichée : l’observation du navigateur complète celle du serveur. Des journaux peuvent contenir des données sensibles ; ne partage pas un flux brut d’un vrai projet.

*Sources : deck de préparation et transcription finale de la vidéo 2.3, relus le 30 octobre 2026. Commandes à relire par l’auteur.*
