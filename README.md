# App-Security
A.
3 exemples d'approches différentes :
- hashage
- chiffrement
- signature


HASHAGE
Les algorithmes de hashages sont impossibles à inverser (pas de chemin inverse)
- peu de collision (ne donne pas d'indice sur la chaine de caractère utilisée en entrée)
- taille fixe
> vérifier l'intégrité d'un fichier (pas d'altération du code)
> vérifier les mots de passe
Chaîne originale : Bonjour les gens
Hash : babbaabababababb

CHIFFREMENT
Algorithme réversible, on peut déchiffrer des informations
- utilise des clefs pour le chiffrement et le déchiffrement (symétrique ou asymétrique)
> sécuriser le transfert d'information (HTTPS)
> sauvegarder des fichiers sensibles
Chaîne originale : Bonjour les gens
Chiffré (Rot1) : Cpokpvs mft hfot

SIGNATURE
combine les 2 approches précédentes :
hashage + chiffrement = signature
> vérifier l'origine d'un message
> ne chiffre pas l'information


	1. FAIBLESSES DU HASHAGE
	Les vecteurs d'attaque pour ces systèmes de sécurité :

- collision > le hacker peut trouver puis réutiliser les hashs similaires
(les réinjecter et donner l'impression que le fichier est "intègre")
- attaque par Brute-force > le hacker essaie tous les mdp possibles jusqu'à
trouver le hash (et donc le mdp original)

	SOLUTIONS
	Pour lutter contre ce type d'attaques:
- choisir le bon algorithme (limiter les collisions)
- augmenter le coût de génération : ralentir le système pour empêcher la génération de mdp
- introduire une "variance" (algo pour que le hash varie en fonction de chaque utilisateur)
-> principe des clés "salt/pepper" (freins suppl. contre le Brute-force)

ressource: https://grafikart.fr/tutoriels/secure-donnee-site-web-2209#autoplay

	2. FAIBLESSES DU CHIFFREMENT
- Le hacker peut trouver comment faire le chemin inverse
(facilité de déchiffrer une chaîne de caractères)
- vol/interception de la clef de chiffrement/déchiffrement par un tier
	SOLUTIONS
- choisir le bon algo
- protéger/changer les clefs fréquemment

> Mêmes principes de faiblesses/solutions pour la SIGNATURE

HASHER LES MDP
> en cas de piratage de données, pas de mdp original en clair dispo grâce au hashage
ex. avec PHP :
> le dev. ajoute une fonction password_hash dans le code
le mdp devient ce hash :
nom de l'algo + coût de génération + clé de salage + hash généré
PS: dans beaucoup de frameworks, le système de hashage est pré-intégré
Dans JS, pas de fonction pré-écrite => ajouter le package "décrypte"



B.
				LES FAILLES


	1. INJECTIONS SQL
> le hacker exploite les failles du code SQL (base de données)
si il comprend la syntaxe du code, il peut alors écrire une fausse requête
pour accéder à des infos. confidentielles (utilisateurs) ou modifier des informations 

  > Voici un exemple de code sensible à l'injection SQL :
db.query(`SELECT id, title FROM recipe WHERE id = ${req.param('id')}`
-> requête générée par le hacker :
SELECT id, title FROM recipe WHERE id = -1 UNION SELECT email, password FROM users 
# éviter les injections: éviter les concaténations (failles)
> utiliser des requêtes "préparées”
Pour vérifier si un site est sensible aux injections SQL : utiliser l'outil  sqlmap





	2. FAILLES XSS (Cross-Site Scripting)
> le hacker injecte des scripts malveillants dans les pages web (HTML, JavaScript...)
 > exploite les données entrantes des sites type formulaires, commentaires :
pour rediriger un utilisateur vers une autre page











