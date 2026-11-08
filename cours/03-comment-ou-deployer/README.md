# Cadrer et choisir son déploiement

Les repères détaillés sont disponibles pour :

- [3.1 — Cadrer le service : exigences et risques](01-service-production-et-risques/contenu.md)
- [3.2 — Comprendre les modèles d’hébergement et les responsabilités](02-modeles-hebergement-et-responsabilites/contenu.md)

## Vidéo 3.1 — Contenu couvert

**Cadrer les exigences et les risques.** Préparer la reprise avant la panne et relier ses conséquences à l’usage du service ; distinguer exigences fonctionnelles et non fonctionnelles, puis préciser les attentes avec le client. Identifier les risques, estimer leur probabilité et leur impact, discuter leur acceptabilité, choisir une réponse et prévoir les contrôles. La vidéo présente les quatre réponses — accepter, éviter, réduire, transférer — ainsi que la distinction délégation/transfert, le risque résiduel et la nécessité de réexaminer l’analyse. Un cas fictif de dépassement de budget LLM fait réfléchir aux arbitrages à anticiper sans imposer une solution unique.

## Vidéo 3.2 — Contenu couvert

**Répartir l’exploitation.** Comparer VPS, plateforme managée et environnement client selon les couches prises en charge, la liberté disponible et le travail d’entretien. Déléguer une base de données est possible sans déléguer toute l’application ; une interface comme Coolify simplifie les gestes sans remplacer l’exploitation. La vidéo distingue aussi construction à partir du code et livraison d’une image OCI, puis précise les rôles techniques, l’autorisation des interventions et la coordination entre acteurs.

## Suite du chapitre — Aperçu prévisionnel

Les axes ci-dessous restent les grandes lignes envisagées, pas des acquis détaillés dans ce compagnon ; leur ordre et leur regroupement pourront évoluer. Les vidéos disponibles ne choisissent pas encore l’hébergement d’un projet et ne développent pas la méthode de documentation des arbitrages.

**Choisir sans surdimensionner.** Le choix d’hébergement sera relié aux besoins actuels, à l’évolution plausible du service et aux compétences disponibles pour l’exploiter. Le coût sera examiné au-delà du prix affiché, en tenant compte du temps d’exploitation et des conséquences des raccourcis techniques. Il s’agira de retenir une solution proportionnée et de reconnaître les conditions qui pourraient conduire à la réviser.

**Documenter dès le cadrage.** La documentation sera envisagée comme un support de transmission qui explique le service, ses dépendances et les décisions prises. Elle conservera les raisons des choix, leurs limites, les hypothèses à confirmer et les raccourcis acceptés, sans contenir de secrets. Ce socle sera enrichi pendant le projet afin qu’une autre personne puisse comprendre le système et reprendre son exploitation.
