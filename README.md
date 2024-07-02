# A. APPROCHES DES MÉTHODES

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


# B. LES TYPES DE FAILLE

	1. INJECTIONS SQL
> le hacker exploite les failles du code SQL (base de données)
si il comprend la syntaxe du code, il peut alors écrire une fausse requête
pour accéder à des infos. confidentielles (utilisateurs) ou modifier des informations 

  > Voici un exemple de code sensible à l'injection SQL :
db.query(`SELECT id, title FROM recipe WHERE id = ${req.param('id')}`
-> requête générée par le hacker :
SELECT id, title FROM recipe WHERE id = -1 UNION SELECT email, password FROM users 

pour éviter les injections: éviter les concaténations (failles)
> utiliser des requêtes "préparées”
Pour vérifier si un site est sensible aux injections SQL : utiliser l'outil  sqlmap

2. FAILLES XSS (Cross-Site Scripting)
> le hacker injecte des scripts malveillants dans les pages web (HTML, JavaScript...)
 > exploite les données entrantes des sites type formulaires, commentaires pour:
Récupérer des identifiants / code de paiements (écoute du clavier)
Récupérer des cookies (non HTTP) et le contenu du localStorage
Rediriger vers un site de phishing ou déclencher le téléchargement de virus

3. Failles CSRF (Cross-Site Request Forgery)
- attaques par requête intersites
Faire exécuter des actions indésirables à des utilisateurs authentifiés:
> changement de mdp
> suppression de compte
> transfert d'argent
...
ex.: un site pirate qui se cache derrière un CTA

Axes de sécurité :
> bien configurer les cookies :
- configurer les cookies de session avec l'attribut SameSite à Strict ou Lax pour éviter qu'ils ne soient envoyés avec des requêtes intersites.
> Token CSRF: jeton unique ajouté à chaque formulaire ou requête
pour vérifier l'authenticité des requêtes

4. Attaques temporelles (attaques par chronométrage)
- Techniques pour déduire des informations sensibles en mesurant le temps que prend une opération
- l’attaquant n’a pas besoin d’accès aux données

Préventions
- comparaisons en temps constant
- blindage temporel
- ajout d'aléa
- algorithmes cryptographiques


# C. Cas des APIs

Interfaces logicielles : une API représente un contrat entre différentes applications
ou composants logiciels, permettant :
> se connecter, partager des données, utiliser des fonctionnalités
de manière cohérente et sécurisée
> > la modularité, la réutilisabilité et l'efficacité du développement logiciel

Vulnérabilité:
- grand nombre d'informations précieuses
- multiples points d'entrée négligés ou oubliés
Types d'attaque: injection, MITM (machine-in-the-middle), DDoS (pour submerger le trafic)
> Les utilisateurs non autorisés peuvent exploiter les vulnérabilités d'une API pour:
- accéder à des données sensibles
- perturber les services
- détourner le système à leur profit

ressources: https://www.akamai.com/fr/glossary/what-are-api-security-risks
        https://chatgpt.com

# Améliorer la Sécurité des APIs
- Authentification Robuste
- Contrôle d’Accès Granulaire
- Chiffrement des Communications
- Validation des Entrées
- Limitation des Taux de Requête
- Utilisation des API Keys
- Surveillance et Journalisation
- Gestion des Versions
- Politique de CORS (Cross-Origin Resource Sharing)
- Sécurité des Données Sensibles
- Gestion des Erreurs
- Tests de Sécurité Réguliers
- Mises à Jour et Patching

# Menaces auxquelles sont confrontées les applications web et les APIs
- Injection SQL
- Cross-Site Scripting (XSS)
- Cross-Site Request Forgery (CSRF)
- Man-in-the-Middle (MitM) Attacks
- Attaques par Déni de Service (DoS/DDoS)
- Exposition des Données Sensibles
- Injections de Commandes (Command Injection)
- Vulnérabilités de Sécurité (Bibliothèques et Dépendances)
- Manipulation des paramètres d'URL
- Utilisation malveillante des Fonctionnalités (Abus)
- Fuite d'Informations (Leakage)
- Faiblesse dans la Gestion des Sessions et des Cookies
- Utilisation de Composants non-sécurisés

# Approches pour la sécurisation
- Authentification et Gestion des Sessions
- Contrôle d'Accès (RBAC - Role-Based Access Control)
- Chiffrement des Données (en transit et au repos)
- Validation et Assainissement des Entrées
- Protection contre les Attaques (SQL Injection, XSS, CSRF, DoS)
- Utilisation de Pare-feu d'Application Web (WAF)
- Gestion des Vulnérabilités et Tests de Sécurité
- Sécurité des APIs 
- Surveillance et Journalisation des Activités
- Formation et Sensibilisation à la Sécurité
