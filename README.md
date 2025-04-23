# DuoBoloNetwork
 Master repository for the DuoBoloNetwork engine, launcher and online stack

# Folders

## Engine

Contiens le code du jeu, (server, client) et l'editeur.

### Cibles
#### Serveur

Cible xmake (rel,deb)-server.

Executable lancé dans un container docker par le backend aws. N'est pas censé être lancé par l'utilisateur car il nécessite des variables fournies par le backend.

#### Client

Cible xmake (release,debug).

Executable lancé par le client. Doit être lancé avec les paramètres -i pour l'ip du serveur et des paramètres d'authentification pour que le serveur s'assure de la validité de la connexion. Est lancé directement par le launcher.

#### Editeur

Cible xamek (rel,deb)-editor.

Cible permettant d'éditer des niveaux pour le jeu (.dbs). Ne permet pas de faire de test de jeu, c'est un éditeur de données uniquement.

## Launcher

Contient le code du launcher du jeu. Sers d'interface avec l'API AWS permettant la connexion, le matchmaking, l'affichage des statistiques... Lance le client avec les bons paramètres. Codé en rust pour le backend de l'application, HTML/CSS pour l'interface et javascript pour une partie de la logique.

## Online

Contiens le code pour le déploiement de l'infrastructure online sur AWS. À utiliser de paire avec AWS SAM CLI.

Codé en python pour les fonctions à exécuter sur le cloud. Utilise docker pour le serveur. Les définitions des resources (bases de données, bases d'utilisateurs, api...) dans template.yaml et matchmaking.yaml.