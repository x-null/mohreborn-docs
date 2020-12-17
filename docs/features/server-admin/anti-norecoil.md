NoRecoil cheat disables weapon kick/recoil when shooting.
It gives huge advantage to players who use spraying weapons like Thompson etc.

Anti-NoRecoil tries to detect cheaters with recoil removed.
It does that server-side (which means cheaters can't bypass it) and then it applies
recoil server-side for those players.

However, server-side recoil emulation adds significant server load and detection is still not
perfect and can cause false-positives, meaning that some players will be falsely marked as cheaters
and will have server-side recoil added on top of the one their game client already adds.

You can test anti-norecoil feature by using **sv_recoilemulation** cvar:

```
set sv_recoilemulation <0-1>
```