# Player voting

MoH:AA/SH/BT is known to have broken voting system.
It's rarely used by server admins and players.

Reborn introduces new, upgraded vote system, that server admins and players can use
to build servers that take players will into consideration.

If server admin has enabled player voting on his server, you can cast new votes and vote
to propose a change in server settings to other players.

To cast a vote, you need to use **callvote** command in your game console as follows:

```
callvote <command>
```

!!! info
    You can open your game console by hitting tilde (~) on your keyboard while being
    connected to the server.
    
This is exactly the same way you would create votes on non-Reborn servers.
What's different is that once you create a vote, all players will see summary of the vote
in the bottom left corner of the screen.

The vote summary consists of:

- Command that will be executed on the sever once the voting passes
- Percentage of "No" votes
- Percentage of "Yes" votes
- Time left until voting ends

Other players can vote "yes" or "no" by sending command from their game console:

```
vote yes
```

or

```
vote no
```

Once the vote passed - the proposed command will be executed on server.

!!! note
    Server admin can limit what commands can be used in voting on the server.

If server owner allowed to vote for map changes with **map** or **gamemap** commands,
you can call a vote for a map change like so:

```
callvote map dm/mohmdm6
```

However, server admin can control what maps are allowed for voting.
For example - if server is OBJ only, server admin might want to limit maps available
for voting only to those that support OBJ gameplay.

To know what maps you can use in votes, you can type **allowedmaps** command in your game console.