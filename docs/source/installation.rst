Installation de Docker sur différents systèmes
==============================================

L'objectif de ce document est de conduire le lecteur pas à pas à travers l'installation de Docker sur différentes plateformes: macos, windows (Pro, Education, Home/Famille), Debian et Ubuntu.

Installation sous macos
-----------------------

La présente section va vous conduire pas à pas dans l'installation de Docker pour Macos. Avant de commencer, voici les pré-requis système nécessaires pour que cette installation fonctionne:

- Votre mac doit être plus récent que 2010. Vous pouvez tester si votre machine possède le support harware nécessaire en exécutant la commande suivante dans un terminal: sysctl kern.hv_support. Cette dernière doit afficher la valeur 1.
- Votre version de macos doit être plus récente que El Capitan 10.11.
- Vous devez avoir au minimum 4 GB de RAM
- Si virtualbox est installé sur votre ordinateur, il faut que ce soit une version plus récente que 4.3.30. Docker for Mac d'utilise pas virtualbox, mais il y a des incompatibilités avec les anciennes versions de vitualbox.
- Si votre système ne rempli pas un des ces pré-requis, vous pouvez toujours installer `Docker Toolbox <https://docs.docker.com/toolbox/overview/>`_.

Voici la procédure d'installation:

1. Télécharger Docker.dmg depuis `le site officiel <https://store.docker.com/editions/community/docker-ce-desktop-mac>`_.
2. Double-cliquez sur l'image Docker.dmg afin d'ouvrir l'installeur et glissez/déposez le logo Docker sur le dossier Applications.

.. image:: https://docs.docker.com/docker-for-mac/images/docker-app-drag.png
  :width: 500px
  :align: center

4. Double-cliquez sur Docker.app dans votre répoertoire Application afin de démarrer Docker. Votre OS va vous demander d'authoriser Docker.app à accéder à votre ordinateur avec un accès privilégié en fournissant votre mot de passe. Cet accès privilégié est nécessaire pour que Docker puisse installer les composants réseau.
5. L'icone de balaine dans votre bar de status signifie que Docker est en train de tourner et qu'il est accessible depuis votre terminal. En cliquant sur cet icone, vous avez accès aux préférences et autres options.

Voilà, vous avez installé Docker avec succès. Afin de tester si votre installation fonctionne, tapez les lignes suivantes dans un terminal::

  $ docker --version
  Docker version 18.03, build c97c6d6

  $ docker-compose --version
  docker-compose version 1.23.1, build 8dd22a9

  $ docker-machine --version
  docker-machine version 0.14.0, build 9ba6da9
  
Finalement, on peut tester si un serveur web tel que nginx fonctionne en exécutant la commande suivante dans votre terminal::

  $ docker run --rm -p 80:80 --name webserver nginx
  
Une fois cette commande exécutée, vous devriez pouvoir ouvrir un navigateur web, vou srendre à l'adresse `localhost <http://localhost>`_ et voir s'afficher une page telle que celle-ci:

.. image:: https://gyazo.com/4ffcaebd22e46635bb54709fd266bddf.png
  :width: 500px
  :align: center

  
Installation sous Windows
-------------------------

L'installation windows va être différente selon votre version de l'OS. En effet, si vous disposez d'une version Pro ou Entreprise ou Education (1607 Anniversary Update, Build 14393 ou plus récent), vous pouvez bénéficier d'une version native de Docker. Si vous disposez d'une version Windows Home ou Famille, nous utiliserons Docker Toolbox.

Dans tous les cas, il va vous falloir vous assurer que les fonctionnalités de virtualisation sont activées dans votre BIOS ou UEFI, ce qui est le cas par défaut sur beaucoup de machines, mais pas toutes. Pour effectuer cette vérification:

- Si vous êtes sur Windows 10, installer `Speccy <https://www.ccleaner.com/speccy/download/standard>`_. Lorsque vous démarrez ce logiciel, regarder sur l'onglet CPU Information pour vérifier si la virtualisation est supportée et activée.

.. image:: https://i.gyazo.com/789e3e234bbf3348f18de154338c4ea4.png 
  :width: 500px
  :align: center

- Si vous êtes sur Windows 8, choisissez **Start > Task Manager** et rendez-vous sur l'onglet **Performance**. Sous CPU, vous pouvez voir si la virtualisation est activée.

