# Sécurité et limites du prototype

Monocore 0.4.1 est un prototype de navigation visuelle. Il n’applique pas une liste fermée de destinations après l’ouverture d’un site HTTPS. L’atelier Room 0.17.0 produit un brouillon non signé ; il n’active pas un filtre dans les exécutables existants.

La protection visée repose sur une sélection maintenue, une publication authentifiée et des restrictions effectives, pas sur l’absence d’une barre URL ni sur la seule présence d’une icône.

| Risque | État / traitement |
|---|---|
| Destination choisie par un tiers non membre | Accès de room et profil d’onglet vérifiés côté serveur |
| Le chef approuve à la place de l’équipe | Export soumis aux votes de tous les relecteurs figés |
| Rejeu d’un vote sur une ancienne révision | Révision de proposition vérifiée |
| SSRF lors d’une proposition | Aucune requête serveur vers l’URL fournie ; les refus d’IP explicites ne sont pas un filtre DNS complet |
| Domaine autorisé compromis ou trompeur | Non résolu par le vote ; surveillance et retrait nécessaires |
| Redirection hors carte | Non bloquée dans 0.4.1 ; futur contrôle Electron requis |
| Fausse carte importée | Pas d’import automatique ; futur mécanisme de signature requis |
| Identités multiples d’une même personne | Profils de session, pas de preuve d’identité civile ni d’expertise |
| Perte au redémarrage | Atelier en mémoire ; exporter explicitement avant fermeture |

Ne pas utiliser ces versions comme unique protection d’un enfant ou d’une personne accompagnée. Les termes « contrôlé » et « approuvé » doivent préciser par qui, quand, pour quel usage et avec quelles limites.

Pour signaler un problème, écrire à pascal@com-non-verbale.fr avec un exemple reproductible sans données réelles. Ne pas publier de secret ou de code de room dans une issue publique. Aucune promesse de délai de réponse ou d’audit indépendant n’est annoncée.

Références : documentation de sécurité Electron et recommandations OWASP sur les redirections, listées dans `docs/04-MODE-RESTREINT.md`.
