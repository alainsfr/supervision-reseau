Voici un résumé des procédures essentielles pour utiliser SSH, de la configuration de base à la connexion.
1. La procédure de connexion standard

Par défaut, la connexion se fait via un terminal en utilisant l'adresse IP (ou le nom de domaine) du serveur et votre nom d'utilisateur.


ssh utilisateur@adresse_ip_du_serveur

    Si c'est la première connexion : Votre terminal affichera un message d'alerte demandant de valider l'empreinte (fingerprint) du serveur. Tapez yes.

    Ensuite : Saisissez le mot de passe de l'utilisateur (il ne s'affiche pas à l'écran par sécurité) et validez.

2. La procédure recommandée : Authentification par clés SSH

Pour éviter de taper votre mot de passe et renforcer la sécurité, on utilise un couple de clés (une publique et une privée).

    Générer le couple de clés (sur votre ordinateur local) :
    

    ssh-keygen -t ed25519

    (Appuyez sur Entrée pour accepter l'emplacement par défaut. Vous pouvez ajouter une "passphrase" pour sécuriser la clé).

    Copier la clé publique sur le serveur :
    

    ssh-copy-id utilisateur@adresse_ip_du_serveur

    (Entrez le mot de passe du serveur une dernière fois).

    Se connecter sans mot de passe :
    Désormais, la commande ssh utilisateur@adresse_ip_du_serveur vous connectera instantanément et de manière plus sécurisée.

3. Procédures de gestion courantes

    Changer le port par défaut (Sécurité) : Par défaut, SSH utilise le port 22. Les administrateurs le modifient souvent dans le fichier de configuration du serveur (/etc/ssh/sshd_config) pour éviter les attaques automatisées. Si le port est modifié (par exemple, 2222), connectez-vous avec l'option -p :
    

    ssh -p 2222 utilisateur@adresse_ip_du_serveur

    Quitter la session : Pour fermer proprement la connexion à distance, tapez simplement :
    Bash

    exit