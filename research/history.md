# ThreeWave CTF Release History

Reconstructed history of ThreeWaveCTF by Dave Kirsch aka "Zoid".

## USENET Announcement September 1996

Zoid shared a comment about working on server-side Quake mod/s in a Linux Quake related discussion on September 3rd 1996:

```text
Dave Kirsch
3 Sept 1996

In article <50f2p6$d...@wapping.ecs.soton.ac.uk>,
Nicholas Lamb <njl...@ecs.soton.ac.uk> wrote:

>dar...@mail.nova.net.au (Kevin Littlejohn) writes:
>
>Recipe for Linux registered Quake by <ruth>
>
>Ingredients: DOS registered Quake, Linux Shareware Quake 1.01
>
>* Mount your DOS partition from Linux (as msdos or as vfat)
>* Softlink pak0.pak and pak1.pak from the Linux id1 directory to
> the real pak files on the DOS partition (copying them wastes space
> unless you are going to delete the DOS version of Quake)
Actually, even if it wastes space, you will notice a significant speed
improvement (in load and access time) by copying the pak files onto the
Linux e2 file system, since its access time is much, much better than a
mounted MSDOS FAT file system.

>>Anyone know if I can make mods to my 1.01 linux version? Or am I
>>doomed to play the same old same old?
>
>Now that you have paid ID for a registered Quake CD you are entitled to
>changed everything, and you can. Instructions are as for the DOS or
>Windoze versions of the game (except we use TCP/IP all the time)

Yup. With my server at quake.threewave.com (204.191.124.66), I have
~/quake/threewave/progs.dat with my custom mods, and just do:
./xquake -decidated 16 -game threewave
in the Quake directory to load it up. What's cool, is Quake reloads the
progs.dat on level change, so when I'm editing the Quake C files, I just
copy a new progs.dat into the ~/quake/threewave directory and on the next
level change, my modifications are integrated.

I have two Linux machines and one Win95. Win95 I use for a 'console'
(running a X server) and the major server running on one Linux machine, a
Pentium 60. I also have a 486-33 running Linux that I use for hacking on
Quake-C in order to test out new Quake-C stuff. Surprisingly, a 486-33
with 8MB actually runs Quake (as a server) pretty well! Level loading is
quite slow, but once its loaded, it can handle eight clients no problem.
```
--- [rec.games.computer.quake.servers](https://groups.google.com/g/rec.games.computer.quake.servers/c/xlbzgXg3dyg/m/VooGYhC5fAEJ)

Later that month, Zoid posted a message announcing his CTF server mod to `rec.games.computer.quake.announce` on September 18th 1996:


```text
Dave Kirsch
18 Sept 1996

Quake.ThreeWave.COM is a Linux based Quake Server in Ottawa, ON. The
home page for the server is http://quake.threewave.com/
The server address is 204.191.24.66
The server features several modifications to the standard Quake deathmatch
server in the hopes of making the game more interesting and exciting. Note
that currently I'm working with my Capture the Flag modifications, so the
sever is running in team mode and some of the following changes are not
active. See http://quake.threewave.com for more information.

ThreeWave Server Changes

+------------+---------------------------------------------------------------+
| |The basic premise is: attack the enemy base, grab their flag |
| |then take it back to your base. In the variation I've written |
| |into Quake, you must touch your base flag when carrying the |
| |enemy flag in order to score. |
| |1. Two sections of the map are designated as base encampments. |
| |Currently only e1m4, The Grisly Grotto and e1m1, The Slipgate |
| |complex are available with the bases at the start and end of |
| |the level. |
| |2. When you join the game (or enter the level) you are assigned|
| |to a team and you are spawned at the base. If you die, you are |
| |not spawned at the base, but at one of the deathmatch start |
|Capture the |spots. This way, you don't kill a guy trying to get the flag at|
|Flag |the base and he comes back to life immediately there. |
| |3. The flags are based on the key models. If you pick up the |
| |enemy flag, you must touch your flag in order to win. Note that|
| |if you get back to your base, your flag might not be there if |
| |the other team has it! Get the rest of your team to go get your|
| |flag back! The player who touches his base flag when carrying |
| |the other team's gets 20 frags, and everyone on his team gets |
| |10 frags. Also, when you get a flag, you have that nice glow |
| |around you (such as when you get the quad damage) If you kill |
| |an opposing team player who has your flag, he drops it. If you |
| |touch your flag, it will teleport back to your base. |
+------------+---------------------------------------------------------------+
| |The next level is chosen randomly. The levels e1m7 (House of |
|Random Level|Chthon), e2m6 (The Dismal Oubliette), e3m4 (Satan's Dark |
|Selection |Delight) and end (Shub-Niggurath's Pit) removed since they |
| |are really suck for DM games, though e1m7 is a nice DM |
| |level, but causes massive lag for some reason. |
+------------+---------------------------------------------------------------+
| |Runes are spawned randomly, one of each with an unique |
|Rune |power. A player can only carry one rune at time and there |
|Artifacts |are only four in the level at once. You can get a rune by |
| |finding it, or by fragging the player who has it and picking |
| |it up after they drop it. |
+------------+---------------------------------------------------------------+
|MOTD |A Message Of The Day is printed upon connection to the |
| |server, or at the beginning of the next level. |
+------------+---------------------------------------------------------------+
| |Includes support for MultiSkin 1.1 but also fixes it so that |
| |corpses get the right skin and skins are presistant across |
| |levels. Also changed so that skins are not available in |
|Skins |teamplay, since you can't tell what color people are with |
| |many of the skins. |
| |IMPULSE 200 for next skin |
| |IMPULSE 201 for previous skin |
+------------+---------------------------------------------------------------+
|Suicide |A person can suicide four times, then can't suicide anymore. |
|Protection |They are not kicked from the server, but a told that they |
| |simply can't suicide anymore. |
+------------+---------------------------------------------------------------+
| |When telefragged, the person who was killed stays dead for |
| |three to nine seconds. This is needed to get rid of the |
|Telefrag |"frag snowball" effect one sees at the beginning of a new |
|Delay |level, when 16 players try to fit into five deathmatch |
| |spots. The telefrags would snowball and eventually crash the |
| |server. With this delay, its reduced so that it doesn't |
| |snowball. |
+------------+---------------------------------------------------------------+
| |This is really useful in for a Linux server, since I save |
|Server |the log files. Reports on why a client connects, how they |
|Logging |died, etc. This is still being fine tuned. Just because I'm |
| |not in the game playing doesn't mean I don't know what is |
| |going on! |
+------------+---------------------------------------------------------------+
| |From Ron Mercer's Teleweapon patch. The lightning gun |
| |discharge in water bug, where if you are near the water (but |
| |not in) you get fragged. Now only targets in the water will |
| |get damaged. Also, if you fire the lightning gun into the |
| |water while you are not in the water yourself, you will cook |
| |who ever is in the water. They'll receive two points of |
|Lightning |damage for each cell you fire into the water. |
|Gun Changes |Note that Ron Mercer's Teleweapon patch included the |
| |facility for making entities other than players to be able |
| |to go through teleporters (such as rockets, nails, etc.) |
| |This is a neat idea and had it installed when I first added |
| |his patch, but my server was locking up. Seemed to go into |
| |an endless loop. I've changed it back so that only players |
| |can teleport again and the server seems stable. |
+------------+---------------------------------------------------------------+
| |New weapon added. "Mike" <amic...@asu.alasu.edu>'s Morning |
| |Star, renamed to grappling hook. Changed to use existing |
| |models (vore ball for hook, spikes for the chain links). |
| |This weapon lets you hook the ceiling (or walls or whatever) |
| |and get pulled toward it (think of Batman's grapple in the |
|Grappling |movies). You can also hang from the ceiling and snipe at |
|Hook |people. Don't worry, its doesn't make camping any more |
| |effective, as a rocket at the ceiling usually deals with |
| |anyone handing around. |
| |IMPULSE 22 to select hook or |
| |Select Axe Twice to select the hook as well. |
+------------+---------------------------------------------------------------+
| |Removed redundant messages such as "You got the shells" or |
|Message |"You got the armor." This was just cluttering up the message |
|Reduction |stream and isn't needed since pickups are already signified |
| |by a flash and an audio cue. Makes it so that the messages |
| |displayed at the top of the screen are much more meaningful. |
+------------+---------------------------------------------------------------+

The server is welcome for anyone to play. Come on down and check out
the new Capture the Flag mods I've installed! They really give a meaning
to organized teamplay.

Special thanks to id software for making Quake, and for making Quake-C, then
releasing all the source for it! I can't believe what I'm allowed to do for
the piddly $50 I spent on my registered Quake.

--
/// Dave 'Zoid' Kirsch __ | http://mindlink.net/zoid
dave....@istar.ca \/ | R&D Dept. -- iSTAR Internet Inc.
```

-- [rec.games.computer.quake.announce](https://groups.google.com/g/rec.games.computer.quake.announce/c/ODar_i97-SA/m/hVYXeG5jVmQJ)


## BluesNews Announcement October 1996

Zoid sent an email to BluesNews that was published on October 02 1996.

> Capture the Flag\
> I got an email from Dave Kirsch who wanted to pass along some info about his server running his capture the flag mod (I'm just passing along the entire thing, I haven't had a chance to check it out from the wilds of the south).
>
>> So, I was up this morning at six AM (don't ask) and I ran QSpy. I took a look at about 300 servers. To my surprise, almost all of them were empty, *except* mine and a friend of mine who runs my patches. They were both half full.
>>
>> What is this I thought?
>>
>> Capture the Flag.
>>
>> If you've never played this, you don't know what you're missing. My players whine and moan that they can't play regular deathmatch anymore, because it seems pointless. They say there's nothing greater than the adrenalin you get when you grab the enemy flag by penetrating their base and you're high-tailing it out of there as fast as you can with two or three guys chasing you as you try to get back to your base in order to successfully capture. If you're lucky (and hopefully have some teammates to cover you), you'll get back to base and score! But wait, you got back, and your flag isn't there, the other team has it! One of your teammates is going to have the frag the enemy player with the flag and return it so you can score.
>>
>> Regular team play is crap. It essentially comes down to "don't shoot the guys the same color as you." It also has no real location based fighting--its just random roaming.
>>
>> My server (and my friends) are packed pratically 24hrs a day. I can't even get on my own server most of the time! :)
>>
>> Check out my server home page at http://quake.threewave.com/. I'm hoping you can mention it in your news updates. I'll be releasing the source to the Capture the Flag patch in the next few days.
>>
>> My server is at quake.threewave.com (204.191.124.66) and my friend Bjorn's server is at quake.mindlink.net (204.174.17.22).

-- [https://www.bluesnews.com/archives/sept96-5.html](https://www.bluesnews.com/archives/sept96-5.html)


## v2.01

A public release of version 2.01 of the mod was announced on BluesNews on October 4h 1996:

> Capture the Flag Patch Available\
> Rarely, if ever, have I gotten as strong a response to an article here in the rag as the reaction to the story about Dave Kirsch's capture the flag server. Obviously many of you are really enjoying playing this version of the game. Good news! As promised, the patch is now available here. To install the patch you need a utility to unpack the pak0.pak and pak1.pak files as well as qbsp to modify the entity lists. Full documentation is with the patch.

-- [https://www.bluesnews.com/archives/sept96-5.html](https://www.bluesnews.com/archives/sept96-5.html)

Which linked to:

* http://quake.threewave.com/3wave201.zip

**A copy of this release has not been acquired at the time of writing.**

There were prior versions of the mod, although this may be the first public release (based on the language used in the BluesNews update).

## v2.1

Version 2.1 of the mod was announced on BluesNews on October 6th 1996:

> Capture The Flag 2.1\
> Newly released Capture The Flag 2.1 is Quake 1.06 compatible and contains a few tweaks (e.g., grappling teammmates) and minor bug fixes.
>
> Also if you are running a public server with Capture the Flag on it, or know of one, please send the server's address to patch author Dave 'Zoid' Kirsch, so he can put a list of CTF servers up on the home page.

-- [https://www.bluesnews.com/archives/oct96-1.html](https://www.bluesnews.com/archives/oct96-1.html)

Which linked to:

* http://quake.threewave.com/3wave21.zip
* http://quake.threewave.com/capture.html

Some historical locations for this file include:

* [Monster Media Number 17 (Monster Media)(January 1997)](https://archive.org/details/Monster_Media_Number_17_Monster_Media_January_1997)
* [DP Tool Club CD ASC #03, 08, 31-34](https://archive.org/details/dptoolclub-cdasc)

The content of the archive is as follows:

```text
-rw-rw-r--  0 0      0         133 27 Sep  1996 AUTOEXEC.CFG
-rw-rw-r--  0 0      0        7963  2 Oct  1996 CONFIG.CFG
-rw-rw-r--  0 0      0        1765  4 Oct  1996 CAPTURE.TXT
-rw-rw-r--  0 0      0      468428  6 Oct  1996 PROGS.DAT
-rw-rw-r--  0 0      0       17503  6 Oct  1996 README.TXT
-rw-rw-r--  0 0      0      104360  6 Oct  1996 CAPTURE.DIF
-rw-rw-r--  0 0      0          29 27 Sep  1996 FILE_ID.DIZ
drwxrwxr-x  0 0      0           0  3 Jan  1997 SRC/
drwxrwxr-x  0 0      0           0  3 Jan  1997 MAPS/
-rw-rw-r--  0 0      0      468428  6 Oct  1996 SRC/PROGS.DAT
-rw-rw-r--  0 0      0        9904  6 Oct  1996 SRC/DEMON.QC
-rw-rw-r--  0 0      0       14657  6 Oct  1996 SRC/OGRE.QC
-rw-rw-r--  0 0      0         222  6 Oct  1996 SRC/JCTEST.QC
-rw-rw-r--  0 0      0       12411  6 Oct  1996 SRC/BOSS.QC
-rw-rw-r--  0 0      0        7880  6 Oct  1996 SRC/SHALRATH.QC
-rw-rw-r--  0 0      0       15088  6 Oct  1996 SRC/MISC.QC
-rw-rw-r--  0 0      0        9542  6 Oct  1996 SRC/DOG.QC
-rw-rw-r--  0 0      0       12725  6 Oct  1996 SRC/SHAMBLER.QC
-rw-rw-r--  0 0      0        7208  6 Oct  1996 SRC/FIGHT.QC
-rw-rw-r--  0 0      0         141  6 Oct  1996 SRC/FLAG.QC
-rw-rw-r--  0 0      0        2910  6 Oct  1996 SRC/BUTTONS.QC
-rw-rw-r--  0 0      0       20108  6 Oct  1996 SRC/ZOMBIE.QC
-rw-rw-r--  0 0      0        7116  6 Oct  1996 SRC/TARBABY.QC
-rw-rw-r--  0 0      0        9537  6 Oct  1996 SRC/OLDONE.QC
-rw-rw-r--  0 0      0        9684  6 Oct  1996 SRC/KNIGHT.QC
-rw-rw-r--  0 0      0        7747  6 Oct  1996 SRC/FISH.QC
-rw-rw-r--  0 0      0       11498  6 Oct  1996 SRC/WORLD.QC
-rw-rw-r--  0 0      0       18781  6 Oct  1996 SRC/PLAYER.QC
-rw-rw-r--  0 0      0       29104  6 Oct  1996 SRC/TEAMPLAY.QC
-rw-rw-r--  0 0      0        7117  6 Oct  1996 SRC/COMBAT.QC
-rw-rw-r--  0 0      0       35206  6 Oct  1996 SRC/ITEMS.QC
-rw-rw-r--  0 0      0         469  6 Oct  1996 SRC/PROGS.SRC
-rw-rw-r--  0 0      0       32052  6 Oct  1996 SRC/WEAPONS.QC
-rw-rw-r--  0 0      0       47532  6 Oct  1996 SRC/CLIENT.QC
-rw-rw-r--  0 0      0        2455  6 Oct  1996 SRC/PROGDEFS.H
-rw-rw-r--  0 0      0        7994  6 Oct  1996 SRC/FILES.DAT
-rw-rw-r--  0 0      0         450  6 Oct  1996 SRC/SPRITES.QC
-rw-rw-r--  0 0      0       10727  6 Oct  1996 SRC/ENFORCER.QC
-rw-rw-r--  0 0      0       14521  6 Oct  1996 SRC/AI.QC
-rw-rw-r--  0 0      0        9825  6 Oct  1996 SRC/SOLDIER.QC
-rw-rw-r--  0 0      0       10663  6 Oct  1996 SRC/WIZARD.QC
-rw-rw-r--  0 0      0       18298  6 Oct  1996 SRC/HKNIGHT.QC
-rw-rw-r--  0 0      0        8996  6 Oct  1996 SRC/MODELS.QC
-rw-rw-r--  0 0      0        6062  6 Oct  1996 SRC/SUBS.QC
-rw-rw-r--  0 0      0        4798  6 Oct  1996 SRC/MONSTERS.QC
-rw-rw-r--  0 0      0        1697  6 Oct  1996 SRC/AMTEST.QC
-rw-rw-r--  0 0      0        7693  6 Oct  1996 SRC/PLATS.QC
-rw-rw-r--  0 0      0       17138  6 Oct  1996 SRC/DOORS.QC
-rw-rw-r--  0 0      0        5794  6 Oct  1996 SRC/HOOK.QC
-rw-rw-r--  0 0      0       18457  6 Oct  1996 SRC/DEFS.QC
-rw-rw-r--  0 0      0        6116  6 Oct  1996 SRC/FLAME.QC
-rw-rw-r--  0 0      0       14259  6 Oct  1996 SRC/TRIGGERS.QC
-rw-rw-r--  0 0      0       30836 17 Sep  1996 MAPS/E1M1.ENT
-rw-rw-r--  0 0      0       44058 21 Sep  1996 MAPS/E1M2.ENT
-rw-rw-r--  0 0      0       38838 23 Sep  1996 MAPS/E1M6.ENT
-rw-rw-r--  0 0      0       44142 23 Sep  1996 MAPS/E1M5.ENT
-rw-rw-r--  0 0      0       37223 25 Sep  1996 MAPS/E1M8.ENT
-rw-rw-r--  0 0      0       46337 25 Sep  1996 MAPS/E1M4.ENT
-rw-rw-r--  0 0      0       48571 28 Sep  1996 MAPS/E1M3.ENT
-rw-rw-r--  0 0      0       35022 29 Sep  1996 MAPS/E2M1.ENT
-rw-rw-r--  0 0      0       28146 29 Sep  1996 MAPS/E2M2.ENT
-rw-rw-r--  0 0      0       39829 29 Sep  1996 MAPS/E2M3.ENT
-rw-rw-r--  0 0      0          52  4 Oct  1996 MAPS/DOBSP.SH
-rw-rw-r--  0 0      0         431  6 Oct  1996 MAPS/DOBSP.BAT
```

The header from the readme file is as follows:


```text
Title    : Threewave Capture
Filename : 3wave201.zip
Version  : 2.10
Date     : 96-09-13
Author   : Dave 'Zoid' Kirsch
Email    : zoid@mindlink.net
Credits  : John Spickes aka Guru <jspickes@eng.umd.edu> for JTEAM
           Aegis - moral support and general overexcited Quake guy
           Beowulf - my cat who keeps getting me fragged when he jumps on my
                     keyboard or starts chasing my mouse
           "Mike" <amichael@asu.alasu.edu> for Morning Star (Hook)
           Tom "Bjorn" Klok <tomtom@mindlink.net> for original ideas
		       such as the runes and capture games, various suggestions
    		   and bug fixes.  Check his server at quake.mindlink.net,
    		   204.174.17.22
```

-- README.TXT


## v2.2

Version 2.2 of the mod was announced on BluesNews on October 8th 1996:

> New Capture the Flag\
> Dave 'Zoid' Kirsch has released version 2.2 of his insanely popular teamplay patch on his server's page. Read what's new. Dave has also opened another server running the Capture the Flag patch at quake2.threewave.com (204.191.124.67) because his original CTF server, quake.threewave.com (204.191.124.66) is always full.

-- [https://www.bluesnews.com/archives/sept96-5.html](https://www.bluesnews.com/archives/sept96-5.html)

Which linked to:

* http://quake.threewave.com/3wave22.zip
* http://quake.threewave.com/
* https://www.bluesnews.com/archives/ctf-22.txt

The release was also announced on Redwoods:

> Threewave has a v2.2 of the Capture the Flag server mod. Thanks to Scary's for that tidbit.

-- [http://redwood.gatsbyhouse.com/quake/1096.html](https://web.archive.org/web/19970327200948/http://redwood.gatsbyhouse.com/quake/1096.html) (archived)

**A copy of this release has not been acquired at the time of writing.**


## v2.3

Version 2.3 of the mod was announced on BluesNews on October 14th 1996:

> CTF 2.3\
> The latest and greatest. Download it from bluesnews.com, here's the text file.

-- [https://www.bluesnews.com/archives/oct96-2.html](https://www.bluesnews.com/archives/oct96-2.html)

Which links to:

* ftp://bluesnews.com/pub/quakec/teamplay/3wave23.zip
* https://www.bluesnews.com/archives/chg23.txt

It was announced on Redwood's on October 15th:

> There is a new Capture the Flag 2.3.

-- [http://redwood.gatsbyhouse.com/quake/1096.html](https://web.archive.org/web/19970327200948/http://redwood.gatsbyhouse.com/quake/1096.html) (archived)

Some historical locations for the file include:

* [The Arsenal Files Collection #8 (Arsenal Computer) (1996)](https://archive.org/details/The_Arsenal_Files_Collection_8_Arsenal_Computer_1996)
* [Shareware Extravaganza 8 (Most Significant Bits)](https://archive.org/details/Shareware_Extravaganza_8_Most_Significant_Bits)
* [Cream of the Crop 23](https://archive.org/details/Cream_of_the_Crop_23)
* [Quake 'em](https://archive.org/details/cdrom-quake-em)
* [The Toolkit for Quake (2nd Edition) Archive](https://www.quaddicted.com/files/commercial/)

The contents of the archive is as follows:

```text
-rw-------  0 0      0      110231 14 Oct  1996 capture.dif
-rw-------  0 0      0        1765  4 Oct  1996 capture.txt
-rw-------  0 0      0       22399 14 Oct  1996 readme.txt
-rw-------  0 0      0         126 14 Oct  1996 autoexec.cfg
-rw-------  0 0      0        1619 12 Oct  1996 config.cfg
-rw-------  0 0      0      469744 14 Oct  1996 progs.dat
-rw-rw-r--  0 0      0       30836 17 Sep  1996 maps/e1m1.ent
-rw-rw-r--  0 0      0       44058 21 Sep  1996 maps/e1m2.ent
-rw-rw-r--  0 0      0       48571 28 Sep  1996 maps/e1m3.ent
-rw-rw-r--  0 0      0       46337 25 Sep  1996 maps/e1m4.ent
-rw-rw-r--  0 0      0       44142 23 Sep  1996 maps/e1m5.ent
-rw-rw-r--  0 0      0       38838 23 Sep  1996 maps/e1m6.ent
-rw-r--r--  0 0      0       37223 25 Sep  1996 maps/e1m8.ent
-rw-rw-r--  0 0      0       35022 29 Sep  1996 maps/e2m1.ent
-rw-rw-r--  0 0      0       28163  6 Oct  1996 maps/e2m2.ent
-rw-rw-r--  0 0      0       39829 29 Sep  1996 maps/e2m3.ent
-rw-rw-r--  0 0      0       45578  8 Oct  1996 maps/e2m5.ent
-rw-rw-r--  0 0      0       42672  7 Oct  1996 maps/e4m3.ent
-rw-------  0 0      0         465  8 Oct  1996 maps/dobsp.bat
-rwxr-xr-x  0 0      0          52  4 Oct  1996 maps/dobsp.sh
drwx------  0 0      0           0 14 Oct  1996 src/
-rw-------  0 0      0       14521  6 Oct  1996 src/ai.qc
-rw-------  0 0      0        1697  6 Oct  1996 src/amtest.qc
-rw-------  0 0      0       12411  6 Oct  1996 src/boss.qc
-rw-------  0 0      0        2910  6 Oct  1996 src/buttons.qc
-rw-------  0 0      0       46562 14 Oct  1996 src/client.qc
-rw-------  0 0      0        7117  9 Oct  1996 src/combat.qc
-rw-------  0 0      0       18457  6 Oct  1996 src/defs.qc
-rw-------  0 0      0        9904  6 Oct  1996 src/demon.qc
-rw-------  0 0      0        9542  6 Oct  1996 src/dog.qc
-rw-------  0 0      0       17138  6 Oct  1996 src/doors.qc
-rw-------  0 0      0       10727  6 Oct  1996 src/enforcer.qc
-rw-------  0 0      0        7208  6 Oct  1996 src/fight.qc
-rw-------  0 0      0        7747  6 Oct  1996 src/fish.qc
-rw-------  0 0      0         141  6 Oct  1996 src/flag.qc
-rw-------  0 0      0       18298  6 Oct  1996 src/hknight.qc
-rw-------  0 0      0       35887 14 Oct  1996 src/items.qc
-rw-------  0 0      0         222  6 Oct  1996 src/jctest.qc
-rw-------  0 0      0        9684  6 Oct  1996 src/knight.qc
-rw-------  0 0      0       15088  6 Oct  1996 src/misc.qc
-rw-------  0 0      0        8996  6 Oct  1996 src/models.qc
-rw-------  0 0      0        4798  6 Oct  1996 src/monsters.qc
-rw-------  0 0      0       14657  6 Oct  1996 src/ogre.qc
-rw-------  0 0      0        9537  6 Oct  1996 src/oldone.qc
-rw-------  0 0      0        7693  6 Oct  1996 src/plats.qc
-rw-------  0 0      0       18781  6 Oct  1996 src/player.qc
-rw-------  0 0      0         506  7 Oct  1996 src/progs.src
-rw-------  0 0      0        7880  6 Oct  1996 src/shalrath.qc
-rw-------  0 0      0       12725  6 Oct  1996 src/shambler.qc
-rw-------  0 0      0        9825  6 Oct  1996 src/soldier.qc
-rw-------  0 0      0         450  6 Oct  1996 src/sprites.qc
-rw-------  0 0      0        6062  6 Oct  1996 src/subs.qc
-rw-------  0 0      0        7116  6 Oct  1996 src/tarbaby.qc
-rw-------  0 0      0       14259  6 Oct  1996 src/triggers.qc
-rw-------  0 0      0       32016  9 Oct  1996 src/weapons.qc
-rw-------  0 0      0       10663  6 Oct  1996 src/wizard.qc
-rw-------  0 0      0       11558 12 Oct  1996 src/world.qc
-rw-------  0 0      0       20108  6 Oct  1996 src/zombie.qc
-rw-------  0 0      0        2455 14 Oct  1996 src/progdefs.h
-rw-------  0 0      0      469744 14 Oct  1996 src/progs.dat
-rw-------  0 0      0        1561  7 Oct  1996 src/telefrag.qc
-rw-------  0 0      0         631 14 Oct  1996 src/charset.txt
-rw-------  0 0      0        7994 14 Oct  1996 src/files.dat
-rw-------  0 0      0        6116  6 Oct  1996 src/flame.qc
-rw-------  0 0      0        6024 12 Oct  1996 src/hook.qc
-rw-------  0 0      0       30661 14 Oct  1996 src/teamplay.qc
```

The head of the readme is as follows:


```text
Title    : Threewave Capture
Filename : 3wave23.zip
Version  : 2.30
Date     : 96-10-14
Author   : Dave 'Zoid' Kirsch
Email    : zoid@mindlink.net
Credits  : John Spickes aka Guru <jspickes@eng.umd.edu> for JTEAM
           Aegis - moral support and general overexcited Quake guy
           Beowulf - my cat who keeps getting me fragged when he jumps on my
                     keyboard or starts chasing my mouse
           "Mike" <amichael@asu.alasu.edu> for Morning Star (Hook)
           Tom "Bjorn" Klok <tomtom@mindlink.net> for original ideas
		       such as the runes and capture games, various suggestions
    		   and bug fixes.  Check his server at quake.mindlink.net,
    		   204.174.17.22
```

-- readme.txt


## v2.5

Version 2.5 of the mod was announced on BluesNews on November 6th 1996:

> New Capture the Flag\
> Version 2.5 of Dave "Zoid" Kirsch's crime-fighting Capture the Flag patch, has been released. Here is the new version (this is a server side patch, you don't need to download it to play), here's what's new, and here is what Zoid has to say:
>
>> This is not the release of the custom stuff I'm working on. It's the last release (hoping there's no bugs) of the source before then. The custom stuff should be ready sometime next week. This should hold you over until then. :)
>>
>> Server operators should upgrade to 2.5 as it fixes ways of cheating and serveral bugs.
>>
>> Players, bug your server operator to upgrade now!
>>
>> Thanks for the overwhelming support, thank yous, and general enthusiasm for this patch. It's going to be even more exciting when I get the custom CTF release done.
>
> For tips and info on how to play, check out these quality strategy guides: Starks CTF Tips/News and Vader's Capture Guide, and of course the home of CTF, Threewave.

-- [https://www.bluesnews.com/archives/nov96-1.html](https://www.bluesnews.com/archives/nov96-1.html)

With links:

* ftp://bluesnews.com/pub/quakec/teamplay/3wave25.zip
* https://www.bluesnews.com/archives/ctf25new.txt

It was also announced on Redwoods:

> =November 6== 9:15p.m. CST\
> New version 2.5 of Capture the Flag is out. Download 3wave25.zip (408k). Here are the changes. Thanks to my buddy blue for emailing me about it.

-- [http://redwood.gatsbyhouse.com/quake/1196.html](https://web.archive.org/web/19970327200928/http://redwood.gatsbyhouse.com/quake/1196.html) (archived)

With links:

* http://quake.threewave.com/
* http://redwood.gatsbyhouse.com/quake/files/3wave25.zip
* http://quake.threewave.com/chg25.txt

This version was announced on November 7th on QuakeHole:

> CTF 2.5 7:35am - 11/07/96\
> Its out, go get it. This should be the last version before the full one with models / bsp's included. Zoid has added some new maps including DM3 and DM6. As well as a few E4 maps. Go to homecuts' homepage and download it, or just click here. You dont need this patch to ply on CTF servers, only if you want to run your own server. Oh, um... Blue I think is the name the guy goes by, he emailed me about this, but Zoid got to me first. btw, I should be getting that Verite card via FedEx today.. Ill do a few benchmarks on my system before and after. Many of the posts Ive seen about this card are overlooking quite a few things. Ill try and give it a fair shake.

-- [http://www.quakehole.com/frames/oldnews.html](https://web.archive.org/web/19971210064427/http://www.quakehole.com/frames/oldnews.html) (archived)

With links:

* http://quake.threewave.com/
* http://quake.threewave.com/3wave25.zip

This release was also announced on Stomped:

> 11/07 - ThreeWave 2.5 Release
> (Update by Christian Antkow aka: Disruptor)
>
> Dave "Zoid" Kirsh sent me an e-mail stating that his Capture The Flag Quakeserver patch is out. It's available as 3wave25.zip off Threewave's Webpage.

> Improvements to 2.5 are;
	>
	> Remote Adminstration
	> Version number is now printed upon connect
	> Flamethrower removed.
	> New maps
	> Better logging
	> Significant changes to the internal handling of team colors
	> Proper messages for explaining why the losers suddenly gibbed when trying to change team colors.
	> Earth Rune
	> McBain's Previous Weapon Impulse
	> Hook velocity lowered to 800 from 1000
	> Capture the Flag Status report
> ... and a few more.

-- [http://www.stomped.com/whatsnew.html](https://web.archive.org/web/19961121230336/http://www.stomped.com/whatsnew.html) (archived)

With links:

* http://quake.threewave.com/3wave25.zip

Some historical locations for this release include:

* ftp://bluesnews.com/pub/quakec/teamplay/3wave25.zip
* ftp://ftp.canvasnet.com/quake/ctf/3wave25.zip
* http://quake.threewave.com/3wave25.zip
* http://redwood.gatsbyhouse.com/quake/files/3wave25.zip
* http://redwood.stomped.com/files/3wave25.zip
* http://www.gore.org/files/server/3wave25.zip

**A copy of this release has not been acquired at the time of writing.**


## v2.51

Version 2.51 of the mod was announced on BluesNews on November 7th 1996:

> New New CTF\
> The new release, Version 2.51 fixes a bug in 2.50 that occasionally caused a dropped flag to fall through the floor (oops). Couple more CTF sites that I should mention are Enders and Mantis Quake.

-- [https://www.bluesnews.com/archives/nov96-1.html](https://www.bluesnews.com/archives/nov96-1.html)

With links:

* ftp://bluesnews.com/pub/quakec/teamplay/3wave251.zip

This updated was announced on QuakeHole on November 8th:

> CTF 2.51 9:15am - 11/08/96\
> New version, (again) go get it.

-- [http://www.quakehole.com/frames/oldnews.html](https://web.archive.org/web/19971210064427/http://www.quakehole.com/frames/oldnews.html) (archived)

Some historical locations for this release include:

* ftp://bluesnews.com/pub/quakec/teamplay/3wave251.zip
* ftp://ftp.canvasnet.com/quake/ctf/3wave251.zip
* http://quake.threewave.com/3wave251.zip
* http://web.ukonline.co.uk/Members/jc.burton/3wave251.zip

Some additional locations include:

* [Cream of the Crop 23](https://archive.org/details/Cream_of_the_Crop_23)

The contents of the archive include:

```text
-rw-rw-r--  0 0      0      118496  7 Nov  1996 capture.dif
-rw-rw-r--  0 0      0        1765  4 Oct  1996 capture.txt
-rw-rw-r--  0 0      0       27893 18 Nov  1996 readme.txt
-rw-rw-r--  0 0      0         126  7 Nov  1996 autoexec.cfg
-rw-rw-r--  0 0      0        2451  3 Nov  1996 config.cfg
-rw-rw-r--  0 0      0      476816  7 Nov  1996 progs.dat
-rw-rw-r--  0 0      0       14410  1 Nov  1996 maps/dm3.ent
-rw-rw-r--  0 0      0       11745 23 Oct  1996 maps/dm6.ent
-rw-rw-r--  0 0      0       30836 17 Sep  1996 maps/e1m1.ent
-rw-rw-r--  0 0      0       44058 21 Sep  1996 maps/e1m2.ent
-rw-rw-r--  0 0      0       48571 28 Sep  1996 maps/e1m3.ent
-rw-rw-r--  0 0      0       46337 25 Sep  1996 maps/e1m4.ent
-rw-rw-r--  0 0      0       44142 23 Sep  1996 maps/e1m5.ent
-rw-rw-r--  0 0      0       38838 23 Sep  1996 maps/e1m6.ent
-rw-rw-r--  0 0      0       36972 27 Oct  1996 maps/e1m8.ent
-rw-rw-r--  0 0      0       35022 29 Sep  1996 maps/e2m1.ent
-rw-rw-r--  0 0      0       28163  6 Oct  1996 maps/e2m2.ent
-rw-rw-r--  0 0      0       39829 29 Sep  1996 maps/e2m3.ent
-rw-rw-r--  0 0      0       45578  8 Oct  1996 maps/e2m5.ent
-rw-rw-r--  0 0      0       42672  7 Oct  1996 maps/e4m3.ent
-rw-rw-r--  0 0      0       46326 21 Oct  1996 maps/e4m4.ent
-rw-rw-r--  0 0      0       48880 18 Oct  1996 maps/e4m5.ent
-rw-rw-r--  0 0      0       43154 19 Oct  1996 maps/e4m6.ent
-rw-rw-r--  0 0      0         106 19 Oct  1996 maps/dobsp.bat
-rw-rw-r--  0 0      0          52  4 Oct  1996 maps/dobsp.sh
drwxrwxr-x  0 0      0           0  7 Nov  1996 src/
-rw-rw-r--  0 0      0       14521  6 Oct  1996 src/ai.qc
-rw-rw-r--  0 0      0        1697  6 Oct  1996 src/amtest.qc
-rw-rw-r--  0 0      0       12411  6 Oct  1996 src/boss.qc
-rw-rw-r--  0 0      0        2910  6 Oct  1996 src/buttons.qc
-rw-rw-r--  0 0      0       46144  1 Nov  1996 src/client.qc
-rw-rw-r--  0 0      0        7098  6 Nov  1996 src/combat.qc
-rw-rw-r--  0 0      0       18439  1 Nov  1996 src/defs.qc
-rw-rw-r--  0 0      0        9904  6 Oct  1996 src/demon.qc
-rw-rw-r--  0 0      0        9542  6 Oct  1996 src/dog.qc
-rw-rw-r--  0 0      0       17138  6 Oct  1996 src/doors.qc
-rw-rw-r--  0 0      0       10727  6 Oct  1996 src/enforcer.qc
-rw-rw-r--  0 0      0        7208  6 Oct  1996 src/fight.qc
-rw-rw-r--  0 0      0        7747  6 Oct  1996 src/fish.qc
-rw-rw-r--  0 0      0       18298  6 Oct  1996 src/hknight.qc
-rw-rw-r--  0 0      0       33942  4 Nov  1996 src/items.qc
-rw-rw-r--  0 0      0         222  6 Oct  1996 src/jctest.qc
-rw-rw-r--  0 0      0        9684  6 Oct  1996 src/knight.qc
-rw-rw-r--  0 0      0       15088  6 Oct  1996 src/misc.qc
-rw-rw-r--  0 0      0        8996  6 Oct  1996 src/models.qc
-rw-rw-r--  0 0      0        4798  6 Oct  1996 src/monsters.qc
-rw-rw-r--  0 0      0       14657  6 Oct  1996 src/ogre.qc
-rw-rw-r--  0 0      0        9537  6 Oct  1996 src/oldone.qc
-rw-rw-r--  0 0      0        7693  6 Oct  1996 src/plats.qc
-rw-rw-r--  0 0      0       18781 23 Oct  1996 src/player.qc
-rw-rw-r--  0 0      0         622  4 Nov  1996 src/progs.src
-rw-rw-r--  0 0      0        7880  6 Oct  1996 src/shalrath.qc
-rw-rw-r--  0 0      0       12725  6 Oct  1996 src/shambler.qc
-rw-rw-r--  0 0      0        9825  6 Oct  1996 src/soldier.qc
-rw-rw-r--  0 0      0         450  6 Oct  1996 src/sprites.qc
-rw-rw-r--  0 0      0        6062  6 Oct  1996 src/subs.qc
-rw-rw-r--  0 0      0        7116  6 Oct  1996 src/tarbaby.qc
-rw-rw-r--  0 0      0       14259 19 Oct  1996 src/triggers.qc
-rw-rw-r--  0 0      0       33618  4 Nov  1996 src/weapons.qc
-rw-rw-r--  0 0      0       10663  6 Oct  1996 src/wizard.qc
-rw-rw-r--  0 0      0       11729  5 Nov  1996 src/world.qc
-rw-rw-r--  0 0      0       20108  6 Oct  1996 src/zombie.qc
-rw-rw-r--  0 0      0        2455  7 Nov  1996 src/progdefs.h
-rw-rw-r--  0 0      0        1560 19 Oct  1996 src/telefrag.qc
-rw-rw-r--  0 0      0         655 31 Oct  1996 src/charset.txt
-rw-rw-r--  0 0      0        8185  7 Nov  1996 src/files.dat
-rw-rw-r--  0 0      0         650 29 Oct  1996 src/log.qc
-rw-rw-r--  0 0      0        6654  4 Nov  1996 src/hook.qc
-rw-rw-r--  0 0      0        5085 31 Oct  1996 src/admin.qc
-rw-rw-r--  0 0      0       33630  7 Nov  1996 src/teamplay.qc
-rw-rw-r--  0 0      0        3164  7 Nov  1996 src/flag.qc
```

The header from the readme is as follows:

```text
Title    : Threewave Capture
Filename : 3wave251.zip
Version  : 2.51
Date     : 96-11-06
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
Credits  : John Spickes aka Guru <jspickes@eng.umd.edu> for JTEAM
           Aegis - moral support and general overexcited Quake guy
           Beowulf - my cat who keeps getting me fragged when he jumps on my
                     keyboard or starts chasing my mouse
           "Mike" <amichael@asu.alasu.edu> for Morning Star (Hook)
           Tom "Bjorn" Klok <tomtom@mindlink.net> for original ideas
               such as the runes and capture games, various suggestions
               and bug fixes.  Check his server at quake.mindlink.net,
               204.174.17.22
           Kevin "Trojan[CampQ]" Hodgson <kevin@caseware.com> for modifing
               e4m5.
           Byron "Wonko" Long <byron@caseware.com> for adding Flag Status
               reports via impulse 23.
           Michael "McBain" Peckman for the PreviousWeaponCommand (impulse
			   69)
```

-- readme.txt

## Client v3.0 Beta 1

This version was announced on BluesNews on November 13th 1996:

> CTF Beta Test\
> Thank you to Dave "Zoid" Kirsch, originator of the now legendary Capture the Flag mod, sends word that the eagerly awaited update to CTF that includes the client-side patch will be issued for a beta test sceduled for this evening:
>
>> BETA TEST TONIGHT!
>>
>> I'll running a beta test of the new custom ThreeWave stuff tonight at 7PM EST on quake2.threewave.com. The new BETA pak will be available here for download. The beta test will be up for at least tonight and possibly tomorrow. The test includes the new skins, models, sounds and three new levels (McKinley Base, The Kiln and DySpHoRiA).
>>
>> The BETA pak file will be made available here shortly after 6PM EST. The server will be switched to using the new levels at 7PM. The download is expected to be a 1.5MB ZIP file.
>>
>> I'm looking forward to this people. Custom CTF will rock!

-- [https://www.bluesnews.com/archives/nov96-2.html](https://www.bluesnews.com/archives/nov96-2.html)

This was followed shortly by another annuncement on the same day:

> CTF Beta Here\
> Due to overwhelming demand, Dave "Zoid" Kirsch asked me to mirror the beta of the Client CTF patch (1.5MB). The server that's running the new version is quake2.threewave.com, so what are you waiting for...

-- [https://www.bluesnews.com/archives/nov96-2.html](https://www.bluesnews.com/archives/nov96-2.html)

With links:

* ftp://bluesnews.com/pub/quakec/teamplay/3wctfc3b.zip

This release was mentioned on QuakeHole:

> All kinds of stuff 8:15pm - 11/13/96\
> ...\
> CTF in beta tonight. (with custome maps)

-- [http://www.quakehole.com/frames/oldnews.html](https://web.archive.org/web/19971210064427/http://www.quakehole.com/frames/oldnews.html) (archived)

And mentioned on Redwoods:

> =November 13== 10:15a.m. CST\
> You can download the new Client CTF beta (1.5MB) with all the new goodies from this site. Go to Threewave for a list of servers running the new mods already. I got this stuff from blue's.

-- [http://redwood.gatsbyhouse.com/quake/1196.html](https://web.archive.org/web/19970327200928/http://redwood.gatsbyhouse.com/quake/1196.html) (archived)

With links:

* http://redwood.gatsbyhouse.com/files/3wctfc3b.zip

Some historical locations for this release include:

* ftp://bluesnews.com/pub/quakec/teamplay/3wctfc3b.zip
* ftp://ftp.canvasnet.com/incoming/quake/3wctfc3b.zip
* http://quake.threewave.com/3wctfc3b.zip
* http://redwood.gatsbyhouse.com/files/3wctfc3b.zip
* http://redwood.stomped.com/files/3wctfc3b.zip

**A copy of this release has not been acquired at the time of writing.**


## Client v3.0 Beta 2

A second beta was announced on November 15th on BluesNews:

> CTF Beta II\
> The second beta for the Custom Capture the Flag patch is scheduled to be released on Sunday evening. The beta client patch will be available on CTF's home, Threewave, and here. What's new from the first beta (from Threewave):
>
>> The Beta2 will include...
>>
>> An Entirely New Level by DaBug.
>> All New Bases and More Health in DySpHoRiA.
>> No Hallway Struts, and Better Secrets in McKinley Base.
>> No Rocket Launchers or Crossbeams in the Bases of the Kiln.
>> As well as Various Fixes and Modifications, custom tailored to enhance your enjoyment.

-- [https://www.bluesnews.com/archives/nov96-2.html](https://www.bluesnews.com/archives/nov96-2.html)

This release was postponed, mentioned on BluesNews on November 17th:

> Second CTF Beta Postponed\
> The second public beta of Capture the Flag 3, originally scheduled for tonight, has been delayed for one day. Stay tuned for further details. While I'm on the subject, welcome aboard to Blake Winton who will be taking over the webmaster chores over at CTF's home, Threewave, allowing Zoid to concentrate on the patch's development. Blake's got big plans for that site, which is only fitting, given the enormous popularity of CTF.

-- [https://www.bluesnews.com/archives/nov96-3.html](https://www.bluesnews.com/archives/nov96-3.html)

## Client v3.0 Beta 3

A private third beta was created, but the public version was scrapped according to an announcement on BluesNews on November 18h:

> CTF 3 Release Info\
> I got word from Blake Winton, new ThreeWave webmaster, that last night's private beta eliminates the need for another public beta (I kinda saw that coming...), so now we're set for a final release "in a few days..."
>
	> CTF3 Final Release!!!\
	> After the supremely successful private beta testing last night, it has been decided that a public beta will not occur. But don't lynch us yet, because The FINAL release should be out in a few days. That's everything, including the client and server side patches, and all the source for the server. It's been a lot of hard work and a long time in coming, but it'll be worth it. Special thanks to the #QuakeEd beta testing team, without whose hard work this wouldn't be released nearly this soon.

-- [https://www.bluesnews.com/archives/nov96-3.html](https://www.bluesnews.com/archives/nov96-3.html)

## v3.0

Version 3.0 of the mod was announced on BluesNews on November 21 1996:

> CTF 3.0 Released\
> The eagerly awaited full release of Capture the Flag 3.0 has been released on Threewave. There is a list of servers and mirror sites there. Here is the Client patch (4M) and the Server patch (400K).

-- [https://www.bluesnews.com/archives/nov96-3.html](https://www.bluesnews.com/archives/nov96-3.html)

With links:

* ftp://bluesnews.com/pub/quakec/teamplay/3wave301.zip
* ftp://bluesnews.com/pub/quakec/teamplay/3wave30.zip

The release was also announced on QuakeHole:

> CTF 3.0 is out 9:55pm - 11/21/96\
> Heh, I goofed.. usually when I get email from QHQ about something just being released (reaper) I assume its an exclusive.. go download it from the Threewave homepage, and read the instructions if you dont understand.. they are on that page as well. Not much else going on that I'm aware of.. go check out Bane's page.. its pretty cool.. maybe I'll update my links page tonight? haha um.. yea.. maybe.. btw.. I changed my bios from MR to Award.. seems MR was having a problem with the DMA addressing with the Verite card.. I gained a good 5-6 fps on start map.. That problem with the dynamic lighting is much less apparent now as well.

-- [http://www.quakehole.com/frames/oldnews.html](https://web.archive.org/web/19971210064427/http://www.quakehole.com/frames/oldnews.html) (archived)

Historical locations for the server:

* ftp://bluesnews.com/pub/quakec/teamplay/3wave30.zip
* ftp://ftp.cdrom.com/pub/idgames2/quakec/teamplay/ctf/3wave30.zip
* ftp://ftp.cdrom.com/pub/quake/planetquake/threewave/ctf/server/3wave30.zip
* ftp://ftp.pathfinder.com/pub/quake/threewave/3wave30.zip
* ftp://ftp.vision.net.au/pub/quake_stuff/extras/3wave30.zip
* ftp://home.interpac.net/pub/quake/3wave/3wave30.zip
* http://aggiequake.tamu.edu/files/3wave30.zip
* http://aries.neca.com/~zoid/3wave30.zip
* http://ftp.sunet.se/planetquake/threewave/ctf/server/3wave30.zip
* http://lucci.in-net.com/files/3wave30.zip
* http://redwood.gatsbyhouse.com/quake/files/3wave30.zip
* http://redwood.stomped.com/files/3wave30.zip
* http://wasatchfault.com/otherfiles/Flag/3wave30.zip
* http://web.ukonline.co.uk/Members/jc.burton/3wave30.zip
* http://www.cl.ais.net/orion/3wave30.zip
* http://www.gatsbyhouse.com/quake/3wave30.zip
* http://www.ice.net/~vortex/darkmessiah/ctf3/3wave30.zip
* http://www.nuqneh.org/3wave30.zip
* http://www.time2quake.com/filez/threewave/ctf/server/3wave30.zip
* https://www.quaddicted.com/files/idgames2/planetquake/threewave/ctf/server/3wave30.zip
* https://www.quaddicted.com/files/mirrors/ftp.planetquake.com/threewave/ctf/server/3wave30.zip

Historical locations for the client:

* ftp://bluesnews.com/pub/quakec/teamplay/3wctfc30.zip
* ftp://ftp.cdrom.com/pub/idgames2/quakec/teamplay/3wctfc30.zip
* ftp://ftp.cdrom.com/pub/idgames2/quakec/teamplay/ctf/3wctfc30.zip
* ftp://ftp.pathfinder.com/pub/quake/threewave/3wctfc30.zip
* ftp://ftp.stomped.com/pub/quake/quakec/conversions/3wctfc30.zip
* ftp://ftp.sunet.se/pub2/pc/games/idgames2/newstuff/3wctfc30.zip
* ftp://ftp.torget.se/quake/multiplayer/3wctfc30.zip
* http://aries.neca.com/~zoid/3wctfc30.zip
* http://reality.sgi.com/rae/quake/idfiles/3wctfc30.zip
* http://wasatchfault.com/otherfiles/3wctfc30.zip
* http://www.bluesnews.com/files/3wctfc30.zip
* http://www.gatsbyhouse.com/quake/3wctfc30.zip
* http://www.gore.org/files/server/3wctfc30.zip
* http://www.nuqneh.org/3wctfc30.zip
* http://www.wasatchfault.com/otherfiles/3wctfc30.zip
* http://www.webraven.com.au/games/quake/files/mods/3wctfc30.zip

Contents of the server archive `3wave30.zip`:

```text
-rw-------  0 0      0      118856 21 Nov  1996 ctf.dif
-rw-------  0 0      0        1765 21 Nov  1996 capture.txt
-rw-------  0 0      0       31615 21 Nov  1996 server.txt
-rw-------  0 0      0         127 21 Nov  1996 autoexec.cfg
-rw-------  0 0      0        2555 21 Nov  1996 config.cfg
-rw-------  0 0      0      473512 21 Nov  1996 progs.dat
-rw-------  0 0      0       14410  1 Nov  1996 maps/dm3.ent
-rw-rw-r--  0 0      0       11745 23 Oct  1996 maps/dm6.ent
-rw-rw-r--  0 0      0       30836 17 Sep  1996 maps/e1m1.ent
-rw-rw-r--  0 0      0       44058 21 Sep  1996 maps/e1m2.ent
-rw-rw-r--  0 0      0       48571 28 Sep  1996 maps/e1m3.ent
-rw-rw-r--  0 0      0       46337 25 Sep  1996 maps/e1m4.ent
-rw-rw-r--  0 0      0       44142 23 Sep  1996 maps/e1m5.ent
-rw-rw-r--  0 0      0       38838 23 Sep  1996 maps/e1m6.ent
-rw-r--r--  0 0      0       36972 27 Oct  1996 maps/e1m8.ent
-rw-rw-r--  0 0      0       35022 29 Sep  1996 maps/e2m1.ent
-rw-rw-r--  0 0      0       28163  6 Oct  1996 maps/e2m2.ent
-rw-rw-r--  0 0      0       39829 29 Sep  1996 maps/e2m3.ent
-rw-rw-r--  0 0      0       45578  8 Oct  1996 maps/e2m5.ent
-rw-rw-r--  0 0      0       42672  7 Oct  1996 maps/e4m3.ent
-rw-rw-r--  0 0      0       46326 21 Oct  1996 maps/e4m4.ent
-rw-rw-r--  0 0      0       48880 18 Oct  1996 maps/e4m5.ent
-rw-rw-r--  0 0      0       43154 19 Oct  1996 maps/e4m6.ent
-rw-------  0 0      0         106 19 Oct  1996 maps/dobsp.bat
-rwxr-xr-x  0 0      0          52  4 Oct  1996 maps/dobsp.sh
drwx------  0 0      0           0 21 Nov  1996 src/
-rw-------  0 0      0       14521  6 Oct  1996 src/ai.qc
-rw-------  0 0      0        1697  6 Oct  1996 src/amtest.qc
-rw-------  0 0      0       12411  6 Oct  1996 src/boss.qc
-rw-------  0 0      0        2910  6 Oct  1996 src/buttons.qc
-rw-------  0 0      0       46143 21 Nov  1996 src/client.qc
-rw-------  0 0      0        7098  6 Nov  1996 src/combat.qc
-rw-------  0 0      0       18439  1 Nov  1996 src/defs.qc
-rw-------  0 0      0        9904  6 Oct  1996 src/demon.qc
-rw-------  0 0      0        9542  6 Oct  1996 src/dog.qc
-rw-------  0 0      0       17138  6 Oct  1996 src/doors.qc
-rw-------  0 0      0       10727  6 Oct  1996 src/enforcer.qc
-rw-------  0 0      0        7208  6 Oct  1996 src/fight.qc
-rw-------  0 0      0        7747  6 Oct  1996 src/fish.qc
-rw-------  0 0      0       18298  6 Oct  1996 src/hknight.qc
-rw-------  0 0      0       34028 10 Nov  1996 src/items.qc
-rw-------  0 0      0         222  6 Oct  1996 src/jctest.qc
-rw-------  0 0      0        9684  6 Oct  1996 src/knight.qc
-rw-------  0 0      0       15088  6 Oct  1996 src/misc.qc
-rw-------  0 0      0        8996  6 Oct  1996 src/models.qc
-rw-------  0 0      0        4798  6 Oct  1996 src/monsters.qc
-rw-------  0 0      0       14657  6 Oct  1996 src/ogre.qc
-rw-------  0 0      0        9537  6 Oct  1996 src/oldone.qc
-rw-------  0 0      0        7693  6 Oct  1996 src/plats.qc
-rw-------  0 0      0       18820  7 Nov  1996 src/player.qc
-rw-------  0 0      0         622  4 Nov  1996 src/progs.src
-rw-------  0 0      0        7880  6 Oct  1996 src/shalrath.qc
-rw-------  0 0      0       12725  6 Oct  1996 src/shambler.qc
-rw-------  0 0      0        9825  6 Oct  1996 src/soldier.qc
-rw-------  0 0      0         450  6 Oct  1996 src/sprites.qc
-rw-------  0 0      0        6062  6 Oct  1996 src/subs.qc
-rw-------  0 0      0        7116  6 Oct  1996 src/tarbaby.qc
-rw-------  0 0      0       14259 19 Oct  1996 src/triggers.qc
-rw-------  0 0      0       31666  7 Nov  1996 src/weapons.qc
-rw-------  0 0      0       10663  6 Oct  1996 src/wizard.qc
-rw-------  0 0      0       11730  7 Nov  1996 src/world.qc
-rw-------  0 0      0       20108  6 Oct  1996 src/zombie.qc
-rw-------  0 0      0        2598 21 Nov  1996 src/progdefs.h
-rw-------  0 0      0       33718 17 Nov  1996 src/teamplay.qc
-rw-------  0 0      0        1560 19 Oct  1996 src/telefrag.qc
-rw-------  0 0      0         655 31 Oct  1996 src/charset.txt
-rw-------  0 0      0        8622 21 Nov  1996 src/files.dat
-rw-------  0 0      0         650 29 Oct  1996 src/log.qc
-rw-------  0 0      0        6654  4 Nov  1996 src/hook.qc
-rw-------  0 0      0        5085 31 Oct  1996 src/admin.qc
-rw-------  0 0      0        3446 17 Nov  1996 src/flag.qc
```

Header from server readme file:

```text
Title    : Threewave Capture
Filename : 3wave30.zip
Version  : 3.00
Date     : 96-11-21
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
Credits  :

John Spickes aka Guru <jspickes@eng.umd.edu> for JTEAM
Aegis - moral support and general overexcited Quake guy
Beowulf - my cat who keeps getting me fragged when he jumps on my keyboard
  or starts chasing my mouse
"Mike" <amichael@asu.alasu.edu> for Morning Star (Hook)
Tom "Bjorn" Klok <tomtom@mindlink.net> for original ideas such as the runes
  and capture games, various suggestions and bug fixes.  Check his server at
  quake.mindlink.net, 204.174.17.22
Kevin "Trojan[CampQ]" Hodgson <kevin@caseware.com> for modifing e4m5.
Byron "Wonko" Long <byron@caseware.com> for adding Flag Status reports
  via impulse 23.
Michael "McBain" Peckman for the PreviousWeaponCommand (impulse 69)

The level editing team for the 3.0 custom release:
ctf1  McKinley Base          Dave 'Zoid' Kirsch <zoid@threewave.com>
ctf2  The Kiln               Brian Wight <briwig@odc.net>
ctf3  DySpHoRiA              Chris 'b0rt' Thibodeaux <chrislt@u.washington.edu>
ctf4  The Forgotten Mines    Brian Wight <briwig@odc.net>
ctf5  Da Ancient War Grounds Matthew 'DaBug' Hooper <junebug@linknet.net>
ctf6  Vertigo                Dale 'Midiguy' B. <midiguy@crl.com>
ctf7  Tale of Two Cities     Jamie Mactaggart <Maareck@msn.com>
ctf8  The StrongBox          Brent '[Drizzt]' Mcleod <mcleod@westworld.com>

The custom Skin man:  Ryan 'Grey_Ghost' Lacouture <vallore@wt.net>

                 +---------- The ThreeWave Web Dudes ----------+
                 |  Blake 'Coder' Winton <news@threewave.com>  |
                 |  Synthesizer Punk <anarchy@wasteland.org>   |
                 +---------------------------------------------+

                           - And Special Thanks To -
                           Brian 'Whaleboy' Cozzens
                                    - of -
                                    QuakeX
                            The Quake Expansion Group
                        http://www.planetquake.com/quakex/
                       For his work on the Team Logo textures
                               And the Flag models


Type of Mod
-----------
Quake C  : yes
Sound    : yes
MDL      : yes

Format of QuakeC
----------------
unified diff  : yes
context diff  : no
.qc files     : yes
progs.dat     : yes
```

-- readme.txt


Contents of the client archive `3wctfc30.zip`:

```text
-rw-rw-r--  0 0      0     9700015 20 Nov  1996 pak0.pak
-rw-rw-r--  0 0      0        4087 21 Nov  1996 readme.txt
```

Header from server readme file:

```text
Title    : Threewave Capture
Filename : 3wctfc30.zip
Version  : 3.0
Date     : 96-11-21
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
```

-- readme.txt

## v3.01

Version 3.01 was announced on BluesNews on November 22nd:

> CTF Bug\
> There is a bug in the Capture the Flag 3.0 release that causes vertigo (ctf6) to crash the server. There's a 3.01 patch for server operators on Threewave, or you can download it from here 3wctf01.zip (4M). The pak0.pak in this file fixes the bug on the map, but it's only required on the server. If you are connecting as a client with 3.0, you don't need to download the new file, 3.0 or 3.01 will work equally well.

-- [https://www.bluesnews.com/archives/nov96-3.html](https://www.bluesnews.com/archives/nov96-3.html)

Links:

* ftp://bluesnews.com/pub/quakec/teamplay/3wctf301.zip

The update was mentioned on QuakeHole on the 22nd:

> ... Someone on irc told me that there is a new server for CTF3, the initial release had a bug. *server only*

-- [http://www.quakehole.com/frames/oldnews.html](https://web.archive.org/web/19971210064427/http://www.quakehole.com/frames/oldnews.html) (archived)

It was also mentioned on Redwood's on November 24th:

> Also, I meant to put this up the other day but you can download the new Capture the Flag 3.01 (4MB) from this site as well as the Server source (400k). I'm seriously thinking about making redwood.tamu.edu a CTF server because the other server on our campus seemed kinda choppy. I'll probably do it over the thanksgiving holidays and let everybody know when I do.

-- [http://redwood.gatsbyhouse.com/quake/1196.html](https://web.archive.org/web/19970327200928/http://redwood.gatsbyhouse.com/quake/1196.html) (archived)

Links:

* http://redwood.gatsbyhouse.com/quake/files/3wctf301.zip
* http://redwood.gatsbyhouse.com/quake/files/3wave30.zip

Historical locations for the file include:



The contents of the archive is as follows:

```text
-rw-rw-r--  0 0      0     9701080 22 Nov  1996 pak0.pak
-rw-rw-r--  0 0      0        4348 22 Nov  1996 readme.txt
```

The header from the readme is as follows:

```text
Title    : Threewave Capture
Filename : 3wctf301.zip
Version  : 3.01
Date     : 96-11-22
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
```

-- readme.txt








