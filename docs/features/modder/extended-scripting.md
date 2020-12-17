## Introduction

Reborn patch has introduced a number of new scripting commands available for people to utilize in their mods.

## File Handlers
ScriptThread -> Listener -> Class

### fopen

fopen( String filename, String accessType )

Opens file. Example:

```
local.file = fopen "main/config.txt" "a+"
```

or

```
local.file = fopen("main/config.txt" "a+")
```

Result:

```
Command returns file handle that is needed for identification and further operations on this file.
```

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - fopen

### fclose

fclose( Integer filehandle )


Closes file. Example:

```
local.return = fclose local.file
```

or

```
local.return = fclose(local.file)
```

Result:

```
If file is successfully closed, a zero value is returned.
On failure, EOF is returned.
```

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - fclose

### feof

feof( Integer filehandle )

Checks for end of file. Example:

```
local.return = feof local.file
```

or

```
local.return = feof(local.file)
```

Result:

```
A non-zero value is returned in the case that the End-of-File indicator associated with the file is set.
Otherwise, a zero value is returned.
```

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - feof

### fseek

fseek( Integer filehandle, Integer offset, Integer origin )

Sets the position indicator associated with the file to a new position
defined by adding offset to a reference position specified by origin.

Example:

```
local.return = fseek local.file 154 0
```

or

```
local.return = fseek(local.file 154 0)
```

Where origin:

- 0 = SEEK_SET
- 1 = SEEK_CUR
- 2 = SEEK_END

Result:

```
If successful, the function returns a zero value.
Otherwise, it returns nonzero value.
```

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - fseek

### ftell

ftell( Integer filehandle )

Returns the current value of the position indicator of the file. Example:

```
local.return = ftell local.file
```

or

```
local.return = ftell(local.file)
```

Result:

```
On success, the current value of the position indicator is returned.
If an error occurs, -1 is returned.
```

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - ftell

### frewind

frewind( Integer filehandle )

Sets the position indicator associated with file to the beginning of the file.
Example:

```
local.return = frewind local.file
```

or

```
local.return = frewind(local.file)
```

Result:

```
none
```

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - rewind

### foutc

foutc( Integer filehandle, String character )

Writes a character to the file and advances the position indicator.
Example:

```
local.return = fputc local.file "a"
```

or

```
local.return = fputc(local.file "a")
```

Result:

```
If there are no errors, the same character that has been written is returned.
If an error occurs, EOF is returned and the error indicator is set.
```

You have to cast returned value to char.
If you pass longer string, only first character will be written to file.

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - fputc

### fputs

fputs( Integer filehandle, String text )

Writes text to the file and advances the position indicator.
Example:

```
local.return = fputs local.file "This is example"
```

or

```
local.return = fputs(local.file "This is example")
```

Result:

```
On success, a non-negative value is returned.
On error, the function returns EOF.
```

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - fputs

### fgetc

fgetc( Integer filehandle )

Reads single character from file.
Example:

```
local.char = fgetc local.file
```

or

```
local.char = fgetc(local.file)
```

Result:

```
The character read is returned as an int value.
```

You need to cast it to char if you want to use it in string.

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - fgetc

### fgets

fgets( Integer filehandle, Integer maxbuffsize )

Reads string line from file.
Where:

- **maxbuffsize** specifies maximum buffer size that will be allocated to store the string in memory.

Example:

```
local.text = fgets local.file 256
```

or

```
local.text = fgets(local.file 256)
```

Result:

```
If the End-of-File is encountered and no characters have been read 0 (null) is returned.
If an error occurs 0 (null) is returned.
```

If a memory allocation error occurs, -1 is returned.

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - fgets

### ferror

ferror( Integer filehandle )

Checks if the error indicator associated with file is set, returning a value different from zero if it is.

Example:

```
local.ret = ferror local.file
```

or

```
local.ret = ferror(local.file)
```

Result:

```
If the error indicator associated with the file was set, the function returns a nonzero value.
Otherwise, it returns a zero value.
```

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - ferror

### fflush

fflush( Integer filehandle )

