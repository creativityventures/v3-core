# Chapitre 1 — Presentation de StakeWise v3

StakeWise v3 est un protocole de liquid staking qui remplace le pool unique de sa version precedente par une multitude de **vaults** independants, permissionless : n'importe qui peut deployer son propre vault de staking, en choisir les parametres (prive ou public, avec liste blanche ou liste noire, avec ou sans jeton ERC20 enveloppant les parts), et en devenir l'administrateur qui percoit une part des recompenses. C'est le meme changement de paradigme, applique au liquid staking, que Morpho Blue applique au pret et emprunt (marches isoles et permissionless plutot qu'un pool unique gouverne) : StakeWise v3 remplace un pool central par une multitude de vaults independants.

Chaque vault suit sa propre comptabilite de parts, mais tous peuvent optionnellement emettre un second jeton transversal, l'**osToken** (Overcollateralized Staked Token), un actif liquide que l'on peut emprunter contre sa position stakee dans n'importe quel vault du protocole, un mecanisme proche d'un CDP mais adosse a une position de staking plutot qu'a un depot de collateral classique.

Ce parcours s'appuie sur le depot cloné a la date d'ecriture. Fichiers centraux : `contracts/vaults/ethereum/EthVault.sol` (le vault de base, assemble par heritage multiple de modules), `contracts/vaults/modules/VaultState.sol`, `VaultEnterExit.sol`, `VaultOsToken.sol`, `VaultValidators.sol`, `VaultFee.sol`, `VaultMev.sol`.

Rien n'a ete installe, compile ni execute pour ecrire ces chapitres.

[Chapitre suivant : architecture en modules assembles par heritage](02-architecture.md)
