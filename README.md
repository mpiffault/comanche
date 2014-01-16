
Comanche Serveur Web en Perl / Projet DA2i
======

Binôme
------

- Elodie JOLY
- Martin PIFFAULT

Résumé
------

Fonctionnalités implémentées et opérationnelles.

  - [X] gestion du port d'écoute
  - [X] protocole HTTP/1.1
  - [X] gestion de la page par défaut
  - [X] gestion des fichiers index dans les répertoires
  - [X] gestion des logs
  - [X] gestion des clients en //
  - [X] gestion du max de clients
  - [X] routes statiques
  - [X] routes avec expression régulière
  - [X] cgi statiques
  - [X] cgi avec expression régulière
  - [X] paramètres de cgi


Détail
------

La plupart des fonctionnalitées sont pleinement opérationnelles. Les défauts constatés sont les suivants:

  - La validitée logique des paramètres du fichier de configuration n'est pas vérifiée (port d'écoute valide, existence des fichiers default ou basedir).

  - Dans les routes avec expression régulière, la partie gauche est bien utilisée comme telle, mais seul une correspondance avec le premier groupement est faite dans la partie droite. L'ajout d'un autre référence que \1 entrainera une nullité de la route.

  - Paramètres CGI: la validité de la chaine des variables n'est pas vérifiée.

  - La fonction status écrit sur la sortie standard du terminal sur lequel il a été démarré.

  - La fonction reload ne prend pas en compte un changement de port (mais conseille à l'utilisateur de redémarrer).

Développement
=============

Implémentation
--------------

  - Le PID du service est conservé dans un fichier .comanche.pid, protégé en écriture.

  - Le type mime des fichiers est déterminé avec la fonction mimetype() de File::MimeInfo.

  - Les erreurs 503 Service Unavailable sont envoyées par le répartiteur lui même.

  - Si le fichier de configuration est mal formé, comanche ne démarre pas et indique où l'erreur a été détectée.

  - Les paramètres du fichier de configuration sont stockés dans un hachage.

  - Pour les routes avec expression régulière, le \1 de l'expression de droite est remplacée explicitement par le contenu du premier groupement de l'expression de gauche.

  - Pour les variables des CGI, seule la variable d'environnement QUERY_STRING est définie. D'autre part, la recherche des paramètres se fait sur la chaine de requête. Étant donné que seul le premier regroupement est pris en compte, il faut créer les route vers les cgi en prenant garde à bien isoler le nom du script (cad ne pas grouper les paramètres avec le nom de la page). Cf fichier de configuration joint.

  - Lors de l'arrêt du daemon, celui-ci attend la fin de tous les ouvriers.

Gestion
-------

M. PIFFAULT a traité la partie système (Gestion des signaux, processus, etc.), le traitement des requêtes, la construction des réponses, le log.

E. JOLY a traité la lecture du fichier de configuration, le listage des dossiers et la gestion des CGI + paramètres.

Autres
------

Les fonctionnalités supplémentaires basedir et reload ont été implémentées.

Le projet est sur github : https://github.com/mpiffault avec des dossiers correspondants au fichier de configuration tel qu'il est.