#Sécurité des applications web 


#Intro-
Au sens large, la sécurité c’est l’ensemble des moyens (techniques, organisationnels, humains, légaux) pour minimiser la surface d'exposition d'une application ou d'un système contre les menaces :
-Passives visant à écouter ou copier des informations illégalement ;
-Actives consistant à altérer des informations ou le bon fonctionnement d’un service.
Au-delà de ces notions importantes, la sécurisation d’une application ou d’un système s’attache aux 6 aspects suivants :
-L’authentification ;
-Le contrôle d’accès ;
-L’intégrité des données ;
-La confidentialité des données ;
-La non-répudiation ;
-La protection contre l’analyse du trafic.


##Vulnérabilités courantes (SQL Injection, XSS, CSRF)

###SQL
####Qu’est ce qu’une requête SQL? 
Une requête SQL (Structured Query Language) est une instruction utilisée pour interagir avec une base de données relationnelle. 
SQL est le langage standard pour gérer et manipuler les bases de données. 
Les requêtes SQL permettent de réaliser diverses opérations comme la récupération de données, l'insertion de nouvelles données, la mise à jour de données existantes et la suppression de données.

####Qu’est ce que l’injection SQL?
L'injection SQL est une technique malveillante utilisée par des attaquants pour exploiter des vulnérabilités dans les applications web qui manipulent des bases de données SQL. Elle consiste à insérer ou "injecter" du code SQL malveillant dans une requête SQL légitime, dans le but de contourner les contrôles d'accès, récupérer des données sensibles, modifier la base de données ou exécuter d'autres actions non autorisées.

Pour vérifier si votre site est sensible aux injections SQL vous pouvez utiliser l'outil sqlmap

###XSS
####Qu’est ce que XSS?
XSS (Cross-Site Scripting) est une vulnérabilité de sécurité courante dans les applications web, où un attaquant injecte du code malveillant (souvent JavaScript) dans le contenu d'un site web, qui est ensuite exécuté par le navigateur des utilisateurs. Cette attaque permet aux attaquants de contourner les politiques de sécurité du navigateur et d'accéder à des informations sensibles ou d'effectuer des actions en tant que l'utilisateur sans son consentement.


 #####3 types d'attaques XSS :

	-XSS Réfléchi (Reflected XSS) :
Ce type d'attaque se produit lorsque les données injectées par l'attaquant sont renvoyées immédiatement par le serveur dans la réponse HTTP. Les attaquants incluent généralement des liens malveillants dans des e-mails ou d'autres communications, incitant les utilisateurs à cliquer sur ces liens.
	-XSS Persistant (Stored XSS) :
Ce type d'attaque se produit lorsque les données injectées par l'attaquant sont stockées de manière persistante sur le serveur (par exemple, dans une base de données) et sont ensuite affichées aux utilisateurs dans des pages web. Cela peut se produire dans les forums, les sections de commentaires, ou tout autre endroit où les utilisateurs peuvent soumettre des données.
	-XSS Basé sur le DOM (DOM-based XSS) :
Ce type d'attaque se produit lorsque la vulnérabilité réside dans le code client (JavaScript) plutôt que dans le code serveur. Le code malveillant modifie le DOM (Document Object Model) de la page web, permettant l'exécution de scripts malveillants.

#####Conséquences d'une Attaque XSS:
	Vol de Cookies et de Sessions
Redirections Malveillantes 
Manipulation du DOM
Exécution de Scripts Malveillants

