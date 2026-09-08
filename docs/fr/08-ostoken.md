# Chapitre 8 — VaultOsToken : un jeton surcollateralise emprunte contre la position stakee

`mintOsToken` permet a un deposant de tout vault du protocole d'emprunter des osToken contre ses parts, sans jamais les retirer du vault : les parts continuent d'accumuler des recompenses de staking normalement, pendant que l'osToken emprunte devient un actif liquide utilisable ailleurs (echange, collateral dans un autre protocole...) — le meme principe qu'un CDP MakerDAO deja documente pour un autre compte, mais adosse a une position de staking productive plutot qu'a un simple depot de collateral inerte.

`_calcMaxOsTokenShares` plafonne le montant empruntable en fonction de la valeur des parts du deposant et d'un ratio de collateralisation fixe par la gouvernance du protocole (au niveau global, pas vault par vault) : emprunter au maximum de ce plafond expose la position a une liquidation si la valeur des parts sous-jacentes se degrade (penalite de staking) ou si le prix de l'osToken derive de son ancrage attendu.

`liquidateOsToken` et `redeemOsToken` sont les deux issues d'une position devenue trop risquee ou simplement remboursee : la liquidation, ouverte a n'importe qui des qu'une position depasse son ratio de collateralisation maximal, saisit des parts du vault au benefice du liquidateur ; le rachat (`redeemOsToken`) permet a un detenteur d'osToken d'echanger directement son jeton contre les parts sous-jacentes d'un vault, un mecanisme d'ancrage de prix supplementaire independant de la liquidation.

[Chapitre suivant : VaultMev et le partage du MEV](09-mev.md)
