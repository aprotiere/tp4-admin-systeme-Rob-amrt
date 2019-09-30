# Welcome to StackEdit!


## Exercice 1. Gestion des utilisateurs et des groupes 
#### • Commencez par créer deux groupes groupe1 et groupe2
Avec la commande ``addgroup groupe1 && addgroup groupe2``

#### • Créez ensuite 4 utilisateurs u1, u2, u3, u4 avec la commande useradd, en demandant la création de leur dossier personnel et avec bash pour shell
Avec la commande ``useradd -m [nom_utilisateur]``

#### Placez les utilisateurs dans les groupes : - u1, u2, u4 dans groupe1 - u2, u3, u4 dans groupe2

Avec la commande ``gpasswd groupe1 -M u1,u2,u4`` pour le groupe1

Avec la commande ``gpasswd groupe2 -M u2,u3,u4`` pour le groupe2

#### • Donnez deux moyens d’afficher les membres de groupe2
Avec la commande : ``grep '^groupe2' /etc/group``

####  • Faites de groupe1 le groupe propriétaire de /home/u1 et /home/u2 et de groupe2 le groupe propriétaire de /home/u3 et /home/u4
Avec la commande ``chown :[nom_groupe] [chemin_dossier]``

####  • Remplacez le groupe primaire des utilisateurs :
  - groupe1 pour u1 et u2 
Avec la commande : ``usermod u1 -g groupe1``  puis  
``usermod u2 -g groupe1``

- groupe2 pour u3 et u4 
Avec la commande : ``usermod u3 -g groupe2`` puis ``usermod u4 -g groupe2``

#### • Créez deux répertoires /home/groupe1 et /home/groupe2 pour le contenu commun aux groupes, et mettez en place les permissions permettant aux membres de chaque groupe d’écrire dans le dossier associé.
Avec la commande ``chmod 720 [nom_dossier]``

#### • Comment faire pour que, dans ces dossiers, seul le propriétaire d’un fichier ait le droit de renommer ou supprimer ce fichier ?
Grace à la mise en place d'un sticky bit.
Avec par exemple la commande ```chmod 1720 [nom_dossier]``

#### • Pouvez-vous vous connecter en tant que u1 ? Pourquoi ?
Non on ne peut pas se connecter sur u1 car le mot de passe de login n'existe pas.

#### • Activez le compte de l’utilisateur u1 et vérifiez que vous pouvez désormais vous connecter avec son compte.
Pour activer le compte u1, il faut utiliser la commande ``passwd u1``
Il faut initialiser un nouveau mot de passe. 
Il est maintenant possible de se connecter.


