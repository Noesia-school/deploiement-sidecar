# 2.2 — Trouver et sécuriser le chemin jusqu’au serveur

## Intention

Comprendre trois étapes : trouver une adresse avec DNS, joindre un service sur un port, puis protéger la connexion avec TLS.

## Repères dans la vidéo

- **01:04 — Adresses IP** : distinguer les formats IPv4 et IPv6 ; une adresse réseau permet de situer la destination.
- **02:17 — DNS** : un résolveur recherche l’adresse associée à un nom d’hôte. Le schéma montre la délégation depuis la racine vers `.training`, puis les responsables du domaine et de sa zone.
- **03:58 — Observer avec dig** : réponse complète, réponse courte avec `+short`, puis délégation avec `+trace +nodnssec`. Les enregistrements A correspondent à IPv4, AAAA à IPv6.
- **05:54 — Acheminer et joindre** : les routeurs relaient les paquets ; le port distingue le service à joindre. HTTP utilise par défaut 80, HTTPS 443. Un port explicite se place après le nom d’hôte, précédé de `:`.
- **07:48 — Situer les couches réseau** : HTTP, transport et adressage apportent chacun des informations utiles à l’échange.
- **08:35 — Protéger avec TLS** : vérifier l’identité du serveur, chiffrer les données en transit et contrôler leur intégrité. Le certificat est examiné pour les noms couverts, les dates et la chaîne de confiance. L’analogie des peintures illustre l’accord sur un secret sans l’envoyer directement.
- **13:55 — Examiner le certificat** : d’abord dans le navigateur, puis avec OpenSSL. La démonstration distingue une connexion TLS et la lecture des champs du certificat avec `x509`.
- **18:27 — Introduire curl** : outil utilisable comme client HTTP ; libcurl permet à d’autres logiciels d’utiliser ses fonctions de transfert.
- **20:18 — Relier le trajet** : `curl -v` est utilisé sur la racine du site en HTTP, puis en HTTPS. La seconde observation ajoute notamment la négociation TLS avant l’échange HTTP.

## Notions à retenir

- DNS trouve une destination ; il ne transporte pas ensuite les pages du site.
- Une résolution DNS réussie ne prouve ni la connexion au port, ni la validation TLS, ni le bon fonctionnement de l’application.
- HTTPS associe HTTP et TLS. Le chiffrement ne remplace pas la vérification de l’identité du serveur.
- Envoyer le nom en SNI avec `-servername` aide le serveur à choisir son certificat ; cela ne contrôle pas la correspondance du certificat au nom demandé.
- Lire un certificat n’est pas valider la connexion. Les [commandes de référence](commandes.md) conservent les contrôles explicites de nom et de confiance du deck.

## Pour reprendre l’observation

Lire les étapes dans l’ordre : résolution, connexion au port, TLS pour HTTPS, puis réponse HTTP. Les IP, certificats et sorties peuvent changer ; ce sont les observations du moment qui comptent. N’ajoute pas d’identifiants à un essai HTTP et ne désactive pas la vérification TLS pour masquer une erreur.

Le proxy inverse et la base de données sont développés en vidéo 2.3.
