# 2.1 — Suivre une requête depuis le navigateur

## Intention

Relier une action dans InterNote à une requête HTTP et à la réponse du serveur, avec les outils de développement du navigateur (DevTools).

## Repères dans la vidéo

- **04:11 — Découvrir InterNote** : une application privée de carnet de terrain. Des notes d’intervention peuvent servir à générer un rapport avec un LLM.
- **06:16 — Ouvrir les DevTools** : clic droit, Inspecter, puis onglet Network (Réseau). Recharger la page pour voir ses requêtes ; distinguer document, styles, scripts et appels Fetch à l’API.
- **08:10 — Lire un échange** : URL, méthode, statut et en-têtes dans Headers ; données JSON dans Response. Relier les identifiants et titres reçus à la liste affichée.
- **10:42 — Comprendre JSON et l’API** : JSON structure les données échangées ; l’API fournit une interface que le navigateur peut appeler. L’URL distingue notamment la liste des interventions d’une intervention précise.
- **13:43 — Lire puis modifier une intervention** : un GET récupère la fiche numéro 6 ; l’enregistrement des notes déclenche un PUT sur la même URL. Payload montre les données envoyées, dont la note modifiée.
- **15:54 — Interpréter les statuts** : 2xx pour les succès, 4xx pour les problèmes liés à la demande, 5xx pour les erreurs serveur ; les redirections 3xx sont aussi évoquées dans la documentation consultée.
- **17:38 — Comparer avec et sans session** : copier l’URL de l’API puis l’ouvrir en navigation privée donne une réponse « connexion requise » et un statut 401. Le serveur a répondu ; ce refus n’est pas une absence de connexion réseau.
- **18:47 — Changer de rôle** : InterNote est serveur pour le navigateur et client du fournisseur de LLM. La génération déclenche un POST ; la réponse observée contient des fragments de texte au format JSON.

## Notions à retenir

- **HTTP** organise l’échange requête/réponse. Une méthode décrit la demande, un statut renseigne sur son traitement.
- **GET** demande une ressource ; dans cette démonstration, **PUT** met à jour la fiche et **POST** demande une génération.
- **En-têtes** : métadonnées de l’échange. **Corps** : contenu transporté. **Payload** : données envoyées avec la requête.
- **Client et serveur** sont des rôles dans un échange, pas des identités fixes.
- Le navigateur montre ses propres échanges avec InterNote, pas la requête qu’InterNote envoie au fournisseur de modèle.

## Pour reprendre l’observation

Choisis une action sur des données d’exercice, nettoie la liste Network, effectue l’action, puis rapproche méthode, URL, statut et résultat visible. Cette vidéo utilise les DevTools, sans commande curl ni script à reproduire. Ne partage pas de cookies, de jetons ou d’export réseau contenant une session authentifiée.

La vidéo 2.2 suit le chemin jusqu’au serveur avec DNS, les ports et TLS ; la vidéo 2.3 ouvre ensuite la partie serveur.
