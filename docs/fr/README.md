# Parcours francais de StakeWise v3 — Liquid staking

Lecture commentee du protocole de vaults de liquid staking permissionless StakeWise v3, en francais, un mecanisme par chapitre.
Aucun code n'a ete installe, compile ni execute : ce parcours est purement documentaire.

1. [Presentation de StakeWise v3](01-presentation.md)
2. [Architecture : des vaults assembles par heritage multiple de modules](02-architecture.md)
3. [Les variantes de vaults : public, prive, liste noire, parts ERC20](03-variantes.md)
4. [VaultState : la comptabilite par parts et le taux de change](04-comptabilite.md)
5. [updateState : recompenses, penalites et frais d administration](05-updatestate.md)
6. [VaultEnterExit : une file d attente de sortie en deux etapes](06-exitqueue.md)
7. [VaultValidators : enregistrer des validateurs Beacon Chain deleguees](07-validators.md)
8. [VaultOsToken : un jeton surcollateralise emprunte contre la position stakee](08-ostoken.md)
9. [VaultMev : partager la valeur extraite par les proposants de blocs](09-mev.md)
10. [VaultFee : les frais d administration, plafonnes et delai de reduction](10-frais.md)
11. [VaultSubVaults : composer un meta-vault a partir de plusieurs vaults](11-subvaults.md)
12. [Gouvernance : VaultsRegistry, VaultAdmin et les listes d acces](12-gouvernance.md)
13. [Limites connues et perimetre de ce parcours](13-limites-et-perimetre.md)
