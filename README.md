# 2006Scape - an open source, actively developed emulation server. Pull requests welcome! ![Gameplay Image](https://i.imgur.com/WHnQz2W.png)

### Discord Link: https://discord.gg/hZ6VfWG
### Client/Launcher Download: https://2006Scape.org/

## Installation + Running (Developers)
### Locally with IntelliJ
1. Import Project in IntelliJ

2. Hit File > Project Settings > Set SDK to Java 8 (Download [Java 8 SDK](https://adoptopenjdk.net/?variant=openjdk8) if you don't have one already)

3. Navigate to `2006Scape Server` > `src` > `main` > `java` > `com.rs2`, right click GameEngine and hit Run ([Image](https://i.imgur.com/HHooeVu.png))

   [(You Can Also Run The Server With The -c/-config Argument)](https://wiki.2006scape.org/index.php/Command_line_arguments)
5. Navigate to `2006Scape Client` > `src` > `main` > `java`, right click Client and hit Run ([Image](https://i.imgur.com/gSmqGLn.png))

### With Docker
#### Quick start
To run 2006Scape on your docker server, simply run
```
docker run -d -it -p 43594:43594 -p 43595-43596:43595-43596 2006-Scape/2006Scape
```
#### Docker Compose
```docker
version: "3"
services:
  2006Scape-server:
    image: registry.gitlab.com/2006-Scape/2006Scape
    container_name: 2006Scape-server
    environment:
      - PUID=2006
      - PGID=2006
      - TZ=Etc/UTC
    volumes:
      - 2006scape-config:/serverconfig.json:ro
      - 2006scape-data:/2006scape
      - 2006scape-saves:/2006Scape/2006Scape-Server/data/characters
    ports:
      - 43594:43594 # Server
      - 43595-43596:43595-43596
    restart: unless-stopped
volumes:
  2006scape-data:
  2006scape-config:
  2006scape-saves:
```

### From the Command Line
To compile any module from the command line, run `mvn -B clean install`

## Using Parabot with your local server
- **1:** Download the latest Parabot Client from [here](https://github.com/2006-Scape/Parabot/releases)
- **2:** Run the parabot client with the following arg:
```fix
java -jar Parabot.jar -local
```
- **3:** ???
- **4:** PROFIT

## Additional Information
### Rune-Server project thread: [Project thread](https://www.rune-server.ee/runescape-development/rs2-server/projects/686444-2006rebotted-remake-server-will-allow-supply-creatable-bots.html)
### Server source layout
- `2006Scape Server` contains all the server code; mark `src` as the Sources directory
- `2006Scape Client` contains all the client code; likewise mark `src`
  - If more than 2 arguments are passed in (can be anything), the client runs locally
