You can limit how many players can connect to your server from the same IP address.
This feature helps to protect your server against fake players.

You can control the limit with **sv_maxconnperip** cvar.

```
set sv_maxconnperip <0-100>
```

To turn off the protection, set this cvar to -1.
If you set it to 0, all connections will be rejected.

When more players with same IP address will try to connect to the server, they will be rejected.

!!! note
    Maximum value is 100, but patch supports only 64 players, so real limit is from 0 to 64.

