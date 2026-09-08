# Chapitre 9 — VaultMev : partager la valeur extraite par les proposants de blocs

Un validateur Ethereum percoit, en plus de la recompense de consensus classique, une part de la valeur extractible par les mineurs/validateurs (MEV — Maximal Extractable Value) via les pourboires de transaction et les paiements de constructeurs de blocs. `mevEscrow()` determine ou cette valeur MEV doit etre acheminee : soit vers un `SharedMevEscrow` commun a tous les vaults du protocole qui n'en ont pas de dedie, soit vers un `OwnMevEscrow` propre a un vault specifique s'il en a deploye un.

Un vault avec son propre escrow MEV recoit l'integralite du MEV genere par ses propres validateurs de facon isolee ; un vault utilisant l'escrow partage voit sa part de MEV calculee par le keeper au prorata de sa contribution, mutualisee avec tous les autres vaults dans la meme situation. Ce choix (escrow propre ou partage) est fait une fois au deploiement du vault et conditionne comment ses recompenses totales (chapitre 5) integrent cette composante MEV, generalement plus volatile que la recompense de consensus de base.

Separer le MEV de la recompense de consensus dans deux escrows distincts, plutot que de tout regrouper dans le solde du vault directement, permet au keeper de verifier et d'auditer chaque source de revenu independamment avant de les agreger dans le calcul de `totalAssetsDelta` du chapitre 5.

[Chapitre suivant : VaultFee, les frais d administration](10-frais.md)
