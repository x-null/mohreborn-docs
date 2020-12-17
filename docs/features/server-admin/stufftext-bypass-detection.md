If your server makes heavy use of stufftext commands and you want to make sure
that those commands take effect on players who joined your server, you might want to enable
this feature in order to detect players that have their MOHAA game modified to ignore
stufftext command.

You can enable it as follows:

```
set sv_stufftextdetection <0-1>
```

Players that use stufftext bypass will be kicked from server.

!!! warn
    Keep in mind that this feature is **unstable** and it can kick clean players.

!!! info
    Since many server admins abuse stufftext to hack players and fiddle with player's
    game config, we may remove this feature in future Reborn patch versions.