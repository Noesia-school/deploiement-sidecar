# 3.1 — Cadrer le service : exigences et risques

## Intention

Partir des usages, des besoins et des contraintes du client pour préciser les exigences du service, examiner ce qui pourrait les menacer et choisir des réponses proportionnées avant le déploiement. Un service exploitable n’est pas un service sans panne : la reprise se prépare avant l’incident.

## Repères dans la vidéo

Les horodatages sont approximatifs, issus de la transcription de la vidéo finale.

- **01:36 — Préparer la reprise** : la robustesse ne supprime pas toute possibilité de panne.
- **02:04 — Relier la panne à l’usage** : une matinée d’interruption peut suspendre un essai personnel, retarder une équipe ou toucher les engagements d’un client envers des tiers. Ce n’est pas une hiérarchie automatique : un outil interne de paie en fin de mois peut être très critique.
- **03:29 — Distinguer les exigences** : les fonctionnelles décrivent ce que le service doit faire ; les non fonctionnelles, comment et dans quelles conditions il doit fonctionner. La vidéo se concentre sur ces dernières.
- **04:15 — Préciser les attentes** : disponibilité, confidentialité, intégrité, reprenabilité, soutenabilité financière et humaine, conformité. Cette liste est un point de départ non exhaustif à discuter avec le client.
- **04:42 — Délimiter une contrainte** : « les dossiers doivent rester en Europe » demande de préciser les données et opérations concernées, notamment bases, sauvegardes, journaux et flux LLM.
- **05:31 — Rendre les exigences vérifiables** : par exemple, disponibilité du lundi au vendredi de 8 h à 18 h ou budget d’appels LLM de 500 € maximum par semaine. HDS et ISO 27001 sont évoqués comme exemples de demandes de conformité à clarifier, pas comme prescriptions universelles par secteur.
- **06:22 — Aborder les risques** : identifier les causes et conséquences possibles, estimer probabilité et impact, choisir une réponse, puis prévoir les contrôles. Certaines réponses précisent le cadrage et contraignent les choix ultérieurs ; prévoir un contrôle ne signifie pas l’avoir réalisé.
- **07:10 — Lire la matrice** : impact sur l’axe horizontal, probabilité sur l’axe vertical. Les situations illustrent deux dimensions distinctes, sans multiplication ni score chiffré.
- **08:26 — Comparer des situations** : divulgation de données publiques ou médicales, saturation, perte de statistiques secondaires, indisponibilité d’une API tierce. Les conséquences dépendent des données et du parcours réellement empêché.
- **10:11 — Discuter l’acceptabilité** : placer les risques ne suffit pas à décider. La frontière d’acceptabilité dépend des besoins et exigences convenus avec le client.
- **10:41 — Choisir une réponse** : accepter, éviter, réduire ou transférer. L’aparté à **11:38** distingue délégation d’une opération et transfert des conséquences ; la couverture contractuelle reste déterminante.
- **12:08 — Garder les limites en tête** : risque résiduel après traitement, analyse non exhaustive et réexamen lors d’un changement. À **12:52**, la roue de Deming, ou PDCA (Plan, Do, Check, Act), situe cette révision dans une boucle continue.
- **13:22 — Réfléchir au dépassement de budget** : un assistant public consomme 120 € en six heures, pour 500 € par semaine. Le client est injoignable et aucune consigne d’arbitrage n’a été prévue. La vidéo invite à faire pause avant de comparer les options et leurs conséquences.
- **15:12 — Conclure le cadrage** : exigences précises, risques examinés, réponses et limites, points encore ouverts. La conclusion annonce la répartition des responsabilités dans la prochaine vidéo et la documentation des arbitrages dans la dernière vidéo du chapitre, sans en développer ici la méthode.

## Notions à retenir

### Des exigences explicites, pas seulement des qualités générales

Une attente comme « disponible » ne dit pas encore quand le service doit fonctionner. Il faut la préciser selon l’usage pour pouvoir la vérifier. Les exemples d’horaires, de budget, de localisation et de conformité ne sont ni des exigences imposées à tous les projets ni des décisions prises pour InterNote. La soutenabilité concerne aussi l’effort humain nécessaire à l’exploitation, pas seulement la facture.

### Probabilité, impact et acceptabilité ne se confondent pas

La **probabilité** s’apprécie à partir de l’exposition, des protections et des indicateurs disponibles. L’**impact** concerne l’activité, les personnes, les données et les pertes financières possibles. L’**acceptabilité** se discute ensuite selon le besoin du client ; la matrice ne fixe pas de seuil universel.

Les positions des exemples sont des **hypothèses pédagogiques**, pas des fréquences sectorielles ni des estimations réutilisables telles quelles :

- Pour la divulgation, la comparaison suppose une même probabilité et fait varier l’impact entre données déjà publiques et dossiers médicaux. Elle ne démontre pas que tous ces services sont exposés de la même manière.
- La saturation illustre des demandes retardées ou refusées lors d’un pic de trafic imprévu ; son impact dépend du service.
- La perte de statistiques est présentée comme peu probable et peu dommageable dans un cas où ces données sont secondaires pour l’activité.
- Une API LLM indisponible peut bloquer tout le service ou seulement une aide à la saisie si la saisie manuelle reste possible. Ce contournement n’est pas supposé exister dans toutes les applications.

### Quatre réponses, sans promesse de risque zéro

- **Accepter** : assumer explicitement un risque jugé acceptable dans le contexte du projet.
- **Éviter** : renoncer à l’activité risquée ou contourner le besoin initial.
- **Réduire** : limiter le risque, par exemple en restreignant des accès trop larges ; cela demande généralement du temps ou de l’effort.
- **Transférer** : faire couvrir certaines conséquences par un tiers, par exemple une assurance, selon la couverture convenue.

Confier l’hébergement ou les sauvegardes à un prestataire ne supprime pas les conséquences d’une perte de données et ne transfère pas automatiquement toutes les responsabilités. Les responsabilités et les risques acceptés doivent être **convenus explicitement**, selon le contrat et les obligations applicables ; les annoncer ne suffit pas à s’en dégager.

Le **risque résiduel** est ce qui subsiste après traitement. Il faut aussi garder à l’esprit les risques non identifiés : l’analyse n’est jamais exhaustive. Un changement de besoins, d’exigences, d’usages ou de données appelle un nouvel examen.

## Pour reprendre la réflexion

Reprends le cas fictif du budget à **13:22** et fais pause avant la discussion des réponses. À rythme constant, 120 € en six heures correspondent à 20 €/h : les 500 € seraient atteints à 25 heures depuis le lancement, puis dépassés. C’est une projection conditionnelle, pas une prévision certaine.

Compare les conséquences de laisser tourner le service, limiter les demandes, désactiver l’IA ou couper le service. Les options de limitation et de fonctionnement sans IA ne sont possibles que si l’application les permet ; aucune autorisation ni capacité technique manquante n’est à inventer.

La leçon n’est pas de désigner une option universellement correcte ni de reprocher son choix à l’élève : sans consignes préalables, chaque option a des conséquences. Le cadrage doit anticiper l’arbitrage, y compris quand le client n’est pas joignable, et préciser qui peut décider et qui agit. Cette vidéo ne choisit ni hébergement ni procédure opérationnelle et ne comporte pas de commande à reproduire.

La [vidéo 3.2 — Comprendre les modèles d’hébergement et les responsabilités](../02-modeles-hebergement-et-responsabilites/contenu.md) reprend cette question de la répartition du travail entre hébergeur, intervenant et équipe du client.
