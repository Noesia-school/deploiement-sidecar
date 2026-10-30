# 2.3 — Observer ce qui exécute l’application

## Intention
Ouvrir la partie serveur : comprendre les composants qui traitent une requête, puis rapprocher une action dans le navigateur d’un événement dans le journal de l’application.

## Repères dans la vidéo
- **00:41 — Situer le serveur** : une machine destinée à répondre aux clients, avec une partie matérielle et une partie logicielle. Linux organise les ressources et l’exécution des programmes.
- **02:04 — Passer du code à l’exécution** : le code seul ne répond à personne ; un programme doit s’exécuter, écouter sur un port et traiter les demandes.
- **02:46 — Introduire le proxy inverse** : il reçoit les requêtes, choisit l’application destinataire selon des règles et peut prendre en charge TLS. Le schéma front-end/back-end illustre un routage selon le chemin de l’URL.
- **04:37 — Conserver les fiches** : PostgreSQL stocke, organise, retrouve et modifie les données. La persistance permet de les retrouver après un arrêt de l’application.
- **05:45 — Suivre le parcours complet** : navigateur → proxy → application → base de données, puis retour des données et de la réponse vers le navigateur.
- **06:26 — Situer Docker** : des conteneurs isolent les services tout en leur permettant de communiquer sur la même machine Linux. L’utilisation détaillée de Docker viendra dans son chapitre dédié.
- **06:57 — Observer le serveur du formateur** : connexion SSH, changement de prompt, déplacement dans le dossier de déploiement, puis `docker compose ps`. Le tableau montre l’application, la base `db` et le proxy.
- **08:43 — Lire un journal** : chaque événement peut indiquer l’heure, le composant, la méthode HTTP, la route et le statut.
- **09:57 — Corréler navigateur et serveur** : suivre les cinq derniers événements puis les nouveaux avec Compose ; ouvrir une intervention dans le navigateur ; retrouver le GET, l’identifiant de la fiche et le statut 200 dans les deux observations.

## Notions à retenir
- **SSH** ouvre une session distante chiffrée et authentifiée. Après connexion, les commandes s’exécutent sur le serveur, pas sur l’ordinateur local.
- **Proxy inverse** : reçoit et relaie. **Application** : traite la demande. **Base de données** : conserve et retrouve les données.
- La persistance suppose un stockage durable correctement préparé ; la présence d’un conteneur ne suffit pas à la garantir.
- Un journal montre ce qu’un composant a enregistré. Rapprocher son événement du résultat dans le navigateur aide à comprendre le parcours complet.

## Pour reprendre l’observation
Les [commandes de référence](commandes.md) documentent la démonstration du formateur : aucun accès à son serveur n’est promis. Sans serveur d’exercice, la conclusion invite à pratiquer les DevTools, DNS et le terminal, et à reproduire les schémas du chapitre.

La transition vers le chapitre 3 pose la question du service sur lequel un client compte : attentes, risques et responsabilités avant de choisir le déploiement.

*Source : transcription finale de la vidéo 2.3, repères relus le 30 octobre 2026.*
