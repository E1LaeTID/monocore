# Monocore

**[Découvrir com-non-verbale.fr →](https://com-non-verbale.fr/)**

[Présentation et téléchargements de Monocore](https://com-non-verbale.fr/monocore) · [Communication en équipe avec la Room](https://com-non-verbale.fr/equipes)

Ce dépôt présente la conception et l’évolution de Monocore. Le site com-non-verbale.fr réunit la présentation du service, les démonstrations disponibles et les retours des groupes.

> **État du dépôt : documentation initiale.** Le code des deux applications et les exécutables restent dans les archives livrées séparément ; ils ne sont pas encore importés dans ce dépôt. Les versions et validations ci-dessous décrivent ces archives, pas des exécutables publiés ici.

**Le navigateur non verbal. Une carte de services préparée pour les personnes qui l’utilisent.**

Pour rejoindre un lieu, une carte montre des repères et des chemins. Sur le Web, Monocore applique cette idée aux services en ligne : choisir une famille de pictogrammes, explorer ses sous-catégories, puis rejoindre une destination.

Il devient possible de retrouver un service sans mémoriser son adresse ni saisir une recherche. Les URL continuent à fonctionner en dessous de l’interface. Les navigateurs habituels proposent déjà favoris et protections : Monocore ajoute une organisation visuelle du parcours et, dans cette nouvelle variante Room, une préparation collective des destinations.

## Deux projets complémentaires

| Composant | Fonction disponible | État |
|---|---|---|
| `monocore/` | Application Electron, carte sans barre de saisie URL, catalogue local | Démonstration 0.4.1 |
| `ordia-room/` | Service com-non-verbale, échanges et disponibilités en équipe | Base 0.16.2 conservée |
| Room : atelier de navigation | Proposer une URL, recueillir les décisions, exporter les destinations approuvées | Prototype ajouté, 0.17.0 |
| Monocore restreint | Importer une carte authentifiée et bloquer les destinations non prévues | À développer et à auditer |

La démonstration Monocore compte 24 familles, 171 sous-catégories et 489 références éditoriales. Chacune des sous-catégories contient au moins trois domaines distincts. Ces références ne constituent pas une liste de partenaires ni de services certifiés ; les accès peuvent évoluer depuis leur contrôle ponctuel.

## À quoi cela peut servir ?

- **Arriver dans un pays** : retrouver des services locaux choisis avec un organisme d’accueil — transport, démarches, apprentissage linguistique, soins. Le pays est un contexte choisi, pas une autorisation administrative déduite automatiquement.
- **Apprendre ou naviguer accompagné** : préparer avec l’enfant ou la personne concernée une carte adaptée aux activités prévues, puis tester la compréhension des repères.
- **Organiser un groupe** : regrouper les services utiles à un objectif et examiner ensemble les destinations avant de distribuer la carte.

**La promesse est de mieux s’orienter et de réduire les choix non vérifiés. Ce prototype ne supprime pas le risque d’arnaque.** Un site approuvé peut être trompeur, compromis ou changer. La version actuelle laisse aussi suivre des liens HTTPS hors du catalogue. Elle n’est donc pas encore un contrôle parental, un navigateur verrouillé ou un dispositif de sécurité certifié.

## Essayer

### Carte Monocore

Avec Node.js installé :

```sh
cd monocore
npm ci
npm start
```

Sous PowerShell, employer `npm.cmd`. Pour l’aperçu dans un navigateur habituel, ouvrir `monocore/ui/preview.html`. Les liens y ouvrent des onglets habituels.

Les distributions Windows, Linux et macOS de la démonstration 0.4.1 ont été préparées séparément. Elles ne contiennent pas le nouvel atelier Room et ne sont pas reconstruites dans ce dossier. Voir [les instructions de packaging](monocore/docs/CONSTRUIRE_DISTRIBUTIONS.md). Aucun lien de release GitHub n’est inventé dans ce dépôt préparatoire.

### Room et atelier des destinations

```sh
cd ordia-room
npm ci
npm start
```

Ouvrir `http://localhost:8100`, démarrer une room, inviter un autre profil et confirmer la lecture de l’introduction. Dans la room, déplier **« Monocore · Préparer la carte de navigation du groupe »**.

1. Proposer le nom du service, son URL HTTPS et la raison de son ajout.
2. Les profils présents au moment de la proposition deviennent les relecteurs de cette proposition.
3. Chacun approuve, émet une objection ou s’abstient. L’abstention ne vaut pas accord.
4. Le responsable peut exporter les destinations approuvées par tous les relecteurs. Il ne peut pas passer outre un vote manquant ou une objection.
5. Le fichier exporté reste un **brouillon JSON non signé**, non importé automatiquement dans Monocore.

Tout le nouvel atelier reste en mémoire dans la room : aucune nouvelle table ni inscription commerciale n’est ajoutée. L’atelier est perdu à la fermeture, à l’expiration ou au redémarrage du serveur. Les stockages des bilans déjà existants conservent leurs règles propres.

## Lire la documentation

- [Comprendre l’intérêt de la carte](docs/01-EXPLIQUER-LA-CARTE.md)
- [Parcours et règles de la Room](docs/02-ROOM-VALIDATION.md)
- [Architecture et endpoints](docs/03-ARCHITECTURE-API.md)
- [Conception de la future navigation restreinte](docs/04-MODE-RESTREINT.md)
- [Identifiants, domaines et pictogrammes](docs/05-IDENTIFICATION-DOMAINES.md)
- [Feuille de route et essais utilisateurs](docs/06-ROADMAP.md)
- [Préparer la publication sur GitHub](docs/07-PUBLICATION-GITHUB.md)
- [Sécurité et limites](SECURITY.md)
- [Contribuer](CONTRIBUTING.md) · [Périmètre des licences](LICENSES.md)

Contact : [pascal@com-non-verbale.fr](mailto:pascal@com-non-verbale.fr).
