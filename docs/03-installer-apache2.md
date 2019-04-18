# Installer Apache2 Web Server

Apache est le serveur Web le plus utilisé sur les systèmes Linux.

Les serveurs Web sont utilisés pour servir les pages Web demandées par les ordinateurs clients.

Les clients demandent et affichent généralement des pages Web à l'aide d'applications de navigateur Web telles que Firefox, Opera, Chromium ou Internet Explorer.

Pour que Wordpress fonctionne, il faut d'abord installer Apache2 Web Server sur Ubuntu Server.

## Procédure d'installation

Dans le terminal, entrer la commande suivante:

>```sudo apt install apache2```

La connexion vous demandera de taper un mot de passe.

*Tapez le mot de passe enregistré dans le serveur.*

Confirmer l'installation en tapant "Y" après le message:
```Do you want to continue? [Y/n]```

Pour vérifier que Apache2 a été installé, entrer la commande suivante:

>```dpkg --get-selections | grep apache```

Cette commande affiche tous les paquets installés contenant *apache* dans leur nom.

Exemple de sortie: ```apache2 install```

Pour connaître le chemin où Apache2 a été installé, entrer la commande suivante:

>```which apache2```

Exemple de sortie: ```/usr/sbin/apache2```

Suivante: [Installer MySQL Server](04-installer-mysql.md)