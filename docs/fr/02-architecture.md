# Chapitre 2 — Architecture : des vaults assembles par heritage multiple de modules

`EthVault.sol`, le contrat de vault de base pour Ethereum, n'implemente presque rien lui-meme : il herite simultanement de `VaultImmutables`, `VaultAdmin`, `VaultVersion`, `VaultFee`, `VaultState`, `VaultValidators`, `VaultEnterExit`, `VaultOsToken`, `VaultMev` et `VaultEthStaking`, chacun un module autonome dans `contracts/vaults/modules/` qui apporte une responsabilite precise (comptabilite de parts, file d'attente de sortie, position osToken, enregistrement de validateurs, frais, partage du MEV).

Cette architecture en mixins permet de composer des variantes de vaults sans dupliquer de code : `EthPrivVault` ajoute simplement le module `VaultWhitelist` par-dessus les memes modules de base pour restreindre les depots a une liste blanche, `EthBlocklistVault` ajoute `VaultBlocklist` pour l'inverse (tout le monde sauf une liste noire), `EthErc20Vault` ajoute `VaultToken` pour rendre les parts elles-memes transferables comme un jeton ERC20 classique plutot que de rester un solde interne non transferable (chapitre 3).

Chaque vault est deploye comme un proxy upgradeable (motif UUPS d'OpenZeppelin) par une fabrique dediee (`EthVaultFactory`), et non comme un contrat directement instancie : cela permet a la gouvernance du protocole de faire evoluer l'implementation partagee de tous les vaults d'une meme version sans devoir migrer chaque vault individuellement.

[Chapitre suivant : les variantes de vaults : prive, liste noire, ERC20](03-variantes.md)