If the given file was open for writing and the last i/o operation was an output operation, any unwritten data in the output buffer is written to the file.

!!! note
    The file remains open after this command.

Example:

```
local.ret = fflush local.file
```

or

```
local.ret = fflush(local.file)
```

Result:

```
A zero value indicates success.
If an error occurs, EOF is returned and the error indicator is set.
```

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - fflush

### fexists

fexists( String filename )

Checks if file with given filename exists.
Example:

```
local.ret = fexists "folder/folder2/file.txt"
```

or

```
local.ret = fexists("folder/folder2/file.txt")
```

Result:

```
If file exists, function returns 1. Otherwise it returns 0.
```

!!! important
    You can open only 32 files at once.

###freadall

freadall( Integer filehandle )

Reads whole file into a string at once. File has to be opened in binary mode (rb, rb+)

Example:

```
local.content = freadall local.file
```

or

```
local.content = freadall(local.file)
```

Result:

```
Function returns file content as string.
```

!!! warning
    Don't read binary files with this function because it may cause memory leaks.

!!! important
    You can open only 32 files at once.

### fsaveall

fsaveall( Integer filehandle, String content )

Writes string content to file at once. File has to be opened in binary mode (wb, wb+, ab). The content will start to be saved from the current file position.

Example:

```
local.ret = fsaveall local.file local.content
```

Result:

```
Function returns number of character written to file or -1 if content is NULL.
```

!!! important
    You can open only 32 files at once.

### fremove

fremove( String filename )

Removes the file with given filename.
Example:

```
local.ret = fremove local.filename
```

Result:

```
If the file is successfully deleted, a zero value is returned.
On failure, a nonzero value is returned and the errno variable is set to the corresponding error code.
```

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - remove

### frename

frename( String oldname, String newname )

Renames the file with given filename.
Example:

```
local.ret = frename local.oldname local.newname
```

Result:

```
If the file is successfully renamed, a zero value is returned.
On failure, a nonzero value is returned and the errno variable is set to the corresponding error code.
```

!!! important
    You can open only 32 files at once. This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - rename

### fcopy

fcopy( String filename, String copyname )

Creates a copy of file.
Example:

```
local.ret = fcopy local.filename local.copyname
```

Result:

```
If the file is successfully copied, a zero value is returned.
When function fails to open original file, a -1 value is returned.
When function fails to create a second file, a -2 value is returned.
When function fails during data copy process, a -3 value is returned.
```

!!! important
    You can open only 32 files at once.

### freadpak

freadpak( String filename )

Reads file located inside .pk3 file in text mode and returns it's content as string.
Example:

```
local.content = freadpak local.filename
```

Result:

```
If the file is successfully read, function returns a string with it's content.
When function fails to find, open or read a file from .pk3, a -1 value is returned.
```

!!! important
    You can open only 32 files at once.

### flist

flist( String path, String extension, Integer scanSubDirectories )

Returns a list (array) of files with given extension located in given path. Function handles .pk3 folder structure and normal system directories. When scanSubDirectories equals 1, function will include subdirectories located under directory path.

Extension needs to have "." (dot) included. Otherwise it will act as filter.

Example:

```
local.list = flist local.path local.extension local.scanSubDirectories
```

Result:

```
List with filenames and their paths found.
```

!!! important
    You can open only 32 files at once.

## iHuddraws

ScriptThread -> Listener -> Class

### ihuddraw_align

ihuddraw_align( Entity player, Integer index, String h_align, String v_align )

Sets the alignment of a huddraw element for individual player.

Where:

- h_align = "left", "center", "right"
- v_align = "bottom", "center", "top"
- index = index of huddraw element to be set
- player = entity of player that will have his huddraw element set

Example:

```
ihuddraw_align $player[1] 15 right top
```

or

```
ihuddraw_align( $player[1] 15 "right" "top" )
```

### ihuddraw_alpha

ihuddraw_alpha( Entity player, Integer index, Float alpha )

Sets the alpha of a huddraw element for individual player.

Where:

- index = index of huddraw element to be set
- player = entity of player that will have his huddraw element set

Example:

