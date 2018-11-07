======================================================================================
Se construire un environnement de développement local sur mesure avec Python et Docker
======================================================================================

Installation de Docker sur différents systèmes
==============================================

L'objectif de ce document est de conduire l'étudiant pas à pas à travers l'installation de Docker sur différentes plateformes: macos, windows (Pro, Education, Home/Famille), Debian et Ubuntu.

Instatallation sous macos
-------------------------

La présente section va vous conduire pas à pas dans l'installation de Docker pour Macos. Avant de commencer, voici les pré-requis système nécessaires pour que cette installation fonctionne:

- Votre mac doit être plus récent que 2010. Vous pouvez tester si votre machine possède le support harware nécessaire en exécutant la commande suivante dans un terminal: sysctl kern.hv_support. Cette dernière doit afficher la valeur 1.
- Votre version de macos doit être plus récente que El Capitan 10.11.
- Vous devez avoir au minimum 4 GB de RAM
- Si virtualbox est installé sur votre ordinateur, il faut que ce soit une version plus récente que 4.3.30. Docker for Mac d'utilise pas virtualbox, mais il y a des incompatibilités avec les anciennes versions de vitualbox.
- Si votre système ne rempli pas un des ces pré-requis, vous pouvez toujours installer `Docker Toolbox <https://docs.docker.com/toolbox/overview/>`_.

Voici la procédure d'installation:

1. Télécharger Docker.dmg depuis `le site officiel <https://store.docker.com/editions/community/docker-ce-desktop-mac>`_.
2. Double-cliquez sur l'image Docker.dmg afin d'ouvrir l'installeur et glissez/déposez le logo Docker sur le dossier Applications.

.. raw:: html

  <img src="https://docs.docker.com/docker-for-mac/images/docker-app-drag.png" width="500">

4. Double-cliquez sur Docker.app dans votre répoertoire Application afin de démarrer Docker. Votre OS va vous demander d'authoriser Docker.app à accéder à votre ordinateur avec un accès privilégié en fournissant votre mot de passe. Cet accès privilégié est nécessaire pour que Docker puisse installer les composants réseau.
5. L'icone de balaine dans votre bar de status signifie que Docker est en train de tourner et qu'il est accessible depuis votre terminal. En cliquant sur cet icone, vous avez accès aux préférences et autres options.

Voilà, vous avez installé Docker avec succès. Afin de tester si votre installation fonctionne, tapez les lignes suivantes dans un terminal:

  $ docker --version
  Docker version 18.03, build c97c6d6

  $ docker-compose --version
  docker-compose version 1.23.1, build 8dd22a9

  $ docker-machine --version
  docker-machine version 0.14.0, build 9ba6da9
  
Finalement, on peut tester si un serveur web tel que nginx fonctionne en exécutant la commande suivante dans votre terminal:

  $ docker run --rm -p 80:80 --name webserver nginx
  
Une fois cette commande exécutée, vous devriez pouvoir ouvrir un navigateur web, vou srendre à l'adresse `localhost <http://localhost>`_ et voir s'afficher une page telle que celle-ci:

.. raw:: html

  <img src="https://gyazo.com/4ffcaebd22e46635bb54709fd266bddf.png" width="500">

  
Installation sous Windows
=========================

L'installation windows va être différente selon votre version de l'OS. En effet, si vous disposez d'une version Pro ou Entreprise ou Education (1607 Anniversary Update, Build 14393 ou plus récent), vous pouvez bénéficier d'une version native de Docker. Si vous disposez d'une version Windows Home ou Famille, nous utiliserons Docker Toolbox.

Dans tous les cas, il va vous falloir activé les fonctionnalités de virtualisation dans votre BIOS. Ces fonctionnalité



