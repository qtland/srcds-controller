### Installation
*The installation part assumes you have created `gameserver` user without that user having any sudo or root permission.*

> [!CAUTION]
> Only follow these instructions, if you have **NOT** installed steamcmd or SRCDS yet. You will need to log into the above-mentioned `gameserver` user account.
> SRCDS Controller currently only supports Linux installations, and isn't recommended for Windows installations.

## Installing SteamCMD (tf/csgo)

Arch Linux:
```
pacman -Syy lib32-gcc-libs lib32-libcurl-gnutls lib32-ncurses5-compat-libs
wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz
tar zxf steamcmd_linux.tar.gz
```

CentOS:
```
yum install ncompress libgcc.x86_64 libgcc.i686 glibc.i686 zlib.i686 ncurses-libs.i686
wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz
tar zxf steamcmd_linux.tar.gz
```

Fedora Linux:
```
dnf install libstdc++.i686 ncurses-compat-libs.i686 libcurl.i686
wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz
tar zxf steamcmd_linux.tar.gz
```

Debian / Ubuntu / Linux Mint:
```
dpkg --add-architecture i386
apt-get update
apt-get install lib32z1 libncurses5:i386 libbz2-1.0:i386 lib32gcc-s1 lib32stdc++6 libtinfo5:i386 libcurl3-gnutls:i386 libsdl2-2.0-0:i386
wget https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz
tar zxf steamcmd_linux.tar.gz
```

## Installing SRCDS (tf)
Once you have finished installing steamcmd and unzipped the tar file, you still need to download the TF2 SRCDS files.

> [!IMPORTANT]
> You will need to replace `/home/$USER/srcds/` to `/home/$USER/mvm/` if you wish to install an MvM (*Mann vs. Machine*) server.
> The script only works if there is a TF2 SRCDS installation under those paths specified above.

 
```
./steamcmd.sh +force_install_dir /home/$USER/srcds/ +login anonymous +app_update 232250 +quit
```


## Installing SRCDS Controller JS packages (tf)

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


### Preparing files for SRCDS Controller (csgo/tf)
> [!IMPORTANT]
> The script doesn't require sudo permissions so therefor you must run the script under the `gameserver` user.

You need to create an `int` folder in `gameserver`'s root (`/home/gameserver/int`).  The shell scripts exist in case your servers are unable to start or crash on startup. You can create the required files by invoking the script with command line arguments:
```
./gen -g tf -t mvm
./gen -g tf -t cas
./gen -g tf -t comp
```
After the script has been successfully executed, you need to move the files from `/home/gameserver/srcds-controller/int/` to `/home/gameerver/int/`. Also, files generated in `/home/gameserver/srcds-controller/tf/cfg/` has to be moved to the root directory of the SRCDS installation (`/home/gameserver/srcds` or `/home/gameserver/mvm/`)

For CSGO:
```
./gen -g csgo -t casual
./gen -g csgo -t competitive
./gen -g csgo -t deathmatch
```
> [!WARNING]
> There are no support for CS:GO yet. You need to check back to see if there is any updates regarding CS:GO support.


### Running SRCDS Controller
Navigate to `/home/gameserver/int` and invoke the `run.sh` script, this will start a PM2 Daemon with your servers.
