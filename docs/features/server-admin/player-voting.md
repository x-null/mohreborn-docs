# Player voting

MoH:AA/SH/BT is known to have broken voting system.
It's rarely used by server admins and players.

Reborn introduces new, upgraded vote system, that server admins and players can use
to build servers that take players will into consideration.

As server administrator, there are few cvars and configuration files
that let you control new voting mechanism.

### g_allowvote

**g_allowvote** cvar is used to enable or disable voting on server.

```
set g_allowvote <0-1>
```

### g_votetimeout

**g_votetimeout** cvar sets vote expiration time.

Time is counted in minutes. After this time, vote will expire and server will evaluate Yes and No votes and make a decision whether vote has passed or not.
If you want to set vote expire time to less than 1 minute, type 0.x, where x is a number.

```
set g_votetimeout <0-5>
```

Examples:

- 0.5 -> 30 seconds
- 1.5 -> 90 seconds
- 0.33 -> around 20 seconds (1/3 of minute)

By default it's set to 1 minute.

## Configuring vote limitations

You can control what server commands players can vote for.
You may want to let players vote for map changes, but not for map restarts or player kicks/bans, or vice versa.

**allowedvotes.cfg** file stores a list of all commands that players can use when calling a vote with **callvote** command.

Each command entry should appear in a new line.
Player will only be able to cast votes with commands from this list.
If the list is empty, they won't be able to cast a vote even if voting is enabled on the server.

This is an example of such file:

```
restart
map
```

If you allow **map** or **gamemap** commands to be used in votes, you can additionally
control what maps players can vote for when they want to change a map.

The list of maps allowed to be used during voting is stored in **allowedmaps.cfg** file.

Each map name should be placed in a new line.
Players can see the list of allowed maps by issuing **allowedmaps** command from game console during gameplay.

This is an example of such file:

```
dm/mohdm2
obj/obj_team2
```

