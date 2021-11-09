> Effective May 31, 2014, 
> GameSpy will cease providing all hosted services for all games still using GameSpy.
> If you have any questions about how this impacts your favorite title please contact 
> the game’s publisher for more information. Thanks for a great ride!
>
> GameSpy Industries, Inc. in http://www.poweredbygamespy.com/pricing/
> {: .blockquote-citation}

It means that after May 31, 2014 - GameSpy masterserver, 
which kept list of all online MoH servers has been shut down. 

In-game browser stopped to work and players can't find new servers to play on anymore.

xNULL team and community decided to create a replacement for default masterserver and 
created custom Reborn MasterServer that supports MoH:AA/SH/BT and GameSpy protocol
in order to save the game we all love so much.

## Game Launcher

The easiest way to play MoH:AA/SH/BT games is to download and install MoH Reborn Game Launcher.
This is an open-source software created by us, to make player's lives easier.

It will patch your game executables so that they will query Reborn MasterServer instead of original one
to get list of all online servers and show them in the in-game server browser.

!!! todo
    Game Launcher is not ready yet.
    You can help us develop it by contributing to: [MoH Reborn Launcher](https://github.com/x-null/mohreborn-launcher)

## Alternative solutions

If you don't want to install and use Reborn Game Launcher (which we highly recommend),
you can still make the in-game server browser work.
This will however require a bit more technical knowledge.

### Manual executables replacement

You can replace your game executables with the ones that are already patched.
Simply download right bundle, unpack binaries and copy them to your game installation folder.

When asked whether you want to overwrite original files, click "Yes".

!!! warning "MAKE A BACKUP OF YOU ORIGINAL FILES BEFORE INSTALLING THE PATCHED ONES"

We provide patched binaries for both game clients and game servers. Game servers need to be
patched in order to register in xNULL Masterserver and be visible to player in the in-game server browser.

- MoH:AA 1.11 (compatible with Reborn patch)
    - [Game (Windows) + Server (Windows & Linux)](../assets/moh-binaries/mohaa_1_11_full.zip)
- MoH:SH 2.15
    - [Game (Windows) + Server (Windows & Linux)](../assets/moh-binaries/mohsh_2_15_full.zip)
    - [Game (Windows) + Server with Daven's fixes (Windows & Linux)](../assets/moh-binaries/mohsh_2_15_full_fixes.zip)
- MoH:SH Demo
    - [Game (Windows) + Server with Daven's fixes (Windows & Linux)](../assets/moh-binaries/mohsh_demo_full_fixes.zip)
- MoH:BT 2.30
    - [Game (Windows) + Server (Windows & Linux)](../assets/moh-binaries/mohbt_2_30_full.zip)
    - [Game (Windows) + Server with Daven's fixes (Windows & Linux)](../assets/moh-binaries/mohbt_2_30_full_fixes.zip)
- MoH:BT 2.40
    - [Game (Windows) + Server with Daven's fixes (Windows & Linux)](../assets/moh-binaries/mohbt_2_40_full_fixes.zip)
- MoH:BT Demo
    - [Game (Windows) + Server with Daven's fixes (Windows & Linux)](../assets/moh-binaries/mohbt_demo_full_fixes.zip)
    
### Hosts redirection

You can edit your hosts file on your computer. The file will have priority over your DNS server.
We will override master.x-null.net to the xNULL master server.

#### Windows

Go to: `%SystemRoot%\system32\drivers\etc\`

Open file called `hosts` in your favourite text editor (Notepad is enough)
Add the following line to the bottom of the file: 
```
5.104.78.162 master.gamespy.com
```
Save the file and launch MOHAA, you should now see servers in the serverlist.

#### Linux, MacOS

Open the file: `/etc/hosts` in your favourite text editor
Add the following line to the bottom of the file: 
```
5.104.78.162 master.gamespy.com
```
Save the file and launch MOHAA, you should now see servers in the serverlist.

### Manual executable patching with hex editor

!!! todo
    Coming soon!
