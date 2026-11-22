# Monocore — votre carte de navigation, vos repères de voyage

**Vous changez de pays. Retrouvez vos repères, aussi sur le Web.**

**[Découvrir et tester Monocore sur com-non-verbale.fr →](https://com-non-verbale.fr/monocore)**  
[Découvrir le service en équipe](https://com-non-verbale.fr/equipes) · [Site du projet](https://com-non-verbale.fr/)

À l’arrivée dans une ville, une carte aide à retrouver les transports, le logement et les services essentiels. Monocore transpose cette idée aux destinations en ligne : des familles de pictogrammes et des chemins visuels pour explorer les services utiles sans saisir une adresse dans une barre URL.

Le projet s’adresse notamment aux voyageurs, aux nouveaux arrivants et aux personnes qui souhaitent naviguer avec des repères plus simples dans leur propre pays. Les pictogrammes doivent être appris et testés avec les personnes concernées : ils ne constituent pas un langage universel automatiquement compris.

## Un premier cas concret : origine, position actuelle, prochaine destination

La démonstration **Monocore 0.5.1** ajoute un bandeau supérieur avec **une à trois horloges**, visibles pendant l’exploration de la carte et la consultation d’un site.

| Position | Repère affiché |
|---|---|
| Origine — facultative | Heure et date du fuseau de départ, conservé comme référence |
| Actuel — toujours affiché | Heure et date du fuseau de l’appareil ou d’un fuseau choisi manuellement |
| Prochaine destination — facultative | Heure et date du lieu que vous préparez |

Chaque horloge affiche une heure sur 24 h, une date complète, le fuseau et son décalage UTC. Un repère J−1/J+1 indique les différences de date par rapport à la position actuelle ; les cas extrêmes traversant la ligne de changement de date sont également pris en charge.

**Préparer un trajet entre Paris, New York et Tokyo devient un exemple concret : retrouver une destination sur la carte tout en gardant les dates locales à portée de regard.** Le bandeau aide à comparer les repères ; il ne réalise ni ne corrige une réservation. L’heure et le fuseau annoncés par le prestataire restent à vérifier.

Les réglages sont enregistrés sur l’appareil. Aucune géolocalisation, aucun compte et aucun appel à une API de localisation ne sont nécessaires aux horloges. Le fuseau de l’appareil n’est pas une preuve de votre emplacement et l’heure affichée dépend de son horloge système.

## Réglages simplifiés dans la version 0.5.1

Saisissez une **ville, un pays ou un décalage UTC**, puis choisissez le résultat. Les accents et noms alternatifs sont reconnus ; le pays et la région distinguent les homonymes. Les résultats indiquent `UTC+01:00`, `UTC-05:00` ou des décalages avec minutes, ainsi que l’écart avec l’horloge actuelle.

Le dictionnaire hors ligne adapte **237 338 villes et localités** de GeoNames cities500 et plus de **1,26 million de noms/variantes**. Il n’est pas exhaustif ; le choix direct du fuseau reste disponible. Attribution : [GeoNames, CC BY 4.0](https://download.geonames.org/export/dump/readme.txt).

L’installateur Windows propose **Mettre à jour / réinstaller** une installation enregistrée pour le compte courant, ou créer une **installation indépendante** dans un autre dossier avec son propre profil. L’assistant est compilé ; son déroulement graphique reste à valider sur Windows. Voir [le guide de recherche et d’installation](docs/09-RECHERCHE-LIEUX-ET-INSTALLATION.md).

## Garder le cap : la prochaine étape du projet

L’ambition est de proposer des cartes par destination, préparées pour un besoin, une langue et une durée : transports, démarches, hébergement, apprentissage, services de proximité. La personne pourrait rejoindre les services examinés sans devoir suivre une succession de liens inconnus.

Le futur mode restreint devra contrôler les adresses et les redirections, signaler un changement de destination et empêcher une sortie non autorisée. Son objectif est de réduire le risque de détournement du parcours et de demandes d’informations trompeuses. Ce filtrage doit être appliqué dans le navigateur, pas seulement représenté par un pictogramme.

**Aujourd’hui, le catalogue est une démonstration éditoriale, pas une distribution de destinations certifiées. Le blocage hors carte, la signature des cartes et la validation collective pour une diffusion fiable ne sont pas encore activés dans Monocore.** Une carte ne garantit pas l’absence de fraude et ne remplace pas les protections habituelles du navigateur ou de l’appareil.

## Ce qui est disponible, ce qui reste à construire

| Élément | État |
|---|---|
| Carte non verbale et catalogue de démonstration | Disponible : 24 familles, 171 sous-catégories, 489 références |
| Horloges et dates de trois positions au maximum | Disponible dans les distributions 0.5.1 livrées pour mise en ligne |
| Windows x64, Linux x64, macOS Intel et Apple Silicon | Distributions de démonstration non signées ; macOS non notarié |
| Service Room de com-non-verbale | Essai des échanges et disponibilités depuis le site |
| Atelier de revue collective des URL | Prototype distinct préparé dans l’archive Room 0.17.0 ; pas ajouté au site existant par cette mise à jour |
| Cartes de destination signées et révocables | À développer |
| Blocage des redirections et URL hors carte | À développer et à auditer |

Le dépôt GitHub contient actuellement la documentation. Les sources complètes et les distributions sont livrées séparément ; les téléchargements du site dépendent de leur installation par l’éditeur. Aucune release binaire GitHub n’est annoncée ici.

## Développeurs : construisons des Monocore pour les voyageurs

Nous invitons les développeurs, structures d’accueil et personnes concernées à tester ce premier parcours sur [com-non-verbale.fr](https://com-non-verbale.fr/monocore), puis à proposer des améliorations dans ce dépôt.

- Concevoir des cartes locales adaptées à des tâches concrètes et tester la compréhension des signes.
- Examiner des services de référence et leurs conditions d’accès sans les présenter comme partenaires sans accord.
- Définir un registre de domaines, des contrôles humains et une publication signée avec retrait des destinations obsolètes.
- Tester les redirections, les domaines ressemblants et les parcours d’authentification avant de présenter un mode comme restreint.
- Améliorer l’accessibilité, les langues et les retours des utilisateurs sans collecter leur navigation par défaut.

Le domaine actuel héberge la démonstration et les essais. Une évolution vers un service de cartes selon la destination reste à concevoir ; aucun nouveau domaine ni nouveau standard de balisage n’est déjà établi.

## Documentation

- [Horloges et dates du voyage](docs/08-HORLOGES-VOYAGE.md)
- [Comprendre la carte](docs/01-EXPLIQUER-LA-CARTE.md)
- [Room et revue collective](docs/02-ROOM-VALIDATION.md)
- [Architecture et endpoints](docs/03-ARCHITECTURE-API.md)
- [Exigences du futur mode restreint](docs/04-MODE-RESTREINT.md)
- [Identification des domaines](docs/05-IDENTIFICATION-DOMAINES.md)
- [Feuille de route](docs/06-ROADMAP.md)
- [Sécurité et limites](SECURITY.md) · [Contribuer](CONTRIBUTING.md) · [Licences](LICENSES.md)

Contact : [pascal@com-non-verbale.fr](mailto:pascal@com-non-verbale.fr).