**Si la vitualisation n'est pas activée dans le BIOS ou l'UEFI**, il faut l'activer. Pour savoir comment procéder, taper dans google le modèle de votre ordinateur suivi de "enable virtualization". Vous trouverez alors très rapidement une procédure adaptée pour activer cette fonctionnalité.

Installation sous Windows Pro, Entreprise ou Education
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Après avoir vérifié que la virtualisation était supportée et activée (voir ci-dessus), nous 
allons pouvoir installer **Docker for windows**. Ces instructions ont été testées sur un 
Windows 10 Education (build?) installer sur un Laptop HP EliteBook. Les pré-requis système 
suivants doivent être vérifié pour installer Docker for Windows:

- Windows 10 64bits: Pro, Enterprise or Education (1607 Anniversary Update, 
  Build 14393 ou plus récent)
- Le CPU doit avoir un support du second niveau de translation d’adresse 
  (SLAT - Second Level Address Translation). C'est normalement le cas sur les machines relativement 
  récente (2010+).
- Au moins 4 GB de RAM
- Si votre système ne rempli pas un des ces pré-requis, vous pouvez toujours installer 
  `Docker Toolbox <https://docs.docker.com/toolbox/overview/>`_.

Voici la procédure d'installation:

1. Télécharger Docker for Windows Installer.exe depuis 
   `le site officiel de Docker <https://store.docker.com/editions/community/docker-ce-desktop-windows>`_ 
   et exécutez l'installeur.
2. Suivez la procédure, acceptez la licence et procédez à l'installation. Cliquez sur Finish une 
   fois l'installation terminer et Docker démarrera automatiquement. Si Docker ne démarre pas, vous pouvez chercher Docker for Windows dans vos applications et le démarrer manuellement.

.. image:: https://docs.docker.com/docker-for-windows/images/docker-app-search.png
  :width: 250px
  :align: center
  
3. Rendez-vous dans les settings de Docker qui faisant un click-droit sur l'icone Docker ci-dessous:

.. image:: https://i.gyazo.com/9c6dbe741cd5b50ba31260242fc57dff.png 
  :width: 300px
  :align: center
  
4. Une fois dans les settings, rendez-vous dans Shared Drives et sélectionnez les disques 
   que vous désirez partager entre Windows et Docker, puis valider votre sélection avec Apply:

.. image:: https://i.gyazo.com/27422d04f4a6e198563007ee5be77711.png
  :width: 500px
  :align: center

Voilà, vous avez installé Docker avec succès. Afin de tester si votre installation fonctionne, tapez les lignes suivantes dans un terminal PowerShell ou cmd.exe::

  $ docker --version
  Docker version 18.03, build c97c6d6

  $ docker-compose --version
  docker-compose version 1.23.1, build 8dd22a9

  $ docker-machine --version
  docker-machine version 0.14.0, build 9ba6da9
  
Finalement, on peut tester si un serveur web tel que nginx fonctionne en exécutant la commande suivante dans votre terminal::

  $ docker run --rm -p 80:80 --name webserver nginx
  
Une fois cette commande exécutée, vous devriez pouvoir ouvrir un navigateur web, vou srendre à l'adresse `localhost <http://localhost>`_ et voir s'afficher une page telle que celle-ci:

.. image:: https://gyazo.com/4ffcaebd22e46635bb54709fd266bddf.png"
  :width: 500px
  :align: center

Installation sous Windows Home ou Famille
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Après avoir vérifié que la virtualisation était supportée et activée (voir `Installation sous Windows 64 bits`_) 
et avoir vérifié que votre windows est bien une version 64 bits, voici la procédure d'installation 
pour Docker Toolbox. Ces instructions a été testée sur un Windows 10 Home 64bits à jour installés 
sur différentes machines.

- Télécharger la dernière version de `Virtualbox <https://download.virtualbox.org/virtualbox/5.2.20/VirtualBox-5.2.20-125813-Win.exe>`_ 
  depuis le site officiel et exécuter l'installeur en acceptant la licence et en suivant les instructions.
- Télécharger `DockerToolbox.exe <https://download.docker.com/win/stable/DockerToolbox.exe>`_ 
  depuis le site officiel et exécuter l'installer puis accepter la licence.