```
ihuddraw_alpha $player[1] 15 1
```

or

```
ihuddraw_alpha( $player[1] 15 1 )
```

### ihuddraw_color

ihuddraw_color( Entity player, Integer index, Float red, Float green, Float blue )

Sets the color for a huddraw element for individual player.

Where:

- index = index of huddraw element to be set
- player = entity of player that will have his huddraw element set

Example:

```
ihuddraw_color $player[1] 15 1 1 1
```

or

```
ihuddraw_color( $player[1] 15 1 1 1 )
```

### ihuddraw_font

ihuddraw_font( Entity player, Integer index, String fontname )

Sets the font to use for a huddraw element, for individual player.

Where:

- index = index of huddraw element to be set
- player = entity of player that will have his huddraw element set

Example:

```
ihuddraw_font $player[1] 15 "verdana-14"
```

or

```
ihuddraw_font( $player[1] 15 "verdana-14" )
```

### ihuddraw_rect

ihuddraw_rect( Entity player, Integer index, Integer x, Integer y, Integer width, Integer height )

Specifies the position of the upper left corner and size of a huddraw element for individual player

Where:

- index = index of huddraw element to be set
- player = entity of player that will have his huddraw element set

Example:

```
ihuddraw_rect $player[1] 15 -140 65 0 0
```

or
```
ihuddraw_rect( $player[1] 15 -140 65 0 0 )
```

### ihuddraw_shader

ihuddraw_shader( Entity player, Integer index, String shader )

Sets the shader to use for a particular huddraw element for individual player

Where:

- index = index of huddraw element to be set
- player = entity of player that will have his huddraw element set

Example:

```
ihuddraw_shader $player[1] 15 "textures/hud/axis"
```

or

```
ihuddraw_shader( $player[1] 15 "textures/hud/axis" )
```

### ihuddraw_string

ihuddraw_string( Entity player, Integer index, String string )

Sets a string to be displayed. Clears the shader value of huddraw element for individual player

Where:

- index = index of huddraw element to be set
- player = entity of player that will have his huddraw element set

Example:

```
ihuddraw_string $player[1] 15 "I luv Reborn 1.12 Patch!"
```

or

```
ihuddraw_string( $player[1] 15 "I luv Reborn 1.12 Patch!" )
```

### ihuddraw_virtualsize

ihuddraw_virtualsize( Entity player, Integer index, Integer virtual )

Sets if the huddraw element (for individual player) should use virutal screen resolution for positioning and size.

Where:

- index = index of huddraw element to be set
- player = entity of player that will have his huddraw element set

Example:

```
ihuddraw_virtualsize $player[1] 15 1
```

or

```
ihuddraw_virtualsize( $player[1] 15 1 )
```

## Player

ScriptThread -> Listener -> Class

### netname

netname( Entity player )

Gets player's name and returns it as string.
Example:

```
local.player_name = netname $player[1]
```

or

```
local.player_name = netname( $player[1] )
```

### getip

getip( Entity player )

Gets player's ip address with port and returns it as string.
Example:

```
local.player_ip = getip $player[1]
```

or

```
local.player_ip = getip( $player[1] )
```

Result:

```
127.0.0.1:12203
```

### getping

getping( Entity player )

Gets player's ping and returns it as integer.
Example:

```
local.player_ping = getping $player[1]
```

or

```
local.player_ping = getping( $player[1] )
```

### getclientnum

getclientnum( Entity player )

Gets player's client number and returns it as integer.
Example:

```
local.player_clnum = getclientnum $player[1]
```

or

```
local.player_clnum = getclientnum( $player[1] )
```

## Player 

Player (player) -> Sentient -> Animate -> Entity -> SimpleEntity -> Listener -> Class

### addkills

addkills( Integer kills )

Adds number of kills to player. (Can be also negative)
Example:

```
$player[1] addkills 5
```

or

```
$player[1] addkills -5
```

Result:

```
If player had 8 kills, he will have 13 kills
```

or

```
If player had 8 kills, he will have 3 kills
```

### adddeaths

adddeaths( Integer deaths )

