## Chat filtering

Sometimes you may want to keep game chat free from mean curse words
in order to make your server friendly to younger players.

Chat filtering lets you ban certain bad words from being used in public game chat.

You can also use it to ban words that are used to describe places on the game map. 
This way it will be harder for spectators to spoil the fun for others.

Chat filters are controlled with following commands:

- [chatfilteradd](#chatfilteradd)
- [chatfilterremove](#chatfilterremove)
- [listchatfilter](#listchatfilter)

!!! hint
    All listed commands work via RCon.
    They can be used by admin accounts, by prefixing them with **ad_** keyword.
    
    See [Admin accounts and permissions](accounts-and-permissions.md) for more information.

Filtered words are stored in **chatfilter.cfg** file that can be edited by hand with text editor.

- Each word should be added in a new line.
- Line comments are supported, and work by adding double slashes in front of the line that should
  be commented out.

Below is an example of chatfilter.cfg file:

```
piss
piss off
pissoff
// comment
shit
wank
bollocks
rush B
```

!!! note
    Only basic words are supported in current version, so wildcards do not work. 
    You will need to add the different versions of words you wish to block as new entries.
    
If a player uses a filtered word, they will be sent a message in game to warn them.
The message is blocked and not displayed on the screen.
Users are given (by default) 3 chances before being kicked from the server for using bad words.

### g_badchatlimit cvar

The default limit of warnings that player can receive before being kicked is configurable
with **g_badchatlimit** cvar.

Setting this cvar to high numbers is not recommended because it will make chat filters useless. 
Don't set **g_badchatlimit** to negative numbers, as this may lead to undefined patch behavior.

When **g_badchatlimit** is set to 0, player that says a bad word will be kicked immediately, without any warning.

### <a name="chatfilteradd"></a> chatfilteradd

**chatfilteradd** command adds the given word to the list of chat filtered words.

Usage:

```
chatfilteradd <word>
```

for example:

```
chatfilteradd bollocks
```

### <a name="chatfilterremove"></a> chatfilterremove

**chatfilterremove** command removes the word from chat filtered words list.

Players will be able to use that word again, without being punished.

Usage:

```
chatfilterremove <word>
```

for example:

```
chatfilterremove bollocks
```

### <a name="listchatfilter"></a> listchatfilter

**listchatfilter** command lists all words that are filtered from the chat.

It supports paging, which means that it splits all filtered words into smaller groups,
which allows you to view them without scrolling inside game console.

Usage:

```
listchatfilter <page number #>
```

for example:

```
listchatfilter 3
```

There are 20 pages maximum, you can choose between page 1-20.

## Disabling chat

It is possible to disable game chat entirely. This may be useful, when you do not have time
and resources for proper chat administration, or when you simply prefer more focused gameplay,
and you consider game chat to be a distraction.

You may also wish to disable only voice taunts, which can be annoying when players
spam them.

You can disable chat globally with following cvars:

- [sv_disablechat](#disable-chat-cvar)
- [sv_disabletaunt](#disable-taunts-cvar)

or individually for selected players with following commands:

- [dischat](#disable-chat-command)
- [distaunt](#disable-taunts-command)

### <a name="disable-chat-cvar"></a> sv_disablechat cvar

When this cvar is set to 1, server's chat will be disabled and players won't be able to send messages at all.
This includes global/public chat, team chat, and private chat.

In-game messages about kills and deaths will still be visible.

### <a name="disable-taunts-cvar"></a> sv_disabletaunt cvar

This cvar disables taunts for all players on a server, when set to 1.
You can disable it by setting it back to 0.

### <a name="disable-chat-command"></a> dischat

**dischat** command disables all chat abilities for player with given ID/game slot (clientnum).
You can check player's clientnum with **status** command.

If the command is used on player with chat already disabled, it will re-enable it.

Usage:

```
dischat <clientnum #>
```

for example:

```
dischat 5
```

### <a name="disable-taunts-command"></a> distaunt

**distaunt** command disables all taunt abilities for player with given ID/game slot (clientnum).
You can check player's clientnum with **status** command.

If the command is used on player with taunts already disabled, it will re-enable it them.

Usage:

```
distaunt <clientnum #>
```

for example:

```
distaunt 5
```