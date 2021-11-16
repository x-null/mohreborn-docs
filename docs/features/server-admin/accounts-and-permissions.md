## Managing admin accounts

### Permissions

Not all actions, that your admins can perform, come with equal consequences.
While some of them are hard to misuse, others can give ultimate power.

This is why you have to assign appropriate privileges to every admin account,
which tell what commands given admin is permitted to issue on the server.

Each permission controls selected commands, and you can fine-tune what given
admin account can do, by combining those permissions.

#### List of available permissions

| Name                    | Numeric Value | Allowed commands                                                               | Description                                                                 |
|-------------------------|--------------:|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
| ACCESSLEVEL_PROTECTNAME | 1             | ad_protname, ad_unprotname, ad_listprotnames                                   | One can protect/unprotect and list protected names                          |
| ACCESSLEVEL_MAPCHANGE   | 2             | ad_map                                                                         | One can change maps                                                         |
| ACCESSLEVEL_RESTART     | 4             | ad_restart                                                                     | One can restart the game                                                    |
| ACCESSLEVEL_GAMETYPE    | 8             | ad_gametype                                                                    | One can change gametype                                                     |
| ACCESSLEVEL_FRAGLIMIT   | 16            | ad_fraglimit                                                                   | One can change frag limit                                                   |
| ACCESSLEVEL_TIMELIMIT   | 16            | ad_timelimit                                                                   | One can change time limit                                                   |
| ACCESSLEVEL_KICK        | 32            | ad_kick, ad_kickr, ad_clientkick, ad_clientkickr                               | One can kick players from game                                              |
| ACCESSLEVEL_BADCMD      | 64            | wuss, tele, noclip, dog                                                        | One can use bad commands, for admin debug/scripting purposes                |
| ACCESSLEVEL_BAN         | 128           | ad_banip, ad_banipr, ad_banid, ad_banidr, ad_banname, ad_listips, ad_listnames | One can ban and list players IPs/names                                      |
| ACCESSLEVEL_REMOVEBAN   | 256           | ad_unbanip, ad_unbanname, ad_listips, ad_listnames                             | One can unban and list players IPs/names                                    |
| ACCESSLEVEL_CHATFILTER  | 512           | ad_chatfilteradd, ad_chatfilterremove, ad_listchatfilter, ad_dischat           | One can add/remove/list words in chat filters list and disable players chat |
| ACCESSLEVEL_ADMINPROCMD | 1024          | Not used                                                                       | Unused in this version                                                      |
| ACCESSLEVEL_LISTADMINS  | 2048          | ad_listadmins                                                                  | One can view a list of ClientAdmins                                         |
| ACCESSLEVEL_RCON        | 4096          | ad_rcon                                                                        | One can have a full access to RCon console                                  |
| ACCESSLEVEL_MAX         | 16383         | All above commands                                                             | One has all rights                                                          |

### Creating, editing and deleting accounts

Reborn patch uses **admin.ini** file to store admin accounts credentials.

To create new accounts, edit or delete existing ones, you have to edit this file with text editor of your choice
(for example Windows Notepad).

They are loaded during patch initialization which happens on each map change and during first game server startup.

Each account has to be represented as new line in the file.
It consists of account login, password and access level which determines account privileges.

The template looks as follows:

```
login= password= rights=
```

Below is **admins.ini** file example, which defines 2 admin accounts with different rights:

```
login=->|ClanTag|<- MyName password=mySeCrEt rights=16383
login=test password=another_password rights=1
```

!!! note
    Don’t use TAB’s to make spaces between login, password, rights. Instead use spaces. 
    Engine can handle TAB’s but it’s more safe to use spaces.

#### Combining permissions

You can combine several permissions which you want to give to admin account, by taking numeric values
assigned to each permission and adding them together.

For example, if we want to create new admin account with permissions to use commands:

- ad_restart
- ad_map
- ad_kick, ad_kickr, ad_clientkick, ad_clientkickr

We take numeric values of permissions:

- ACCESSLEVEL_RESTART: **4**
- ACCESSLEVEL_MAPCHANGE: **2**
- ACCESSLEVEL_KICK: **32**

and add them toghether:

**4** + **2** + **32** = **38**

Then we create new entry in **admins.ini** file:

```
login=chris123 password=mySuperSecretPassw0rd! rights=38
```

## Managing server using admin account

### Logging-in

Connect to the server with your game client, by joining to the game as regular player.
Then open your game console (use tilde '~' on your keyboard) and type the following command:

```
ad_login <login> <password>
``` 

for example:

```
ad_login chris123 mySuperSecretPassw0rd!
```

Based on validity of provided credentials, you will receive one of two possible messages:

- "Admin System> You have been authed as admin"
- "USAGE: ad_login - wrong login or password. Please try again."

Once you've successfully authenticated yourself, you will remain logged-in until you disconnect
from the server.

### Issuing commands

Once you have successfully logged-in to your admin account, you can start
issuing commands.

All server admin commands start with **ad_** prefix.

Open your game console during gameplay and simply type a command, for example:
**ad_status**.

You will see result of executing the command in your console.

If you are not logged-in to your admin account or don't have enough permissions,
you will receive appropriate information. 

## Server audit

Sometimes you want to make an audit and investigate who issued what commands
and from which admin account.

It is possible to do this by configuring your server to include such information in server logs.
You have to add ```+set developer 2``` to your server command-line startup script.

!!! note
    There can be a difference in what information is logged based on OS (Windows vs Linux).