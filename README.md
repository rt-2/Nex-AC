[Download latest release (v1.9.49)](https://github.com/NexiusTailer/Nex-AC/tree/master/src/v1.9.49)

# [Nex-AC - Anticheat system](http://forum.sa-mp.com/showthread.php?t=579963)

Nex Anticheat (Nex-AC) - is a comprehensive protection which combines powerful anticheat and protection against various attacks (flood, DoS).  
Anticheat detects popular cheats instantly punishing cheaters.  
Anti-DoS combines customizable anti-flood, anti-DoS at network level and a lot of protection tools against hacking, crashers etc.

## List of basic anti-cheats:
* Anti-AirBreak (onfoot/in vehicle)
* Anti-teleport hack (onfoot/into/in/between vehicles)
* Anti-teleport pickups
* Anti-FlyHack (onfoot/in vehicle)
* Anti-SpeedHack (onfoot/in vehicle)
* Anti-Health hack (onfoot/in vehicle) and armour hack
* Anti-Weapon hack and (add/infinite) ammo hack
* Anti-Special actions hack (including jetpack)
* Anti-GodMode from bullets (onfoot/in vehicle)
* Anti-Invisible hack
* Anti-Money hack
* Anti-Tuning hack
* Anti-lagcomp-spoof
* Anti-Parkour mod
* Anti-Quick turn
* Anti-Rapid fire
* Anti-FakeSpawn
* Anti-FakeKill
* Anti-Pro Aim
* Anti-CJ run
* Anti-CarShot
* Anti-CarJack
* Anti-UnFreeze
* Anti-AFK Ghost
* Anti-Reconnect
* Anti-High ping
* Anti-Fake NPC
* Anti-Dialog hack
* Protection from sandbox
* Protection from invalid version
* Protection from flood by seat changing
* Protection from connection flood in one slot
* Anti-Rcon hack (brute/brute-force)
* Anti-callback functions flood *(complete list below)*
* Anti-crashers *(complete list below)*
* Anti-NOPs *(complete list below)*
* Anti-DoS

# Additional features:
##### * Setting anticheat from file
The settings is located in a separate file (scriptfiles\nex-ac_settings.cfg)
##### * Statistics viewing
Ability to view statistics of the anticheat for all the time of server work since its launch
Displayed automatically when the server turns off. Stored in a server log (server_log.txt)
##### * Logging the most important actions
Optionally, you can enable debug-mode for logging all actions
##### * Multilingual
Ability to set any of the available languages.  
It also simplifies the process of translation of anticheat into other languages

## List of publics which are protected by anti-flood:
* OnDialogResponse
* OnEnterExitModShop
* OnPlayerClickMap
* OnPlayerClickPlayer
* OnPlayerClickTextDraw
* OnPlayerCommandText
* OnPlayerEnterVehicle
* OnPlayerExitVehicle
* OnPlayerPickUpPickup
* OnPlayerRequestClass
* OnPlayerSelectedMenuRow
* OnPlayerStateChange
* OnVehicleMod
* OnVehiclePaintjob
* OnVehicleRespray
* OnVehicleDeath
* OnPlayerText
* OnPlayerEnterCheckpoint
* OnPlayerLeaveCheckpoint
* OnPlayerRequestSpawn
* OnPlayerExitedMenu
* OnPlayerEnterRaceCheckpoint
* OnPlayerLeaveRaceCheckpoint
* OnPlayerClickPlayerTextDraw
* OnVehicleDamageStatusUpdate
* OnPlayerSelectObject

## Anti-NOPs:
* SpawnPlayer
* SetPlayerPos
* SetVehiclePos
* SetPlayerAmmo
* SetPlayerHealth
* SetPlayerArmour
* SetVehicleHealth
* GivePlayerWeapon
* SetPlayerPosFindZ
* SetPlayerInterior
* PutPlayerInVehicle
* ResetPlayerWeapons
* SetPlayerArmedWeapon
* SetPlayerSpecialAction
* TogglePlayerSpectating
* RemovePlayerFromVehicle

## Anti-Crashers:
* Invalid tuning
* Invalid vehicle seat
* Illegal characters in the dialogs (deleting)
* Invalid attached objects
* Weapon Crasher

# Functions:
#### public OnCheatDetected(playerid, ip_address[], type, code)

> Called when triggers one of the anti-cheats
> * `playerid` - ID of the cheater
> * `ip_address[]` - IP-address of the cheater
> * `type` - Type of cheating (when `0` it returns the ID, when `1` - IP)
> * `code` - Code (ID) of the anti-cheat
> * This callback does not handle returns


#### EnableAntiCheat(code, enable)

> Use to enable/disable one of the anti-cheats
> * `code` - ID of the anti-cheat
> * `enable` - `1` to enable/`0` to disable
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the `code` parameter contains an invalid ID of the anti-cheat


#### EnableAntiCheatForPlayer(playerid, code, enable)

> Use to enable/disable one of the anti-cheats for a particular player
> * `playerid` - ID of the player who needs to enable/disable the anti-cheat
> * `code` - ID of the anti-cheat
> * `enable` - `1` to enable/`0` to disable
> * Returns `1` if the function executed successfully, `0` if the player is not connected or `-1` if the `code` parameter contains an invalid ID of the anti-cheat



Added in v1.3:


#### IsAntiCheatEnabled(code)

> Use to check whether one of the anti-cheats is enabled/disabled
> * `code` - ID of the anti-cheat
> * Return `1 (true)` if enabled or `0 (false)` if disabled


#### IsAntiCheatEnabledForPlayer(playerid, code)

> Use to check whether one of the anti-cheats is enabled/disabled for a particular player
> * `playerid` - ID of the player to be checked whether the anti-cheat enabled/disabled for him
> * `code` - ID of the anti-cheat
> * Return `1 (true)` if enabled or `0 (false)` if disabled



Added in v1.8.8:


#### AntiCheatGetHealth(playerid, &Float:health)

> Use to get the amount of a player's health
> * `playerid` - The ID of the player
> * `&Float:health` - Variable for storage health, passed by reference
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the player is not connected


#### AntiCheatGetArmour(playerid, &Float:armour)

> Use to get the amount of a player's armour
> * `playerid` - The ID of the player
> * `&Float:armour` - Variable for storage armour, passed by reference
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the player is not connected


#### AntiCheatGetVehicleHealth(vehicleid, &Float:health)

> Use to get the amount of the vehicle health
> * `vehicleid` - The ID of the vehicle
> * `&Float:health` - Variable for storage health, passed by reference
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the vehicle does not exist


#### AntiCheatGetWeaponData(playerid, slot, &weapons, &ammo)

> Use to get weapons and ammo in a certain slot of a player
> * `playerid` - The ID of the player
> * `slot` - The slot in which need to get the weapons and ammo
> * `&weapons` - Variable for storage weapon ID, passed by reference
> * `&ammo` - Variable for storage amount of ammo, passed by reference
> * Returns `1` if the function executed successfully, `0` if the player is not connected or `-1` if the slot is specified incorrectly


#### AntiCheatGetSpawnWeapon(playerid, &weapon1, &weapon1_ammo, &weapon2, &weapon2_ammo, &weapon3, &weapon3_ammo)

> Use to get spawn weapons and ammo of a player
> * `playerid` - The ID of the player
> * `&weapon1` - Variable for storage the weapon 1, passed by reference
> * `&weapon1_ammo` - The variable for storage the amount of ammo for the weapon 1, passed by reference
> * `&weapon2` - Variable for storage the weapon 2, passed by reference
> * `&weapon2_ammo` - The variable for storage the amount of ammo for the weapon 2, passed by reference
> * `&weapon3` - Variable for storage the weapon 3, passed by reference
> * `&weapon3_ammo` - The variable for storage the amount of ammo for the weapon 3, passed by reference
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the player is not connected


#### AntiCheatGetPos(playerid, &Float:x, &Float:y, &Float:z)

> Use to get a player's position
> * `playerid` - The ID of the player
> * `&Float:x` - The variable for storage the x coordinate, passed by reference
> * `&Float:y` - The variable for storage the y coordinate, passed by reference
> * `&Float:z` - The variable for storage the z coordinate, passed by reference
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the player is not connected


#### AntiCheatGetVehicleVelocity(vehicleid, &Float:x, &Float:y, &Float:z)

> Use to get the vehicle speed
> * `vehicleid` - The ID of the vehicle
> * `&Float:x` - The variable for storage the x speed, passed by reference
> * `&Float:y` - The variable for storage the y speed, passed by reference
> * `&Float:z` - The variable for storage the z speed, passed by reference
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the vehicle does not exist


#### AntiCheatGetSpeed(playerid)

> Use to get a player's speed
> * `playerid` - The ID of the player
> * Returns the player's speed or `0` if the player is not connected


#### AntiCheatGetAnimationIndex(playerid)

> Use to get the index (ID) of a player's current animation
> * `playerid` - The ID of the player
> * Returns the ID of the animation or `0` if the player is not connected


#### AntiCheatGetDialog(playerid)

> Use to get the ID of the opened dialog of a player
> * `playerid` - The ID of the player
> * Returns the ID of the dialog or `-1` if the player is not connected


#### AntiCheatGetEnterVehicle(playerid)

> Use to get the ID of the vehicle which a player try to enter
> * `playerid` - The ID of the player
> * Returns the ID of the vehicle or `0` if the player is not connected


#### AntiCheatGetVehicleID(playerid)

> Use to get the ID of the vehicle in which a player is
> * `playerid` - The ID of the player
> * Returns the ID of the vehicle or `0` if the player is not connected


#### AntiCheatGetWeapon(playerid)

> Use to get a player's current weapon ID
> * `playerid` - The ID of the player
> * Returns the ID of weapon or `-1` if the player is not connected


#### AntiCheatGetVehicleSeat(playerid)

> Use to get the seat in the vehicle on which the player is
> * `playerid` - The ID of the player
> * Returns the ID of the seat or `-1` if the player is not connected


#### AntiCheatGetSpecialAction(playerid)

> Use to get the ID of the special action of a player
> * `playerid` - The ID of the player
> * Returns the ID of the special action or `0` if the player is not connected


#### AntiCheatGetLastSpecialAction(playerid)

> Use to get the ID of the previous special action of a player
> * `playerid` - The ID of the player
> * Returns the ID of the previous special action or `0` if the player is not connected


#### AntiCheatGetLastShotWeapon(playerid)

> Use to get the ID of the last weapon from which a player shot
> * `playerid` - The ID of the player
> * Returns the ID of the last weapon or `-1` if the player is not connected


#### AntiCheatGetLastPickup(playerid)

> Use to get the ID of the last pickup which a player picked
> * `playerid` - The ID of the player
> * Returns the ID of the last picked up pickup or `-1` if the player is not connected


#### AntiCheatGetLastUpdateTime(playerid)

> Use to get a player's last update timestamp
> * `playerid` - The ID of the player
> * Returns the timestamp of the last update or `0` if the player is not connected


#### AntiCheatGetLastReloadTime(playerid)

> Use to get a player's last (weapon) reload timestamp
> * `playerid` - The ID of the player
> * Returns the timestamp of the last reload or `0` if the player is not connected


#### AntiCheatGetLastEnteredVehTime(playerid)

> Use to get a player's last entering vehicle attempt timestamp
> * `playerid` - The ID of the player
> * Returns the timestamp of the last entering attempt or `0` if the player is not connected


#### AntiCheatGetLastShotTime(playerid)

> Use to get a player's last shot timestamp
> * `playerid` - The ID of the player
> * Returns the timestamp of the last shot or `0` if the player is not connected


#### AntiCheatGetLastSpawnTime(playerid)

> Use to get a player's last spawn timestamp
> * `playerid` - The ID of the player
> * Returns the timestamp of the last spawn or `0` if the player is not connected


#### AntiCheatIntEnterExitsIsEnabled(playerid)

> Use to check whether enter/exit markers in interiors are enabled/disabled for a player
> * `playerid` - The ID of the player
> * Returns `1 (true)` if enabled or `0 (false)` if disabled


#### AntiCheatStuntBonusIsEnabled(playerid)

> Use to check whether stunt bonus is enabled/disabled for a player
> * `playerid` - The ID of the player
> * Returns `1 (true)` if enabled or `0 (false)` if disabled


#### AntiCheatIsInModShop(playerid)

> Use to check whether a player is in ModShop or not
> * `playerid` - The ID of the player
> * Returns `1 (true)` if it is or `0 (false)` if it is not


#### AntiCheatIsFrozen(playerid)

> Use to check whether a player is frozen or not
> * `playerid` - The ID of the player
> * Returns `1 (true)` if frozen or `0 (false)` if not frozen


#### AntiCheatIsDead(playerid)

> Use to check whether a player is dead or not
> * `playerid` - The ID of the player
> * Returns `1 (true)` if dead or `0 (false)` if not dead


#### AntiCheatIsConnected(playerid)

> Use to check whether a player is on a server or not
> * `playerid` - The ID of the player
> * Returns `1 (true)` if it is or `0 (false)` if it is not



Added in v1.9.37:


#### public OnCheatWarning(playerid, ip_address[], type, code, code2, count)

> Called when triggers any warnings of one of the anti-cheats
> * `playerid` - ID of the suspected cheater
> * `ip_address[]` - IP-address of the suspected cheater
> * `type` - Type of cheating (when `0` it returns the ID, when `1` - IP)
> * `code` - Code (ID) of the anti-cheat
> * `code2` - Sub-code (ID) of the anti-cheat check
> * `count` - Count of warnings triggered on suspected cheater
> * This callback does not handle returns


#### public OnFloodWarning(playerid, publicid, count)

> Called when triggers any anti-flood warnings on one of the protected publics
> * `playerid` - ID of the suspected flooder
> * `publicid` - ID of the public that was called too quickly
> * `count` - Count of warnings triggered on suspected flooder
> * This callback does not handle returns


#### public OnNOPWarning(playerid, nopid, count)

> Called when triggers any NOP warnings on one of the protected functions
> * `playerid` - ID of the suspected cheater
> * `nopid` - ID of the NOP check
> * `count` - Count of warnings triggered on suspected cheater
> * This callback does not handle returns


#### AntiCheatKickWithDesync(playerid, code)

> Use to kick with desync a particular player by the anticheat
> * `playerid` - ID of the player who will be kicked with desync for the delay time
> * `code` - ID of the anti-cheat (with some codes the player's vehicle will be resynced after his disconnection)
> * Returns `1` if the function executed successfully, `0` if the player is not connected or `-1` if the player has already been kicked


#### AntiCheatIsKickedWithDesync(playerid)

> Use to check whether a player is (being) kicked or not
> * `playerid` - The ID of the player
> * Returns `1` for kick onfoot, `2` for kick in a vehicle (driver), `3` if player is already disconnected or `0` if he isn't kicked



Added in v1.9.40:


#### AntiCheatGetSpawnPos(playerid, &Float:x, &Float:y, &Float:z)

> Use to get a player's spawn position
> * `playerid` - The ID of the player
> * `&Float:x` - The variable for storage the x coordinate, passed by reference
> * `&Float:y` - The variable for storage the y coordinate, passed by reference
> * `&Float:z` - The variable for storage the z coordinate, passed by reference
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the player is not connected



Added in v1.9.41:


#### EnableAntiNOP(nopcode, enable)

> Use to enable/disable one of the anti-NOPs
> * `nopcode` - ID of the anti-NOP
> * `enable` - `1` to enable/`0` to disable
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the `nopcode` parameter contains an invalid ID of the anti-NOP


#### EnableAntiNOPForPlayer(playerid, nopcode, enable)

> Use to enable/disable one of the anti-NOPs for a particular player
> * `playerid` - ID of the player who needs to enable/disable the anti-NOP
> * `nopcode` - ID of the anti-NOP
> * `enable` - `1` to enable/`0` to disable
> * Returns `1` if the function executed successfully, `0` if the player is not connected or `-1` if the `nopcode` parameter contains an invalid ID of the anti-NOP


#### IsAntiNOPEnabled(nopcode)

> Use to check whether one of the anti-NOPs is enabled/disabled
> * `nopcode` - ID of the anti-NOP
> * Return `1 (true)` if enabled or `0 (false)` if disabled


#### IsAntiNOPEnabledForPlayer(playerid, nopcode)

> Use to check whether one of the anti-NOPs is enabled/disabled for a particular player
> * `playerid` - ID of the player to be checked whether the anti-NOP enabled/disabled for him
> * `nopcode` - ID of the anti-NOP
> * Return `1 (true)` if enabled or `0 (false)` if disabled



Added in v1.9.42:


#### AntiCheatGetVehicleDriver(vehicleid)

> Use to get the ID of the driver of the vehicle
> * `vehicleid` - The ID of the vehicle
> * Returns the ID of the driver or `INVALID_PLAYER_ID` if the vehicle does not exist


#### AntiCheatGetVehicleInterior(vehicleid)

> Use to get the ID of the interior of the vehicle
> * `vehicleid` - The ID of the vehicle
> * Returns the ID of the interior or `0` if the vehicle does not exist


#### AntiCheatGetVehiclePaintjob(vehicleid)

> Use to get the ID of the paintjob of the vehicle
> * `vehicleid` - The ID of the vehicle
> * Returns the ID of the paintjob or `3` if the vehicle does not exist



Added in v1.9.43:


#### AntiCheatGetVehiclePos(vehicleid, &Float:x, &Float:y, &Float:z)

> Use to get a vehicle position
> * `vehicleid` - The ID of the vehicle
> * `&Float:x` - The variable for storage the x coordinate, passed by reference
> * `&Float:y` - The variable for storage the y coordinate, passed by reference
> * `&Float:z` - The variable for storage the z coordinate, passed by reference
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the vehicle does not exist


#### AntiCheatGetVehicleZAngle(vehicleid, &Float:z_angle)

> Use to get the vehicle z rotation
> * `vehicleid` - The ID of the vehicle
> * `&Float:z_angle` - The variable for storage the z rotation, passed by reference
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the vehicle does not exist


#### AntiCheatGetVehicleSpawnPos(vehicleid, &Float:x, &Float:y, &Float:z)

> Use to get a vehicle spawn position
> * `vehicleid` - The ID of the vehicle
> * `&Float:x` - The variable for storage the x coordinate, passed by reference
> * `&Float:y` - The variable for storage the y coordinate, passed by reference
> * `&Float:z` - The variable for storage the z coordinate, passed by reference
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the vehicle does not exist


#### AntiCheatGetVehicleSpawnZAngle(vehicleid, &Float:z_angle)

> Use to get the vehicle spawn z rotation
> * `vehicleid` - The ID of the vehicle
> * `&Float:z_angle` - The variable for storage the z rotation, passed by reference
> * Returns `1 (true)` if the function executed successfully or `0 (false)` if the vehicle does not exist



Added in v1.9.46:


#### AntiCheatGetInterior(playerid)

> Use to get the ID of the interior in which a player is
> * `playerid` - The ID of the player
> * Returns the ID of the interior or `0` if the player is not connected

# Multilingual:
The script can be configured in any of the available languages. To do it, just download the desired localization, save it in a directory with the main include *(nex_ac.inc)* and recompile your script.

* *.lang* files can be opened even in default notepad and easily edited

##### *It is also recommended to check for using any other anticheats in order to avoid conflicts with them.*

# Installation:
1. Download version of the anticheat which compatible with the version of your server
2. Download the language file *(.lang)* in your preferred language
3. Copy both files to a folder *"/pawno/include"* which is located in a folder with the server
4. In gamemode and all filterscripts, after *#include "a_samp"* write the following: *#include "nex-ac"*  
***Warning! If you use Streamer Plugin by Incognito, foreach, sscanf or Pawn.RakNet, include it before nex-ac!***  
*Also keep in mind that filterscript must have "#define FILTERSCRIPT" before including the anticheat*
5. Compile the modified scripts

*Do you get an error when you compiling this anticheat with YSI? Check out [some tips](http://forum.sa-mp.com/showpost.php?p=3556462&postcount=202)*

## Thanks:
* Magic_York, Roberto_York, TheHero, Nike_33, Vitalik_Gonsor, Mix_Rargard, Unisheld, f0Re3t - testing
* ZiGGi, Urukhay, Yashas, theYiin, RaefaldhiAmartya, PatchwerkQWER, kvann, rt-2 - advices on the code
* Carper - German translation
* Jstylezzz - Dutch translation
* J4Rr3x, Sasino97 - Italian translation
* Alex Westbrook, JustBored - Spanish translation
* lashona, ArthourP, DAKYSKYE - Georgian translation
* wampiros6 - Polish translation
* DeitY, Dragony92 - Serbian translation
* NicK_ - PT/BR translation
* KyleSmith, infin1tyy - Improved English translation
* M4D - Persian (Farsi) Translation
* Valera_Kovshikov - Ukrainian translation
* RaefaldhiAmartya - Indonesian translation
* vannesenn - Croatian translation
* j3rry, vic1997 - French translation
* zaibaslr2 - Lithuanian translation
* UnforgiveNNN - Romanian translation
* Pedro. - Hungarian translation
* Ben_Lovejoy - Finnish translation
* Rengar - Latvian translation
* bgedition - Bulgarian translation
* Jensenn - Turkish translation
* Sanady - Slovak translation
* Grig - Armenian translation
* SooBad - Czech translation
* OldPawn - Estonian translation
* Negativ_Tm - Turkmen translation
* Trung.Tin - Vietnamese translation
* willbedie - Albanian translation
* aktah - Thai translation
* Michael.Richmond - Moldavian translation
* NemanjaMAX - Bosnian translation

This script also contains materials from third-party open source projects.

P.s. I developed this anticheat for about a year and spent on it a lot of effort and time. I really hope that it will be useful to you.

Enjoy!