Adds number of deaths to player. (Can be also negative)
Example:

```
$player[1] adddeaths 5
```

or

```
$player[1] adddeaths -5
```

Result:

```
If player had 8 deaths, he will have 13 deaths
```

or

```
If player had 8 deaths, he will have 3 deaths
```

### getkills

getkills( void )

Gets number of player's kills and returns it as integer
Example:

```
local.player_kills = $player[1] getkills
```

or

```
local.player_kills = $player[1] getkills( )
```

Result:

```
Number of players that this player has killed.
```

### getdeaths

getdeaths( void )

Gets number of player's deaths and returns it as integer.
Example:

```
local.player_deaths = $player[1] getdeaths
```

or

```
local.player_deaths = $player[1] getdeaths( )
```

Result:

```
Number of player's deaths.
```

!!! important
    Before using this function, check game type that is currently running. When g_gametype is 3 or 4, deaths aren't counted and result of this function will equal to kills amount that player has

### isadmin

isadmin( void )

Checks if player is currently logged in as server administrator.
Example:

```
local.admin = $player[1] isadmin
```

or

```
local.admin = $player[1] isadmin( )
```

Result:

```
Returns 1 if player is logged in as administrator, otherwise it returns 0.
```

### getconnstate

getconnstate( void )

Gets state of player's connection.
Example:

```
local.connection_state = $player[1] getconnstate
```

or

```
local.connection_state = $player[1] getconnstate( )
```
Result:

```
Returns integer value:
0 = CS_FREE - given player slot is free
1 = CS_ZOMBIE - given player slot is in zombie state (his data is still kept after he disconnected or lost connection)
2 = CS_CONNECTED - player has connected to server, but he's not yet in the game
3 = CS_PRIMED - player has passed through authorization checks and finished downloading any missing files
4 = CS_ACTIVE - player is in game and can start playing
```

### getactiveweap

getactiveweap( Integer weaponhand )

Gets currently active weapon from player's hand of given index
Example:

```
local.weapon = $player[1] getactiveweap 0
```

or

```
local.weapon = $player[1] getactiveweap(0)
```

Result:

```
Weapon entity.
```

!!! important
    You can use weaponhand index from 0-2 range, but it's preffered to use only 0 index, because other indexes my return false values that might crash server

### .secfireheld

.secfireheld( void )

Returns 1 if player is holding secondary fire button.
Example:

```
if( $player[1].secfireheld == 1 )
...
```

Result:

```
1 = player is holding secondary fire button
0 = opposite
```

### .userinfo

.userinfo( void )

Returns player's userinfo
Example:

```
local.userinfo = $player[1].userinfo
```

Result:

```
String with player's userinfo
```

### .inventory

.inventory( void )

Returns player's inventory
Example:

```
local.inventory= $player[1].inventory

local.inventorySize = $player[1].inventory.size

local.item1 = $player[1].inventory[0]
```

Result:

```
Array with entities in player's inventory. You can assign it to a variable or access directly.
```

### bindweap

bindweap( Entity weapon )

Binds weapon to player. Sets him as weapon owner.
2nd use of the command will unbind the weapon from player.

Example:

```
$player[1] bindweap local.weapon
local.weapon anim fire
$player[1] bindweap local.weapon
```

Result:

```
Sets player as weapon owner.
```

!!! warning
    This is sort of a hack&trick scripting command. It should only be used by experienced users and only like shown in the example - just before firing the weapon and just after, to unbind it from the player. Otherwise you can have errors, weapon model glued to player, or server crashes. It should be used only for some kind of remote turrets etc.

## Maths

ScriptThread -> Listener -> Class

### cos

cos( Float x )

Returns the cosine of an angle of x radians.

Example:

```
local.result = cos local.x
```

Result:

```
Cosine of x.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - cos

### sin

sin( Float x )

Returns the sine of an angle of x radians.
Example:

```
local.result = cos local.x
```

Result:

```
Cosine of x.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - cos

### tan

tan( Float x )

Returns the tangent of an angle of x radians.
Example:

```
local.result = tan local.x
```

Result:

