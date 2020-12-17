## Introduction

EventSystem Engine has been introduced since Release Candidate 2.5 Beta version of the patch.

You can use it to bind certain events with your scripts, which will be executed when such events will take place.
In short, EventSystem Engine allows scripters to have scripted events.

Right now, EventSystem Engine supports 8 events:

Scripter can write a script that will get executed by EventSystem Engine when one of them occurs.
Such a script is called event callback handler and it have to be registered in the system before it can be used by it.
To register event callback handlers, EventSystem Engine provides scripters with two commands:

registerev - registers event callback handler
unregisterev - unregisters event callback handler

To see their full documentation please see Reborn Scripting Commands

When scripter registers event callback handler it will get bound with certain event types listed earlier.

EventSystem Engine will then execute his script (event callback handler) whenever events of given type will occur.


!!! important
    EventSystem Engine allows only 1 to 1 binds, which means that you can't register one event type with more than one event callback handler.
    
    When scripter registers event callback handler, it won't be overwritten by next registerev commands, which means that EventSystem Engine will execute only those event callback handlers that where registered before any other callback handlers (in short: only firstly registered callback handlers).
    
    After map change, all events will be unregistered, so there's a need to register them again each map change, which shouldn't be a problem.

!!! note
    Future EventSystem Engine may get improved or it's architecture may get changed a bit.

## Events

### Connected

connected ( Entity entity )

Event that is generated when player has entered the server.

Registering:

```
local.result = registerev connected global/example.scr::connected
```

or

```
local.result = registerev connected global/connectedhandler.scr
```

Callback handler:

```
connected local.player:
       // your code here
end
```

or

```
main local.player:
        // your code here
end
```

Where:

- local.player - player that has connected to server

### Disconnected

disconnected ( Entity player )

