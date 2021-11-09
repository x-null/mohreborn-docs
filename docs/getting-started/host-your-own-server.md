This guide will take you through installing the Reborn Patch on your MoH:AA Server and
basic configuration.

## Installation

### Linux

!!! warning "MAKE A BACKUP OF YOU ORIGINAL FILES BEFORE INSTALLING THE PATCH"
    It should be enough to backup following files:
    
    - mohaa_lnxded
    - fgameded.so 
    
    But if you are not sure, it's better to make a copy of whole MoH:AA directory.


**Steps**

- Download latest Linux patch version from [HERE](../downloads.md#linux) and unzip it.
- **Make a backup of your existing server**.
  
    There are only a couple of files changed by the patch,
    but if you are not familiar with all the files and folders on your server,
    this can become confusing, so it's safer to backup everything.

- Shut down your MOHAA server via your host in the normal way. If your host has an auto restart feature, ensure your server does not restart after you have stopped it.
- Rename file **fgameded.so** to **fgamededmohaa.so**

    The file will be located in your MOHAA base folder (*for example /opt/MOHAA/*).
    Base game folder location may differ depending on what host you are on.
    Some hosts may provide a HTTP file manager where you can rename the file or use FTP.

- Copy **fgameded.so** file that comes with the patch and paste it into your server's MOHAA base folder.
- Copy all of the rest of files that come with the patch and paste them into your server's MOHAA base folder.
- Hurray! You are done with installing the patch!
 
    It should run without crashing.
    If it crashes, or doesn't start at all, you probably made a mistake during installation process.
    Restore your back-up copy and repeat the installations steps, this time with more caution.

!!! note
    It is important that you keep the original files and just rename them, otherwise the server will not work. 

### Windows

!!! warning "MAKE A BACKUP OF YOU ORIGINAL FILES BEFORE INSTALLING THE PATCH"
    It should be enough to backup following files:
    
    - mohaa_server.exe
    - gamex86.dll
    
    But if you are not sure, it's better to make a copy of whole MoH:AA directory.

**Steps**

- Download latest Windows patch version from [HERE](../downloads.md#windows) and unzip it.
- **Make a backup of your existing server**.
  
    There are only a couple of files changed by the patch,
    but if you are not familiar with all the files and folders on your server,
    this can become confusing, so it's safer to backup everything.

- Shut down your MOHAA server via your host in the normal way. If your host has an auto restart feature, ensure your server does not restart after you have stopped it.
- Rename file **gamex86.dll** to **gamex86mohaa.dll**

    The file will be located in your MOHAA main folder (*for example C:/MOHAA/main*).
    MoHAA main folder location may differ depending on what host you are on.
    Some hosts may provide a HTTP file manager where you can rename the file or use FTP.

- Copy **gamex86.dll** file that comes with the patch and paste it into your server's MoHAA /main/ folder.
- Copy all of the rest of files that come with the patch and paste them into your server's MoHAA /main/ folder.
- Hurray! You are done with installing the patch!
 
    It should run without crashing.
    If it crashes, or doesn't start at all, you probably made a mistake during installation process.
    Restore your back-up copy and repeat the installations steps, this time with more caution.

!!! note
    It is important that you keep the original files and just rename them, otherwise the server will not work. 

### Docker

You can run game server as Docker container. Provided images come with preinstalled Reborn patch and other fixes.
They also include all required OS libraries, so it's super easy to run your server with single command.

#### Linux version

You can use the following pull command to pull the docker image:

```bash
docker pull appelpitje/mohaa-server:AA-Reborn
```

To run a container, you can use:

```bash
docker run -p 12203:12203/udp -p 12300:12300/udp appelpitje/mohaa-server:AA-Reborn
```

#### Windows version

You can use the following pull command to pull the docker image:

```bash
docker pull appelpitje/mohaa-server:AA-Reborn-win32
```

To run a container, you can use:

```bash
docker run -p 12203:12203/udp -p 12300:12300/udp appelpitje/mohaa-server:AA-Reborn-win32
```

### Troubleshooting

If your server crashes after installation, it can be caused by incompatible MoH:AA binary files versions.
You may want to replace them with binaries that are known to be working with the patch.

You can find them and download from [HERE](../downloads.md#compatible-binaries).

If you tried compatible binaries and are still experiencing problems - don't hesitate and contact us using any available
channel (see: [xNULL Community](../index.md#xnull-community)).

## Basic configuration

This is a template for server configuration file, that should let you set up your Reborn Server from scratch in few seconds.

```
//************** Reborn Patch ***************
//************* www.x-null.net **************
//************ www.mohaaaa.co.uk ************
//*** Note some additional mods required ****
//*** Example Freezetag Mefy mod required ***

//************** Server info ****************

seta sv_hostname "Place your server name here"
seta g_motd "Message here"
sets "+Admin" "Place admin name here" 
sets "+Clan" "Set clan here"
sets "+Teamspeak3" "109.70.148.54:9987"
//sets "+Mumble" ""
sets "+Location" "UK"
sets "+Hosted By" "www.mohaaaa.co.uk"
sets "+webiste" "www.mohaaaa.co.uk"
sets "+Email" "admin@mohaaaa.co.uk"

//************ General Settings **************
seta skill 0 //added
seta sv_timeout "200"
seta sv_precache "1"
seta sv_maxRate "25000"
seta sv_privateClients ""
seta sv_maxclients "20"
seta sv_reconnectlimit "10"
seta sv_zombietime "1"
seta g_inactivity "0"
seta g_forcerespawn "0"
seta g_syncronousclients "0"
seta g_smoothClients "1"
seta sv_fps 20
seta sv_allowdownload 0
seta sv_floodprotect "1"
seta cheats "0"
seta sv_pure "0"

//*********** Server Network Settings ********

seta sv_flood_waitdelay "10"
seta sv_flood_persecond "4"
seta sv_flood_msgs "4"
seta noipx "1"

//************** Logs ************************
//seta fs_basepath .
//seta fs_userpath /log
//seta fs_outputpath /log
//seta logfilename "qconsole.log" //deactivated
//seta writeconfig "config.log" //deactivated
seta logfile 3
seta g_logSync "1"
seta sv_chatter 1

//seta developer 0 //1,2,3 modes available 
seta sv_debuggamespy 0	//information gamespy

//*************** Extras ********************
seta sv_maxPing "0" //disactivated, use High Ping Limiter System
seta sv_minPing "0" //activated

//************* Server Passwords ************
seta rconpassword "xxxxx"
//seta sv_privatePassword ""
//seta password "x" // deactivated

//******** Game Play Default Settings *******
seta g_gravity "800"
seta g_knockback "1000"
seta g_quadfactor "3"
seta g_speed "320"
seta g_healrate 0
seta g_healthdrop 1
seta g_realismmode 1
seta g_forceteamspectate 1
seta g_spectate_allow_full_chat 0
seta sv_team_spawn_interval 0
seta g_inactivespectate 0
seta g_inactivekick 0
seta g_teamswitchdelay 10
seta g_allowjointime 20  //default 30
seta cg_forcemodels 1

//*************** Team Preferences **********
seta g_teamdamage "0"

//**************** Voting *******************
//seta g_allowVote "0" //deactivated
//seta g_votetimeout "0.3"

//************* Masterservers ***************
// add up to 4 additional master servers
// Note: This feature does not work in MoHAA
// but may be implemented in future Reborn Releases 
seta sv_master1 "mohmaster.2015.com"
seta sv_master2 "master0.gamespy.com"
seta sv_master3 "master1.gamespy.com"
//seta sv_master1 "scapp.net"
//seta sv_master2 ""
//seta sv_master3 ""
seta sv_gamespy 1

//*******************************************
//************** ProMod *********************
//seta "promod" "0" //deactivated
//seta "playmode" "public1noac" //deactivated
//*******************************************
//*******************************************


//*******************************************
//*** Extended Gametypes (Freezetag etc.)****
//*******************************************
//************ Caputure the flag ************
//set g_extgametype ctf
//set g_ctf_settings "respawn: 0 returnboth: 1 capturepress: -1"

//************ Demolition *******************
//set g_extgametype dem
//set g_dem_settings "respawn: 1 attacker: swap mef_team_spawn_interval: 6"

//************ Freeze-Tag *******************
//set g_extgametype ft
//set g_ft_settings "meltgun: on melttime: 35" //deactived

//************ Freeze-Tag-CTF ***************
//set g_extgametype ftctf
//set g_ftctf_settings "pointlimit: 6 countdown: 30 meltgun: off mef_team_spawn_interval: 6"

//************ Freeze-Tag-Demolition ********
//set g_extgametype ftdem
//set g_ftdem_settings "settime: 20 defusetime: 10 ticktime: 60"

//************ Freeze-Tag-Objective *********
//set g_extgametype ftobj
//set g_ftobj_settings "meltgun: on melttime: 30"


//******************Gametype ****************
// Set the type of game: 1=Deathmatch 2=Team match 3=Roundbased 4=Obj
seta g_gametype 4 
seta g_extgametype obj //deactivated


seta roundlimit "5"
seta timelimit "0"
seta fraglimit "7"
seta dmrespawning "0"
seta dmroundlimit "0"

//*******************************************
//************* Maprotatin / Map ************
//seta sv_maplist "obj/obj_team1 obj/obj_team2 obj/obj_team4 "
//map obj/obj_team1	//starts with hunt

seta sv_maplist "obj/obj_team1 obj/obj_team2 obj/obj_team4"
map obj/obj_team2   //= stalingrad

//********** Reborn Patch settings ***********
//*************   1.12  **********************

//** Sets banning 1=on 0=off  
seta sv_banning 1 

//** Sets filter 1=on 0=off reads filterchat.cfg
seta sv_filterchat 1

//** Sets In-game chat 1=on 0=off
sv_disablechat 0

//** Sets Kinping //was 998
seta sv_kickping 0 

//** sets how many connections from Same IP
seta sv_maxconnperip 3 

//** Set Kick Bad cmd 1=on 0=off
seta sv_kickbadcmd 1

//** Sets Sound Distance
seta sv_sounddistance "8000" // deprecated, doesn't change anything

//** Sets Anti Wall hack mode 1,2,3,4,5,6
//** 1=Bone A-WH; 2=Hitbox A-WH; 3=BonePredict 
//** A-WH; 4=FramePredict A-WH; 
//** 5=Testing(better accuracy); 
//** 6=tweaked mode 5 (RC3.1.005+ only)) 
seta sv_antiwh "0" 

//** Skips AntiWH checks for players above given
//** ping (<0...999>)
sv_antiwhskipping 400

//** Sets Anti shoot through walls 1=on 0=off
seta sv_antistwh "1"

//** Sets recoil emulation 1=on 0=off
seta sv_recoilemulation "0"

//** Sets stufftext detection 1=on 0=off
seta sv_stufftextdetection "0"

//** Sets Anti cham 1=on 0=off
seta anticham "0" // works only with anticham mod

//** Sets server update check delay (hours)
seta sv_updatedelay 24  

//** Turns Teambalancing feature 0=off; 1=on
seta g_teambalance 0

//** Sets an IP from which your 
//** remote tool like CI, ForeSight or Scapp is
//** communicating with the patch. It will be let
//** through the anti-getstatus flood as trusted
//** IP.(XXX.XXX.XXX.XXX)
seta sv_remotetoolip "127.0.0.1"

//** GetStatus/GetInfo Anti Flood Protection 1=on 0=off
seta sv_packetantiflood 1
```