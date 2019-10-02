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
Non on ne peut pas se connecter sur u1 car le mot de passe de login n'existe pas car la commande ``useradd`` ne génère pas automatiquement de mot de passe à la création d'un utilisateur.

#### • Activez le compte de l’utilisateur u1 et vérifiez que vous pouvez désormais vous connecter avec son compte.
Pour activer le compte u1, il faut utiliser la commande ``passwd u1``
Il faut initialiser un nouveau mot de passe. 
Il est maintenant possible de se connecter.

#### • Quels sont l’uid et le gid de u1 ?
Grace à la commande ``id u1`` on peut voir que son uid et gid est 1001.

#### • Quel utilisateur a pour uid 1003 ?
L'utilisateur u3 à pour uid 1003 car il est le troisième utilisateur à avoir été créé.

#### • Quel est l’id du groupe groupe1 ?
Le gid du groupe 1 est 1001 car il est le premier groupe à avoir été créé.

#### • Quel groupe a pour gid 1002 ? (Rien n’empêche d’avoir un groupe dont le nom serait 1002...)
Avec la commande ``grep "1002" /etc/group`` on peut voir que c'est le groupe 2 qui possède le gid 1002

#### • Retirez l’utilisateur u3 du groupe groupe2. Que se passe-t-il ? Expliquez.
Avec la commande ``gpasswd -d u3 groupe2`` on retire u3 du groupe 2. Il ne peut donc plus accéder au dossier groupe2 car celui-ci n'est plus dans le groupe2.

#### • Modifiez le compte de u4 de sorte que : 
— il expire au 1 er juin 2019 
Avec la commande ``usermod --expiredate 06/01/2019 u4``
— il faut changer de mot de passe avant 90 jours 
``chage -M 90 u4``
— il faut attendre 5 jours pour modifier un mot de passe 
``chage -m 5 u4``
— l’utilisateur est averti 14 jours avant l’expiration de son mot de passe 
``chage -W 14 u4``
— le compte sera bloqué 30 jours après expiration du mot de passe
``chage -I 30 u4``

#### • Quel est l’interpréteur de commandes (Shell) de l’utilisateur root ?
Avec la commande ``echo $SHELL`` ce qui donne /bin/bash

#### • à quoi correspond l’utilisateur nobody ?
nobody est le nom conventionnel d'un compte d'utilisateur à qui aucun fichier n'appartient, qui n'est dans aucun groupe qui a des privilèges et dont les seules possibilités sont celles que tous les "autres utilisateurs" ont.

#### 19- Par défaut, combien de temps la commande sudo conserve-t-elle votre mot de passe en mémoire ? Quelle commande permet de forcer sudo à oublier votre mot de passe ?
Le temps par défaut est 15 minute.
La commande pour forcer sudo à oublier son mot de passe est `sudo -k`


