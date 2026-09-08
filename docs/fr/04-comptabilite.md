# Chapitre 4 — VaultState : la comptabilite par parts et le taux de change

Comme Rocket Pool ou Morpho Blue deja documentes pour ce compte, chaque vault StakeWise v3 utilise une comptabilite par parts plutot qu'un solde direct : `_totalAssets` et `_totalShares` definissent un taux de change commun a tout le vault, `convertToShares`/`convertToAssets` traduisant l'un vers l'autre. `getShares(compte)` retourne le nombre de parts d'un deposant, sa valeur en actifs se deduisant de ce taux de change courant plutot que d'etre stockee directement.

`totalAssets()` ne reflete pas necessairement le solde reel detenu par le contrat a un instant donne : une partie des actifs peut etre engagee sur la Beacon Chain via des validateurs actifs (chapitre 7), invisible depuis un simple `balanceOf` du contrat. C'est le role du "keeper" (un oracle externe au protocole, hors du detail de ce parcours) de rapporter periodiquement l'etat reel agrege du vault, y compris les recompenses et penalites de staking, via `updateState` (chapitre 5).

`donateShares` permet a n'importe qui d'envoyer volontairement des parts au vault sans les racheter, une facon simple d'augmenter la valeur de toutes les parts existantes — par exemple pour subventionner un vault ou compenser manuellement une perte, en dehors du cycle normal de recompenses.

[Chapitre suivant : updateState, recompenses et penalites priorisees](05-updatestate.md)
