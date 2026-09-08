# Chapitre 7 — VaultValidators : enregistrer des validateurs Beacon Chain deleguees

`registerValidators` permet a un "validators manager" designe par l'administrateur du vault (`setValidatorsManager`) d'enregistrer de nouveaux validateurs Beacon Chain finances par les actifs deposes dans le vault, en fournissant les donnees de depot requises (cle publique, signature, racine des donnees de depot) — la meme etape que le `newValidator` de Rocket Pool deja documente pour ce compte, mais sans le systeme de bond de l'operateur de noeud : ici, c'est le vault entier, finance par ses deposants, qui porte le cout du validateur, pas un operateur individuel apportant sa propre mise.

L'autorisation du validators manager peut passer soit par une transaction directe (s'il est l'administrateur ou l'adresse designee), soit par une signature EIP-712 hors chaine verifiee par `_isValidatorsManager` — le meme motif de delegation par signature deja rencontre dans plusieurs autres parcours de cette bibliotheque (Rocket Pool, MakerDAO, Comet), applique ici a la delegation du droit d'operer les validateurs plutot qu'a une simple approbation de jeton.

`withdrawValidators` et `consolidateValidators` couvrent les operations post-Pectra (la mise a niveau Ethereum qui a introduit des retraits et consolidations de validateurs pilotables depuis le contrat de depot Beacon Chain) : le vault peut desormais initier ces operations directement depuis le contrat, sans dependre exclusivement du comportement historique des cles de validateur elles-memes.

[Chapitre suivant : VaultOsToken, un jeton emprunte contre la position stakee](08-ostoken.md)
