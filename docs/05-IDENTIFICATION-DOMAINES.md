# Domaines et repères non verbaux

## Ne pas confondre les identifiants

| Élément | Rôle |
|---|---|
| Icône de famille | Repère commun à plusieurs services |
| Identifiant du domaine | Référence unique dans un registre déterminé |
| Identifiant de destination | URL ou parcours précis d’un service |
| Identifiant de carte | Ensemble publié pour un contexte et une période |

Les icônes de catégories ne peuvent pas, à elles seules, garantir l’unicité de millions de domaines. Un identifiant stable de registre pourra être représenté par un signe composite. La lisibilité et la distinction de ces signes doivent être testées ; cette représentation n’est pas encore normalisée.

## Procédure envisagée

Le représentant propose le domaine et pose un marquage expérimental dans son code. Le service émet un défi aléatoire lié à la demande, au domaine et à une échéance, puis contrôle sa restitution. La présence d’un signe ou d’une balise copiée ne suffit pas. Le contrôle du domaine ne prouve ni la qualité ni l’habilitation du service.

Le dossier doit distinguer : propriétaire ou représentant, usage proposé, domaine canonique, redirections constatées, éventuels domaines auxiliaires, droits graphiques, date de revue et échéance. Un changement substantiel entraîne une nouvelle revue. Une carte publiée conserve une révision permettant de retirer une destination.

Le marquage peut utiliser `meta name="monocore:..."` comme convention applicative expérimentale. Il ne constitue pas un nouveau standard HTML reconnu, une certification ou une autorisation de publication automatique.

Un même domaine peut proposer plusieurs chemins d’accès dans des catégories différentes. Inversement, un même groupe commercial peut contrôler plusieurs domaines : aucune équivalence ni autorisation croisée ne doit être déduite automatiquement.
