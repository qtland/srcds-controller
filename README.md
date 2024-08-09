# SRCDS Controller
SRCDS Controller as the name suggests is a shell script that controls the SRCDS server processes of qtland servers. There are two versions of the SRCDS Controller. There are **`tf`** (*Team Fortress 2*) and **`csgo`** (*Counter-Strike: Global Offensive Legacy*).

You can modify this shell script to your needs and works with any type of Source Engine server.


# Prerequisite
You need the latest version of node.js and npm with `pm2` globally installed. **It is always considered a security risk if you run SRCDS Controller under a user that has root permissions and isn't recommended.**
You also need to generate the correct configuration files found within the game folders. Failure to do so makes the shell script not work.