####Prévention des Attaques XSS:
-Échapper les Entrées et les Sorties : L'échappement des entrées et des sorties est une pratique qui consiste à traiter les données utilisateur avant de les afficher dans le navigateur, afin de s'assurer qu'elles ne contiennent pas de code pouvant être exécuté. Cela aide à prévenir les attaques XSS en transformant les caractères spéciaux en entités HTML inoffensives
-Utiliser des Bibliothèques de Sécurité : C’est une pratique recommandée pour assurer que les données sont correctement échappées, ce qui aide à prévenir les attaques XSS. Ces bibliothèques sont conçues pour simplifier et standardiser le processus d'échappement des données, réduisant ainsi les erreurs humaines et les vulnérabilités potentielles.
-Content Security Policy (CSP) : Le Content Security Policy (CSP) est un mécanisme de sécurité pour les applications web, consistant en un ensemble de règles que vous configurez pour définir les sources de contenu autorisées à être chargées par votre application. En implémentant une CSP, vous spécifiez précisément à partir de quelles origines de confiance votre application peut charger divers types de ressources, tels que des scripts JavaScript, des styles CSS, des images et d'autres médias.
	-Valider et Sanitize les Données : Valider les données du côté serveur et nettoyer toutes les entrées utilisateur pour s'assurer qu'elles ne contiennent pas de scripts.
	-Utiliser des Frameworks Sécurisés : Utiliser des frameworks web qui incluent des mécanismes de protection contre les XSS par défaut.





###CSRF
####Qu’est ce que le CSRF?
Les CSRF sont une technique d'attaque contre les sites web où un attaquant manipule un utilisateur pour qu'il exécute des actions non voulues sur un site où il est déjà authentifié.

####Voilà comment cela se passe!
-Authentification implicite : Lorsque vous vous connectez à un site web, votre navigateur stocke des cookies qui prouvent que vous êtes authentifié.
Action malveillante : L'attaquant crée une action malveillante, comme changer votre mot de passe ou effectuer un paiement, et il crée un lien ou un formulaire caché qui exécute cette action.
-Leurre de l'utilisateur : L'attaquant incite l'utilisateur à cliquer sur ce lien malveillant, par exemple en l'envoyant par e-mail ou en le publiant sur un forum. L'utilisateur pense que c'est sûr car il est déjà connecté au site.
-Exécution de l'action : Lorsque l'utilisateur clique sur le lien, son navigateur envoie la requête malveillante au site web avec les cookies d'authentification. Le site pense que c'est une requête légitime de l'utilisateur authentifié et il exécute l'action demandée.
-Conséquences : Cela permet à l'attaquant de faire des choses en votre nom sans que vous le sachiez, comme transférer de l'argent ou modifier vos informations personnelles.

####Technique de protections:
	-Token CSRF :
 Un jeton unique est ajouté à chaque formulaire ou requête pour vérifier qu'elle vient bien de vous et non d'un attaquant.
-En-tête Referer : 
Vérifie que la requête provient bien du même site web.
-Cookie SameSite :
 Limite l'envoi de cookies lors de requêtes cross-site.
-Headers HTTP : 
Utilisation d'en-têtes spécifiques pour vérifier l'authenticité des requêtes.
-Protection CORS :
Configuration pour limiter les requêtes entre différents domaines.

###Envoie de fichier malicieux
####Qu’est ce que c’est que l'envoie de fichier malicieux?
Les fichiers malicieux sont souvent des programmes ou des scripts conçus pour compromettre la sécurité d'un système. Ils peuvent inclure des virus, des chevaux de Troie, des ransomwares ou d'autres formes de logiciels nuisibles.

####Méthodes d'Infection:
	-Phishing : Les attaquants peuvent inciter les utilisateurs à télécharger des fichiers malicieux via des e-mails ou des liens malveillants.
-Téléchargements Non Sécurisés : Les utilisateurs peuvent télécharger des fichiers à partir de sources non fiables ou compromises sur Internet.
-Exploitation de Vulnérabilités : Les attaquants peuvent exploiter des vulnérabilités dans les logiciels pour exécuter des scripts malicieux à distance.

####Ce que cela provoque:
	-Perte de Données 
-Prise de Contrôle du Système
-Dégradation des Performances

####Prévention
-Sensibilisation et Formation
-Utilisation de Logiciel de Sécurité
-Filtrage des Téléchargements :

###Les attaques temporelles
####Qu’est ce que c’est que les attaques temporelles?
Les attaques temporelles, aussi appelées attaques de timing, sont des techniques utilisées par les pirates informatiques pour déduire des informations sensibles en mesurant le temps que prend une opération ou une réponse.

