# Construire Monocore 0.4.1
Les sources de navigation ne changent pas. La chaîne de packaging est isolée dans `build-tools`, pour que les utilisateurs du prototype source ne restaurent pas ces dépendances.

Depuis le dossier `monocore` :
```
npm ci --prefix build-tools
node build-tools/node_modules/electron-builder/cli.js --config build-tools/electron-builder.json --win --x64 --publish never
node build-tools/node_modules/electron-builder/cli.js --config build-tools/electron-builder.json --linux --x64 --publish never
node build-tools/node_modules/electron-builder/cli.js --config build-tools/electron-builder.json --mac --x64 --arm64 --publish never
```
Sous PowerShell, employer `npm.cmd`. Les téléchargements de la chaîne de packaging nécessitent Internet. Les distributions sont placées dans `../executables`. La signature et la notarisation macOS nécessitent un Mac et une identité Apple appropriée. La livraison actuelle est non signée ; les archives macOS contiennent une application .app. Les boutons web ne déclenchent aucune mise à jour automatique de l’application. L’icône système actuelle est celle d’Electron ; les pictogrammes et la navigation internes restent ceux du prototype.

Windows : installateur NSIS avec choix du dossier. Linux : AppImage x64, peut nécessiter les bibliothèques FUSE de la distribution. macOS : ZIP Intel x64 ou Apple Silicon arm64. Ces distributions ne remplacent pas une validation réelle sur chaque OS.

Documentation officielle : https://www.electron.build/docs/features/multi-platform-build/

## Installateur fourni dans cette livraison
L’installateur Windows fourni a été compilé directement avec NSIS à partir de `build-tools/monocore-installer.nsi`, car Wine n’est pas disponible dans l’environnement de construction Linux. Le script inclut les pages d’accueil, de choix du dossier et de fin, les raccourcis ainsi que la désinstallation. Sa désinstallation efface la liste explicite des fichiers installés et ne supprime pas récursivement un dossier arbitraire.

Pour le reproduire : générer `win-unpacked` avec electron-builder `--win --x64 --dir`, placer le script NSIS à côté de ce dossier, puis lancer `makensis monocore-installer.nsi` depuis ce même emplacement. NSIS doit être installé sur la machine de construction. Le script vise la liste des fichiers de la version 0.4.1 ; actualiser la liste de désinstallation si les fichiers embarqués changent.