```
Tangent of x.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - tan

### acos

acos( Float x )

Returns the principal value of the arc cosine of x, expressed in radians.
Example:

```
local.result = acos local.x
```

Result:

```
Floating point value in the interval [-1,+1].
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - acos

### asin

asin( Float x )

Returns the principal value of the arc sine of x, expressed in radians.
Example:

```
local.result = asin local.x
```

Result:

```
Floating point value in the interval [-1,+1].
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - asin

### atan

atan( Float x )

Returns the principal value of the arc tangent of x, expressed in radians.

Notice that because of the sign ambiguity, a function cannot determine with certainty in which quadrant the angle falls only by its tangent value. You can use atan2 if you need to determine the quadrant.

Example:

```
local.result = atan local.x
```

Result:

```
Principal arc tangent of x, in the interval [-pi/2,+pi/2] radians.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - atan

### atan2

atan2( Float y, [I]Float[I] x )

Returns the principal value of the arc tangent of y/x, expressed in radians.

To compute the value, the function uses the sign of both arguments to determine the quadrant.

Example:

```
local.result = atan2 local.y local.x
```

Result:

```
Principal arc tangent of y/x, in the interval [-pi,+pi] radians.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - atan2

### cosh

cosh( Float x )

Returns the hyperbolic cosine of x.
Example:

```
local.result = cosh local.x
```

Result:

```
Hyperbolic cosine of x.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - cosh

### sinh

sinh( Float x )

Returns the hyperbolic sine of x.
Example:

```
local.result = sinh local.x
```

Result:

```
Hyperbolic sine of x.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - sinh

### tanh

tanh( Float x )

Returns the hyperbolic tangent of x.
Example:

```
local.result = tanh local.x
```

Result:

```
Hyperbolic tangent of x.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - tanh

### exp

exp( Float x )

Returns the base-e exponential function of x, which is the e number raised to the power x.

Example:

```
local.result = exp local.x
```

Result:

```
Exponential value of x.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - exp

### frexp

frexp( Float x )

Breaks the floating point number x into its binary significand (a floating point value between 0.5(included) and 1.0(excluded)) and an integral exponent for 2, such that:

x = significand * 2exponent
If x is zero, both parts (significand and exponent) are zero.

Example:

```
local.result = frexp local.x
```

Result:

```
local.result["significand"] - significand part
local.result["exponent"] - exponent part
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - frexp

### ldexp

ldexp( Float x, Integer exponent )

Returns the resulting floating point value from multiplying x (the significand) by 2 raised to the power of exp (the exponent).

Example:

```
local.result = ldexp local.x local.exponent
```

Result:

```
The function returns float number:

x * 2<sup>exp</sup>
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - ldexp

### log

log( Float x )

Returns the natural logarithm of x.

The natural logarithm is the base-e logarithm, the inverse of the natural exponential function (exp). For base-10 logarithms, a specific function log10 exists.

Example:

```
local.result = log local.x
```

Result:

```
Natural logarithm of x.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - log

### log10

log10( Float x )

Returns the common (base-10) logarithm of x.
Example:

```
local.result = log10 local.x
```

Result:

```
Common logarithm of x, for values of x greater than zero.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - log10

### modf

modf( Float x )

Breaks x into two parts: the integer part and the fractional part.
Example:

```
local.result = modf local.x
```

Result:

```
local.result["intpart"] - integer part
local.result["fractional"] - fractional part
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - modf

### pow

pow( Float x, Integer exponent )

Returns base raised to the power exponent:

baseexponent

Example:

```
local.result = pow local.x local.exponent
```

Result:

```
The result of raising base to the power exponent.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - pow

### sqrt

sqrt( Float x )

Returns the square root of x.
Example:

```
local.result = sqrt local.x
```

Result:

```
Square root of x.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - sqrt

### ceil

ceil( Float x )

Returns the smallest integral value that is not less than x.
Example:

```
local.result = ceil local.x
```

Result:

```
The smallest integral value not less than x.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - ceil

### floor

floor( Float x )

Returns the largest integral value that is not greater than x.
Example:

```
local.result = floor local.x
```

Result:

```
The largest integral value not greater than x.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - floor

