# Accéder au Serveur

## Se connecter à votre serveur

Ouvrir le terminal et faire une connexion sécurisée à distance via le protocol [SSH](https://tools.ietf.org/html/rfc4251).

Changer les champs nécessaires où:

*username* = nom d'utilistateur de votre serveur.

*ipaddress* = l'adresse IP de votre serveur.

>```ssh -l username ipaddress```

ou

>```ssh username@ipaddress```

Confirmer l'installation en tapant "Y" après le message:
```Do you want to continue? [Y/n]```

La connexion vous demandera de taper un mot de passe.

*Tapez le mot de passe enregistré dans le serveur.*

Un message de bienvenue est affiché:
```Welcome to Ubuntu 18.04.2 LTS```

### Mise à jour et mise à niveau

Faire le mise à jour des paquets installés sur Ubuntu Server avec la commande:

>```sudo apt update```

 Après cela, faire le mise à niveau:

>```sudo apt upgrade```

La connexion vous demandera de taper un mot de passe.

*Tapez le mot de passe enregistré dans le serveur.*

Confirmer l'installation en tapant "Y" après le message:
```Do you want to continue? [Y/n]```

Suivante: [Installer Apache2 Web Server](03-installer-apache2.md)