####Prévention
-Mettre en œuvre des temps de réponse uniformes, même pour les entrées incorrectes.
-Utiliser des bibliothèques ou des fonctions qui prennent toujours le même temps pour répondre, quel que soit l'entrée.
-Surveiller et analyser les motifs de trafic inhabituels qui pourraient indiquer une tentative d'attaque.

##2-Pratiques de codage sécurisé

 ###Utilisations du Hachage
-Mots de Passe
  Les mots de passe sont transformés en hashes pour les stocker de manière sécurisée. Lors de la connexion, le mot de passe entré est haché et comparé au hash stocké.
-Intégrité des Données 
Vérification des fichiers :
Les fonctions de hachage comme SHA-256 sont utilisées pour créer des "empreintes digitales" de fichiers. Cela permet de vérifier si un fichier a été modifié ou corrompu en comparant les hashes.
 	-Transmission de données :
 Lors de la transmission de données, un hash peut être utilisé pour s'assurer que les données reçues sont identiques aux données envoyées.
-Signatures Numériques
 Les fonctions de hachage sont utilisées dans les signatures numériques pour garantir que les données n'ont pas été altérées. Cela assure l'authenticité et l'intégrité des messages et des documents.
-Tables de Hachage
 En informatique, les tables de hachage sont utilisées pour stocker et rechercher des données rapidement. Un hash de la clé de donnée détermine où la donnée sera stockée ou retrouvée dans une structure de données.
-Cryptographie
Les fonctions de hachage sont fondamentales dans de nombreux protocoles de cryptographie, comme HMAC (Hash-based Message Authentication Code), pour garantir l'intégrité et l'authenticité des messages.

	
###Chiffrement
####Qu’est ce que le chiffrement?
Le chiffrement est une technique de sécurité qui transforme des données lisibles en données illisibles à l'aide d'un algorithme et d'une clé. Cela protège les informations sensibles contre l'accès non autorisé.

####Utilisations du Chiffrement
-Confidentialité des Données
Stockage : 
Les données sensibles (comme les fichiers ou les bases de données) sont chiffrées pour les protéger contre l'accès non autorisé.

Transmission : 
Les données envoyées sur Internet (comme les e-mails ou les transactions en ligne) sont chiffrées pour empêcher les interceptions.

-Authentification
Signatures Numériques :
Utilisées pour vérifier l'authenticité d'un document ou d'un message. Le document est chiffré avec une clé privée et peut être vérifié avec la clé publique correspondante.
Certificats SSL/TLS :
Utilisés pour authentifier les sites web et établir des connexions sécurisées (HTTPS).

####Intégrité des Données
HMAC (Hash-based Message Authentication Code) :
Combine une clé secrète avec un message haché pour garantir que le message n'a pas été altéré.

####Sécurité des Systèmes :
-Disques Durs :
Les systèmes de chiffrement de disque complet (comme BitLocker ou FileVault) chiffrent tout le contenu d'un disque dur pour protéger les données en cas de vol ou de perte.
-Applications et Services :
Les services de messagerie (comme WhatsApp ou Signal) utilisent le chiffrement de bout en bout pour sécuriser les communications entre utilisateurs.

####Types de Chiffrement
-Chiffrement Symétrique :
Principe : 
Utilise la même clé pour chiffrer et déchiffrer les données.
Utilisation : Rapide et efficace pour chiffrer de grandes quantités de données.
-Chiffrement Asymétrique :
Principe :
Utilise une paire de clés : une clé publique pour chiffrer les données et une clé privée pour les déchiffrer.
Utilisation :
Principalement utilisé pour échanger des clés symétriques de manière sécurisée et pour les signatures numériques.

###Signature numérique
####Qu’est ce que la signature numérique?
Une signature numérique est un mécanisme cryptographique qui permet de vérifier l'authenticité et l'intégrité d'un message, document ou autre fichier numérique. Elle est similaire à une signature manuscrite, mais beaucoup plus sécurisée.