Event that is generated when player has disconnected from the server. (it's executed just right before real disconnection)

Registering:

```
local.result = registerev disconnected global/example.scr::disconnected
```

or

```
local.result = registerev disconnected global/disconnectedhandler.scr
```

Callback handler:

```
disconnected local.player:
       // your code here
end
```

or

```
main local.player:
        // your code here
end
```

Where:

- local.player - player that has disconnected from server.

### Spawn

spawn ( Entity player )

Event that is generated when player has spawned for the first time after entering the server, and each time he respawns. (It won't be generated for the first time when player is already spawned and map restart will occur. To force this event to be called after map restart, you have to move player to spectator before map restart.)

Registering:

```
local.result = registerev spawn global/example.scr::spawn
```

or

```
local.result = registerev spawn global/spawnhandler.scr
```

Callback handler:

```
spawn local.player:
       // your code here
end
```

or

```
main local.player:
        // your code here
end
```

Where:

- local.player - player that has spawned or respawned.

### Damage

damage ( Entity target, Entity inflictor, Float damage, Vector position, Vector direction, Vector normal, Integer knockback, Integer damageflags, Integer meansofdeath, Integer location, Entity entity)

Event that is generated when entity (not only player) gets damaged.

Registering:

```
local.result = registerev damage global/example.scr::damage
```

or

```
local.result = registerev damage global/damagehandler.scr
```

Callback handler:

```
damage local.target local.inflictor local.damage local.position local.direction local.normal local.knockback local.damageflags local.meansofdeath local.location local.entity:
	// your code here
end
```

or

```
main local.target local.inflictor local.damage local.position local.direction local.normal local.knockback local.damageflags local.meansofdeath local.location local.entity:
	// you code here
end
```

Where:

- local.target - target entity isn't always player or actor entity. It can be a weapon entity or <b>world</b> entity
- local.inflictor - inflictor entity, entity that deals damage
- local.damage - float damage, damage amount
- local.position - vector position
- local.direction - vector direction
- local.normal - vector normal
- local.knockback - int knockback value
- local.damageflags - int damageflags
- local.meansofdeath - int meansofdeath
- local.location - int location id
- local.entity - entity that get's damage, often a player but can be any oder damageable entity

### Kill

kill ( Entity attacker, Float damage, Entity inflictor, Vector position, Vector direction, Vector normal, Integer knockback, Integer damageflags, Integer meansofdeath, Integer location, Entity player)

Event that is generated when player gets killed or when player kills somebody.

Registering:

```
local.result = registerev kill global/example.scr::kill
```

or

```
local.result = registerev kill global/killhandler.scr
```

Callback handler:

```
kill local.attacker local.damage local.inflictor local.position local.direction local.normal local.knockback local.damageflags local.meansofdeath local.location local.player:
	// your code here
end
```

or

```
main local.attacker local.damage local.inflictor local.position local.direction local.normal local.knockback local.damageflags local.meansofdeath local.location local.player:
	// you code here
end
```

Where:

- local.attacker - attacker entity (player) that killed
- local.damage - float damage, damage amount
- local.inflictor - inflictor entity, in most cases it isn't a player entity, it can be a weapon entity or <b>world</b> entity
- local.position - vector position
- local.direction - vector direction
- local.normal - vector normal
- local.knockback - int knockback value
- local.damageflags - int damageflags
- local.meansofdeath - int meansofdeath
- local.location - int location id
- local.player - player entity that got killed

### Keypress

keypress ( Entity player, Integer keynum )

Event that is generated when player has sent special key press command to server.

Registering:

```
local.result = registerev keypress global/example.scr::keypress
```

or

```
local.result = registerev keypress global/keypresshandler.scr
```

Callback handler:

```
keypress local.player local.keynum:
       // your code here
end
```

or

```
main local.player local.keynum:
        // your code here
end
```

Where:

- local.player - player that has sent special keypress command to server
- local.keynum - KeyID

To use this special event, scripter needs to bind certain player keys with command:

```
keyp #id
```

where **#id** is a number.

Example:

```
bind NumPad1 keyp 1
```

When error occurs (for example player instead of number has sent command like: keyp randomtext) a default KeyID will be returned, which is 0.

### Servercommand

servercommand ( Entity player, String command, String args )

Event that is generated when player has sent special server command to server.

Registering:

```
local.result = registerev servercommand global/example.scr::servercommand
```

or

```
local.result = registerev servercommand global/servercommandhandler.scr
```

Callback handler:

```
servercommand local.player local.command local.args:
       // your code here
end
```

or

```
main local.player local.command local.args:
        // your code here
end
```

Where:

- local.player - player that has sent special server command to server
- local.command - command
- local.args - command arguments as single not splitted string

To use this special event, scripter needs to bind certain player keys with command:

```
scmd command arg1 arg2 arg3 ...
```

where **command** is a command, and **arg1...** are command arguments.

Example:

```
bind NumPad1 scmd getplayerpos UnnamedSoldier
```

### Intermission

intermission ( Integer type )

Event that is generated when server enters intermission state, which happens during map changes, map restarts and player intermission screen.

Registering:

```
local.result = registerev intermission global/example.scr::intermission
```


or

```
local.result = registerev intermission global/intermissionhandler.scr
```

Callback handler:

```
intermission local.type:
       // your code here
end
```

or

```
main local.type:
        // your code here
end
```

Where:

- local.type - type of server intermission

```
0 = Player intermission screen
1 = Map change (happens after using commands: map, gamemap , but also right after player intermission screen)
2 = Map restart (happens after restart command)
```

## Miscellaneous

Kill and damage locations

```
-1 - General - ie:bash, rocket in the kisser, blown away, played catch, etc.. 
0 - Head 
1 - Helmet 
2 - Neck 
3 - Upper Torso 
4 - Middle Torso 
5 - Lower Torso 
6 - Pelvis 
7 - Upper Right Arm 
8 - Upper Left Arm 
9 - Upper Right Leg 
10 - Upper Left Leg 
11 - Lower Right Arm 
12 - Lower Left Arm 
13 - Lower Right Leg 
14 - Lower Left Leg 
15 - Right Hand 
16 - Left Hand 
17 - Right Foot 
18 - Left Foot
```

Means of Death

```
0 - none
1 - suicide
2 - crush
3 - crush_every_frame
4 - telefrag
5 - lava
6 - slime
7 - falling
8 - last_self_inflicted
9 - explosion
10 - explodewall
11 - electric
12 - electricwater
13 - thrownobject
14 - grenade
15 - beam
16 - rocket
17 - impact
18 - bullet
19 - fast_bullet
20 - vehicle
21 - fire
22 - flashbang
23 - on_fire
24 - gib
25 - impale
26 - bash
27 - shotgun
```

Default Damage Multipliers

```
-1 - 1.00
0 - 2.00
1 - 2.00
2 - 2.00
3 - 1.00
4 - 0.95
5 - 0.90
6 - 0.85
7 - 0.80
8 - 0.80
9 - 0.80
10 - 0.80
11 - 0.60
12 - 0.60
13 - 0.60
14 - 0.60
15 - 0.50
16 - 0.50
17 - 0.50
18 - 0.50
```