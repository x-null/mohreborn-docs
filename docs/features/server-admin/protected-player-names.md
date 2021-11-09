It is a common problem that malicious players join servers under well-established,
well-known names of other respected players and cause harm to their name and reputation.

Sometimes they also might pretend to be server admin by stealing their name.

With Reborn patch, you can password-protect player names, so only person that knows
a password can use given name on your server.

This functionality is controlled with following commands:

- [protname](#protname)
- [unprotname](#unprotname)
- [listprotnames](#listprotnames)

!!! hint
    All listed commands work via RCon.
    They can be used by admin accounts, by prefixing them with **ad_** keyword.
    
    See [Admin accounts and permissions](accounts-and-permissions.md) for more information.
    
Protected names are stored in **protectednamefilter.cfg** file that can be edited by hand with text editor.

- Each protected name should be added in a new line.
- Line comments are supported, and work by adding double slashes in front of the line that should
  be commented out.

Below is an example of protectednamefilter.cfg file:

```
name=->|ClanTag|<- MyName password=sEcUrE_password
name=bestPlayer password=weakOne
name=[CLAN]-CL DontStealMyName password=veryhardtoguess

// and so on
```

To set the password and join server with protected name, player has to type:

```
setu cl_namepass <password>
```

in the MoHAA game console in order to use protected name.

### <a name="protname"></a> protname

**protname** command protects given name with password.

Usage:

```
protname <playername> <password>
```

for example:

```
protname RazoRapiD testpassword
```

### <a name="unprotname"></a> unprotname

**unprotname** command removes the name from the list of protected names.
From this point, given name can be used by anyone without the need of 
providing server with password.

Usage:

```
unprotname <name>
```

for example:

```
unprotname RazoRapiD
```

### <a name="listprotnames"></a> listprotnames

**listprotnames** command lists protected names, stored in protectednamefilter.cfg.

It supports paging, which means that it splits all protected names into smaller groups,
which allows you to view them without scrolling inside game console.

Usage:

```
listprotnames <page number #>
```

for example:

```
listprotnames 3
```

There are 20 pages maximum, you can choose between page 1-20.