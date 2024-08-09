# SRCDS Controller
SRCDS Controller as the name suggests is a shell script that controls the SRCDS server processes of qtland servers. There are two versions of the SRCDS Controller. There are **`tf`** (*Team Fortress 2*) and **`csgo`** (*Counter-Strike: Global Offensive Legacy*).

You can modify this shell script to your needs and works with any type of Source Engine server.


# Prerequisite
You need the latest version of node.js and npm with `pm2` globally installed. **It is always considered a security risk if you run SRCDS Controller under a user that has root permissions and isn't recommended.**
You also need to generate the correct configuration files found within the game folders. Failure to do so makes the shell script not work.

### Installation
*The installation part assumes you have created a different user without that user having any sudo or root permissions and the correct generated required files exist within that user.*
*This installation also assumes you have the game files downloaded via steamcmd.*

### Installation for TF2 (tf)
> [!CAUTION]
> You must install these packages under the root user or with a user that has sudo permissions.

Arch Linux:
```
pacman -S nodejs npm
npm i pm2 -g
```

Void Linux:
```
xbps-install nodejs
npm i pm2 -g
```

CentOS / Fedora / Red Hat Enterprise Linux:
```
dnf module install nodejs
npm i pm2 -g
```

Debian / Ubuntu:
```
apt-get install nodejs npm
npm i pm2 -g
```

### Installation for CS:GO (csgo)
> [!CAUTION]
> `screen` is usually pre-installed in most Linux distributions. You can verify this by typing `screen -v` into your terminal.

### Preparing files for SRCDS Controller (csgo/tf)
> [!IMPORTANT]
> You need the `int` folder in your user's root (`/home/$USER/int`).  The shell scripts exist in case your servers are unable to start or crash on startup.

Inside the `gen` folder you can see `tf` and `csgo` folders. These folders should belong to the root games directory (*If you installed the SRCDS in a standalone folder* `/home/$USER/srcds/<gamename>`)