- Décocher Virtualbox dans les options d'installation (l'installeur utilise une ancienne version de 
  virtualbox), car nous avons déjà installé la version la plus récente

.. image:: https://i.gyazo.com/57544ba378295ac4fdba53135f208196.png
  :width: 500px
  :align: center
  
- Continuer l'installation en suivant les recommandations de l'installeur.
- Executer Docker Quickstart Terminal et attendre que le script d'installation se termine.

.. image:: https://i.gyazo.com/51d0bbd1d17717dc9d65b7ff70e41c53.png
  :width: 500px
  :align: center

- Lorsque tout est installé, Docker Quickstart Terminal affiche une invite de commande

.. image:: https://i.gyazo.com/2a330cc3fce498fa4ac062e6b463b226.png
  :width: 500px
  :align: center
  
Voilà, vous avez installé Docker avec succès. Afin de tester si votre installation fonctionne, tapez 
les lignes suivantes dans le Docker Quickstart Terminal::

  $ docker --version
  Docker version 18.03, build c97c6d6

  $ docker-compose --version
  docker-compose version 1.23.1, build 8dd22a9

  $ docker-machine --version
  docker-machine version 0.14.0, build 9ba6da9
  
Finalement, on peut tester si un serveur web tel que nginx fonctionne en exécutant la commande 
suivante dans votre terminal::

  $ docker run --rm -p 80:80 --name webserver nginx
  
Une fois cette commande exécutée, vous devriez pouvoir ouvrir un navigateur web, vou srendre à 
l'adresse ip suivante `192.168.99.100 <http://192.168.99.100>`_ et voir s'afficher une page telle que celle-ci:

.. image:: https://i.gyazo.com/f9d58a1464ad69be71d6e599bf347d44.png
  :width: 500px
  :align: center
  
Installation sous Debian
------------------------

La meilleure solution pour une installation complète de Docker, Docker-Compose et Docker-Machine sur 
Debian est d'utiliser les dépôts officiels de Docker. La procédure qui suit va vous guider dans une
installation complète de ces outils. Les instructions présentées ci-dessous sont une synthèse tirée
directement de la documentation de Docker. Elles ont été testées sur Debian Stretch et Debian Buster 
(testing).

- Mettez à jour vos paquets::
  
    $ sudo apt update
    
- Installer les pré-requis::

  $ sudo apt install apt-transport-https ca-certificates curl gnupg2 software-properties-common
  
- Ajouter la clé GPG pour le dépôt officiel de Docker::

  $ curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
  
- Ajouter le repo officiel de Docker aux sources de apt::

  $ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
  
- Mettre à jour la base de données des paquets de apt::

  $ sudo apt update
  
- Assurez-vous que vous aller installer Docker à partir du repo officiel de Docker et non à partir des dépôts par défaut de Debian::

  $ apt-cache policy docker-ce
  
Vous verrez ceci, même si les numéros de version peuvent varier::

  docker-ce:
    Installed: (none)
    Candidate: 18.06.1~ce~3-0~debian
    Version table:
      18.06.1~ce~3-0~debian 500
        500 https://download.docker.com/linux/debian stretch/stable amd64 Packages
        
Notez que docker-ce n'est pas installé, mais que le candidat à l'installation provient du repo officiel 
de Docker pour Debian

- Finalement, installez Docker CE::

  $ sudo apt install docker-ce
  
- Ajoutez votre utilisateur au groupe docker::

  $ sudo usermod -aG docker ${USER}
  
- Pour que l'ajout au groupe docker soit actif, exécutez la commande suivante::

  $ su - ${USER}

- Vérifiez que votre utilisateur appartient au groupe docker::

  $ id -nG

- Télécharger la dernière version de Docker Compose::

  $ sudo curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

- Donner les permissions nécessaires à docker-compose::

  $ sudo chmod +x /usr/local/bin/docker-compose

- Télécharger et installer Docker Machine avec la commande suivante::

  $ base=https://github.com/docker/machine/releases/download/v0.14.0 &&
  mkdir -p "$HOME/bin" &&
  curl -L $base/docker-machine-Windows-x86_64.exe > "$HOME/bin/docker-machine.exe" &&
  chmod +x "$HOME/bin/docker-machine.exe"

