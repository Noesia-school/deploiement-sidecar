# Conteneuriser une application avec Docker

Chapitre pas encore publié.

Les axes ci-dessous donnent les grandes lignes envisagées ; leur ordre et leur regroupement pourront évoluer.

**Comprendre ce que transporte un conteneur.** Le chapitre distinguera l’application, ses dépendances, l’image qui les rassemble et le conteneur qui les exécute. Docker sera situé comme l’outil utilisé pour construire et manipuler une image au format OCI, réutilisable dans des environnements compatibles. Ce repère permettra de comprendre ce qui est préparé une fois et ce qui dépend encore du lieu d’exécution.

**Préparer une image identifiable.** La construction partira d’une application qui fonctionne localement et d’un Dockerfile préparé avec l’aide de l’IA, puis relu et vérifié. L’attention portera sur les fichiers réellement embarqués, la séparation entre image, configuration et secrets, ainsi que l’identification de la version publiée dans un registre. L’objectif sera de pouvoir reprendre le même artefact ailleurs et vérifier son démarrage avec une configuration fournie à l’exécution.

**Décrire un système avec ses dépendances.** Docker Compose servira à relier l’application à un service de données, à leur réseau et aux volumes nécessaires. Le chapitre distinguera le cycle de vie des conteneurs de celui des données persistantes et reliera la description du système à un schéma compréhensible. L’état des services et leurs journaux aideront à interpréter les erreurs de configuration, sans transformer le parcours en catalogue de commandes.
