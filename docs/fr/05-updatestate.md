# Chapitre 5 — updateState : recompenses, penalites et frais d administration

`updateState`, appelee avec les donnees fournies par le keeper externe, calcule la variation nette des actifs du vault depuis la derniere mise a jour (`totalAssetsDelta`) puis la traite dans `_processTotalAssetsDelta`. Si la variation est positive (profit de staking), une partie proportionnelle (`feePercent`, module `VaultFee`) est convertie en nouvelles parts frappees au benefice du `feeRecipient`, l'administrateur du vault — le meme motif de frais de performance deja rencontre dans Compound v3 (`CometRewards`) et Rocket Pool.

Si la variation est negative (penalite de staking, par exemple une inactivite prolongee de validateurs), le code applique une regle de priorite remarquable : la penalite est d'abord imputee proportionnellement aux actifs deja **en file d'attente de sortie** (`_totalExitingAssets`, chapitre 6) avant d'affecter le reste du vault. Un deposant qui a deja demande a sortir n'echappe donc pas a une penalite survenue apres sa demande, mais celle-ci est repartie au prorata entre lui et les deposants restes dans le vault plutot que de retomber integralement sur l'un ou l'autre groupe.

Cette mise a jour ne se produit que lorsque le keeper a effectivement "recolte" (`harvested`) de nouvelles donnees pour ce vault : entre deux recoltes, `totalAssets` reste inchangee et aucune part de frais n'est frappee, une cadence de mise a jour periodique plutot que continue.

[Chapitre suivant : VaultEnterExit, la file d attente de sortie](06-exitqueue.md)
