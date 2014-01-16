
Projet
======

Bin�me
------

- Elodie JOLY
- Martin PIFFAULT

R�sum�
------

Cochez (en mettant un X) les fonctionnalit�s qui sont impl�ment�es **et** op�rationnelles dans votre projet.

  - [X] gestion du port d'�coute
  - [X] protocole HTTP/1.1
  - [X] gestion de la page par d�faut
  - [X] gestion des fichiers index dans les r�pertoires
  - [X] gestion des logs
  - [X] gestion des clients en //
  - [X] gestion du max de clients
  - [X] routes statiques
  - [X] routes avec expression r�guli�re
  - [X] cgi statiques
  - [X] cgi avec expression r�guli�re
  - [X] param�tres de cgi


D�tail
------

La plupart des fonctionnalit�s sont op�rationnelle. Les d�fauts constat�s sont les suivants:

  - La validit�e logique des param�tres du fichier de configuration n'est pas v�rifi�e (port d'�coute valide, existence des fichiers default ou basedir).

  - Dans les routes avec expression r�guli�re, la partie gauche est bien utilis�e comme telle, mais seul une correspondance avec le premier groupement est faite dans la partie droite. L'ajout d'un autre r�f�rence que \1 entrainera une nullit� de la route.

  - Param�tres CGI: la validit� de la chaine des variables n'est pas v�rifi�e.

  - La fonction status �crit sur la sortie standard du terminal sur lequel il a �t� d�marr�.

  - La fonction reload ne prend pas en compte un changement de port (mais pr�vient l'utilisateur).

D�veloppement
=============

Impl�mentation
--------------

Le PID du service est conserv� dans un fichier .comanche.pid, prot�g� en �criture.

Le type mime des fichiers est d�termin� avec la fonction mimeinfo() de File::MimeInfo.



Gestion
-------

Expliquez ici en quelques lignes comment a �t� faite la r�partition des t�ches dans le d�veloppement du projet entre les membres du bin�me, puis supprimez cette ligne.

Autres
------

Donnez ici toutes les autres informations qui vous paraissent importantes.