Voilà, vous avez installé Docker avec succès. Afin de tester si votre installation fonctionne, tapez 
les lignes suivantes dans un termina::

  $ docker --version
  Docker version 18.03, build c97c6d6

  $ docker-compose --version
  docker-compose version 1.23.1, build 1719ceb

  $ docker-machine version
  docker-machine version 0.14.0, build 9371605
  
Finalement, on peut tester si un serveur web tel que nginx fonctionne en exécutant la commande 
suivante dans votre terminal::

  $ docker run --rm -p 80:80 --name webserver nginx
  
Une fois cette commande exécutée, vous devriez pouvoir ouvrir un navigateur web, vou srendre à 
l'adresse `localhost <http://localhost>`_ et voir s'afficher une page telle que celle-ci:

.. image:: https://gyazo.com/4ffcaebd22e46635bb54709fd266bddf.png
  :width: 500px
  :align: center

Installation sous Ubuntu
------------------------

Pour une installation complète de Docker, Docker-Compose et Docker-Machine sur 
Ubuntu, la méthode recommandée est d'utiliser les dépôts officiels de Docker pour Ubuntu. 
La procédure qui suit va vous guider dans une installation complète de ces outils. Les 
instructions présentées ci-dessous sont une synthèse tirée directement de la documentation 
de Docker. Elles ont été testées sur Ubuntu 16.04, 18.04 (LTS) et 18.10.

- Mettez à jour vos paquets::
  
    $ sudo apt update
    
- Installer les pré-requis::

  $ sudo apt install apt-transport-https ca-certificates curl software-properties-common
  
- Ajouter la clé GPG pour le dépôt officiel de Docker::

  $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
  
- Ajouter le repo officiel de Docker aux sources de apt::

  $ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
  
- Mettre à jour la base de données des paquets de apt::

  $ sudo apt update
  
- Assurez-vous que vous aller installer Docker à partir du repo officiel de Docker et non à partir 
  des dépôts par défaut de Debian::

  $ apt-cache policy docker-ce
  
Vous verrez ceci, même si les numéros de version peuvent varier::

  docker-ce:
    Installed: (none)
    Candidate: 18.03.1~ce~3-0~ubuntu
    Version table:
      18.03.1~ce~3-0~ubuntu 500
          500 https://download.docker.com/linux/ubuntu bionic/stable amd64 Packages
        
Notez que docker-ce n'est pas installé, mais que le candidat à l'installation provient du repo 
officiel de Docker pour Ubuntu Bionic

- Finalement, installez Docker CE::

  $ sudo apt install docker-ce
  
- Ajoutez votre utilisateur au groupe docker::

  $ sudo usermod -aG docker ${USER}
  
- Pour que l'ajout au groupe docker soit actif, exécutez la commande suivante::

  $ su - ${USER}

- Vérifiez que votre utilisateur appartient au groupe docker::

  $ id -nG

- Télécharger la dernière version de Docker Compose::

  $ sudo curl -L "https://github.com/docker/compose/releases/download/1.23.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

- Donner les permissions nécessaires à docker-compose::

  $ sudo chmod +x /usr/local/bin/docker-compose

- Télécharger et installer Docker Machine avec la commande suivante::

  $ base=https://github.com/docker/machine/releases/download/v0.14.0 &&
  mkdir -p "$HOME/bin" &&
  curl -L $base/docker-machine-Windows-x86_64.exe > "$HOME/bin/docker-machine.exe" &&
  chmod +x "$HOME/bin/docker-machine.exe"

Voilà, vous avez installé Docker avec succès. Afin de tester si votre installation fonctionne, 
tapez les lignes suivantes dans un termina::

  $ docker --version
  Docker version 18.03, build c97c6d6

  $ docker-compose --version
  docker-compose version 1.23.1, build 1719ceb

  $ docker-machine version
  docker-machine version 0.14.0, build 9371605
  
Finalement, on peut tester si un serveur web tel que nginx fonctionne en exécutant la commande 
suivante dans votre terminal::

  $ docker run --rm -p 80:80 --name webserver nginx
  
Une fois cette commande exécutée, vous devriez pouvoir ouvrir un navigateur web, vou srendre 
à l'adresse `localhost <http://localhost>`_ et voir s'afficher une page telle que celle-ci:

.. image:: https://gyazo.com/4ffcaebd22e46635bb54709fd266bddf.png
  :width: 500px
  :align: center






