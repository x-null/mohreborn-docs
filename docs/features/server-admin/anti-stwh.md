Some cheats make it possible to shoot and kill players through solid walls.
Reborn patch introduced fix that detects bullets going through walls and blocking them,
by setting their damage to 0.

This fix is enabled by default, however it may cause false-positives, especially for players
that often use clipping as their gameplay mechanic.

It's controlled by **sv_antistwh** cvar:

```
set sv_antistwh <0-1>
```

Disabling this protection can be important for those who play clan wars where clipping is considered
a part of important tactic.

However, most players will never notice that this protection is enabled, so think well before turning it off.

 