# Chapitre 11 — VaultSubVaults : composer un meta-vault a partir de plusieurs vaults

Au-dela des vaults simples, le protocole introduit un module `VaultSubVaults` qui permet a un vault de niveau superieur (un "meta-vault") de repartir les depots qu'il recoit entre plusieurs vaults sous-jacents enregistres dans un `ISubVaultsRegistry` dedie, plutot que de faire tourner lui-meme des validateurs directement. C'est un motif de composition proche des coffres tiers de l'ecosysteme Morpho (MetaMorpho, mentionne au chapitre 13 du parcours Morpho Blue de ce compte) : une couche d'agregation et de diversification construite au-dessus des briques de base du protocole.

Un meta-vault expose les memes interfaces de depot, de sortie et d'osToken que n'importe quel autre vault a ses propres deposants ; en interne, il traduit ces operations en depots et retraits proportionnels vers l'ensemble de ses sous-vaults, en s'appuyant sur les memes interfaces `IVaultEnterExit`/`IVaultOsToken` que celles deja documentees dans les chapitres precedents, mais cette fois du point de vue d'un appelant plutot que d'un vault final.

Ce module utilise des structures de donnees plus avancees (`EnumerableSet`, `DoubleEndedQueue` d'OpenZeppelin) pour gerer dynamiquement la liste de ses sous-vaults et une file d'attente propre a la repartition des fonds entre eux — une complexite supplementaire assumee uniquement par les vaults qui choisissent explicitement ce role d'agregateur.

[Chapitre suivant : gouvernance : registre, liste blanche et administration](12-gouvernance.md)
