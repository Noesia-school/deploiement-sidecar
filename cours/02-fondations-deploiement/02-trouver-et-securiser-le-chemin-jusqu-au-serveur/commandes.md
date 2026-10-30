# Commandes de référence — DNS, TLS et HTTP

Ces commandes proviennent du deck de préparation de la vidéo 2.2. Elles donnent des formes de référence, pas une copie exacte de toutes les commandes filmées. En particulier, la vidéo utilise `curl -v` sur la racine en HTTP puis HTTPS ; le deck cible `/api/health` avec des options supplémentaires.

Le nom `internote.deploiement.noesia.training` est celui de la démonstration. Sa présence ici ne garantit pas la disponibilité du service. Les outils `dig`, OpenSSL et curl doivent être disponibles dans le terminal utilisé ; les options OpenSSL ci-dessous sont prévues pour OpenSSL 3. Aucun compte ni secret n’est nécessaire.

## Résoudre le nom et observer la délégation

```sh
dig +short internote.deploiement.noesia.training
dig +trace +nodnssec internote.deploiement.noesia.training
```

- `+short` réduit la sortie aux réponses utiles. La vidéo montre aussi la forme complète de `dig`, sans cette option, pour lire la question et la réponse.
- `+trace` suit les délégations DNS depuis la racine : ce n’est pas une capture des requêtes du navigateur.
- `+nodnssec` allège les informations DNSSEC affichées ; ce n’est pas une vérification de sécurité supplémentaire.
- Une sortie courte vide ne suffit pas à conclure à une panne. La trace peut aussi être limitée par le réseau utilisé.

## Vérifier une connexion TLS

```sh
openssl s_client -brief \
  -connect internote.deploiement.noesia.training:443 \
  -servername internote.deploiement.noesia.training
```

- `-connect` fixe la destination et le port ; ici, le port doit être écrit.
- `-servername` transmet le nom en SNI. **Il ne vérifie pas ce nom.**
- `-brief` résume la connexion ;

Lire le résultat de vérification et le protocole négocié. La confiance dépend aussi du magasin de certificats local, qui peut différer de celui du navigateur. Ne retire pas les contrôles en cas d’échec. Cette commande n’a pas de limite de durée : une attente peut être interrompue avec `Ctrl+C`.

## Lire les champs du certificat

```sh
echo | openssl s_client \
  -connect internote.deploiement.noesia.training:443 \
  -servername internote.deploiement.noesia.training 2>/dev/null | \
  openssl x509 -noout -issuer -dates -subject
```

Le pipe `|` transmet la sortie à la commande suivante. `echo` fournit une ligne vide puis ferme son entrée. `x509` lit le certificat et affiche l’émetteur, les dates, le sujet ; `-noout` évite d’afficher le certificat encodé.

**Cette lecture ne valide pas la connexion.** `2>/dev/null` masque les diagnostics de `s_client` : obtenir des champs lisibles ne prouve pas que la chaîne de confiance et le nom ont été validés. La commande précédente porte cette vérification. Émetteur et dates peuvent changer lors d’un renouvellement.

## Relier DNS, connexion, TLS et HTTP avec curl

Forme de référence du deck :

```sh
curl -v https://internote.deploiement.noesia.training/
```

- `-v` affiche les étapes de connexion et les en-têtes.
- Sans option changeant la méthode, curl effectue ici un GET. Aucune redirection n’est suivie automatiquement.

Dans la séquence filmée vers **20:18–22:20**, la comparaison porte sur le chemin `/`, d’abord avec `http://`, puis avec `https://`, en mode verbeux.

Lire résolution, adresse et port, négociation TLS, puis méthode et statut HTTP. Un succès sur cette requête ne prouve pas tout le parcours utilisateur.