### fmod

fmod( Float numerator, Float denominator )

Returns the floating-point remainder of numerator/denominator.

The remainder of a division operation is the result of subtracting the integral quotient multiplied by the denominator from the numerator:

```
remainder = numerator - quotient * denominator
```

Example:

```
local.result = fmod local.numerator local.denominator
```

Result:

```
The remainder of dividing the arguments.
```

!!! important
    This command works exactly like ANSI C function. For further documentation, please visit: ANSI C - fmod

## Events

ScriptThread -> Listener -> Class

### registerev

registerev( String eventname, String scriptname )

Registers script callback handler for given event type.
Example:

```
local.result = registerev "connected" global/eventhandlers.scr::connected
```

or

```
local.result = registerev("connected" global/eventhandlers.scr::connected)
```

Result:

```
When given even type will occur, EventSystem engine will execute given script.

local.result can have one of the following values:

0 = Registering event callback handler was successful
1 = Event callback handler is already registered for given event
2 = Memory allocation error
```

Please see Reborn Events System documentation for further information.

### unregisterev

unregisterev( String eventname )

Unregisters script callback handler for given event type.
Example:

```
local.result = unregisterev "connected"
```

or

```
local.result = unregisterev("connected")
```

Result:

```
EventSystem engine will unregister events of given type and won't execute their script callback handlers.

local.result can have one of the following values:

0 = Unregistering event callback handler was successful
1 = Event callback handler is already unregistered
```

Please see Reborn Events System documentation for further information.

## Date/Time

ScriptThread -> Listener -> Class

### gettime

gettime( Integer zero )

Gets current time in format: H:M:S
Example:

```
local.time = gettime 0
```

or

```
local.time = gettime(0)
```

Result:

```
String with current time.
```

### gettimezone

gettimezone( Integer zero )

Gets current time zone.
Example:

```
local.timezone = gettimezone 0
```

or

```
local.timezone = gettimezone(0)
```

Result:

```
Integer value that represents current time zone.
eg. 2 = GMT +2
```

### getdate

getdate( String format )

Gets current date in format given as parameter.
Example:

```
local.date = getdate "%D"
```

or

```
local.date = getdate("%D")
```

Result:

```
String with current date.

04/06/18
```


Formatting options:
http://www.cplusplus.com/reference/ctime/strftime/

Max format length is 512 characters.

## Miscellaneous

ScriptThread -> Listener -> Class

### getentity

getentity( Integer entnum)

Returns entity with given entity number
Example:

```
local.entity = getentity 0
```

or

```
local.entity = getentity( 0 )
```

Entities with entity number between 0 and sv_maxclient are reserved for players and thus getentity( 0 ) is equal to $player[0]

### stuffsrv

stuffsrv( String s )

Sends command to server console.
Example:

```
stuffsrv "restart"
stuffsrv( "restart" )
```

or

```
stuffsrv "map dm/mohdm1"
stuffsrv( "map dm/mohdm1" )
```

Result:

```
Server will restart
```

or

```
Server will change map to dm/mohdm1
```

### conprintf

conprintf( String text )

Prints text to a console.
Example:

```
conprintf "This can be a custom error message from the script"
```

or

```
conprintf( "This can be a custom error message from the script" )
```

Result:

```
Text will be printed to the console.
```

### md5string

md5string( String text )

Generates MD5 checksum of text
Example:

```
local.checksum = md5string local.text
```

Result:

```
MD5 checksum as string.
```

### md5file

md5file( String filename )

Generates MD5 checksum of file with given filename
Example:

```
local.checksum = md5file local.filename
```

Result:

```
MD5 checksum as string.
```

### typeof

typeof( Variable var )

Gets the type of variable.
Example:

```
local.type = typeof local.var
```

Result:

```
The type of variable returned as string (array, string, vector, listener, ...)
```

### traced

traced( Vector start, Vector end, [Integer pass_entities], [Vecotr mins], [Vector maxs], [Integer mask])

