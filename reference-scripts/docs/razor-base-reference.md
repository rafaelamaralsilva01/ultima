# Base Reference — Razor Community Edition (razorce.com/guide)

Fonte: [razorce.com/guide](https://www.razorce.com/guide/). Engine base que o Razor Outlands (fork) estende — ver `outlands-extensions.md` pras adições específicas. Blocos de exemplo usam aspas simples (`) no lugar de fenced code block — conteúdo é fiel à fonte, só a formatação visual não é perfeita.

## Commands

## Command Overview

The commands issued in the scripting engine are similar to commands you might enter into a command prompt or shell.  Each line has a starting command and a set of parameters.  Some of those parameters are required, some are optional.

`command (required) [optional]`

All parameters are shown inside of parenthesis or brackets.  Parameters within parenthesis are required while those in brackets are optional and will default to specific value if not provided.

If you want to pass several words as a single parameter you must wrap them using `'` or `"`. For example `'hello goodbye'` is one parameter, while `hello` `goodbye` is two.

For example, if your script is something like:

`# Say 'Hello'
say Hello friends!
`

You will end up just saying `Hello`.  Instead, you if you wrap the words in single (') or double quotes (") the engine will see it as a single parameter.

`# Say 'Hello friends!'
say 'Hello friends!'
`

If you prefix a command with the `@` this will silence any warning/output from the command.  For example:

Example

`// Generate warning if robe is out of reach
lifttype 'robe'

// Silence warning if robe is out of reach
@lifttype 'robe'
`

Without the `@` symbol, if a robe isn't available, you would get an warning message telling you that it couldn't find a robe. But since the `@` symbol was provided, no warning is displayed.

## Action Commands

## attack

Syntax: `attack (serial)` or `attack ('variablename')`

Description: Attack a specific serial or variable tied to a serial.

Example

Attack TargetAttack Variable

`attack '0x21B4'
`

`attack 'attackdummy'
`

## cast

Syntax: `cast ('name of spell')`

Description: Cast a spell by name

Example

Cast specific spell

`cast 'greater heal'
wft
target 'self'
`

## classicuo

Syntax: `classicuo ('setting') ('value')` or `cuo ('setting') ('value')`

Description: This command will change specific settings/properties in your current ClassicUO profile.

Tip

Type `>cuo list` to get a list of profile settings/properties to change

Example

Turn off CUO musicAdjust music volume to 50%

`overhead 'Turn off the music!'
classicuo 'enablemusic' false
`

`overhead 'Turning music to 50%'
classicuo 'musicvolume' 50
`

## cleardragdrop

Syntax: `cleardragdrop`

Description: Clears Razor's the drag/drop queue

Example

Clear on sysmsg message

`if insysmsg 'cannot reach'
    cleardragdrop
endif
`

## clearhands

Syntax: `clearhands ('left'/'right'/'both')`

Description: Undress your hands based on the param.

Example

Undress both handsUndress left hand

`clearhands 'both'
`

`clearhands 'left'
`

## cooldown

Syntax: `cooldown ('name') ('seconds') ['hue'] ['icon name'] ['sound'] ['stay visible'] ['foreground color'] ['background color']`

Description: This command will add a custom cooldown that will display as a gump in-game.

Supported Foreground & Background Colors

You can set the foreground and background color of the specific cooldown down by using one of the colors below:

AliceBlue, AntiqueWhite, Aqua, Aquamarine, Azure, Beige, Bisque, Black, BlanchedAlmond, Blue, BlueViolet, Brown, BurlyWood, CadetBlue, Chartreuse, Chocolate, Coral, CornflowerBlue, Cornsilk, Crimson, Cyan, DarkBlue, DarkCyan, DarkGoldenrod, DarkGray, DarkGreen, DarkKhaki, DarkMagenta, DarkOliveGreen, DarkOrange, DarkOrchid, DarkRed, DarkSalmon, DarkSeaGreen, DarkSlateBlue, DarkSlateGray, DarkTurquoise, DarkViolet, DeepPink, DeepSkyBlue, DimGray, DodgerBlue, Firebrick, FloralWhite, ForestGreen, Fuchsia, Gainsboro, GhostWhite, Gold, Goldenrod, Gray, Green, GreenYellow, Honeydew, HotPink, IndianRed, Indigo, Ivory, Khaki, Lavender, LavenderBlush, LawnGreen, LemonChiffon, LightBlue, LightCoral, LightCyan, LightGoldenrodYellow, LightGray, LightGreen, LightPink, LightSalmon, LightSeaGreen, LightSkyBlue, LightSlateGray, LightSteelBlue, LightYellow, Lime, LimeGreen, Linen, Magenta, Maroon, MediumAquamarine, MediumBlue, MediumOrchid, MediumPurple, MediumSeaGreen, MediumSlateBlue, MediumSpringGreen, MediumTurquoise, MediumVioletRed, MidnightBlue, MintCream, MistyRose, Moccasin, NavajoWhite, Navy, OldLace, Olive, OliveDrab, Orange, OrangeRed, Orchid, PaleGoldenrod, PaleGreen, PaleTurquoise, PaleVioletRed, PapayaWhip, PeachPuff, Peru, Pink, Plum, PowderBlue, Purple, RebeccaPurple, Red, RosyBrown, RoyalBlue, SaddleBrown, Salmon, SandyBrown, SeaGreen, SeaShell, Sienna, Silver, SkyBlue, SlateBlue, SlateGray, Snow, SpringGreen, SteelBlue, Tan, Teal, Thistle, Tomato, Transparent, Turquoise, Violet, Wheat, White, WhiteSmoke, Yellow, YellowGreen

Supported Icon Names

You can use any of the following icons.

NOTE: Icon availability is based on the version of the client you have. If the icon doesn't display, it must be an icon that doesn't exist your data files.

AchievePerfection, ActiveMeditation, Agility, AnimalForm, AnticipateHit, ArcaneEmpowerment, ArchProtection, ArmorPierce, AttuneWeapon, AuraOfNausea, BarakoDraftOfMight, BarrabHemolymphConcentrate, Berserk, Bleed, Bless, Block, BloodOathCaster, BloodOathCurse, BloodwormAnemia, Boarding, Bodyguard, BoneBreaker, BoneBreakerImmune, CaddelliteInfused, CalledShot, CityTradeDeal, Clumsy, CombatTraining, Conduit, Confidence, ConsecrateWeapon, CorpseSkin, CounterAttack, CriminalStatus, Cunning, Curse, CurseWeapon, DeathRay, DeathRayDebuff, DeathStrike, DefenseMastery, DespairCaster, DespairTarget, Disarm, Disguised, DivineFury, DragonTurtleDebuff, DualWield, ElementalFury, ElementalFuryDebuff, Enchant, EnchantedSummoning, EnemyOfOne, EnemyOfOneDebuff, EssenceOfWind, EtherealBurst, EtherealVoyage, Evasion, EvilOmen, FactionStatLoss, FanDancerFanFire, FeebleMind, Feint, FeintDebuff, FishPie, FistsOfFury, Fly, FocusedEye, ForceArrow, GazeDespair, GiftOfLife, GiftOfRenewal, GrapesOfWrath, Healing, HeatOfBattleStatus, HeightenedSenses, HidingAndOrStealth, HiryuPhysicalResistance, HitLowerAttack, HitLowerDefense, HonorableExecution, Honored, HonoredDebuff, HorrificBeast, HowlOfCacophony, Humility, HumilityDebuff, ImmolatingWeapon, Incognito, InjectedStrike, InjectedStrikeDebuff, Inspire, Intuition, Invigorate, Invisibility, JukariBurnPoiltice, Knockout, KurakAmbushersEssence, LichForm, LightningStrike, MagicReflection, ManaPhase, ManaShield, MassCurse, MassSleep, MedusaStone, Mindrot, MomentumStrike, MortalStrike, MysticalPolymorphTotem, MysticWeapon, NightSight, Onslaught, OrangePetals, PainSpike, Paralyze, Perfection, Perseverance, Pierce, PlayingTheOdds, PlayingTheOddsDebuff, Poison, PoisonImmunity, Polymorph, Potency, PotionGloriousFortune, Protection, PsychicAttack, Rage, RageFocusingBuff, RageFocusingDebuff, Rampage, ReactiveArmor, ReaperForm, Resilience, RoseOfTrinsic, RotwormBloodDisease, RuneBeetleCorruption, SakkhraProphylaxis, SavingThrow, Shadow, ShieldBash, SkillUseDelay, Sleep, Sparks, SpellFocusingBuff, SpellFocusingDebuff, SpellPlague, Spirituality, SplinteringEffect, Stagger, StoneForm, Strangle, Strength, Surge, Swarm, SwarmImmune, SwingSpeedDebuff, TalonStrike, Thrust, ThrustDebuff, Thunderstorm, Tolerance, Toughness, TribulationCaster, TribulationTarget, TrueFear, UnknownGoblin, UnknownRedDrop, UnknownStar, UnknownTomato, UraliTranceTonic, VampiricEmbrace, Veterinary, Warcry, Warding, Weaken, Webbing, Whispering, WhiteTigerForm, WraithForm    

Example

Simple cooldownCooldown with custom hued textCooldown with iconCooldown a custom sound (flute)Cooldown remains when expiredCooldown with custom colorsReset existing cooldown

`cooldown 'Refresh' 20
`

`cooldown 'Refresh' 20 234
`

`cooldown 'Refresh' 15 0 'Agility'
`

`cooldown 'Health Check' 20 0 0 61
`

`# default cooldown, 20 seconds, remains after it expires
cooldown 'Health Check' 20 0 0 0 true

# default cooldown, 25 seconds, 235 hue, icon 30012, no sound, remains after it expires
cooldown 'Health Check' 20 235 30012 0 true
`

`cooldown 'Stay 1' 20 0 0 0 false 'Firebrick' 'Peru'
`

`cooldown 'Refresh' 20

wait 10 seconds

cooldown 'Refresh' 20
`

## dclick

Syntax: `dclick (serial)` or `dclick ('left'/'right'/'hands')`

Description: This command will use (double-click) a specific item or mobile or use the item in one of your hands using `left`, `right` or `hands` to use an item in either hand.

Example

Double-click a specific item idDouble-click a variableDouble-click any item in your handsDouble-click item in right hand

`dclick '0x34AB'
`

`dclick 'myvariable'
`

`dclick 'hands'
`

`dclick 'right'
`

## dclicktype

Syntax: `dclicktype ('name of item'/'graphicId') [inrange (true/false)/backpack] [hue]`

Description: This command will use (double-click) an item type either provided by the name or the graphic ID.

Range Check

If you include the optional `true` parameter, items within range (2 tiles) will only be considered. If you include the optional `backpack` parameter, items in your backpack only be considered.

Getting the graphic name or ID

To get the name or the ID of item, use the `>info` command in Razor and click on the item. You can use either the `Item Name` or `Id`.

Example

Use any item..with range check..with backpack only..with backpack and hue only

`dclicktype 'dagger'
waitfortarget
targettype 'robe'
`

`dclicktype 'dagger' true
waitfortarget
targettype 'robe' true
`

`dclicktype 'dagger' backpack
waitfortarget
targettype 'robe' backpack
`

`dclicktype 'dagger' backpack 45
waitfortarget
targettype 'robe' backpack
`

## dress

Syntax: `dress ('name of dress list')` or `dress (serial)`

Description: This command will execute a spec dress list you have defined in Razor or dress (left and drop) a specific serial

Example

Use existing dress listUsing a serialUsing a variable

`dress 'My Sunday Best'
`

`dress '0x345234'
`

`setvar 'hat'
dress 'hat'
`

## drop

Syntax: `drop (serial) (x) (y) [z]` or `drop (serial) (layer)` or `drop 'ground' (x) (y) [z]`

Description: This command will drop the item you are holding either at your feet, on a specific layer , at a specific X/Y/Z location on the ground or within the defined serial.

Tip

The functionality of `drop 'ground' (x) (y) [z]` is also available in with droprelloc.

Tip

A list of available layers for reference that can be used with this command.

Example

Lift item, drop on your chest/torsoLift item, drop on ground at location

`lift '0x400D54A7'
drop 'self' InnerTorso
`

`lift '0x400D54A7'
drop 'ground' 5926 1148 0
`

## droprelloc

Syntax: `droprelloc (x) (y)`

Description: This command will drop the item you're holding to a location relative to your position.

Example:

Example

Drop Relative Location

`lift '0x400EED2A'
wait 1000
droprelloc 1 1
`

## getlabel

Syntax: `getlabel ('serial') ('variable name')`

Description: This command will get the label (text obtained by single-clicking an item) and save it to a variable.

Example

Find a dogFind a silver kryss

`if findtype '217' as 'a_dog'
    getlabel 'a_dog' 'dog_label'

    if 'Fido' in 'dog_label'
        overhead 'found mydog!' 5
        overhead 'dog_label' 67
    endif    
endif
`

`setvar 'silver_bag'

if findtype '0x140' as 'kryss'
    getlabel 'kryss' 'kryss_label'

    if 'silver' in 'kryss_label'
        overhead 'found silver kryss!' 5

        lift 'kryss' 1
        drop 'silver_bag' -1 -1 0
    endif    
endif
`

## hotkey

Syntax: `hotkey ('name of hotkey')`

Description: This command will execute any Razor hotkey by name.

Example

Hotkey

`skill 'detect hidden'
waitfortarget
hotkey 'target self'
`

## interrupt

Syntax: `interrupt ['layer']`

Description: This command will interrupt a casting action. You can pass an optional layer if you want interrupt to only attempt an interrupt using a specific layer.

Tip

If you don't provide a specific layer to use for interrupt, Razor will search in the following order:

`shirt, shoes, pants, head, gloves, ring, neck, waist, innertorse, bracelet, middletorso, earrings, arms, cloak, outertorso, outerlegs, innerlegs, righthand, lefthand`

Example

ExampleSpecific layer

`cast 'energy bolt'
if hp < 10
    interrupt
    cast 'greater healing'
    wft
    target 'self'
else
    wft
    target 'last'    
endif        
`

`cast 'energy bolt'
if hp < 10
    interrupt 'pants'
    cast 'greater healing'
    wft
    target 'self'
else
    wft
    target 'last'    
endif 
`

## lift

Syntax: `lift ('serial') ['amount'] ['timeout']`

Description: This command will lift a specific item and amount. If no amount is provided, `1` is set as default. If no timeout is provided, `30000` (30 seconds) is set as default

dress command

If you're looking to lift an item to wear, consider using the `dress` command instead.

Example

Lift item and drop to the groundLift item, timeout in 5 seconds if unable

`lift '0x400EED2A'
wait 1000
droprelloc 1 1 0
`

`lift '0x400EED2A' 1 5000
droprelloc 1 1 0
`

## lifttype

Syntax: `lifttype ('gfx') ['amount'] ['hue']` or `lifttype ('name of item') ['amount'] ['hue']`

Description: This command will lift a specific item by type either by the graphic id or by the name from your backpack. If no amount is provided, `1` is defaulted.

Example

Lift by nameLift by item idLift by name, max 5Lift by name, max 5, specific hue

`lifttype 'robe'
wait 1000
droprelloc 1 1
`

`lifttype '0x1FCD'
wait 1000
droprelloc 1 1
`

`lifttype 'fish steak%s%' 5
wait 1000
droprelloc 1 1
`

`lifttype 'fish steak%s%' 5 45
wait 1000
droprelloc 1 1
`

## music

Syntax: `music ('index')`

Description: This command will play music based on the ID.

Tip

The music ID can often be found in `Music\Digital\Config.txt` in the main client files.

Example

Description

`overhead 'playings bucsden'
wait 500
music 11
`

## potion

Syntax: `potion ('potion type')`

Types: `heal, cure, refresh, nightsight, ns, explosion, strength, str, agility`

Description: This command will use a specific potion based on the type.

Example

Use agility potionUse heal potion

`potion 'agility'
`

`potion 'heal'
`

## rename

Syntax: `rename (serial) ('name')`

Description: This command will attempt to rename the mobile to a new name.

Example

Rename using serialRename using variablesRename using last target

`rename '0x453' 'Fluffy'
`

`setvar 'mypet'

rename 'mypet' 'Fluffy'
`

`rename 'lasttarget' 'Fluffy'
`

## random

Syntax: `random ('max number')`

Description: This command will generate a random number between 1 and the max number.

Example

Random Message Check

`clearsysmsg

random 10

if insysmsg 'Random: 5'
    say 'Hello!'
else
    say 'Hail!'
endif
`

## script

Syntax: `script ('name')` or `script ('category\name')`

Description: This command will call another script.

Tip

You can call scripts in categories using a `category1\category2\scriptname` format.

Example

Execute scriptExecute script in category

`if hp = 40
    script 'healcure'
endif
`

`if mana = 40
    script 'magery\meditation'
endif
`

## setability

Syntax: `setability ('primary'/'secondary'/'stun'/'disarm') ['on'/'off']`

Description: This will set a specific ability on or off. If `on` or `off` is missing, `on` is defaulted.

Example

Set stunTurn off stun

`setability 'stun'
`

`setability 'stun' off
`

## setvar

Syntax: `setvar ('variable') ['serial'] ['timeout']` or `setvariable ('variable') ['serial'] ['timeout']`

Description: This command will pause the script until you select a target to be assigned a variable. You can also provide a serial directly, which will bypass the target selection. Default timeout is 30 seconds that can be changed by passing in a new timeout value in milliseconds.

Temp variables

If you use `setvar!` (note the `!`) the variable will not be available in Razor's variable list to be used by other scripts and will go away at the end of the script's execution. You can remove it with the `unsetvar!` command.

Example

Set variable and use itSet variable with serialSet temp variable with serial

`setvar 'dummy'

cast 'magic arrow'
waitfortarget
target 'dummy'
`

`setvar 'spellbook' '0x40000D'

dress 'spellbook'        
`

`setvar! 'tempvar' '0x40000D'

dclick 'tempvar'       
`

## skill

Syntax: `skill ('name of skill')` or `skill last`

Description: This command will use a specific skill (assuming it's a usable skill).

Supported skill names

`anatomy, animallore, itemidentification, itemid, armslore, begging, peacemaking, peace, cartography, detectinghidden, discord, discordance, evaluatingintelligence, evalint, forensicevaluation, forensiceval, hiding, provocation, provo, inscription, poisoning, spiritspeak, stealing, taming, tasteidentification, tasteid, tracking, meditation, stealth, removetrap, imbuing`

Example

Use meditation

`while mana < maxmana
    say 'mediation!'
    skill 'meditation'
    wait 11000
endwhile
`

## sound

Syntax: `sound ('serial')`

Description: This command will play a specific sound based on serial id.

Example

Description

`overhead 'daemon sound'
wait 500
sound '0x166'
`

## unsetvar

Syntax: `unsetvar ('variable')`

Description: This command will remove the variable from the variable list.

Temp variables

If you use `unsetvar!` (note the `!`) with `setvar!` the variable will be removed from the list of variables just available for the script's execution.

Example

Set variable, use it, unsetSet temp variable with serial, unset

`setvar 'dummy'

cast 'magic arrow'
waitfortarget
target 'dummy'

unsetvar 'dummy'
`

`setvar! 'tempvar' '0x40000D'

dclick 'tempvar'       

unsetvar! 'tempvar'
`

## virtue

Syntax: `virtue ('honor'/'sacrifice'/'valor')`

Description: This command will invoke Honor, Sacrifice or Valor.

Example

Invoke HonorInvoke SacrificeInvoke Valor

`virtue 'honor'
`

`virtue 'sacrifice'
`

`virtue 'valor'
`

## walk

Syntax: `walk ('direction')`

Description: This command will turn and/or walk your player in a certain direction.

Example

Walk around

`walk 'North'
walk 'Up'
walk 'West'
walk 'Left'
walk 'South'
walk 'Down'
walk 'East'
walk 'Right'
`

## wait & pause

Syntax: `wait (time in milliseconds)` or `pause (time in milliseconds)` or `wait (duration) (shorthand)`

Description: This command will pause the execution of a script for a given time.

Tips

`1000` milliseconds is equal to `1` second. `1000 x number of seconds = total milliseconds`

To make your script easier to read, you can shorthand instead of defining the full time in milliseconds.

Accepted Shorthand

`seconds`, `second`, `sec`, `s`

`minutes`, `minute`, `min`, `m`

Example

Wait 5 secondsWait 2 seconds (with shorthand)Wait 3 minutes (with shorthand)

`while stam < 100    
    wait 5000
endwhile
`

`while stam < 100    
    wait 2 sec
endwhile

while stam < 100    
    wait 2 seconds
endwhile
`

`say 'AFK for 3 minutes'
wait 3 minutes
say 'Back!'
`

## undress

Syntax: `undress ('name of dress list')'` or `undress 'LayerName'` or `undress (serial)`

Description: This command will either undress you completely if no dress list is provided. If you provide a dress list, only those specific items will be undressed. Lastly, you can define a layer name to undress.

Tip

Available layers for reference

Example

Full nakedSpecfic items in dress listRemove your shirt and pantsUsing a serialUsing a variable

`undress
`

`undress 'My Sunday Best'
`

`undress 'Shirt'
undress 'Pants'
`

`undress '0x345234'
`

`setvar 'hat'
undress 'hat'
`

## Agent Commands

## organizer

Syntax: `organizer ('number') ['set']`

Description: This command will execute a specific organizer agent. If the `set` parameter is included, you will instead be prompted to set the organizer agent's hotbag.

Example

Execute organizer agent 1Set a hotbag on organizer agent 4

`organizer 1
`

`organizer 4 'set'
`

## restock

Syntax: `restock ('number') ['set']`

Description: This command will execute a specific restock agent. If the `set` parameter is included, you will instead be prompted to set the restock agent's hotbag.

Example

Use Restock Agent 1Set a hotbag on Restock Agent 4

`if count garlic < 4
    restock 1
endif
`

`restock 4 'set'
`

## scavenger

Syntax: `scavenger ('clear'/'add'/'on'/'off'/'set')`

Description: This command will control the scavenger agent.

- `clear`: Clear scavenger agent cache

- `add`: Select an item to add to the list

- `on`: Turn on the scavenger agent

- `off`: Turn off the scavenger agent

- `set`: Set the scavenger agent's hotbag

Example

Turn off scavenger

`scavenger 'off'
`

## sell

Syntax: `sell`

Description: This command will set the Sell agent's hotbag.

Example

Set Agent Hotbag

`sell
`

## useonce

Syntax: `useonce ('add'/'addcontainer')`

Description: This command will execute the UseOnce agent. If the `add` parameter is included, you can add items to your UseOnce list. If the `addcontainer` parameter is included, you can add all items in a container to your UseOnce list.

Example

Use top itemAdd to listAdd to container

`useonce
`

`useonce 'add'
`

`useonce 'addcontainer'
`

## Gumps, Menus, & Prompt Commands

## gumpresponse

Syntax: `gumpresponse ('buttonID')`

Description: Responds to a specific gump button

Example

Gump Response

`gumpresponse 4
`

## gumpclose

Syntax: `gumpclose ['gumpID']`

Description: This command will close the last gump that opened. You may pass an optional gump ID.

Example

Close last gumpClose gump with id

`gumpclose
`

`dclick '0x4000174B'
waitforgump 2341449854        
gumpclose 2341449854
`

## menu

Syntax: `menu ('serial') ('index') ['false']`

Description: Selects a specific index within a context menu. Razor will block the menu from appearing by default. If you include the optional `false` parameter, the context menu won't be blocked by Razor.

Context Menu

This command applies to the context menu accessed on some servers via a single-click (such as on yourself, to open your paperdoll or backpack).

Example

Open PaperdollOpen Backpack

`menu 0 0
`

`menu 0 1
`

## menuresponse

Syntax: `menuresponse ('index') ('menuId') ['hue']`

Description: Responds to a specific menu and menu ID

Warning

This command does not work on context menus, they are for a less used menu type.  See the `menu` command to use context/popup menus.

Example

Description

`menuresponse 3 4
`

## promptresponse

Syntax: `promptresponse ('prompt response')`

Description: This command will respond to a prompt triggered from actions such as renaming runes or giving a guild title.

Example

Rename a recall rune

`dclicktype 'rune'
waitforprompt
promptresponse 'to home'
`

## waitforgump

Syntax: `waitforgump (gump id/'any') [timeout]`

Description: This command will wait for a gump. If no `gump id` is provided, it will wait for any gump. Default timeout is 30 seconds that can be changed by passing in a new timeout value in milliseconds.

Timeout parameter

To modify the default 30 second timeout for any gump, you must include include the `any` keyword before the timeout.

`waitforgump 'any' 5000` will wait for 5 seconds

`waitforgump 5000` will wait 30 seconds for a gump with the id of 5000

Example

Wait for any gumpWait for any gump for 10 secondsWait for specific gumpWait for specific gump for 5 seconds

`waitforgump 'any' 
`

`waitforgump 'any' 10000
`

`waitforgump 4
`

`waitforgump 34252 5000
`

## waitformenu

Syntax: `waitformenu (menu id/'any') [timeout]`

Description: This command will wait for a context menu. If no `menu id` is provided, it will wait for any menu. Default timeout is 30 seconds that can be changed by passing in a new timeout value in milliseconds.

Timeout parameter

To modify the default 30 second timeout for any menu, you must include include the `any` keyword before the timeout.

`waitformenu 'any' 5000` will wait for 5 seconds

`waitformenu 5000` will wait 30 seconds for a menu with the id of 5000

Warning

This command does not work on context menus, they are for an less used menu type.  See the `menu` command to use context/popup menus.

Example

Wait for any menuWait for any menu for 5 secondsWait for specific menu

`waitformenu
`

`waitformenu 'any' 5000
`

`waitformenu 4
`

## waitforprompt

Syntax: `waitforprompt (promptid/'any') [timeout]`

Description: This command will wait for a prompt before continuing. If no `prompt id` is provided, it will wait for any prompt. Default timeout is 30 seconds that can be changed by passing in a new timeout value in milliseconds.

Timeout parameter

To modify the default 30 second timeout for any gump, you must include include the `any` keyword before the timeout.

`waitforprompt 'any' 5000` will wait for 5 seconds

`waitforprompt 5000` will wait 30 seconds for a prompt with the id of 5000

Example

Renaming recalling runeRename recalling rune with wait

`dclicktype 'rune'
waitforprompt
promptresponse 'to home'
`

`dclicktype 'rune'
waitforprompt 'any' 5000
promptresponse 'to home'
`

## Ignore Commands

## clearignore

Syntax: `clearignore`

Description: Clears your scripting ignore list

Tip

Works in conjunction with `ignore` and `unignore`

Example

General

`clearignore

if findtype 3572 backpack as 'wand' or findtype 3570 backpack as 'wand'
    overhead 'found' 44
    overhead 'wand' 44

    ignore 'wand'
else
    overhead 'not found' 33
endif
`

## ignore

Syntax: `ignore ('serial')` or `ignore ('list name')`

Description: Adds a specific serial to the script engine's ignore list to avoid finding items when using commands like `findtype`

Example

Ignore by serialIgnore by variable

`clearignore

ignore '0x123A'
`

`clearignore

if findtype 3572 backpack as 'wand' or findtype 3570 backpack as 'wand'
    overhead 'found' 44
    overhead 'wand' 44

    ignore 'wand'
else
    overhead 'not found' 33
endif
`

## unignore

Syntax: `unignore ('serial')` or `unignore ('list name')`

Description: Removes a specific serial to the script engine's ignore list

Example

Unignore by serialUnignore by variable

`unignore '0x123A'
`

`clearignore

if findtype 3572 backpack as 'wand' or findtype 3570 backpack as 'wand'
    overhead 'found' 44
    overhead 'wand' 44

    ignore 'wand'

    wait 1000

    unignore 'wand'
else
    overhead 'not found' 33
endif
`

## List Commands

## clearlist

Syntax: `clearlist ('list name')`

Description: This command will clear a list but doesn't remove it.

Example

General

`if list 'mylist' > 0
    clearlist 'mylist'
endif

pushlist 'sample' 'hello'
`

## createlist

Syntax: `createlist ('list name')`

Description: This command will create an empty list.

Example

SimpleIterating Lists (foreach)

`if not listexists 'sample'
    createlist 'sample'
endif

pushlist 'sample' 'hello'
`

`if not listexists 'words'
    createlist 'words'
endif

pushlist 'words' 'loot'
pushlist 'words' 'taming'
pushlist 'words' 'felucca'
pushlist 'words' 'trammel'
pushlist 'words' 'pk'
pushlist 'words' 'pvp'
pushlist 'words' 'britannia'
pushlist 'words' 'dungeon'
pushlist 'words' 'crafting'
pushlist 'words' 'gm'
pushlist 'words' 'mobs'
pushlist 'words' 'spawn'
pushlist 'words' 'vendor'

# Start at loot, and keep saying each item in the list the end.
foreach 'word' in 'words'
    # Show the current item in the list above your head
    overhead 'word'
endfor
`

## poplist

Syntax: `poplist ('list name') ('list value'/'front'/'back')`

Description: This command will remove an item from the list. You can either pass in the specific item, or use `front` or `back` to remove the item from the front or back of the list.

Tip

You can use `poplist` as an expression.

Example

Remove first item in list

`createlist 'list'
pushlist 'list' 'hello'
pushlist 'list' 'bye'

poplist 'list' 'front'        
`

## pushlist

Syntax: `pushlist ('list name') ('list item') ['front'/'back']`

Description: This command will add an item to the list. You can define where in the list using `front` or `back` to remove the item from the front or back of the list. Default `pushlist` will add the item to end of the list.

Example

Add item to listAdd item to front of list

`createlist 'list'
pushlist 'list' 'hello'
pushlist 'list' 'bye'        
`

`createlist 'list'
pushlist 'list' 'hello'
pushlist 'list' 'bye' 'front'
`

## removelist

Syntax: `removelist ('list name')`

Description: This command will remove a list completely including all items in the list.

Example

General

`removelist 'listname'        
`

## Messaging Commands

## alliance

Syntax: `alliance ('message to send')`

Description: This command will force your character to say an alliance message passed as the parameter.

Example

General

`alliance 'Allies assemble!'
`

## clearsysmsg

Syntax: `clearsysmsg`

Description: Clears the internal system message queue

Example

General

`sysmsg 'hello'
sysmsg 'bye'

if insysmsg 'hello'
    say 'hello!'
endif

clearsysmsg

if insysmsg 'bye'
    say 'this condition wont be met since it was cleared on line 8'
endif
`

## emote

Syntax: `emote ('message to send') [hue]`

Description: This command will force your character to emote the message passed as the parameter.

Tip

This command will append `*` around the emote so `emote 'smiles'` will be displayed in game as `*smiles*`.

Example

EmoteEmote with hue

`emote 'smiles'
`

`emote 'smiles in another color' 454
`

## guild

Syntax: `guild ('message to send')`

Description: This command will force your character to say a guild message passed as the parameter.

Example

Guild message

`guild 'Hello fellow guildmates!'
`

## overhead

Syntax: `overhead ('text') ['color'] ['serial']`

Description: This command will display a message over your head. Only you can see this.

Example

Overhead message

`if stam = 100
    overhead 'ready to go!'
endif
`

## say

Syntax: `say ('message to send') [hue]` or `msg ('message to send') [hue]`

Description: This command will force your character to say the message passed as the parameter.

Example

Say messageSay message with hue

`say 'Hello world!'
`

`say 'Hello world!' 454
`

## sysmsg

Syntax: `sysmsg ('message to display in system message')`

Description: This command will display a message in the lower-left of the client.

Example

Description

`if stam = 100
    sysmsg 'ready to go!'
endif
`

## waitforsysmsg

Syntax: `waitforsysmsg ('message to wait for') [timeout]` or `wfsysmsg ('message to wait for') [timeout]`

Description: This command will wait a specific message to be added to the system message queue before continuing.  Default timeout is 30 seconds that can be changed by passing in a new timeout value in milliseconds.

Example

Wait for system messageWait for system message for 5 seconds

`waitforsysmsg 'ready to go'
overhead 'Ready!'
`

`waitforsysmsg 'ready to go' 5000
overhead 'Done waiting'
`

## whisper

Syntax: `whisper ('message to send') [hue]`

Description: This command will force your character to whisper the message passed as the parameter.

Example

Whisper messageWhisper message with hue

`whisper 'Hello world!'
`

`whisper 'Hello world!' 454
`

## yell

Syntax: `yell ('message to send') [hue]`

Description: This command will force your character to yell the message passed as the parameter.

Example

Yell messageYell message with hue

`yell 'Hello world!'
`

`yell 'Hello world!' 454
`

## Targeting Commands

## clearall

Syntax: `clearall`

Description: Combines the following actions into one command: `Cancel Current Target, Clear Target Queue, Drop What You Are Currently Holding and Clear Drag/Drop Queue` into a single command.

Example

Clear on sysmsg message

`if insysmsg 'cannot find'
    clearall
endif
`

## lasttarget

Syntax: `lasttarget`

Description: This command will target your last target set in Razor.

Example

Cast on last target

`cast 'magic arrow'
waitfortarget
lasttarget
`

## setlasttarget

Syntax: `setlasttarget ('serial')`

Description: This command will set the last target to the serial you pass as a parameter.

Tip

You can use `hotkey 'Set Last Target'` if you prefer getting a cursor and targetting a specific object.

Example

Set last target on variable..with findtype

`setvar 'dog' 0x239
setlasttarget 'dog'
`

`// find a dog
if findtype '217' as 'dog'
    setlasttarget 'dog'
    cast 'lightning'
    wft
    target 'dog'
endif
`

## target

Syntax: `target ('closest/random/next/prev') [type1,type2] [humanoid/monster]` or `target ('closest/random/next/prev') [type1!type2] [humanoid/monster]` or `target (serial)` or `target (clear/cancel)`

Description: This command will target a specific mobile based either the type searched for or the serial. If you provide a list of target types, you can use `,` for a general list and `!` for a priority list.

Type
Notoriety Name
Notoriety Color

`nonfriendly`
Attackable, Criminal, Enemy, Murderer
Gray (but not criminal), Gray, Orange, Red

`friendly`
Innocent, Guild/Ally
Blue, Green

`enemy`
Enemy
Orange

`red`/`murderer`
Murderer
Red

`gray`/`grey`
Attackable, Criminal
Gray (but not criminal), Gray

`criminal`
Criminal
Gray

`blue`/`innocent`
Innocent
Blue

`friend`
Based on your friends list
Any

List Type
Delimiter
Description

General
`,`
When the script tries to acquire a target, it will look for all the target types passed in the list. See Examples.

Priority
`!`
When the script tries to acquire a target, it will prioritize each type. See Examples.

Example

Specific targetGeneral listPriority listTarget closest redTarget closest gray or red monsterTarget random mobileTarget random red monsterNext humanoid targetCancel current targetClear target queue

`cast 'lightning'
waitfortarget
target '0xBB3'
`

`cast 'lightning'
waitfortarget

// General list using a ,
// If a red mobile is closer than a gray mobile, this will target the red mobile
target closest gray,red
`

`cast 'lightning'
waitfortarget

// Priority list using a !
// If a red mobile is closer than a gray mobile, this will target the gray mobile
target closest gray!red
`

`cast 'lightning'
waitfortarget
target closest 'red'
`

`cast 'lightning'
waitfortarget
target closest 'gray,red' monster
`

`cast 'lightning'
waitfortarget
target random
`

`cast 'lightning'
waitfortarget
target random 'red' monster
`

`target next humanoid
`

`target cancel
`

`target clear
`

## targetrelloc

Syntax: `targetrelloc (x-offset) (y-offset)`

Description: This command will target a specific location on the map relative to your position.

Example

Target 1 X, 1 Y from player location

`cast 'fire field'
waitfortarget
targetrelloc 1 1
`

## targetloc

Syntax: `targetloc (x) (y) (z)`

Description: This command will target a specific location on the map.

Example

Specific location

`cast 'fire field'
waitfortarget
targetloc 5923 1145 0
`

## targettype

Syntax: `targettype ('name of item or mobile type'/'graphicId') [inrange (true/false)/backpack] [hue]`

Description: This command will target a specific type of mobile or item based on the graphic id or based on the name of the item or mobile.

Range Check

If the optional parameter is passed in as `true` only items within the range of `2` tiles will be considered. If the optional parameter is passed in as `backpack` only items in your backpack will be considered.

Getting the graphic name or ID

To get the name or the ID of item, use the `>info` command in Razor and click on the item. You can use either the `Item Name` or `Id`.

Example

Target by name (any range)Target by type (any range)Target by type using serial (in range)Target by type using name (in range)Target by name (in backpack)Target by name with hue (in backpack)

`dclicktype 'dagger'
waitfortarget
targettype 'robe'
`

`dclick '0x4005ECAF'
waitfortarget
targettype '0x1F03'
`

`dclick '0x4005ECAF'
waitfortarget
targettype '0x1F03' true
`

`dclick 'dagger'
waitfortarget
targettype 'robe' true
`

`dclicktype 'dagger' backpack
waitfortarget
targettype 'robe' backpack
`

`dclicktype 'dagger' backpack
waitfortarget
targettype 'robe' backpack 45
`

## waitfortarget

Syntax: `waitfortarget [pause in milliseconds]` or `wft [pause in milliseconds]`

Description: This command will cause the script to pause until you have a target cursor.  By default it will wait 30 seconds but you can define a specific wait time if you prefer.

Example

Cast and waitUsing 'wft' shorthand on last target

`cast 'energy bolt'
waitfortarget
hotkey 'Target Closest Enemy'
`

`cast 'energy bolt'
wft
target 'last'
`

## Timer Commands

## createtimer

Syntax: `createtimer ('timer name')`

Description: This command will create a timer and immediately start counting up from 0

Example

Create Timer

`if not timerexists 'sample'
    createtimer 'sample'
endif           
`

## removetimer

Syntax: `removetimer ('timer name')`

Description: This command will remove/delete a specific timer

Example

Delete Timer

`if timerexists 'sample'
    removetimer 'sample'
endif           
`

## settimer

Syntax: `settimer ('timer name') ('number in milliseconds')`

Description: This command will set a timer to a specific number and start to count up immediately.

Example

Set Timer

`// Create a new timer
if not timerexists 'sample'
    createtimer 'sample'
endif

// Reset every 10 seconds
if timer 'sample' > 10000
    settimer 'sample' 0
endif            
`

---

## Expressions

## Statements & Loops

As found in the Razor macro system, you can use `if`, `for`, `foreach`, and `while` when writing a script to add some basic logic and flows.

## if

Syntax:

`if (expression)
    // commands to execute if this expression is true
elseif (expression)
    // commands to execute if the first expression was false, and this expression is true
else
    // commands to execute if both expressions above were false, default to running these
endif
`

Description: This selects a path to execute based on the value of a boolean expression. An `if` statement can be combined with `else` or `elseif` to choose two or more distinct paths based on the result of the boolean expression. All `if` statements must end with `endif`.

Example

if/endifif/elseif/elseif/elseifUsing 'not'

`if stam = 100
    overhead 'Stam at 100!'
endif
`

`if stam = 100
    say 'Stamina full'
elseif stam < 20
    say 'Still a ways to go'
elseif stam < 60
    say 'Getting closer'
else
    say 'waiting'
endif
`

`if stam = 100
    say 'Stamina full'
elseif stam < 20
    say 'Still a ways to go'
elseif stam < 60
    say 'Getting closer'
endif
`

`if not stam = 100
    say 'Stamina is not full'    
endif
`

## for

Syntax:

`for ('number')
    // commmands to execute the number of times defined in the for statement
endfor
`

Description: This allows you to execute a block of commands a specific number of times. All `for` loops must end with `endfor`.

Tip

You can use the index variable to track your position in the for loop.

When using `for` or `while` you have access to the `index` variable. This can be used with `overhead` (for example) to indicate the current loop number.

Example

Say 'Hello' 10 timesOutput current loop number

`for 10
    say 'hello'
    wait 1000
endfor
`

`for 10
    wait 1000
    overhead 'index'
endfor
`

## foreach

Syntax:

`foreach ('variable') in ('list')
    // commands to execute for each item that is in a list
endfor
`

Description: This allows you to iterate over a list containing values. All `foreach` loops must end with `endfor`.

Example

Loop through each item in a list

`createlist 'mylist'
pushlist 'mylist' '0x1'
pushlist 'mylist' '0x2'

foreach 'item' in 'mylist'
   overhead 'item'
endfor
`

## while

Syntax:

`while ('expression')
    // commands to execute as long as the expression is remains true
endwhile
`

Description: This allows you execute a block of commands while a certain expression is true. All `while` loops must end with `endwhile`.

Example

While

`while hits < 100
    say 'I need a heal!'
    wait 1000
endwhile
`

## Expression Operators

When using the `if` or `while` conditions, you can access the following expressions in the statement.

The following operators are supported:

Operator
Description

=
Equal

==
Equal

!=
Not equal

<
Less than

<=
Less than or equal

>
Greater than

>=
Greater than or equal

## Expressions

Expressions are combined with statements like `if` and `while` to alter the execution path of your script.

Below are the several different types of expressions you can use broken into categories.

## List Expressions

## inlist

- `inlist ('list name') ('list item')`

Description: Used to check if a specific item is in a list

Example

General

`if inlist 'my_list' 'item1'
    overhead 'found item!'
endif
`

## list

- `list ('list name')`

Description: Used to check how many items are in a specific list

Example

General

`if list 'mylist' = 10
    overhead '10 items in your list'
endif
`

## listexists

- `listexists ('list name')`

Description: Used to check if a list exists with a specific name.

Example

General

`if not listexists 'mylist'
    createlist 'mylist'
endif
`

## poplist

- `poplist ('list name') ('list value'/'front'/'back')`

Description: This command will remove (pop) an item from the list. You can either pass in the specific item, or use `front` or `back` to remove the item from the front or back of the list.

Example

General

`if poplist 'mylist' back as 'item'
    overhead 'item'
endif
`

## Misc Expressions

## count/counter

- `count ('name of counter')`

- `counter ('name of counter')`

- `count ('name of item') [hue]`

- `count (graphicID) [hue]`

Description: Used to get the current amount of a specific item in player's backpack.
Omitting the hue argument will result in count of all items of the specified type regardless of their hue.
The expression can be used either directly by item type and hue, or by referencing a named counter manually set up in the Counters tab.
More info

Example

Counting garlicCounting runebooksDetecting fancy coins

`if count 'garlic' < 5
    say 'getting low on garlic'
endif
`

`if count 'spellbook' '1121' == 0
    say 'no runebooks found!'
endif
`

`if count 'gold coin' > count 'gold coin' 0
    overhead 'woot woot fancy coins in the pack!'
endif
`

## findtype

- `findtype ('name of item') [inrangecheck (true/false)/backpack] [hue]` OR `findtype (graphicID) [inrangecheck (true/false)/backpack] [hue]`

Description: Used to check if a specific item name of graphic ID exists. Range check, if true, will check within 2 tiles.

The `as` keyword

If you use `findtype` along with `as` you can assign a temporary variable to use throughout the script. See example below.

In-Game Info Gump

Not sure what name to enter or graphic ID to enter? Type `>info` and click on any item or mobile for more information.

Click the blue dot next to the value you want to copy to the clipboard.

Example

Find a sawFind a saw using graphic idFind a saw within 2 tilesFind a saw in your backpackFind a dagger and use it (using as)Find a dagger in backpack with a hue

`if findtype 'saw'
    say 'found saw'
endif
`

`if findtype '4148'
    say 'found saw'
endif
`

`if findtype 'saw' true
    say 'found saw within 2 tiles'
endif
`

`if findtype 'saw' backpack
    say 'found saw in my pack'
endif
`

`if findtype 'dagger' as 'mydagger'
    overhead 'found dagger'
    dclick 'mydagger'
endif
`

`if findtype 'dagger' backpack 45 as 'mydagger'
    overhead 'found dagger'
    dclick 'mydagger'
endif
`

## insysmsg

- `insysmsg ('message to look for')`

- `insysmessage ('message to look for')`

Description: Used to check if certain text appears within the system message log.

System Message Queue

Not sure if a specific message is in Razor's system message queue? Type `>sysmsgs` to see what Razor can find.

Using `clearsysmsg` will clear out the queue completely.

Example

Check for message

`if insysmsg 'too far away'
    overhead 'You are too far away'
endif
`

## itemcount

- `itemcount`

Description: Used to return the current number of items you're carrying

Example

General

`if itemcount < 125
    overhead 'I still have room!'
endif
`

## queued

- `queued`

Description: Used to check if your current queue is active (from restocking, organizing, etc)

Example

GeneralOrganizerRestock

`    if queued
        overhead 'Queue is active'
    else
        overhead 'No queue'
    endif
`

`overhead 'Organizing'

organizer 1

while queued
    overhead 'Currently Organizing'
    wait 500 
endwhile

overhead 'Organized'
`

`overhead 'Restocking'

restock 11
waitfortarget 
target 'self'

while queued
    overhead 'Currently restocking'
    wait 500 
endwhile

overhead 'Restocked'
`

## targetexists

- `targetexists ['any'/'beneficial'/'harmful'/'neutral']`

Description: Used to check if the client current has a target cursor up

Example

General

`if targetexists 'beneficial'
    overhead 'Beneficial target found'
elseif targetexists 'harmful'
    overhead 'Harmful target found'
endif
`

## varexist

- `varexist`

- `varexists`

Description: Used to check if a variable exists.

Example

General

`if not varexist 'myrunebook'
    overhead 'Runebook variable not found -- select one'
    setvar 'myrunebook'
endif

dclick 'myrunebook'
waitforgump 'any'
gumpresponse 5
`

## Player Attribute Expressions

## diffhits

- `diffhits`

- `diffhp`

Description: Used to get the difference between you max hits and current hits.

Example

General

`if diffhits > 40
    overhead 'I need a heal!'
endif
`

## diffmana

- `diffmana`

Description: Used to get the difference between you max mana and current mana.

Example

General

`if diffmana > 40
    skill 'Meditation'
endif
`

## diffstam

- `diffstam`

Description: Used to get the difference between you max stamina and current stamina.

Example

General

` if diffstam > 30
    overhead 'Need stamina'
endif
`

## diffweight

- `diffweight`

Description: Used to get the difference between you max weight and current weight.

Example

General

`if diffweight > 20
    overhead 'I can lift 20 more stone'
endif
`

## followers

Description: Used to get the current number of followers.

Example

General..used with maxfollowers

`if followers = 0
    overhead 'No one following me!'
else
    overhead 'I have followers'
endif
`

`if followers < maxfollowers
    overhead 'You can have more followers!'
else
    overhead 'You hit your followers limit'
endif
`

## findbuff

- `findbuff 'name of buff/debuff`

Description: Used to check if a specific buff/debuff is applied to you.

Example

Check for magic reflection

`if findbuff 'magic reflection'
    overhead 'Im set!'
else
    cast 'magic reflection'
    wft
    target 'self'
endif
`

## hidden

- `hidden`

Description: Used to check if you are hidden.

Example

Check if hidden

`if hidden
    overhead 'they cant see me'
endif
`

## hp & maxhp

- `hp`

- `maxhp`

- `hits`

- `maxhits`

Description: Used to get your current or max hit points/health levels.

Example

Example 1Example 2

`while hp < 100
    say 'not at 100 yet'
    wait 5000
endwhile
`

`if maxhp = 120
    say 'Full hp!'
endif
`

## lhandempty

- `lhandempty`

Description: Used to check if your left hand is empty

Example

General

`if lhandempty
    hotkey 'empty right hand!'
endif
`

## invuln

- `invuln`

- `invul`

- `blessed`

Description: Used to get your invulnerable status

Example

General

`if invuln
    overhead 'I feel.. so powerful.'
endif
`

## mana & maxmana

- `mana`

- `maxmana`

Description: Used to get your current or max mana levels.

Example

General

`while mana < maxmana
    skill 'meditation'
    wait 11000
endwhile
`

## maxfollowers

Description: Used to get the maximum number of allowed followers.

Example

General..used with followers

`if followers = maxfollowers
    overhead 'You hit your limit'       
endif
`

`if followers < maxfollowers
    overhead 'You can have more followers!'
else
    overhead 'You hit your followers limit'
endif
`

## maxweight

- `maxweight`

Description: Used to get your max allowed weight.

Example

General

`if weight <= maxweight
    say 'I am overweight'
endif
`

## mounted

- `mounted`

Description: Used to check if you are currently on a mount

Example

General

`if mounted
    say 'mounted'
else
    say 'not mounted'
endif
`

## name

- `name`

Description: Used to get your name of the currently logged in character

Example

General

`if name = 'Quick'
    overhead 'thats me!'
endif
`

## paralyzed

- `paralyzed`

Description: Used to check if you are currently paralyzed.

Example

General

`if paralyzed
    overhead 'I cannot move!'
endif
`

## poisoned

- `poisoned`

Description: Used to check if you are currently poisoned.

Example

General

`if poisoned
    hotkey 'drink cure'
endif
`

## position

- `position (x, y)`

- `position (x, y, z)`

Description: Used to check if your current position matches the provided.

Example

General

`if position 2729 2133
    overhead 'You are currently in front of the Bucs Den teleporter'
elseif position 2728 2133 5
    overhead 'You are standing on the Bucs Den teleporter'
endif
`

## rhandempty

- `rhandempty`

Description: Used to check if your right hand is empty

Example

General

`if rhandempty
    hotkey 'empty right hand!'
endif
`

## skill

- `skill ('name')`

Description: Used to get the current skill level for a given skill.

Supported skill names

Razor used to rely on a static list of names but now reads from your client's skills.mul file for the names of the skill.

Real vs Shown (or Value)

By default, Razor will compare against the shown skill value that includes other factors such as your stats. If you'd like to compare to the real skill value, use the `!` in front of `skill`.  See the example below.

Example

Compare Shown SkillCompare Real Skill

`if skill 'magery' < 62.5
    cast 'invisibility'
    waitfortarget
    target 'self'
endif
`

`// Note the ! at the end of the skill expression command
// This tells Razor to look at the real value, not the shown value
if skill! 'magery' < 62.5
    cast 'invisibility'
    waitfortarget
    target 'self'
endif
`

## stam & maxstam

- `stam`

- `maxstam`

Description: Used to get your current stamina or max stamina.

Example

General (stam)General (maxstam)

`if stam < 30
    say 'I need to rest'
endif
`

`if maxstam = 120
    say 'I feel so powerful!'
endif
`

## str, dex & int

- `str`

- `dex`

- `int`

Description: Used to get your current strength, dexterity and intelligence.

Example

StrengthDexterityIntelligence

`if str = 100
    say 'Strength does not come from physical capacity. It comes from an indomitable will.'
endif
`

`if dex = 100
    say 'Dexterity comes by experience and practice.'
endif
`

`if str = 100
    say 'The true sign of intelligence is not knowledge but imagination.'
endif
`

## warmode

- `warmode`

Description: Used to get your current combat/war status

Example

General

`if warmode
    overhead 'Lets fight'
else
    overhead 'Peace to you'
endif
`

## weight

- `weight`

Description: Used to get your current weight.

Example

General

`if weight = 300
    say 'I feel heavy'
endif
`

## Timer Expressions

## timer

- `timer ('name')`

Description: Used to check how much time is left in an existing timer

Example

GeneralAlert

`// Create a new timer
if not timerexists 'sample'
    createtimer 'sample'
endif

// Reset every 10 seconds
if timer 'sample' > 10000
    settimer 'sample' 0
endif
`

`# Create a new timer
createtimer 'alert'

while not dead            

    // Reset every 10 seconds
    if timer 'alert' > 10000
        overhead 'ALERT TRIGGERED!'
        settimer 'alert' 0
    endif

endwhile
`

## timerexists

- `timerexist ('name')`

Description: Used to check if a timer exists

Example

General

`// Create a new timer
if not timerexists 'sample'
    createtimer 'sample'
endif

// Reset every 10 seconds
if timer 'sample' > 10000
    settimer 'sample' 0
endif
`

---

## Keywords

## Keywords Overview

## and

Syntax: `(statement) and (statement)`

Description: The `and` keyword links statements together and if all statements are `true` the condition is met.

Example

General

`if insysmsg 'hello' and insysmsg 'bye'
    say 'found'
endif
`

## as

Syntax: `(statement) as (variable)`

Description: The `as` keyword works in conjunction with the `findtype` expression.

Example

General

`if findtype 'dagger' as 'mydagger'
    overhead 'found dagger'
    dclick 'mydagger'
endif
`

## break

Syntax: `break`

Description: The `break` keyword terminate the closest enclosing loop such as a `for` loop.

Example

General

`for 100
    if stam = 100
        break
    else
        say 'loop again'
    endif
endfor
`

## continue

Syntax: `continue`

Description: The `continue` keyword passes control to the next iteration of the enclosing `for` or `while` loop which the keyword appears.

Example

General

`while stam < 100

    if stam = 50
       say 'At 50!'
       // Skip saying 'Not at 50'
       continue
    endif

    say 'Not at 50'

endwhile
`

## in

Syntax: `(word) in (variable string)`

Description: The `in` keyword works in conjunction with the `getlabel` command.

Example

General

`if findtype '217' as 'a_dog'
    getlabel 'a_dog' 'dog_label'

    if 'Fido' in 'dog_label'
        overhead 'found mydog!' 5
        overhead 'dog_label' 67
    endif    
endif
`

## loop/replay

Syntax: `loop` OR `replay`

Description: The `loop` or `replay` keyword will restart the currently run script back to the beginning indefinitely.

Example

General

`if mana = 100
    say 'all done!'
    stop
else
    say 'still meditating'
endif

wait 1000

loop
`

## not

Syntax: `not (statement)`

Description: They `not` keyword returns the opposite of the statement result.

Example

General

`if not 'dead'
    say 'I live!'
endif

if 'dead'
    say 'I died!'
endif
`

`while not hp = 100
    overhead 'My HP isnt full'
endwhile
`

## or

Syntax: `(statement) or (statement)`

Description: The `or` keyword links statements together and if one statements is `true` the condition is met.

Example

General

`if insysmsg 'hello' or insysmsg 'bye'
    say 'found'
endif
`

## stop

Syntax: `stop`

Description: The `stop` keyword will stop the execution of the current script.

Example

General

`if stam = 100
    say 'all done!'
    stop
else
    say 'still waiting'
endif

wait 1000

loop
`

---

## Layers

## Layers Overview

If the command you're using requires a `layername` (such as `dropitem`) can use any of the following keywords (case insensitive):

- `RightHand`

- `LeftHand`

- `Shoes`

- `Pants`

- `Shirt`

- `Head`

- `Gloves`

- `Ring`

- `Talisman`

- `Neck`

- `Hair`

- `Waist`

- `InnerTorso`

- `Face`

- `Bracelet`

- `FacialHair`

- `MiddleTorso`

- `Earrings`

- `Arms`

- `Cloak`

- `Backpack`

- `OuterTorso`

- `OuterLegs`

- `InnerLegs`

---

## Variables

## Variables Overview

Variables (also referred to as aliases) are commonly used values designed to be referenced in any of your scripts.

You can either define your own variables or you can use this list of pre-defined variables.

## Defining Variables

You can create custom variables that are available in your scripts.  This can be done one of two ways.  First, you can create custom variables in the Razor UI by going to the Options tab under the Scripts tab.

Simply click Add, give it a name and target the item or mobile and that variable is available in your scripts.  In the screenshot above, `regbag` is set to a bag.  To use this variable in a script, you simply reference it.

- Open your reg bag

`dclick 'regbag'
`

You can also set variables in scripts by using the `setvar` command.  To update the `regbag` command, you might do something like this:

- Get target cursor to select item or mobile

`setvar 'regbag'
`

The script will pause until you select a target. After you select a target, it will update and move on to the next line in the script.

## Pre-Defined Variables

Along with defining your own variables, you can use these pre-defined variables in your scripts.

Variable
Description

`backpack`
`Returns:` The serial of your own backpack

`hands`
`Returns:` The serial of the item in either hand

`index`
`Returns:` The index of the current loop iteration

`lasttarget` / `last`
`Returns:` The serial of your current last target in Razor

`lastobject`
`Returns:` The serial of your last used object in Razor

`lefthand`
`Returns:` The serial of the item in your left hand

`righthand`
`Returns:` The serial of the item in your right hand

`self`
`Returns:` The serial of your player

## Index Variable

When using `for` or `while` you have access to the `index` variable. This can be used with `overhead` (for example) to indicate the current loop number.

For example, this script snippet will output the numbers 0-9 overhead every second.

`for 10
    wait 1000
    overhead 'index'
endfor
`

`for 10
    if index == 7
        overhead '7th loop'
    endif
endfor
`
