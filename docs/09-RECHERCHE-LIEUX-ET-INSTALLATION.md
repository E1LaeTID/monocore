# Monocore 0.5.1 — recherche des lieux et installation

## Choisir un lieu en quelques actions

Ouvrir le bouton horloge du bandeau, saisir une ville ou un pays et cliquer le résultat. Le choix active l’horloge correspondante. Pour l’actuel, sélectionner un lieu désactive le suivi du fuseau de l’appareil ; il reste possible de le réactiver avec sa case.

Les résultats affichent un décalage UTC signé et complet (UTC+01:00, UTC-05:00, UTC+05:30), ainsi que l’écart avec l’horloge actuelle. Un pays peut afficher plusieurs fuseaux : il n’est jamais réduit arbitrairement à celui de sa capitale. Les homonymes indiquent pays et région. Une recherche partiellement saisie doit être confirmée par un résultat, ou effacée pour conserver le réglage précédent.

Les accents, la casse et les séparateurs sont normalisés. Le dictionnaire reprend les noms alternatifs de GeoNames et les noms de pays dans plusieurs langues. Quelques fautes proches peuvent être proposées explicitement comme suggestions ; elles ne sont pas sélectionnées automatiquement. Le choix direct du fuseau reste accessible si un lieu manque.

## Couverture du dictionnaire

237338 villes et localités ; 1269451 noms/variantes en entrée ; 252 fiches de pays/territoires, y compris des codes historiques présents dans les métadonnées, et 419 identifiants de fuseaux source. Les noms de pays proviennent aussi des données ICU/CLDR du runtime et de quelques alias explicites.

Source : GeoNames cities500, extraction du 22 novembre 2026. Ce jeu couvre les localités de plus de 500 habitants et certains sièges administratifs ; il ne contient pas toutes les villes, tous les villages ou toutes les variantes du monde. Les données sont fournies sans garantie d’exhaustivité ni d’exactitude. Les fuseaux non reconnus par le moteur local ne sont pas proposés.

La recherche est hors ligne, dans un worker lorsque disponible ; l’aperçu local peut utiliser un repli sur le thread principal si le navigateur refuse les workers file://. Le dictionnaire est chargé lors de la première ouverture des réglages. Le premier chargement peut demander quelques secondes. Les saisies ne sont pas envoyées à une API distante et aucune position géographique n’est demandée.

Licence et attribution : LICENSE-GEONAMES.txt. Rapport des sources et empreintes : PLACES-BUILD.json.

## Mise à jour Windows

Le nouvel installateur détecte les installations enregistrées pour le compte Windows courant, dont l’ancienne installation 0.5.0. Après l’accueil, deux choix :

- Mettre à jour / réinstaller une installation existante : choisir son dossier dans la liste ; les fichiers applicatifs sont remplacés et le profil reste conservé.
- Nouvelle installation indépendante : choisir un dossier vide différent. La copie possède ses raccourcis, son entrée de désinstallation et un profil distinct. Les autres installations sont conservées.

Les copies indépendantes créées par ce nouvel installateur sont aussi enregistrées et pourront être choisies pour une mise à jour suivante. Les installations manuelles sans inscription dans le registre ne sont pas découvertes automatiquement. Une mise à jour interactive vers une version antérieure est refusée ; une copie indépendante reste possible. Fermer toutes les fenêtres Monocore avant l’installation. Aucun processus n’est tué automatiquement.

Les profils sont conservés lors d’une désinstallation. L’installateur ne supprime que les fichiers qu’il a installés, sans effacer récursivement un dossier choisi par l’utilisateur. L’ancienne copie reste disponible si l’option indépendante a été retenue.

Il s’agit de l’installation Windows avec assistant, pas d’un mécanisme de mise à jour automatique à distance. Sur macOS, remplacer l’application ; sur Linux, remplacer l’AppImage. Les paquets restent non signés et la version macOS non notariée. L’assistant est compilé, mais son parcours graphique doit encore être testé sur Windows.

## Reconstituer le dictionnaire et l’installateur

Télécharger depuis https://download.geonames.org/export/dump/ les fichiers cities500.zip, countryInfo.txt et admin1CodesASCII.txt dans un dossier brut.

```
python scripts/build-places.py CHEMIN_DOSSIER_BRUT scripts/place-inputs/zone.tab
```

Le fichier de noms de pays fourni dans scripts/place-inputs est utilisé si le dossier brut n’en contient pas. Le rapport enregistre les empreintes des entrées disponibles. Pour une évolution complète des noms de pays et de la cartographie IANA, mettre aussi à jour ces instantanés avec leur provenance. Respecter la licence GeoNames CC BY 4.0.

Après création de win-unpacked avec electron-builder :

```
python build-tools/prepare-nsis.py ../executables
```

Puis compiler avec makensis le fichier monocore-installer.nsi placé dans ../executables. Le générateur inclut la liste exacte des fichiers à retirer lors de la désinstallation.
