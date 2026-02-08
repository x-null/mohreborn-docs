# Features Overview

!!! info
    Remember that MoH Reborn patch currently provides extra features only for MoH:AA 1.11 server version!
    Spearhead and Breakthrough versions are planned for 2026, for both servers and players.


Below you will find short overview of all features that come with Reborn 1.12 patch.

Every feature has also it's own dedicated page where it is described in detail.

## Admin accounts and permissions

!!! success "STABLE"

Traditionally, as a server administrator, you would manage your server via RCon (Remote Console)
commands.

Since RCon access is protected with a single password, getting help in moderating your server meant
that you had to give away this password to other people and give them full control over the server.

Reborn patch let's you create individual admin accounts with selected privileges.
This way you can safely involve other people in server administration when you are away from your PC
and give them specific privileges based on the level of trust you have for them.

## Banning and kicking players

!!! success "STABLE"

### IP Banning

Now you can ban player's IPs with simple command.
It allows you to use wildcards to ban IP ranges.
No more need of external applications for kicking people.
This is a true (not emulated by auto-kicking) ban functionality that forbids player from connecting to the server.

### Name Banning

This feature lets you ban impolite names from being used on your server or any occurrence of
bad words in players names.

### Extended player kicking

Reborn patch extends standard capabilities of kicking players out from the server
with few new commands that add even more options to your admin tools arsenal.

## Chat management

!!! success "STABLE"

You can use it to punish people who use too many impolite, rude words and abuse your server this way.

It is also possible to disable game chat entirely or for selected players.

## Protected player names

!!! success "STABLE"

With this feature you can protect player names with passwords. Only player who knows the password will be able to use protected name on your server. 
It's very useful if you want to protect names of your clan mambers or server admins and make sure no one else but them will be able to use them. This protects you against others spoofing server admins, clan members and against name stealing hacks which automatically change name of a cheater to someone elses name. When this kind of a cheat will try to steal player's protected name, cheater will get kicked.

## Anti Wallhack

!!! warning "UNSTABLE"

The anti-wallhack is a blocker that works server side, it doesn't disable wallhacks on the client but it makes them almost useless. All the integrated blockers are working server side. A wallhack (cham skins, radar) works because the server usually sends all player position information to the client regardless if a player is visible or not. 
This is what wallhacks are using to render players behind walls. 
Now the anti-wallhack technology used in the patch checks for every client if a player is visible or not and sends only information about truly visible players to the client (information about player behind walls isn't send) - information that the client doesn't have can't be used to render players behind walls. 
This method can't be bypassed by clients and blocks successfully all kind of wallhacks, cham skins, etc. 

## Anti NoRecoil

!!! warning "UNSTABLE"

When player is using a NoRecoil cheat, his weapon doesn't kick up when he fires it. 
This system is responsible for detecting NoRecoil cheats and emulating recoil serverside so if player is using this cheat, he will get recoil/kick added to his weapon by the server and he can't do anything about this. 

## Anti Shoot Through Walls Hack

!!! success "STABLE"

STWH stands for Shoot Through Walls Hack. Our system detects player who uses this cheat, and when he tries to shoot through a wall, it blocks his bullet, making the cheat useless.

## High Ping Autokick

!!! success "STABLE"

You can turn on autokick option for players with ping higher than a value you set.

## Connections Limiter

!!! success "STABLE"

You can set a max connections per IP limit. This way you can decide how many people from one IP can join your server. 
This can be used as an additional measure against fake player flood attacks.

## Anti Packet Flood

!!! success "STABLE"

Some cheaters might want to flood your server in order to remove your server from the list of online game servers, drop players from it or even perform a remote crash. To achieve this, they would perform a Denial of Service attack by flooding your server with malicious, spoofed getstatus and getinfo packets. MoH:AA server will have to handle millions of packet requests and will get busy trying to send responses instead of processing game play action. 
This feature will render such attacks useless by detecting IPs from which the attack comes and ignoring their requests.

## Stufftext Bypass Detection

!!! warning "UNSTABLE"

stufftext is a server-side scripting command. It was created for scripters allowing them to change client settings in server-sided mods they write. Many mods make use of it. It can be used to force players to make screenshot (known as Forced SS), force them to turn off ForceModels or force their cvars to good values (this way some cheats could be turned off with server-sided mod). 
However client can bypass this stufftext command so it no longer works on his MoH:AA client. This way he would remain safe from any Admin Mods like Foresight, CI etc. 

This feature checks if player has this stufftext command bypassed, by using special technique and kicks player whenever it detects that he has it bypassed.

## Upgraded Voting System

!!! success "STABLE"

MoH:AA voting was never secure and almost never used. Thats why we have rewritten it. Now you can specify which commands players can use when voting and which maps they can vote for. 
When vote is casted, system will broadcast a graphical message to all players about current vote and other informations like: votes percentage, command that will be sent to server and after how much time the vote will expire.

## Automatic updates

!!! success "STABLE"

This will make updating patch a lot easier for developers and users. 
It automatically checks for new patch updates and installs them while server is running. 
You won't be bothered with restarting or closing the server to have up-to-date patch.

## Reborn Extended Scripting Engine

!!! success "STABLE"

We've managed to extend MoH:AA scripting engine with our own functionality that most of modders have never dreamt of. 
Reborn Extended Scripting Engine introduces 45 new script commands that can be used by modders to create even more powerful, content rich mods. Now they can: operate on files, date and time, create huddraw elements for individual players, communicate with server console, get extended information about each player and many more! 
We've also introduced Scripting EventSystem which allows modders to handle certain game events from their mods. Now they are able to interpret users keyboard input, handle players connection, disconnection, damage, kill events as well as map change, map restart events and more.

## Extras

With Reborn patch server admins can perform even more actions, some of them are: 

- disabling chat for all or only selected players
- disabling taunts for all or only selected players
- turning on simple team balancer
- kicking players with specifing reason of the kick
- sending private server messages to selected players 

These are only examples. You should read the rest of the documentation to learn about them all! 

## Bug and Crash Fixes

Medal of Honor Reborn patch comes with many fixes enabled by default:

- lod_spawn crash fix
- leave_team crash fix
- _fps skin crash fix
- dog, wuss, noclip, tele, give, fullheal, health, giveweapon - bad command fix
- say command buffer overflow crash fix
- userinfo buffer overflow crash fix
- remote crash fix (BufferOverflow - mohaabof & new one - infoboom)
- connect packet crash fix
- mohaa fill flood/crash fix (aka fake players fix)
- RCon flood protection
- getstatus/getinfo packet flood protection
- granade crash fix
- ladder crash fix
- swap team crash fix
- MG42 crouch fix
- landsharking fix
- shoot through Black Windows/Furniture/Light Bulbs fix 
