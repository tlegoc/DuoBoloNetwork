# DuoBoloNetwork
 Master repository for the DuoBoloNetwork engine, launcher and online stack

 To install, please see the [latest release of the launcher](https://github.com/tlegoc/DuoBoloLauncher2/releases). First working version is 0.3.7.

 Please note the repositories inside this repo aren't up to date ! Please use theses links :

- Launcher : https://github.com/tlegoc/DuoBoloLauncher2
- Game + Engine : https://github.com/corentinch59/UQAC_ReseauTP3
- Online API : https://github.com/tlegoc/DuoBoloApi

 ## The Game

### Connection
When launching the game for the first time, you will have to create an account (you can input any email it's not important)  
Once registered, you can connect and press Find match to queue in the matchmaking.  
When enough players are queued (2 per match), the button will turn grey and the text will indicate Match found. you just need to wait a few seconds for the server to start. The game will open by itself.  
### In game
Controls are :
- **WASD** for **left/right/forward/backward**  
- **Q/E** for **up/down**
- **left click** to shot a ball.
The objective is to hit cubes and make them fall off the platform.  
The last person hitting the cube will score it.  
The game lasts 2 minutes.
Once the 2 minutes elapsed, simply press F5 on the launcher to update.  
If you click on your profile icon you can check your statistics.

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
