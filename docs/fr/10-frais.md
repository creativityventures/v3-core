# Chapitre 10 — VaultFee : les frais d administration, plafonnes et delai de reduction

`setFeePercent`, reservee a l'administrateur du vault, fixe la part des profits reversee au `feeRecipient` (chapitre 5), plafonnee a un maximum global fixe par la gouvernance du protocole (`_maxFeePercent`, commun a tous les vaults). Chaque vault choisit donc librement son propre taux de frais, dans une fourchette autorisee, plutot que de se voir imposer un taux unique par le protocole.

Augmenter les frais est immediat, mais le code impose une verification particuliere lors de la creation du vault (`isVaultCreation`) par rapport a une modification ulterieure : ce traitement distinct refere au fait qu'un taux de frais eleve fixe des la creation est visible par tout deposant potentiel avant meme son premier depot, alors qu'une augmentation ulterieure affecterait des deposants deja engages sans qu'ils l'aient anticipee.

`setFeeRecipient` permet de changer l'adresse qui percoit ces frais independamment du taux lui-meme, separant la question de "combien" de celle de "qui" — une adresse de tresorerie multisig, un contrat de distribution automatique, ou toute autre destination choisie par l'administrateur du vault.

[Chapitre suivant : VaultSubVaults, composer des vaults de vaults](11-subvaults.md)