Performs a ray trace from start origin to end origin. It takes optional arguments such as entity number to be ignored/skipped by the trace, mins and maxs of trace box and trace mask.

Example:

```
local.trace = traced local.start local.end
```

or

```
local.trace = traced local.start local.end local.pass_entities local.mins
```

or

```
local.trace = traced local.start local.end local.pass_entities local.mins local.maxs local.mask
```

Result:

```
Array holding detailed information about trace:

local.trace["allSolid"] - <i>Integer</i> : it tells wheter trace was inside of a solid object
local.trace["startSolid"] - <i>Integer</i> : it tells wheter trace started in solid object
local.trace["fraction"] - <i>Float</i>
local.trace["endPos"] - <i>Vector</i> : position where trace finished because it may finish before it reaches end point specified by caller when it hits object with specified mask before it reaches end point
local.trace["surfaceFlags"] - <i>Integer</i>
local.trace["shaderNum"] - <i>Integer</i>
local.trace["contents"] - <i>Integer</i>
local.trace["entityNum"] - <i>Integer</i> : entity number that was hit
local.trace["location"] - <i>Integer</i>
local.trace["entity"] - <i>Entity</i> : entity that was hit by the trace
```

Surface Flags:

| Name                    | Value |
|-------------------------|-------|
| SURF_NODAMAGE           | 1
| SURF_SLICK              | 2
| SURF_SKY                | 4
| SURF_LADDER             | 8
| SURF_NOIMPACT           | 16
| SURF_NOMARKS            | 32
| SURF_CASTSHADOW         | 64
| SURF_PAPER              | 8192
| SURF_WOOD               | 16384
| SURF_METAL              | 32768
| SURF_STONE              | 65536
| SURF_DIRT               | 131072
| SURF_METALGRILL         | 262144
| SURF_GRASS              | 524288
| SURF_MUD                | 1048576
| SURF_PUDDLE             | 2097152
| SURF_GLASS              | 4194304
| SURF_GRAVEL             | 8388608
| SURF_SAND               | 16777216
| SURF_FOLIAGE            | 33554432
| SURF_SNOW               | 67108864
| SURF_CARPET             | 134217728
| SURF_BACKSIDE           | 268435456
| SURF_NODLIGHT           | 536870912
| SURF_HINT               | 1073741824

Masks:

| Name                    | Value |
|-------------------------|-------|
| MASK_SOLID              | 1
| MASK_COLLISION          | 637537057
| MASK_PERMANENTMARK      | 1073741825
| MASK_AUTOCALCLIFE       | 1073750049
| MASK_EXPLOSION          | 1074003969
| MASK_TREADMARK          | 1107372801
| MASK_THIRDPERSON        | 1107372857
| MASK_FOOTSTEP           | 1107437825
| MASK_BEAM               | 1107569409
| MASK_VISIBLE            | 1107569409
| MASK_VEHICLE            | 1107569409
| MASK_BULLET             | 1107569441
| MASK_SHOT               | 1107569569
| MASK_CROSSHAIRSHADER    | 1107897089
| MASK_TRACER             | 1108618017


Contents:

| Name                    | Value |
|-------------------------|-------|
| CONTENTS_SOLID		  | 1
| CONTENTS_LAVA			  | 8
| CONTENTS_SLIME		  | 16
| CONTENTS_WATER		  | 32
| CONTENTS_FOG			  | 64
| CONTENTS_AREAPORTAL	  | 32768
| CONTENTS_PLAYERCLIP	  | 65536
| CONTENTS_MONSTERCLIP	  | 131072
| CONTENTS_WEAPONCLIP	  | 262144
| CONTENTS_SHOOTABLEONLY  | 1048576
| CONTENTS_ORIGIN		  | 16777216
| CONTENTS_BODY			  | 33554432
| CONTENTS_CORPSE		  | 67108864
| CONTENTS_DETAIL		  | 134217728
| CONTENTS_STRUCTURAL	  | 268435456
| CONTENTS_TRANSLUCENT	  | 536870912
| CONTENTS_TRIGGER        | 1073741824
| CONTENTS_NODROP         | 2147483648