It's recommended to have this protection turned on, because it protects your server against flood attacks.

Keep in mind that this protection won't protect you against DDoS attacks with very high network traffic, 
but it can significantly reduce other types of attacks performed by less experienced people.

You can control this protection with **sv_packetantiflood** cvar:

```
sv_packetantiflood <0-1>
```

By default, it's turned on (set to 1).

You may want to turn it off, when server administration applications (CI, Foresight, Scapp etc.) are running,
because the Anti Packet Flood System may block them.

If you use tools that work by sending commands to your server via RCon protocol, it's recommended to use
**sv_remotetoolip** cvar.

It's used to set IP address from which your remote server monitoring tool (like CI, ForeSight or Scapp)
connects to server. This IP will be excluded from list of potential flooders.

```
set sv_remotetoolip <ip>
```

for example:

```
set sv_remotetoolip 127.0.0.1
```

If you use GsProtector, which fulfills the task of packet flood protection, it is recommended to turn it off 
in order to not double the protection as it may block all packets, randomly drop players 
and cause stability issues or player connection issues.

Anti Packet Flood comes with two additional cvars that help to fine tune the behavior:

- sv_packetflooddelay
- sv_packetfiltertime


### sv_packetflooddelay

**sv_packetflooddelay** cvar is used to set the allowed time delay
between two incoming packets from the same IP address.

When delay between two packets is lower than this cvars value,
they will be flagged as flood and dropped by the patch before they reach the engine.

The value is in milliseconds and you can set it as follows:

```
sv_packetflooddelay <0-65000>
```

By default, it's set to 50 milliseconds.

You shouldn't set the value higher than 500ms, because this may block packets of legit connected players,
and you may have problems with your server not showing on game server browsers or have 
server administration applications (like CI, Foresight, Scapp etc.) kick random players from server.

### sv_packetfiltertime

**sv_packetfiltertime** cvar is used as throttle time window.

When Anti Packet Flood System detects, that 5 continuously incoming packets arrived to the server faster
than packet time delay configured by **sv_packetflooddelay** cvar, it will turn on time throttle window.
From this point on, it will drop **all** incoming packets for specified amount of milliseconds.

You can set the throttle window in milliseconds as follows:

```
set sv_packetfiltertime <0-65000>
```

By default it's set to 2000 (ms).

Value of this cvar shouldn't be lower than 100ms, because Anti Packet Flood System will drop incoming packets
for this amount of time, which may be insufficient to protect the server from the packets flood.

!!! note
    Packet Time Throttle Window will be only used when IP Hash Table will fail to initialize.



