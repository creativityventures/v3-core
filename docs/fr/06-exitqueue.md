# Chapitre 6 — VaultEnterExit : une file d attente de sortie en deux etapes

Retirer des fonds d'un vault StakeWise v3 se fait en deux etapes distinctes, le meme motif que la file d'attente de retrait de Lido deja documentee pour ce compte. `enterExitQueue` convertit immediatement les parts du deposant en un `positionTicket` (un numero de position dans la file, calcule a partir du cumul historique des demandes de sortie) plutot que de rendre les actifs sur-le-champ : les parts sont brulees des cet instant, mais les actifs correspondants restent a percevoir plus tard.

Chaque appel a `_updateExitQueue` (declenche automatiquement par `updateState`, chapitre 5) traite autant de la file que les actifs disponibles du vault le permettent, dans l'ordre d'arrivee (FIFO) : les actifs libres, non engages dans des validateurs actifs, sont alloues aux demandes de sortie les plus anciennes d'abord. `getExitQueueIndex` et `calculateExitedAssets` permettent a un sortant de savoir, a partir de son `positionTicket`, si et combien d'actifs lui sont desormais dus.

`claimExitedAssets` finalise le retrait : une fois que la file d'attente a progresse au-dela du ticket du sortant, cette fonction transfere effectivement les actifs qui lui reviennent. Ce decouplage en deux etapes (sortie de la file puis reclamation) permet au vault de continuer a fonctionner normalement (nouveaux depots, nouvelles recompenses) pendant que les sorties en attente se resolvent progressivement, au rythme ou de nouveaux actifs deviennent disponibles.

[Chapitre suivant : VaultValidators, l enregistrement des validateurs](07-validators.md)
