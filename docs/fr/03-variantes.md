# Chapitre 3 — Les variantes de vaults : public, prive, liste noire, parts ERC20

Le vault de base (`EthVault`) est public : n'importe qui peut y deposer de l'ETH. `EthPrivVault` restreint les depots aux adresses ajoutees a une liste blanche par l'administrateur du vault (module `VaultWhitelist`) — utile pour un vault reserve a un cercle ferme de deposants institutionnels, par exemple. `EthBlocklistVault` fait l'inverse : ouvert par defaut, sauf aux adresses explicitement bloquees (module `VaultBlocklist`).

Par defaut, la part de chaque deposant dans un vault reste un solde interne non transferable, comme les parts de Morpho Blue deja documentees pour ce compte. `EthErc20Vault` ajoute le module `VaultToken`, qui transforme ces parts en un veritable jeton ERC20 transferable et echangeable sur des marches secondaires — une variante utile pour la composabilite DeFi, au prix d'une comptabilite legerement plus complexe (suivi des transferts entre comptes qui n'affectent jamais le solde de parts total du vault).

D'autres variantes existent dans le depot pour la chaine Gnosis (`contracts/vaults/gnosis/`) ou pour des cas particuliers (`EthFoxVault`, `EthCommunityVault` dans `contracts/vaults/ethereum/custom/`), hors du perimetre detaille de ce parcours : le principe reste le meme, combiner les modules necessaires par heritage pour obtenir le comportement souhaite.

[Chapitre suivant : VaultState, la comptabilite par parts](04-comptabilite.md)
