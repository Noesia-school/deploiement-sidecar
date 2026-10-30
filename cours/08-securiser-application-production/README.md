# Comprendre et réduire les risques de sécurité

Chapitre pas encore publié.

Les axes ci-dessous donnent les grandes lignes envisagées ; leur ordre et leur regroupement pourront évoluer.

**Examiner l’exposition du système.** Le chapitre reprendra les composants et les accès du service pour relier les chemins possibles aux conséquences d’une compromission. Les protections déjà appliquées seront examinées avec leurs effets, leurs limites et les risques qui subsistent. Cette lecture concernera aussi les données et les copies de sauvegarde qu’un accès compromis pourrait atteindre.

**Relier les droits aux besoins.** Les accès des personnes et des services seront examinés selon leur utilité, leur portée et leur durée. Le moindre privilège permettra de distinguer les opérations nécessaires au fonctionnement de l’application des droits d’administration. Le parcours des secrets, leurs copies possibles et les conditions de récupération ou de retrait des accès compléteront cette compréhension.

**Suivre les données et leurs destinataires.** Le parcours reliera l’application, la base, les fichiers, les sauvegardes et les échanges avec le fournisseur de modèle. Il permettra d’examiner ce qui est transmis, conservé ou supprimé, sans supposer que l’effacement d’une référence supprime toutes les copies. Les options de recours à une API externe ou d’hébergement du modèle seront rapprochées des contraintes du projet, des conditions réelles des offres et des capacités d’exploitation.

**Comprendre les composants et organiser la veille.** La chaîne logicielle sera abordée à travers l’origine du code, ses dépendances et la version réellement exécutée. La veille confrontera ces informations aux avis officiels et aux fins de support pour identifier un besoin d’intervention contextualisé. Une alerte sera distinguée d’un risque effectivement applicable, et les conclusions conserveront leurs sources, leurs incertitudes et les suites à examiner.
