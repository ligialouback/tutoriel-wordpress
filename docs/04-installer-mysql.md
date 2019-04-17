# Installer MySQL Server

MySQL Server est un serveur de base de données SQL (Structured Query Language).

WordPress utilise MySQL pour stocker et récupérer toutes les informations de votre blog.

Pour que Wordpress fonctionne, il faut d'abord installer MySQL Server sur Ubuntu Server.

## Procédure d'installation

Dans le terminal, entrer la commande suivante:

>```sudo apt install mysql-server```

La connexion vous demandera de taper un mot de passe.
*Tapez le mot de passe enregistré dans le serveur.*

Confirmer l'installation en tapant "Y" après le message:
```Do you want to continue? [Y/n]```

Pour vérifier que MySQL a été installé, entrer la commande suivante:

>```dpkg --get-selections | grep mysql```

Cette commande affiche tous les paquets installés contenant "mysql" dans leur nom.

Exemple de sortie: ```mysql-server install```

Pour connaître le chemin où MySQL a été installé, entrer la commande suivante:

>```which mysql```

Exemple de sortie: ```/usr/bin/mysql```

Une fois que l'installation est terminée, le serveur MySQL devrait être démarré automatiquement.

Exécuter la commande suivante pour vérifier si le serveur MySQL est en cours d'exécution:

>```sudo netstat -tap | grep mysql```

Exemple de sortie: ```tcp        0      0 localhost.localdo:mysql 0.0.0.0:*               LISTEN      29036/mysqld```

Si le serveur ne fonctionne pas correctement, taper la commande suivante pour le démarrer mysql:

>```systemctl restart mysql.service```

Taper le mot de passe:

>==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to restart 'mysql.service'.
Authenticating as: username
Password:

Exemple de sortie: ==== AUTHENTICATION COMPLETE ===

Suivante: [Installer Wordpress](05-installer-wordpress.md)