####Principe de la Signature Numérique
 -Création de la Signature :
Hachage du Document :Tout d'abord, le document ou message est passé à travers une fonction de hachage pour créer un hash (empreinte digitale unique du document).
 	-Chiffrement du Hash :Le hash est ensuite chiffré avec la clé privée de l'expéditeur. Ce chiffrement du hash est ce qu'on appelle la signature numérique.

-Vérification de la Signature :
 Déchiffrement de la Signature :Le destinataire utilise la clé publique de l'expéditeur pour déchiffrer la signature numérique, obtenant ainsi le hash original.
Hachage du Document Reçu :Le destinataire passe ensuite le document ou message reçu à travers la même fonction de hachage pour créer un nouveau hash.
Comparaison des Hashs :Si le hash déchiffré et le nouveau hash sont identiques, cela prouve que le document n'a pas été altéré et qu'il provient bien de l'expéditeur légitime.

####Utilisations de la Signature Numérique
-Authentification 
Vérifie l'identité de l'expéditeur, assurant que le document ou message provient bien de la personne ou de l'entité qu'il prétend être.
-Intégrité 
Garantit que le contenu du document ou message n'a pas été modifié depuis sa création.
-Non-répudiation
L'expéditeur ne peut pas nier avoir envoyé le document ou message, car seul lui possède la clé privée utilisée pour créer la signature.



##3-Utilisation de HTTPS et gestion des certificats SSL

1-HTTPS

Qu’est ce que me HTTPS
HTTPS (HyperText Transfer Protocol Secure) est une version sécurisée du protocole HTTP, utilisé pour naviguer sur le web. Il protège les informations échangées entre votre navigateur et le site web.

Fonctionnement
Connexion Sécurisée :
Chiffrement : 
HTTPS chiffre les données échangées, ce qui les rend illisibles pour les pirates. Cela empêche les interceptions de données sensibles comme les mots de passe et les numéros de carte de crédit.
Certificat SSL/TLS : 
Les sites web utilisent un certificat pour prouver leur identité. Ce certificat est vérifié par votre navigateur.

Processus :
Demande de Connexion : 
Votre navigateur demande une connexion sécurisée au site web.
Échange de Certificats : 
Le site envoie son certificat au navigateur, prouvant qu'il est authentique.
Établissement de la Connexion Sécurisée : 
Si le certificat est valide, le navigateur et le site web établissent une connexion sécurisée en échangeant des clés pour chiffrer les données.

Utilités
Confidentialité : 
Protège les informations sensibles échangées entre vous et le site web.

Authenticité : 
Assure que vous communiquez avec le bon site web et non avec un imposteur.
Intégrité des Données : 
Garantit que les données envoyées et reçues n'ont pas été modifiées.

	2-SSL/ TSS
Qu’est ce que c’est?
La gestion des certificats SSL est un processus crucial pour assurer la sécurité des communications sur Internet. Voici quelques points clés expliquant en détail ce que cela implique :

Installation des certificats SSL :
L'installation d'un certificat SSL sur un serveur web est la première étape. Ce certificat contient une clé cryptographique qui permet de sécuriser les échanges de données entre le serveur et les navigateurs web des utilisateurs. Lorsqu'un certificat SSL est installé correctement, il active le protocole HTTPS, indiqué par un cadenas dans la barre d'adresse du navigateur.

Renouvellement des certificats SSL : 
Les certificats SSL ont une durée de validité limitée, généralement d'un an ou de plusieurs années selon le type de certificat et les politiques de l'Autorité de Certification (CA) qui l'a délivré. Il est essentiel de renouveler ces certificats avant leur expiration pour éviter toute interruption dans la connexion sécurisée du site web.

Vérification de l'authenticité des certificats : 
Les certificats SSL sont émis par des Autorités de Certification (CA) de confiance. Avant d'installer un certificat SSL sur un serveur, il est crucial de vérifier que celui-ci a été émis par une CA légitime et qu'il est correctement signé. Cela garantit que les navigateurs web des utilisateurs reconnaîtront le certificat comme valide et digne de confiance.

