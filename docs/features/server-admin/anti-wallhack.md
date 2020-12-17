Reborn's Anti-Wallhack feature prevents cheaters from using wallhack cheats.
It's implemented fully server-side, which means that cheaters can't circumvent it the same
way as traditional client-side anticheat protections.

However, it's not perfect and it adds significant computation load to server.
It also causes player flickering (player model blinking, showing/hiding) when players
go behind a cover (such as walls).

You can try different anti-wallhack modes by setting **sv_antiwh** cvar on your server:
 
```
set sv_antiwh <0-6>
```

In modes 1, 2 and 3, there is additional cvar **sv_antiwhskipping** that is used to define
a player's ping above which anti-wallhack skips checks for particular player.

By default it's set to **400**.

```
set sv_antiwhskipping <0-999>
```

In practice it means that players with ping higher than defined by this cvar will be excluded from
anti-wallhack system. Players with high ping suffer from heavy flickering, and this cvar can help
those players, but it may mean that some cheaters will get excluded from anti-wallhack protection.