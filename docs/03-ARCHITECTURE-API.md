# Architecture et endpoints

## Organisation du dépôt

- `monocore/` : application locale Electron 0.4.1, catalogue et ressources.
- `ordia-room/` : site Node/Express, vues EJS, Socket.IO, accès existants aux bases.
- `ordia-room/models/NavigationReview.js` : URL, propositions, décisions, révisions, export.
- `ordia-room/routes/navigationRoutes.js` : identité, appartenance, limitations et opérations HTTP.
- `ordia-room/public/js/navigation-review.js` : interface de l’atelier.
- `docs/` : documentation commune, spécifications futures et publication.

Les nouvelles données sont attachées à la room en mémoire. Aucune requête SQL nouvelle n’est requise. Les bases existantes du service ne doivent pas être supprimées.

## API de l’atelier

Préfixe : `/api/v1/rooms/:roomId/navigation`. Toutes les opérations demandent le cookie `ordia_access`, un `X-Ordia-Tab` valide, l’appartenance à la room et la lecture de l’introduction. Les mutations sont soumises à la vérification d’origine existante.

| Méthode | Suffixe | Usage |
|---|---|---|
| GET | `/` | Lire les propositions et l’historique borné |
| POST | `/proposals` | Proposer `{title,url,reason}` |
| POST | `/proposals/:id/vote` | Voter `{choice,expectedRevision}` |
| POST | `/proposals/:id/revoke` | Retirer une proposition, responsable uniquement |
| GET | `/export` | Télécharger les destinations approuvées, responsable uniquement |

`choice` vaut `approve`, `reject` ou `abstain`. Une révision périmée retourne `409`. Un accès interdit retourne `403`, un profil absent `401/403`, une limite de capacité `429` selon le code concerné. Les POST de cet atelier sont limités à 35 par fenêtre de dix secondes et identité d’onglet ; ce garde-fou local ne remplace pas les limites d’un reverse proxy.

## Temps réel

Les mutations déclenchent le mécanisme `broadcast` existant. L’événement `room:state` inclut `navigation:{revision,proposals,audit}`. Le serveur vérifie la session et l’appartenance avant diffusion. Les clients non membres ne reçoivent pas ce contenu. Aucune nouvelle room publique Socket.IO n’est créée pour le catalogue.

## Exemple fictif d’export

```json
{
  "schema": "monocore-group-map-draft",
  "version": 1,
  "roomId": "identifiant-de-room",
  "groupName": "Atelier de démonstration",
  "revision": 3,
  "issuedAt": "2026-11-22T08:00:00.000Z",
  "expiresAt": "2026-11-22T12:00:00.000Z",
  "signed": false,
  "enforced": false,
  "destinations": [{
    "id": "identifiant-de-proposition",
    "title": "Service fictif",
    "url": "https://example.org/ecole",
    "origin": "https://example.org",
    "scope": "exact-url",
    "revision": 3,
    "reviewerCount": 2
  }]
}
```

L’exemple est illustratif, pas une preuve signée. `scope:exact-url` exprime la portée à examiner ultérieurement : il ne déclenche aucun filtrage actuel. Le futur format de carte de navigation doit rester distinct du format temporel `.tmap` tant qu’un contrat commun n’est pas défini.
