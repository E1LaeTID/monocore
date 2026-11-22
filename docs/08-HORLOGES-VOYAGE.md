# Monocore 0.5.0 : repères de voyage

La carte, ses familles et le catalogue ne changent pas. Le bandeau supérieur ajoute au plus trois positions : origine, actuel et prochaine destination. La position actuelle reste active ; les deux autres sont facultatives. L’icône horloge ouvre leurs réglages.

Choisir un nom de lieu et son fuseau IANA. Pour l’actuel, le suivi du fuseau de l’appareil est activé par défaut ; il peut être désactivé pour un choix manuel. L’origine conserve son fuseau même quand l’appareil change de fuseau. Aucune géolocalisation n’est demandée.

Le bandeau reste visible dans la carte, les listes, la soumission et pendant l’ouverture des sites. Les réglages s’ouvrent par-dessus l’interface locale : la vue web native est masquée temporairement, puis réaffichée sans rechargement quand le dialogue se ferme. Échap ferme les réglages sans quitter le site.

Les trois heures sont calculées pour le même instant avec Intl.DateTimeFormat. Les dates peuvent différer. J+1/J−1 compare les dates civiles au fuseau actuel. Certains couples de fuseaux à proximité de la ligne de changement de date peuvent présenter un écart de deux dates ; cet écart est affiché, pas tronqué.

Les dates de réservation ne sont ni saisies ni converties automatiquement dans cette version. Vérifier la date, le fuseau et les conditions indiqués par le prestataire. L’appareil fournit l’heure de référence : une horloge système fausse produit une heure fausse. Les changements saisonniers suivent la base de fuseaux du moteur Electron embarqué.

Réglages : stockage local du profil applicatif, clé monocore.travel-clocks.v1. Ils ne sont pas envoyés au site, à la Room ou à un service marketing. Fermer l’application conserve ces réglages si le stockage du profil est disponible. Supprimer le profil ou réinstaller en supprimant les données peut les effacer.

Les horloges ne certifient aucun site ni domaine. Le filtrage des URL et des redirections reste à développer. Aucun composant de validation collective n’est ajouté aux binaires 0.5.0.
