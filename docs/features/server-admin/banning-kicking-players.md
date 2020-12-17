## IP Banning

Banning players by their public IP is controlled with following commands:

- [banip](#banips), [banipr](#banips)
- [banid](#banips-by-id), [banidr](#banips-by-id)
- [unbanip](#unbanips)
- [listips](#listips)

!!! hint
    All listed commands work via RCon.
    They can be used by admin accounts, by prefixing them with **ad_** keyword.
    
    See [Admin accounts and permissions](accounts-and-permissions.md) for more information.
    
Banned IPs are stored in **ipfilter.cfg** file that can be edited by hand with text editor.

- Each IP should be added in a new line.
- Line comments are supported, and work by adding double slashes in front of the line that should
  be commented out.
   
IP banning supports masks for banning IP ranges. 

Star symbol (*) is used as a mask. The mask itself can be placed in every of 4 IP segments separated by dots.

Below is an example of ipfilter.cfg file:

```
192.168.0.1
192.*.0.1
192.*.0.*
// bans every IP (no one will be able to connect to the server, even host)
*.*.*.*
*.168.*.*

// and so on
```

### <a name="banips"></a> banip / banipr

**banip** command bans given IP from connecting to the server. You can use masks to ban ranges of IPs.

Usage:

```
banip <ip-mask>
```

for example:

```
banip 10.*.40.15
```

**banipr** works the same as banip command, but it allows you to give reason of ban as a second argument:

```
banipr <ip-mask> <reason>
```

for example:

```
banipr 10.*.40.15 "offending server admin"
```

It will show the reason of the ban both to players on the server, and to banned player upon disconnection.


### <a name="banips-by-id"></a> banid / banidr

Sometimes you may be in a hurry, or have a hard time typing complicated IP inside console to ban someone.
 
This command bans IP of player with given ID/game slot (clientnum). You can check player's clientnum with **status**.

Usage:

```
banid <clientnum #>
```

for example:

```
banid 10
```

**banidr** command is similar, but it allows you to give reason of ban as a second argument.

Usage:

```
banidr <clientnum #> <reason>
```

for example:

```
banid 10 "offending server admin"
```

It will show the reason of the ban both to players on the server, and to banned player upon disconnection.


### <a name="unbanips"></a> unbanip

**unbanip** command removes banned IP from list of banned IPs and re-initializes the ban-list.
Players with IPs that were banned will be able to join the server again.

Usage:

```
unbanip <ip-mask>
```

for example:

```
unbanip 10.*.40.15
```

!!! important
    The command will look for exactly-matching entry in **ipfilter.cfg** file.
    It means, that it will not scan inside IP ranges for given IP.


### <a name="listips"></a> listips

**listips** command lists all banned IPs. It supports paging, which means that
it splits all banned IPs into smaller groups, which allows you to view them without
scrolling inside game console.

Usage:

```
listips <page number #>
```

for example:

```
listips 3
```

There are 20 pages maximum, you can choose between page 1-20.

## Name Banning

Banning player names is controlled with following commands:

- [banname](#banname)
- [unbanname](#unbanname)
- [listnames](#listnames)

!!! hint
    All listed commands work via RCon.
    They can be used by admin accounts, by prefixing them with **ad_** keyword.
    
    See [Admin accounts and permissions](accounts-and-permissions.md) for more information.

Players with banned names will not be able to connect to the server.

Banned names are stored in **namefilter.cfg** file that can be edited by hand with text editor.

- Each name should be added in a new line.
- Line comments are supported, and work by adding double slashes in front of the line that should
  be commented out.

It is possible to ban any occurrence of given word in players names. 
In order to do so, you have to add **~any** selector after banned name (separated by single <space\> character).

Below is an example of namefilter.cfg file:

```
a55
// Line below will ban all names containing this word (Badass, Classic Killer, assasin etc.)
ass ~any
puta
puta madre
```

### <a name="banname"></a> banname

**banname** command bans the given name.

Players with banned names will not be able to join the server unless they change their name.
You can use an additional parameter **any** (by default set to 0) by setting it to 1,
to ban any occurrence of the given word in players name.

Usage:

```
banname <name> [any=0]
```

for example:

```
banname chris123
```

or

```
banname clos 1
```

to ban names that contain word **clos** in them, eg.: en**clos**ure

### <a name="unbanname"></a> unbanname

**unbanname** command removes the name from list of banned names.

Players with that name (or word in the name) will be able to connect to the server again.

Usage:

```
unbanname <name>
```

for example:

```
unbanname chris123
```

### <a name="listnames"></a> listnames

**listnames** command lists banned names.

**~any** tag next to the word means that all names, containing this word, are banned from the server.

It supports paging, which means that it splits all banned names into smaller groups, 
which allows you to view them without scrolling inside game console.

Usage:

```
listnames <page number #>
```

for example:

```
listnames 3
```

There are 20 pages maximum, you can choose between page 1-20.

## Kicking players from server

Sometimes you do not want to ban someone immediately, but rather kick them from
the server and make them rethink their actions or behavior.

Standard MoH:AA server gives you such possibility with commands:

- kick
- clientkick

When you use them on a player, other players on the server see generic message:
"Player X has left the battle".

However, you may want to specifically point out that someone was deliberately kicked out
from the server, which is different from leaving the server willingly.

This is why Reborn patch adds two new commands:

- [kickr](#kickr)
- [clientkickr](#clientkickr)

which let you kick players with providing a reason of such action.

### <a name="kickr"></a> kickr

**kickr** command kicks player with given name from the server. 

Both, players on the server, and kicked player will be provided with the reason of the kick.

Usage:

```
kickr <name> <reason>
```

for example:

```
kickr chris123 "breaking server rules"
```

### <a name="clientkickr"></a> clientkickr

**clientkickr** command kicks player with given ID/game slot (clientnum).
You can check player's clientnum with **status** command.

The reason of the kick will be displayed both to players on the server and to kicked player.

Usage:

```
clientkickr <clientnum #> <reason>
```

for example:

```
clientkickr 5 "breaking server rules"
```