Gestion des chaînes de certificats : 
Les certificats SSL sont souvent fournis sous forme de chaînes, où chaque certificat dans la chaîne est lié à une autorité de certification de confiance. Les navigateurs web utilisent ces chaînes pour vérifier l'authenticité d'un certificat SSL particulier et s'assurer qu'il n'a pas été compromis ou falsifié.

Sécurité et protection des clés privées : 
Outre l'installation et le renouvellement des certificats SSL, il est également crucial de protéger les clés privées associées à ces certificats. Les clés privées sont utilisées pour déchiffrer les communications chiffrées et doivent être stockées de manière sécurisée sur le serveur web pour éviter tout accès non autorisé.



##4-Meilleures pratiques pour sécuriser les API

###Qu’est ce que les API?
Les API (Application Programming Interfaces) sont des interfaces qui permettent à différentes applications informatiques de communiquer entre elles. Elles définissent les règles et les méthodes que les programmes peuvent utiliser pour échanger des données et effectuer des actions spécifiques. En gros, les API facilitent la collaboration entre différents logiciels en leur permettant de se comprendre et de travailler ensemble de manière harmonieuse

###Risques spécifiques des API :
-Accès non autorisé :
 Si l'authentification et l'autorisation sont mal configurées, des utilisateurs non autorisés peuvent accéder aux données ou aux fonctionnalités de l'API.
-Attaques par injection : 
Les entrées non validées peuvent permettre des injections de code malveillant, compromettant les systèmes derrière l'API.
-Déni de service (DoS) : 
Les API peuvent être submergées par des requêtes excessives, rendant le service indisponible.
-Exposition de données sensibles: 
Les API mal sécurisées peuvent divulguer des informations sensibles.
-Man-in-the-Middle (MITM) : 
Les communications non chiffrées peuvent être interceptées par des attaquants.

 ###Solutions pour éviter ces risques :
-Authentification et Autorisation robustes: 
Utilisez des protocoles comme OAuth 2.0 et des JSON Web Tokens (JWT) pour s'assurer que seuls les utilisateurs autorisés accèdent à l'API.
-Validation stricte des entrées : 
Validez et nettoyez toutes les entrées des utilisateurs pour éviter les attaques par injection.
-Chiffrement des communications: 
Utilisez HTTPS/TLS pour chiffrer les données en transit, empêchant les attaques MITM.
-Limitation des taux de requêtes (Rate limiting): 
Implementez des quotas et des limites de taux pour éviter les attaques par déni de service.
-Contrôle d'accès basé sur les rôles (RBAC) : 
Assurez-vous que les utilisateurs n'ont accès qu'aux données et aux fonctionnalités nécessaires.
-Surveillance et Journalisation : 
Surveillez les activités de l'API en temps réel et conservez des journaux détaillés pour détecter et réagir rapidement aux comportements suspects.
-Tests de sécurité réguliers : 
Effectuez des tests d'intrusion et des analyses de code pour identifier et corriger les vulnérabilités avant qu'elles ne soient exploitées.

En mettant en place ces mesures, vous pouvez protéger vos API contre les risques spécifiques et garantir la sécurité des communications et des données qu'elles manipulent.


## Conclusion
Les API et les applications web partagent de nombreuses menaces en matière de sécurité, mais certaines sont plus spécifiques à l'un ou l'autre en raison de leurs architectures et de leurs modes d'utilisation différents. Les principes de sécurité comme la validation des entrées, l'authentification robuste, et le chiffrement des communications restent cruciaux dans les deux cas.

Sources-
[openclassrooms]
(https://openclassrooms.com/fr/courses/161931-securisez-vos-applications/5702500-identifiez-les-6-aspects-de-la-securite-d-une-application)
[graphikart]
(https://grafikart.fr/tutoriels/securite-injections-sql-59#autoplay)
[akama]
(https://www.akamai.com/fr/glossary/what-is-application-security )
[hostinger]
(https://www.hostinger.fr/tutoriels/securite-applications-web)
[chat GPT]
