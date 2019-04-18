# Installer WordPress

Dans le terminal, entrer la commande suivante:

>```sudo apt install wordpress```

Confirmer l'installation en tapant "Y" après le message:
```Do you want to continue? [Y/n]```

## Configuration Apache2

Pour configurer votre première application WordPress, il faut premièrement configurer un site Web Apache.

Pour que cela se produise, il faut éditer le fichier *wordpress.conf* qui se trouve dans le chemin */etc/apache2/sites-available*. 

Pour vérifier qu’il déjà existe, utiliser la commande suivante: 

>```ls /etc/apache2/sites-available```

Exemple de sortie: ```000-default.conf  default-ssl.conf  wordpress.conf```

Si le fichier *wordpress.conf* n’existe pas, il devrait être créé.

Avec les commandes ci-dessous, il est possible de créer le fichier *wordpress.conf* et au même temps de le modifier.

Dans le terminal, passer à un autre utilisateur avec les privilèges *root*:

>```sudo su```

La connexion vous demandera de taper un mot de passe.

*Taper le mot de passe enregistré dans le serveur.*

Exemple de sortie: ```root@username:/home/username#```

Entrer le code suivant pour rediriger vers le chemin et pour l’ajouter au fichier *wordpress.conf*.

Si le fichier *wordpress.conf* n’existe pas, il sera créé:

> ```
> cat > /etc/apache2/sites-available/wordpress.conf <<EOF
> Alias /blog /usr/share/wordpress
> <Directory /usr/share/wordpress>
>    Options FollowSymLinks
>    AllowOverride Limit Options FileInfo
>    DirectoryIndex index.php
>    Order allow,deny
>    Allow from all
> </Directory>
> <Directory /usr/share/wordpress/wp-content>
>    Options FollowSymLinks
>    Order allow,deny
>    Allow from all
> </Directory>
> EOF
> ```

À la fin, taper *enter* pour fermer le fichier.

Pour sortir de l'utilisateur avec les privilèges *root*, taper:

> ```exit```

Vérifier que le fichier a été créé:

> ```ls /etc/apache2/sites-available```

Exemple de sortie: ```000-default.conf  default-ssl.conf  wordpress.conf```

Vérifier le contenu de le fichier:

> ```cat /etc/apache2/sites-available/wordpress.conf```

Pour activer ce nouveau site wordPress, taper:

> ```sudo a2ensite wordpress```

Exemple de sortie:

```
Enabling site wordpress.
To activate the new configuration, you need to run:
  systemctl reload apache2
```

Lancer la commande:

> ```systemctl reload apache2```

Taper le mot de passe:

> ==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ===
Authentication is required to reload 'apache2.service'.
Authenticating as: username
Password:

Exemple de sortie: ```==== AUTHENTICATION COMPLETE ===```

### Configurer WordPress pour utiliser une base de données MySQL

Dans le terminal, passer à un autre utilisateur avec les privilèges *root*:

> ```sudo su```

Entrer le code suivant pour rediriger vers le chemin et pour l’ajouter au fichier *config-localhost.php*.

Si le fichier *config-localhost.php* n’existe pas, il sera créé:

Changer les champs nécessaires où:

*yourpasswordhere* = le mot de passe enregistré dans votre serveur.

>```
>cat > /etc/wordpress/config-localhost.php <<EOF
><?php
>define('DB_NAME', 'wordpress');
>define('DB_USER', 'wordpress');
>define('DB_PASSWORD', 'yourpasswordhere');
>define('DB_HOST', 'localhost');
>define('WP_CONTENT_DIR', '/usr/share/wordpress/wp-content');
>?>
>EOF
>```

À la fin, taper *enter* pour fermer le fichier.

Pour sortir de l'utilisateur avec les privilèges *root*, taper:

> ```exit```

Vérifier que le fichier a été créé:

> ```ls /etc/wordpress/```

Exemple de sortie: ```config-localhost.php  htaccess```

Vérifier le contenu de le fichier:

> ```cat /etc/wordpress/config-localhost.php```

### Créer cette base de données MySQL

Entrer le code suivant pour rediriger vers le chemin et pour l’ajouter au fichier *wordpress.sql*.

Si le fichier *wordpress.sql* n’existe pas, il sera créé:

Changer les champs nécessaires où:

*yourpasswordhere* = le mot de passe enregistré dans votre serveur.

>```
>cat > wordpress.sql <<EOF
>CREATE DATABASE wordpress;
>GRANT SELECT,INSERT,>UPDATE,DELETE,CREATE,DROP,ALTER
>ON wordpress.*
>TO wordpress@localhost
>IDENTIFIED BY 'yourpasswordhere';
>FLUSH PRIVILEGES;
>EOF
>```

Vérifier que le fichier a été créé:

>```ls wordpress.sql```

Exemple de sortie: ```wordpress.sql```

Vérifier le contenu de le fichier:

> ```cat wordpress.sql```

Changer le contenu de *wordpress.sql* par le default fichier de mysql:

> ```cat wordpress.sql | sudo mysql --defaults-extra-file=/etc/mysql/debian.cnf```

Aller au fichier *wordpress*:

> ```cd /etc/wordpress/```

Modifier le fichier:

> ```sudo mv config-localhost.php config-192.168.0.105.php```

Suivante: [Accéder à WordPress](06-acceder-wordpress.md)