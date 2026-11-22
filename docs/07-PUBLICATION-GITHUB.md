# Préparer le dépôt GitHub

Ce dossier est prêt à être relu et placé dans le dépôt choisi. Le dépôt privé E1LaeTID/monocore a été créé et cette documentation y est déposée. Les sources applicatives et les releases restent à importer ; aucune protection de branche n’est configurée par cette documentation. Le nom Monocore existe aussi dans des projets indépendants : ne pas les confondre avec celui-ci.

## Avant la première publication

1. Conserver `README.md`, `docs/`, `CONTRIBUTING.md`, `SECURITY.md` et `.github/` à la racine.
2. Conserver les deux composants `monocore/` et `ordia-room/` dans leurs dossiers. Ne pas envoyer `node_modules`, fichiers `.env`, exports de participants ou exécutables dans les commits.
3. Définir les droits de redistribution des pictogrammes et du service Room. La licence Monocore existante exclut les ressources graphiques et éléments tiers. Voir `LICENSES.md` ; l’archive n’impose pas une nouvelle licence au service Room.
4. Remplacer les configurations d’exemple comportant vos identifiants d’infrastructure par des valeurs fictives avant un dépôt public. Tout secret précédemment partagé ou publié doit être remplacé auprès du service concerné ; supprimer une ligne du dernier commit ne retire pas un secret de l’historique.
5. Lancer les tests dans chaque composant. Les tests MySQL complets demandent une instance de test ; ne jamais pointer les tests vers la production.
6. Ajouter les installateurs aux releases choisies ou à l’hébergement de téléchargements ; conserver leur version et les empreintes. Ne pas annoncer les anciens exécutables comme intégrant l’atelier 0.17.0.

## Mise en ligne, depuis un dossier local neuf

Créer le dépôt dans votre compte GitHub avec la visibilité choisie. Depuis la racine de ce dossier :

```sh
git init
git add .
git commit -m "Document Monocore and add collaborative destination review"
git branch -M main
```

Ajouter ensuite l’URL réelle du dépôt comme remote `origin`, puis pousser la branche `main`. Ne pas réutiliser une URL de dépôt appartenant à un tiers. Si le dépôt existe déjà, travailler sur une branche dédiée à partir de sa version actuelle et ouvrir une pull request plutôt que remplacer son historique.

## Gouvernance à configurer sur GitHub

Protéger la branche de publication, demander une revue, limiter les droits de release et protéger les clés de signature hors dépôt. Les contributions peuvent suggérer des destinations ; elles ne doivent pas publier automatiquement le catalogue officiel. Un fork reste possible selon les licences et ne doit pas être présenté comme une version officielle.

Les demandes publiques ne doivent contenir aucun token, code de room, liste d’enfants, contact privé ou détail de santé. Un signalement de sécurité passe par le contact indiqué dans `SECURITY.md`.
