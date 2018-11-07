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
3. essai 
..image: https://docs.docker.com/docker-for-mac/images/docker-app-drag.png



