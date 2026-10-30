# Gérer les données, la persistance et les sauvegardes

Chapitre pas encore publié.

Les axes ci-dessous donnent les grandes lignes envisagées ; leur ordre et leur regroupement pourront évoluer.

**Conserver des fichiers sur le VPS.** L’ajout de pièces jointes permettra de relier les fichiers de l’application à un emplacement persistant sur le serveur. Leurs références en base et leur conservation devront rester cohérentes lorsque le conteneur est remplacé. Ce besoin prolongera les repères sur les volumes, sans confondre persistance et sauvegarde.

**Utiliser un stockage objet sur le managé.** Le chapitre abordera le stockage compatible S3 pour conserver les pièces jointes sans dépendre du stockage temporaire du conteneur. Les notions de bucket, d’objet, de clé et d’accès aideront à comprendre ce modèle, qui n’est pas simplement un disque monté. La même image applicative pourra ainsi être reliée à un autre mode de stockage par sa configuration.

**Définir ce qu’il faut préserver.** L’inventaire partira des données que le client doit pouvoir retrouver, de leurs liens et des conséquences d’une perte. Leur emplacement, leur volume et leur croissance plausible éclaireront les besoins de stockage et les temps de transfert. Les éléments reconstructibles seront aussi examinés, car leur récupération dépend encore de sources, d’outils et de temps disponibles.

**Choisir une protection proportionnée.** La stratégie de sauvegarde sera reliée à la perte de données acceptable et au délai de reprise attendu. Fréquence, durée de conservation, séparation des copies et protection des accès seront examinées ensemble. Les principes de copie hors serveur, de transferts et d’immuabilité aideront à comprendre ce qu’une protection couvre et les risques qui demeurent.

**Mettre en œuvre et suivre les sauvegardes.** L’IA pourra aider à adapter une procédure à l’architecture et au périmètre retenus, sans recevoir de secrets ni de données client. La relecture portera notamment sur les exclusions, les suppressions et les effets de l’automatisation. Le contrôle devra permettre de remarquer une sauvegarde manquante ou échouée, sans prendre un journal d’exécution pour une preuve de reprise.

**Éprouver la restauration.** La reprise sera envisagée sur une cible distincte pour préserver les données d’origine. Les contrôles porteront sur les contenus retrouvés, la cohérence entre base et pièces jointes et le fonctionnement de l’application. Les prérequis, la durée observée et les écarts avec les objectifs seront documentés pour rendre les limites de la procédure explicites.
