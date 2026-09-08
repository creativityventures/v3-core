# Chapitre 13 — Limites connues et perimetre de ce parcours

Le depot StakeWise v3 est publie sous licence **Business Source License 1.1** (BUSL-1.1), avec une date de conversion ("Change Date") fixee au 1er janvier 2026. A la date d'ecriture de ce parcours (2026), cette date est deja passee : selon les termes memes du fichier `LICENSE.md`, le code est donc repasse sous licence **MIT**, la meme transition deja documentee pour Compound v3 dans ce meme compte.

Ce parcours ne couvre pas en detail le "keeper" (un service off-chain qui alimente `updateState` en donnees agregees de recompenses et de MEV, dont le contrat `IKeeperRewards` n'est qu'une interface ici), les vaults specifiques a la chaine Gnosis (`contracts/vaults/gnosis/`), les vaults personnalises (`EthFoxVault`, `EthCommunityVault`), ni le detail complet du systeme de gouvernance globale du protocole (`contracts/curators/`, `contracts/nodes/`). Le mecanisme precis de calcul du ratio de collateralisation maximal de l'osToken (`OsTokenConfig`, hors des modules de vault eux-memes) n'est pas non plus detaille.

Rien n'a ete installe, compile, deploye ni execute pour ecrire ces chapitres. Aucun test n'a ete lance ; ces chapitres decrivent ce que le code Solidity dit faire, en renvoyant aux fichiers cites. Le depot fournit sa propre suite de tests (dossier `test/`) pour verification independante.
