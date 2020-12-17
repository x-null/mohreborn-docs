Reborn patch comes with auto-update functionality.

This way your game server will update to the latest patch version without the need
of stopping the server and uploading new files by hand to your game hosting provider.

There are two cvars that control auto-update:

- sv_updatedelay
- sv_updatetest

### sv_updatedelay

**sv_updatedelay** cvar is used to specify for how long will your server wait until next update check.

The value is specified in hours and you can set it as follows:

```
set sv_updatedelay <1-65000>
```

By default it's set to 12 hours, so Reborn-powered server will check for new patch update every 12 hours.

To disable auto-update, you can set it to a very high value, but it's not recommended,
because you may miss important security or stability updates and bug fixes.

Server administrators shouldn't also set it to very low values,
because server might start to check for new updates too often
which may lead to higher server pings and bandwidth consumption.

### sv_updatetest

Reborn patch is released in two channels:

- stable release channel
- test release channel

You might be familiar with this concept, because many web browsers use similar approach.

**sv_updatetest** cvar is used to switch between Stable Release Channel and Test Release Channel.

```
sv_updatetest <0-1>
```

By default, it's set to 0.

When it's set to 1, updates will switch to the Test Release Channel and will update
Reborn patch to test/experimental patch releases, that are not tested and not confirmed to be stable.

If server administrator decides to use Test Release Channel, it is recommended to set this cvar from command line,
by editing executable shortcut (Windows) or startup script (Windows/Linux) and adding following line:

```
+seta sv_updatetest 1
```
