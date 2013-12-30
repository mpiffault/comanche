Comanche
--------

Un mini-serveur web en Perl.

### AUTEURS

Elodie Joly
Martin Piffault

### AVERTISSEMENT

Work in progress : ce morceau de code n'est pas encore fonctionnel...

### DESCRIPTION

Comanche est un mini serveur web écrit dans le cadre d'un projet d'étude.
Le but est d'avoir un petit serveur portable et robuste qui fait peu de choses mais le fait correctement.

S'assurer qu'un fichier comanche.conf correctement écrit (cf. CONFIGURATION) est présent à la racine du dossier.

### UTILISATION

comanche fonctionne comme un daemon:

Pour démarrer le serveur
comanche start

Pour l'arrêter
comanche stop

### CONFIGURATION

La configuration se fait par l'intermédiaire d'un fichier comanche.conf situé dans le même répertoire que comanche. La syntaxe attendue y est la suivante (configuration type) :

    #### comanche.conf ####
    # Port d'écoute
    set port 8088

    # Page renvoyée par défaut
    set default /var/www/index.html

    # Fichier d’index dans les répertoires
    set index index.html

    # Nombre maximal N de requêtes simultanées (>0)
    set clients 10

    # Journal des évènements
    set logfile comanche.log

    # Préfixe des chemins des projections
    set basedir /var/www

    # Routes de projection fichiers
    route ^/(.*)$ to /var/www/\1

    # Routes de projection CGI
    exec ^/(.*)\.exe$ from /var/lib/cgi/\1

    #### ####

### TODO

-    Application
     * Implémentation de la comande 'status' qui doit renvoyer l'état du serveur.
     * Gestion plus fine des ouvriers (enregistrement de leur pid, nombre depuis le démarrage du serveur)
     * Log des événement de démarrage et d'arrêt

-    Dialogue réseau
     * Implémentation de la réponse à la requète (réponse par défaut pour l'instant) comprend notament la gestion des routes, l'ouverture, la lecture et l'envoi au client du contenu du fichier
     * Gestion des fichier text, html et jpg
     * Gestion des cgi
