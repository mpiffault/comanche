
Projet
======

Binôme
------

- Elodie JOLY
- Martin PIFFAULT

Résumé
------

Cochez (en mettant un X) les fonctionnalités qui sont implémentées **et** opérationnelles dans votre projet.

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

La plupart des fonctionnalités sont opérationnelle. Les défauts constatés sont les suivants:

  - La validitée logique des paramètres du fichier de configuration n'est pas vérifiée (port d'écoute valide, existence des fichiers default ou basedir).

  - Dans les routes avec expression régulière, la partie gauche est bien utilisée comme telle, mais seul une correspondance avec le premier groupement est faite dans la partie droite. L'ajout d'un autre référence que \1 entrainera une nullité de la route.

  - Paramètres CGI: la validité de la chaine des variables n'est pas vérifiée.

  - La fonction status écrit sur la sortie standard du terminal sur lequel il a été démarré.

  - La fonction reload ne prend pas en compte un changement de port (mais prévient l'utilisateur).

Développement
=============

Implémentation
--------------

Le PID du service est conservé dans un fichier .comanche.pid, protégé en écriture.

Le type mime des fichiers est déterminé avec la fonction mimeinfo() de File::MimeInfo.



Gestion
-------

Expliquez ici en quelques lignes comment a été faite la répartition des tâches dans le développement du projet entre les membres du binôme, puis supprimez cette ligne.

Autres
------

Donnez ici toutes les autres informations qui vous paraissent importantes.
