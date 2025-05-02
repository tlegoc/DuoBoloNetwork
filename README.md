# DuoBoloNetwork
README repository for the DuoBoloNetwork engine, launcher and online stack

To install, please see the [latest release of the launcher](https://github.com/tlegoc/DuoBoloLauncher2/releases). First working version is 0.3.7.

Child repositories :

- Launcher : https://github.com/tlegoc/DuoBoloLauncher2
- Game + Engine : https://github.com/corentinch59/UQAC_ReseauTP3
- Online API : https://github.com/tlegoc/DuoBoloApi

# Metrics

You can watch metrics about the backend [here](https://cloudwatch.amazonaws.com/dashboard.html?dashboard=DuoBoloNetworkDashboard&context=eyJSIjoidXMtZWFzdC0xIiwiRCI6ImN3LWRiLTc2MTI3MjcwMjcwNiIsIlUiOiJ1cy1lYXN0LTFfMU12UTZZT1pkIiwiQyI6IjZqZTc3MGk0b3F1MzFrbGg4OGI2bnZvbm42IiwiSSI6InVzLWVhc3QtMTo3ZTVhMDIwOS03ZDI2LTRkOWItYjI1OS0zNjFhMjRiYWNhNjUiLCJNIjoiUHVibGljIn0=)

![image](https://github.com/user-attachments/assets/03774c29-e059-46c6-9647-b67002e443f9)

## The Game

| ![image](https://github.com/user-attachments/assets/1224d7f3-1860-48b9-b39e-2b405df468cd) | ![image](https://github.com/user-attachments/assets/9d17ba58-58bc-4b87-bfdc-66d99eeaef27) |
:-------------------------:|:-------------------------:
![image](https://github.com/user-attachments/assets/9ecdeba2-c460-4d66-8b02-774c7271ccf6) | ![image](https://github.com/user-attachments/assets/a3503e37-be87-4228-9af3-f04bbbf8b24c)
![424820761-2dbf318f-dc65-4267-b1a0-63de5b2fc50f](https://github.com/user-attachments/assets/9e69cd7d-946b-4a6e-8f28-5d1c33b4f507) | ![424820843-17d0a965-05d2-48ce-b5cc-fa66b3ad6e1c](https://github.com/user-attachments/assets/ae23c377-fea4-4f10-97d2-58165dba546b)


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
