# Extensões Outlands (wiki.uooutlands.com/Razor_Scripting)

Fonte: [wiki.uooutlands.com/Razor_Scripting](https://wiki.uooutlands.com/Razor_Scripting). Tudo aqui é adição da Outlands sobre o Razor CE base (ver razor-base-reference.md).

The Razor assistant distributed with the Outlands client is a fork of Razor Community Edition. If you need help with the basics of scripting in Razor please follow the link to Quick's documentation here. http://www.razorce.com/guide/

Outlands has additionally extended that scripting engine with the following features.

## Contents

- 1 Modified Commands and Expressions

- 1.1 dclicktype

- 1.2 findtype

- 1.3 findtypelist

- 1.4 targettype

- 1.5 lifttype

- 1.6 overhead and sysmessage interpolation

- 1.7 Loops and index variable

- 2 New Aliases

- 2.1 ground

- 3 New Expressions

- 3.1 find

- 3.2 findlayer

- 3.3 targetexists

- 3.4 followers

- 3.5 hue

- 3.6 name

- 3.7 paralyzed

- 3.8 invul

- 3.9 warmode

- 3.10 noto

- 3.11 dead

- 3.12 maxweight

- 3.13 diffweight

- 3.14 diffhits

- 3.15 diffmana

- 3.16 diffstam

- 3.17 counttype

- 3.18 gumpexists

- 3.19 ingump

- 3.20 varexist

- 3.21 bandaging

- 3.22 cooldown

- 4 New Commands

- 4.1 setvar

- 4.2 unsetvar

- 4.3 ignore

- 4.4 unignore

- 4.5 clearignore

- 4.6 warmode

- 4.7 getlabel

- 4.8 rename

- 4.9 skill

- 4.10 setskill

- 4.11 waitforgump

- 4.12 gumpresponse

- 4.13 gumpclose

- 4.14 cooldown

- 5 New Operators

- 5.1 as

- 5.2 in

- 6 Lists

- 6.1 createlist

- 6.2 clearlist

- 6.3 removelist

- 6.4 pushlist

- 6.5 poplist

- 6.6 listexists

- 6.7 list

- 6.8 inlist

- 6.9 atlist

- 6.10 Iterating lists

- 7 Timers

- 7.1 createtimer

- 7.2 removetimer

- 7.3 settimer

- 7.4 timer

- 7.5 timerexists

- 8 Cooldowns

- 9 PvP Restrictions

## Modified Commands and Expressions

Several commands and expressions that search by type have been greatly expanded:

## dclicktype

 dclicktype ('name') OR ('graphic') [source] [hue] [quantity] [range]

## findtype

 findtype ('name') OR ('graphic') [source] [hue] [quantity] [range]

The hue allows limiting by hue. The source may be the serial of a specific container, 'self' for equipped items, or 'ground'. The quantity is the minimum quantity, and the range is the maximum range from the player.
The lifttype expression is further limited to only operate on 'backpack', 'self', or 'ground' sources.

## findtypelist

Works similar to findtype but the first argument is a list name. If the list exists, found serials are added to the list.

 findtypelist ('listname') ('name of item') OR ('graphic') [src] [hue] [qty] [range]

## targettype

 targettype ('name') OR ('graphic') [source] [hue] [quantity] [range]

## lifttype

 lifttype ('name') OR ('graphic') [amount] [src] [hue]

## overhead and sysmessage interpolation

Both overhead and sysmessage (and their aliases) now allow for string interpolation as follows:

setvar myvar 10
overhead "my var is: {{myvar}}"

## Loops and index variable

All loops now have a scoped running index variable called 'index' that starts at 0.

## New Aliases

## ground

The 'ground' alias is now available. This is useful in the expanded targeting commands as the "source" parameter.

## New Expressions

## find

Searching based on a serial number is now possible with the find expression:

 if find (serial) [src] [hue] [qty] [range]

The parameters work exactly like the findtype command.

## findlayer

Searching a character for equipped items is now possible:

 if findlayer self gloves as mygloves
   overhead 'Wearing gloves!'
 endif

The valid layers are:

 righthand
 lefthand
 shoes
 pants
 shirt
 head
 gloves
 ring
 talisman
 neck
 hair
 waist
 innertorso
 bracelet
 face
 facialhair
 middletorso
 earrings
 arms
 cloak
 backpack
 outertorso
 outerlegs
 innerlegs
 onehandedsecondary
 quiver
 outerbody

## targetexists

An expression to test whether the client currently has a target cursor up:

 if targetexists ['any'/'beneficial'/'harmful'/'neutral']

## followers

An expression to count your current followers:

 if followers < 5
   overhead "Can still tame stuff!"
 endif

## hue

An expression to get the hue of an item:

 if hue someObject = 0x1809
   overhead "Found hue of my item!"
 endif

## name

An expression to get your current character's name:

 if name = 'MyName'
   overhead "It's me!"
 endif

## paralyzed

An expression to test if your character is paralyzed:

 if paralyzed
   overhead "Can't move!"
 endif

## invul

An expression to test if your character is blessed/invulnerable (yellow health bar):

 if invul
   overhead "I'm gonna live forever!"
 endif

## warmode

An expression to test if your character is in warmode:

 if warmode
   overhead "Ready to attack!"
 endif

## noto

An expression to check any mobile's notoriety:

 if noto some_Mobile = hostile
   overhead "Safe to attack!"
 endif

The valid notorieties are

 innocent (blue)
 friend (green)
 hostile (gray)
 criminal (gray)
 enemy (orange)
 murderer (red)
 invulnerable (yellow)

## dead

An expression to check if a mobile is dead:

 if dead someMobile
   overhead "He's dead, Jim!"
 endif

## maxweight

  if maxweight > 400
     overhead "I have a lot of strength"
  endif

## diffweight

 if diffweight > 20
   overhead "I can lift 20 more stone"
 endif

## diffhits

 if diffhits > 40
   overhead "I need a heal!"
 endif

## diffmana

 if diffmana > 40
   useskill Meditation
 endif

## diffstam

 if diffstam > 30
   overhead "Need stamina"
 endif

## counttype

Returns the number of items of the same type in a container. If items are stackable, they will refund the number of items in the stack.

 if counttype (name or graphic) [src] [hue] [range]

## gumpexists

 if gumpexists (gumpId/'any')

Returns true if the gump exists.

## ingump

 if ingump (text) [gumpId/'any']

Look for text in the given gump.

## varexist

Checks if a given variable (or alias if ! is passed) is declared

 if varexist someVar
   overhead "Select shelf"
   setvar someVar
 endif

## bandaging

Checks if a bandage is currently being applied and will return the time left in seconds (works with healing and veterinary).

 if bandaging > 5
   overhead "More than 5 seconds till next bandage"
 endif

Simpler version

 if not bandaging
   hotkey "Bandage Self"
 endif

## cooldown

Checks if the cooldown is active, can be compared against a duration. 

 if cooldown "mycooldown" 
   overhead "cooldown is active"
 endif

 if cooldown "mycooldown" > 2000
   overhead "more than 2 seconds remaining on cooldown"
 endif

## New Commands

## setvar

The setvar command has been modified on Outlands to support a wider set of use cases. The optional second parameter is now the serial of the variable. If provided, you won't be prompted with a target cursor.

 setvar my_name 0x123

This can be used for graphic IDs, hues, serials, names, and more. By default, this creates a persistent variable that will remain even across restarts of the application. To make the variable only live for as long as the current program run, append the '!' operator. The variable will not appear in the Razor variables list, but will still be global and usable from any script while Razor is running.

 setvar! my_name 0x123

## unsetvar

Additionally, a command to unset variables has been added. It supports the same modifiers as setvar:

 unsetvar my_name

## ignore

An ignore list has been added to avoid finding objects when using the various search commands:

 ignore (serial or list)

This also supports the same operators as setvar for controlling the scope of the ignore list.

## unignore

Similar to ignore, the unignore command removes a serial (or list of serials) from the ignore list:

 unignore (serial or list)

This also supports the same operators as setvar for controlling the scope of the ignore list.

## clearignore

Clears the ignore list:

 clearignore

This also supports the same operators as setvar for controlling the scope of the ignore list.

## warmode

A command to explicitly set warmode state has been added:

 warmode ('on' / 'off')

## getlabel

A command to get an item's label - the text you see when single clicking it - has been added.

 getlabel (serial) (name)

This will fetch the label for the item identified by the serial and create a new variable with your choice of name that holds the text.

 getlabel backpack my_label
 overhead my_label

## rename

A command to rename followers has been added:

 rename myFollower Bob

## skill

A command to use skill

 skill discord

A method to check skill levels

 if skill anatomy >= 80

A valid active skill list:

 anatomy
 animallore // "animal lore"
 itemidentification // "item identification" // itemid
 armslore // "arms lore"
 begging
 peacemaking // peacemaking // peace
 cartography // cartography
 detectinghidden // detect hidden
 discord // Discordance
 evaluatingintelligence // "evaluate intelligence" // evalint
 forensicevaluation // "forensic evaluation" // forensiceval 
 hiding
 provocation // provocation // provo
 inscription
 poisoning 
 spiritspeak // "spirit speak" // spirit
 stealing
 taming // "animal taming"
 tasteidentification // "taste id" // tasteid // taste
 tracking 
 meditation 
 stealth 
 removetrap
 resisting spells

## setskill

A command to set skill gain locks has been added:

 setskill Blacksmithing up

The valid choices are up, down, or lock.

## waitforgump

 waitforgump [gumpId]

Wait for a gump to appear. If a gump ID is provided, wait for that particular gump. Otherwise, wait for the next gump.

## gumpresponse

 gumpresponse (buttonId) [gumpId]

Press the given button on the give gump (or the last gump that opened)

## gumpclose

 gumpclose [gumpId]

Close the given gump or the last gump that opened if no gumpId is specified.

## cooldown

 cooldown <'cooldown name'> [milliseconds]

Triggers the cooldown with the chosen name. If no milliseconds are passed in, it uses the cooldown's default value.

## New Operators

## as

There is now an 'as' operator to capture the result of expressions as an alias. This is particularly useful for the `findtype` expression as follows

 if findtype dagger as mydagger
   dclick mydagger
 endif

## in

There is additionally an 'in' operator that can be used to check whether one string is a substring of another:

 if this in thisthatandtheother
   overhead yes
 endif

These are particularly powerful when combined to sort through items:

 if findtype dagger as mydagger
   getlabel mydagger daggerlabel
   if blessed in daggerlabel
     overhead "Found newbie dagger"
   endif
 endif

## Lists

List support includes the following commands:

## createlist

createlist ('list name')

Create a new list

## clearlist

clearlist ('list name')

Clear an existing list

## removelist

removelist ('list name')

Delete a list

## pushlist

pushlist ('list name') ('element value') ['front'/'back'] //comment

Add an item to the front or back of the list

## poplist

poplist ('list name') ('element value'/'front'/'back') //comment

Remove an item from the front of back of the list. 

If used in an expression, the popped value can be saved with 'as' as follows:

if poplist testlist back as popped
    overhead popped
endif

## listexists

Additionally, the following list-related expressions have been added. These may be used within `if` and `while` statements.

listexists ('list name')

True if the list exists

## list

list (list name) (operator) (value)

Compare the length of the list to an integer

## inlist

inlist (list name) (element)

Test if an element is in a list.

## atlist

atlist ('list name') (index)

Return an item in the list at the given index. Index starts at 0.

Example:

if atlist mylist 2 as thirdentry
    overhead thirdentry
else
    overhead "index out of bounds or list item retrievend was no serial"
endif

## Iterating lists

Finally, `for` and `foreach` loops can be used for iteration as follows:

for 10
  say 'hello'
endfor

This will iterate exactly 10 times.

foreach x in my_list
  say x
endfor

This will iterate the elements in my_list, assigning the variable 'x' to the next element on each iteration.

## Timers

Timers represent background timers that run while the rest of your script executes. All units are in milliseconds. They can be queried to check how much time has elapsed since they were started, or reset back to an earlier count.

The following commands for working with timers have been added:

## createtimer

createtimer (timer name)

Create a new timer, starting at 0.

## removetimer

removetimer (timer name)

Destroy an existing timer.

## settimer

settimer (timer name) (value)

Set a timer to the given value. It will begin counting up from the given value immediately.

Additionally, two expressions have been added for timers:

## timer

timer ('timer name') (operator) (value)

Compare the current value of the timer (the time elapsed since it was started in milliseconds) to a given value

## timerexists

timerexists ('timer name')

Check if a timer exists

Example:

// Create a new timer
if not timerexists 'sample'
 createtimer 'sample'
endif
// Reset every 10 seconds
if timer 'sample' > 10000
 settimer 'sample' 0
endif

## Cooldowns

Cooldowns are introduced in Client patch 1.0.0.14

Cooldowns can be triggered using Razor script commands

// starts the cooldown named "mycooldown" with its default cooldown time
cooldown "mycooldown"

// starts the cooldown named "mycooldown" with a 30 second timer (note that milliseconds are used in Razor)
cooldown "mycooldown" 30000

In an expression the cooldown command can be used to check the time left on a cooldown

// checks if the cooldown is running
if cooldown "mycooldown"
   // do something
endif

// checks if the cooldown has more than 5 seconds left
if cooldown "mycooldown" > 5000
   // do something
endif

## PvP Restrictions

When a player is actively engaged in structured PvP—either as part of a PvP event or PvPing while Faction Flagged-a PvP Debuff will be applied. Non-consensual pvp (example PKing) is not affected.

While active, the following automation functions will be disabled in Razor scripting, macros, and the client:

setvar on players
droprelloc
waitforsysmsg
settimer
removetimer
getlabel
rename
cooldown
wait/pause

Expressions:

bandaging
findbuff/finddebuff
mana
maxmana
diffmana
hits
maxhits
diffhits
stam
maxstam
diffstam
poisoned
paralyzed
hidden
str
dex
int
position
timer
followers
hue
blessed
notoriety
dead (on mobs other than the player)
maxweight
diffweight
gumpexists
ingump
cooldown
casting

'pvp' expression:

Added a new pvp expression that lets you check whether the pvp script restrictions above are currently active.

if pvp
 //those commands are disabled
endif

Serial handling:

While affected by pvp script restrictions, any serials that belong to players will resolve as 0x0 in scripts and macros, i.e. be disabled
Example: A player stores the serial of a player in variable player. While flagged for pvp, if they resolve this variable for any command (for example attack player or setlasttarget player, the variable will produce 0x0 instead.

Item handling:

While affected by pvp script restrictions, all commands and expressions that use the find handling (find, findtype, findtypelist, dclicktype, lifttype, counttype) will only find items that are worn by or in the inventory of the player.

Party and guild messages:
These messages will now never be picked up by Razor or the client.
