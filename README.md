# DuoBoloNetwork
 Master repository for the DuoBoloNetwork engine, launcher and online stack

 ## The Game

It's played with **WASD** for movement and **left click** to shot a ball.  
Hitting a cube with a ball and making it fall off the platform will make it disappear.  
The last person hitting the cube will score it.

# Folders

## Engine

Contains the code for the game, server, client and editor. (the editor is broken on latest release)

### Targets
#### Server

Executable launched in a docker container via AWS. It's not supposed to be launched by the user because it need variables given by the backend.

#### Client

Executable launched by the client. Must be launched with parameters -i for the server ip and -u with username for server authentification. It's handled by the launcher.

#### Editeur

Target that allows to edit the level of the game (.dbs). Doesn't allow to test the game, it's only a data editor. (broken at the moment)

## Launcher

Holds the code to launch the game. It's the user interface with the AWS API allowing connection, matchmaking and display statistics. when pressing Find match, a matchmaking ticket will form. You will see the button turning grey with Match found when the matchmaking is finished. Wait a few seconds to allow the server to start and the Game will open up by itself. Coded in Rust for the application backend, HTLM/CSS for the display and some javascript for some logic.

## Online

Holds the code for online infrastructure deployment on AWS. Must be paire with AWS SAM CLI.
Coded in python for cloud execution. Uses docker for the server. Resources are defined in template.yaml and matchmaking.yaml.
