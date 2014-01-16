
Comanche Serveur Web en Perl / Projet DA2i
======

Bin�me
------

- Elodie JOLY
- Martin PIFFAULT

R�sum�
------

Fonctionnalit�s impl�ment�es et op�rationnelles.

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

La plupart des fonctionnalit�es sont pleinement op�rationnelles. Les d�fauts constat�s sont les suivants:

  - La validit�e logique des param�tres du fichier de configuration n'est pas v�rifi�e (port d'�coute valide, existence des fichiers default ou basedir).

  - Dans les routes avec expression r�guli�re, la partie gauche est bien utilis�e comme telle, mais seul une correspondance avec le premier groupement est faite dans la partie droite. L'ajout d'un autre r�f�rence que \1 entrainera une nullit� de la route.

  - Param�tres CGI: la validit� de la chaine des variables n'est pas v�rifi�e.

  - La fonction status �crit sur la sortie standard du terminal sur lequel il a �t� d�marr�.

  - La fonction reload ne prend pas en compte un changement de port (mais conseille � l'utilisateur de red�marrer).

D�veloppement
=============

Impl�mentation
--------------

  - Le PID du service est conserv� dans un fichier .comanche.pid, prot�g� en �criture.

  - Le type mime des fichiers est d�termin� avec la fonction mimetype() de File::MimeInfo.

  - Les erreurs 503 Service Unavailable sont envoy�es par le r�partiteur lui m�me.

  - Si le fichier de configuration est mal form�, comanche ne d�marre pas et indique o� l'erreur a �t� d�tect�e.

  - Les param�tres du fichier de configuration sont stock�s dans un hachage.

  - Pour les routes avec expression r�guli�re, le \1 de l'expression de droite est remplac�e explicitement par le contenu du premier groupement de l'expression de gauche.

  - Pour les variables des CGI, seule la variable d'environnement QUERY_STRING est d�finie. D'autre part, la recherche des param�tres se fait sur la chaine de requ�te. �tant donn� que seul le premier regroupement est pris en compte, il faut cr�er les route vers les cgi en prenant garde � bien isoler le nom du script (cad ne pas grouper les param�tres avec le nom de la page). Cf fichier de configuration joint.

  - Lors de l'arr�t du daemon, celui-ci attend la fin de tous les ouvriers.

Gestion
-------

M. PIFFAULT a trait� la partie syst�me (Gestion des signaux, processus, etc.), le traitement des requ�tes, la construction des r�ponses, le log.

E. JOLY a trait� la lecture du fichier de configuration, le listage des dossiers et la gestion des CGI + param�tres.

Autres
------

Les fonctionnalit�s suppl�mentaires basedir et reload ont �t� impl�ment�es.

Le projet est sur github : https://github.com/mpiffault avec des dossiers correspondants au fichier de configuration tel qu'il est.