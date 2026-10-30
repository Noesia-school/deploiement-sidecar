# Déployer sur une plateforme managée

Chapitre pas encore publié.

Les axes ci-dessous donnent les grandes lignes envisagées ; leur ordre et leur regroupement pourront évoluer.

**Situer la délégation à la plateforme.** Le chapitre précisera ce qu’une offre managée prend en charge et ce qu’il reste à configurer, vérifier et financer. Les notions de PaaS et de serverless aideront à lire les possibilités et les limites d’une offre, notamment sa capacité et sa facturation. Le parcours conservera l’image déjà construite, tout en situant les plateformes qui peuvent recevoir directement le code.

**Transposer le système local en service en ligne.** Les composants décrits localement seront rapprochés des ressources de la plateforme : application, service de données, connexions, configuration et secrets. La propriété du compte et des ressources sera prise en compte dès le déploiement. La vérification portera sur une fonctionnalité réelle utilisant les données, car une URL accessible ou un déploiement déclaré sain ne suffit pas à prouver le fonctionnement du service.

**Préparer les premiers contrôles d’exploitation.** Le raccordement du domaine et de HTTPS sera relié aux réglages du service, aux journaux et aux limites de consommation disponibles. Le chapitre distinguera une alerte de budget, une limite de capacité et un blocage effectif des dépenses. Un contrôle externe complétera les vérifications fonctionnelles, avec une attention à ce qu’il permet réellement d’observer sur la disponibilité et TLS.
