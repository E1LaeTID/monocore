# Validation du 22 novembre 2026

- Monocore 0.4.1 : 8 tests réussis, code de navigation non modifié.
- Room 0.17.0 : 54 tests, dont 47 réussis et 7 non exécutés car une instance MySQL de test n’est pas configurée. Aucun échec.
- Nouvel atelier : 4 tests couvrant normalisation HTTPS, refus des accès locaux explicites, unanimité, révisions, abstention, révocation, limites, isolation HTTP et mise à jour Socket.IO.
- Contrôle DOM ciblé : propositions et votes, séparation des rôles, absence de lien cliquable sur les propositions, contenu affiché comme texte.
- Contrôle de syntaxe JavaScript réussi.
- Sans fichiers de distribution locaux, les tests de téléchargement vérifient la réponse 404 attendue. Si les fichiers sont présents avec la taille du manifeste, le test vérifie le téléchargement partiel. Aucun exécutable n’est reconstruit ici.
- Aucun essai graphique complet ni audit de sécurité indépendant. Aucun import de carte signée ni filtrage Electron ajouté.
