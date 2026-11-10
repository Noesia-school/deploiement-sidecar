# Cadrer et choisir son déploiement

Les repères détaillés sont disponibles pour :

- [3.1 — Cadrer le service : exigences et risques](01-service-production-et-risques/contenu.md)
- [3.2 — Comprendre les modèles d’hébergement et les responsabilités](02-modeles-hebergement-et-responsabilites/contenu.md)
- [3.3 — Choisir sans surdimensionner](03-choisir-sans-surdimensionner/contenu.md)
- [3.4 — Documenter dès le départ](04-documenter-des-le-depart/contenu.md)

## Vidéo 3.1 — Contenu couvert

**Cadrer les exigences et les risques.** Préparer la reprise avant la panne et relier ses conséquences à l’usage du service ; distinguer exigences fonctionnelles et non fonctionnelles, puis préciser les attentes avec le client. Identifier les risques, estimer leur probabilité et leur impact, discuter leur acceptabilité, choisir une réponse et prévoir les contrôles. La vidéo présente les quatre réponses — accepter, éviter, réduire, transférer — ainsi que la distinction délégation/transfert, le risque résiduel et la nécessité de réexaminer l’analyse. Un cas fictif de dépassement de budget LLM fait réfléchir aux arbitrages à anticiper sans imposer une solution unique.

## Vidéo 3.2 — Contenu couvert

**Répartir l’exploitation.** Comparer VPS, plateforme managée et environnement client selon les couches prises en charge, la liberté disponible et le travail d’entretien. Déléguer une base de données est possible sans déléguer toute l’application ; une interface comme Coolify simplifie les gestes sans remplacer l’exploitation. La vidéo distingue aussi construction à partir du code et livraison d’une image OCI, puis précise les rôles techniques, l’autorisation des interventions et la coordination entre acteurs.

## Vidéo 3.3 — Contenu couvert

**Choisir sans surdimensionner.** Un assistant documentaire fictif, distinct d’InterNote, relie simultanéité, dimensionnement, coût humain d’un incident, limites de l’offre, migration, TCO et dette technique. La vidéo distingue vertical et horizontal, prestation dédiée et SaaS mutualisé, puis recommande conditionnellement le managé pour ce cas. La proposition de l’agent reste à challenger ; un engagement critique demande les compétences et intervenants adaptés. La difficulté des écritures distribuées est laissée à approfondir avec le sidecar, sans enseignement de construction d’une architecture distribuée.

## Vidéo 3.4 — Contenu couvert

**Documenter dès le cadrage.** Distinguer documentation technique, PV des échanges et ADR des décisions ; confirmer les accords, relire les propositions de l’agent et conserver les raisons comme l’historique des choix. La démonstration structure la documentation d’InterNote, introduit le réflexe ADR puis applique le cadrage à un scénario fictif. Après discussion, cinq fiches distinguent SQLite, hébergement managé du monolithe, API IA économique, exploitation/reprise et stockage objet pour les pièces jointes futures. Ce sont des orientations documentées, pas un déploiement ni des garanties vérifiées.

## Bilan du chapitre

Les quatre vidéos relient besoins, exigences, risques, responsabilités, proportion et documentation. Le chapitre est clos ; les repères détaillés couvrent 3.1 à 3.4. La documentation doit évoluer avec le projet, en distinguant faits, propositions, décisions acceptées et contrôles restant à réaliser. Aucun accord client réel ni résultat d’exploitation n’est déduit du scénario pédagogique.
