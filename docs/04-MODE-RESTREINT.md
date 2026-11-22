# Future variante restreinte : exigences avant diffusion

**Spécification, non implémentée dans les exécutables 0.4.1.** Retirer la barre d’adresse ne bloque pas les liens, redirections, fenêtres ou sous-ressources des sites. Le prototype actuel autorise les navigations HTTPS après l’ouverture d’une référence.

## Séparer trois décisions

1. **Le groupe choisit** les services qu’il veut proposer pour son objectif.
2. **Une autorité de publication contrôle** les domaines et publie une carte signée, datée, révocable et de portée explicite.
3. **L’application applique** la carte et bloque les sorties non autorisées, sans jamais faire confiance à un drapeau `approved` envoyé par une page web.

Le responsable d’un groupe ne devient pas automatiquement un vérificateur de sécurité. Une liste approuvée par vote peut encore être mauvaise. L’autorité de confiance et ses règles devront être choisies par la structure utilisatrice et expliquées à l’utilisateur.

## Contrat minimal d’une carte publiée

Émetteur et clé de confiance, identifiant de carte, révision monotone, période de validité, contexte choisi (territoire, langue, objectif), destinations, schémas HTTPS, hôtes exacts et éventuels chemins autorisés, domaines auxiliaires justifiés, preuves de contrôle, mécanisme de retrait et version minimale du client. L’export Room ne remplit pas encore ce contrat.

Le client doit vérifier la signature et refuser les versions expirées ou non autorisées. La clé privée ne doit jamais être livrée dans le client ou le dépôt. Une empreinte seule n’identifie pas l’éditeur. Une révocation ne peut pas être instantanée sur un appareil hors ligne : définir la durée maximale de confiance hors ligne et bloquer à son échéance.

## Contrôles dans Electron

- Centraliser les décisions dans le processus principal, pas dans le rendu distant.
- Valider l’URL au chargement initial et à chaque nouvelle navigation, redirection, ouverture de fenêtre et accès à l’historique ; tester également les frames et changements de chemin dans un même document.
- Comparer des composantes URL normalisées : schéma, hôte exact, port et portée du chemin. Ne pas utiliser une simple recherche de texte dans l’adresse.
- Ne pas autoriser automatiquement tous les sous-domaines. Afficher l’hôte normalisé au relecteur ; traiter les domaines internationalisés et les caractères ressemblants.
- Définir séparément les origines nécessaires aux ressources (CDN, médias, authentification) et les destinations accessibles à la personne. Une exception technique ne doit pas devenir une sortie de navigation libre.
- Garder sandbox, isolation des contextes, vérification TLS, absence d’accès Node des sites et refus des protocoles externes non autorisés.
- Tester liens depuis iframes, formulaires, popups, redirections ouvertes, authentification tierce, téléchargements et appels au navigateur système.
- Définir le comportement en cas d’exception : expliquer le blocage, permettre de demander une revue, jamais approuver silencieusement une nouvelle destination.

Le périmètre doit préciser si la restriction concerne les destinations de navigation ou tous les échanges réseau. Ce ne sont pas les mêmes garanties : un site autorisé peut charger des contenus tiers ou transmettre des données.

## Limites à conserver dans le discours

Une carte ne protège pas d’un contenu trompeur sur un domaine autorisé, d’un organisme malveillant, d’une compromission du terminal, d’un partage de données volontaire ou d’une fraude par téléphone. L’open source permet un audit et des variantes, pas une immunité. Le mode ne bloque pas les autres applications de l’ordinateur sans dispositifs système supplémentaires.

Pour les personnes accompagnées, conserver un moyen d’obtenir de l’aide, de comprendre qui a choisi la carte et de demander une modification. Ne pas transformer l’accompagnement en collecte de nationalité, de santé ou de suivi détaillé de navigation par défaut.

## Références techniques primaires

- https://www.electronjs.org/docs/latest/tutorial/security
- https://www.electronjs.org/docs/latest/api/web-contents
- https://cheatsheetseries.owasp.org/cheatsheets/Unvalidated_Redirects_and_Forwards_Cheat_Sheet.html
