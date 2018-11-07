======================================================================================
Se construire un environnement de développement local sur mesure avec Python et Docker
======================================================================================

- `Installation sous macos`_
- `Installation sous Windows 64 bits`_
- `Installation sous Debian`_
- `Installation sous Ubuntu`_

Installation de Docker sur différents systèmes
==============================================

L'objectif de ce document est de conduire l'étudiant pas à pas à travers l'installation de Docker sur différentes plateformes: macos, windows (Pro, Education, Home/Famille), Debian et Ubuntu.

Installation sous macos
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

  
Installation sous Windows 64 bits
=================================

L'installation windows va être différente selon votre version de l'OS. En effet, si vous disposez d'une version Pro ou Entreprise ou Education (1607 Anniversary Update, Build 14393 ou plus récent), vous pouvez bénéficier d'une version native de Docker. Si vous disposez d'une version Windows Home ou Famille, nous utiliserons Docker Toolbox.

Dans tous les cas, il va vous falloir vérifier que votre ordinateur vous assurer que les fonctionnalités de virtualisation sont activées dans votre BIOS ou UEFI, ce qui est le cas par défaut sur beaucoup de machine, mais pas toutes. Pour effectuer cette vérification:

- Si vous êtes sur Windows 10, installer `Speccy <https://www.ccleaner.com/speccy/download/standard`_. Lorsque vous démarrez ce logiciel, regarder sur l'onglet CPU Information pour vérifier si la virtualisation est supportée et activée.

.. raw:: html

  <img src="https://i.gyazo.com/789e3e234bbf3348f18de154338c4ea4.png" width="500">

- Si vous êtes sur Windows 8, choisissez **Start > Task Manager** et rendez-vous sur l'onglet **Performance**. Sous CPU, vous pouvez voir si la virtualisation est activée.

**Si la vitualisation n'est pas activée dans le BIOS ou l'UEFI**, il faut l'activer. Pour savoir comment procéder, taper dans google le modèle de votre ordinateur suivi de "enable virtualization". Vous trouverez alors très rapidement une procédure adaptée pour activer cette fonctionnalité.

Installation sous Windows Pro, Entreprise ou Education
------------------------------------------------------

Après avoir vérifié que la virtualisation était supportée et activée (voir ci-dessus), nous allons pouvoir installer **Docker for windows**. Pour cette installation, les pré-requis système suivants doivent être vérifié:

- Windows 10 64bits: Pro, Enterprise or Education (1607 Anniversary Update, Build 14393 ou plus récent)
- Le CPU doit avoir un support du second niveau de translation d’adresse (SLAT - Second Level Address Translation). C'est normalement le cas sur les machines relativement récente (2010+).
- Au moins 4 GB de RAM
- Si votre système ne rempli pas un des ces pré-requis, vous pouvez toujours installer `Docker Toolbox <https://docs.docker.com/toolbox/overview/>`_.

Voici la procédure d'installation:

1. Télécharger Docker for Windows Installer.exe depuis `le site officiel <https://store.docker.com/editions/community/docker-ce-desktop-windows>`_ et exécutez l'installeur.
2. Suivez la procédure, acceptez la licence et procédez à l'installation. Cliquez sur Finish une fois l'installation terminer et Docker démarrera automatiquement. Si Docker ne démarre pas, vous pouvez chercher Docker for Windows dans vos applications et le démarrer manuellement.

.. raw:: html

  <img src="https://docs.docker.com/docker-for-windows/images/docker-app-search.png" width="250">

Voilà, vous avez installé Docker avec succès. Afin de tester si votre installation fonctionne, tapez les lignes suivantes dans un terminal PowerShell ou cmd.exe:

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

Installation sous Windows Home ou Famille
-----------------------------------------






