# Chapitre 12 — Gouvernance : VaultsRegistry, VaultAdmin et les listes d acces

`VaultAdmin`, le module le plus simple, definit un unique administrateur par vault avec transfert de propriete en une etape — une gouvernance locale, propre a chaque vault, distincte de toute gouvernance globale du protocole. Cet administrateur controle les frais (chapitre 10), le validators manager (chapitre 7), et pour les variantes concernees, la liste blanche ou la liste noire (chapitre 3).

Au niveau du protocole dans son ensemble plutot que d'un vault individuel, un `VaultsRegistry` global (hors du detail de ce parcours) tient la liste des vaults et fabriques legitimes, un peu comme le registre de contrats officiels de Rocket Pool deja documente pour ce compte : c'est ce registre que le keeper et les autres composants du protocole consultent pour verifier qu'un vault donne fait bien partie du systeme StakeWise plutot que d'un clone non officiel du code.

`VaultWhitelist` et `VaultBlocklist` (chapitre 3) partagent la meme structure de base (un mapping d'adresses vers un booleen, gere par un role "whitelister"/"blocklist manager" delegue par l'administrateur) mais avec une semantique inversee : liste blanche interdit par defaut sauf exception, liste noire autorise par defaut sauf exception — deux modules independants que l'administrateur choisit d'ajouter ou non selon le profil de vault qu'il souhaite operer.

[Chapitre suivant : limites et perimetre](13-limites-et-perimetre.md)
