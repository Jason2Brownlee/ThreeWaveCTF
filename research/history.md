# ThreeWave CTF Release History

Reconstructed history of ThreeWaveCTF by Dave Kirsch aka "Zoid".

Developed to ensure that the [ThreeWave CTF Archive](https://github.com/Jason2Brownlee/ThreeWaveCTF) is accurate and complete.

If you have any additional information, missing releases, or private betas that you're happy to contribute to the archive/history, please reach out: jason.brownlee05@gmail.com

## USENET Chatter

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


## BluesNews Announcement

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

It was announced on Shake N' Quake on October 15th:

> Capture The Flag: Capture the Flag 2.3 is out. You can pick it up off of our FTP server. Its about 500k. This is probably the most popular deathmatch Quake C addon.

-- [http://www.canvasnet.com:80/quake/old/october.htm](https://web.archive.org/web/20010524023657/http://www.canvasnet.com:80/quake/old/october.htm) (archived)

Which links to:

* ftp://ftp.canvasnet.com/quake/ctf/3wave23.zip

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

It was announced on Shake 'N Quake on November 7th:

> CTF 2.5: The long awaited Capture the Flag 2.5 is out. Pick it up here!! I haven't yet tried it out, but it is supposed to have the cheating fixed, and be even better than before. For more details, check out the Threewave site, or the Capture the Flag page.

-- [http://www.canvasnet.com:80/quake/old/november.htm](https://web.archive.org/web/20010719130416/http://www.canvasnet.com:80/quake/old/november.htm) (archived)

With links:

* ftp://ftp.canvasnet.com/quake/ctf/3wave25.zip

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

It was announced on Shake 'N Quake on November 8th:

> CTF 2.51: Minor Bugfix from Capture the Flag 2.5. Apparently, flags could fall through the floors. Hmmn, that would make the game just a tad more difficult!
>
> To Download: From Canvasnet or From Threewave

-- [http://www.canvasnet.com:80/quake/old/november.htm](https://web.archive.org/web/20010719130416/http://www.canvasnet.com:80/quake/old/november.htm) (archived)

With links:

* ftp://ftp.canvasnet.com/quake/ctf/3wave251.zip
* http://quake.threewave.com/3wave251.zip

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

It was announced on Shake 'N Quake on November 14th:

> CTF Client beta patch released: Sorry about this being a bit late, but since I was busy with school work I didn't get on this as quickly as possible. With that out of the way just like to report the CTF pack is now in beta form and is available for download. Get your client side copy here, at Blues News, or Threewave. This add-on has over time become the best and most popular out there so check it out. For a list of servers that are using this patch check out the Threewave Homepage.

-- [http://www.canvasnet.com:80/quake/old/november.htm](https://web.archive.org/web/20010719130416/http://www.canvasnet.com:80/quake/old/november.htm) (archived)

With links:

* ftp://ftp.canvasnet.com/incoming/quake/3wctfc3b.zip
* ftp://bluesnews.com/pub/quakec/teamplay/3wctfc3b.zip
* http://quake.threewave.com/3wctfc3b.zip

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
>> CTF3 Final Release!!!\
>> After the supremely successful private beta testing last night, it has been decided that a public beta will not occur. But don't lynch us yet, because The FINAL release should be out in a few days. That's everything, including the client and server side patches, and all the source for the server. It's been a lot of hard work and a long time in coming, but it'll be worth it. Special thanks to the #QuakeEd beta testing team, without whose hard work this wouldn't be released nearly this soon.

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

It was announced on Shake 'N Quake on November 21st:

> CTF 3.0: The full release of Capture the Flag 3.0 has been released on Threewave. Check out the site for a list servers and mirror sites there to play on. The new maps that I played on the Beta3 were simply amazing. By far CTF is going to take on a whole new quality to it with the addition of these great maps. I'll get the file mirrored here soon enough too.

-- [http://www.canvasnet.com:80/quake/old/november.htm](https://web.archive.org/web/20010719130416/http://www.canvasnet.com:80/quake/old/november.htm) (archived)

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

The release was mentioned on Shake 'N Quake on December 8th 1996:

> Late Threewave Info: This might not be very new to most of you know but Threewave the home of CTF has relocated to one of the biggest Quake places out there, Planet Quake. There new URL can be reached here, so change your bookmarks. Also the textures used to make the CTF pack are now available for download here. This will help all you aspiring CTF map makers out there to start editing away. Lastly if you don't have the Threewave CTF pack version 3.01 it is up for download right here.

-- [http://www.canvasnet.com:80/quake/old/november.htm](https://web.archive.org/web/20010719130416/http://www.canvasnet.com:80/quake/old/november.htm) (archived)

With links:

* http://www.planetquake.com/quakex/threewave/
* ftp://ftp.canvasnet.com/quake/ctf/ctf3wad.zip
* ftp://ftp.canvasnet.com/quake/ctf/3wctf301.zip

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


## v3.1

Version 3.1 was discussed on BluesNews on November 24th 1996:

> CTF 3.1\
> There's news about the upcoming Capture the Flag 3.1 on Threewave. Planned enhancements include the guy with the flag no longer glowing (instead he'll have a visible flag, and will trail "green particles"), and a scoring system that will reward players for "assists."

-- [https://www.bluesnews.com/archives/nov96-4.html](https://www.bluesnews.com/archives/nov96-4.html)

It was also mentioned on Redwood's:

> Qsoccer / Rotating brushes? 10:30pm - 11/24/96\
> ...Oh.. CTF 3.1 is out with quite a few changes.. (Thanks Tyler C.)

-- [http://www.quakehole.com/frames/oldnews.html](https://web.archive.org/web/19971210064427/http://www.quakehole.com/frames/oldnews.html) (archived)


This was also mentioned on QuakeHole as a "release":

> ==November 24== 10:00p.m. CST\
> Saw on blue's that Zoid is going to soon have a Capture the Flag 3.1 and some of the changes are talked about.

-- [http://redwood.gatsbyhouse.com/quake/1196.html](https://web.archive.org/web/19970327200928/http://redwood.gatsbyhouse.com/quake/1196.html) (archived)


## Demos

Demos of CTF maps were released circa December 2nd 1996:

* `demo1.zip`: Multiplayer CTF Demo (McKinley Base).
* `demo2.zip`: Multiplayer CTF Demo (Da Ancient War Grounds)
* `demo3.zip`: Multiplayer CTF Demo (The Strongbox)

Content of `demo1.zip`:

```text
-rw-rw-r--  0 0      0     4510146 30 Nov  1996 ctfdemo1.dem
-rw-rw-r--  0 0      0        2581  2 Dec  1996 ctfdemo1.txt
```

Header of `demo1.zip/ctfdemo1.txt`:

```text
File name:      oh-1196-ctfa.zip
Description:    Demo file of a 16 player LAN CTF3.01 deathmatch.
                This demo was recorded on 11/30/96 at the Perry,
                Ohio DeathFest.  We had 22+ people in attendance
                so we ran dedicated servers most of the night,
                hence the lack of demos.

                As you may notice, we're using CTF3.01 with my
                TeleWeapons v2.1 patch integrated.

                This demo starts off with 2 1/2 minutes of me
                just standing there waiting for people to join
                the game.  Go get some munchies while you wait;
                it's boring.
Playtime:       22 minutes, 12 seconds.
Level:          CTF1.  McKinley Base
...
```

-- ctfdemo1.txt

**At the time of writing a copy of `demo2.zip` has not been acquired.**

Contents of `demo3.zip`:

```text
-rw-rw-r--  0 0      0     2980403 30 Nov  1996 ctfdemo3.dem
-rw-rw-r--  0 0      0        2178  2 Dec  1996 ctfdemo3.txt
```

Header of `demo3.zip/ctfdemo1.txt`:

```text

File name:      oh-1196-ctfc.zip
Description:    Demo file of a 6 player LAN CTF3.01 deathmatch.
                This demo was recorded on 11/30/96 at the Perry,
                Ohio DeathFest.  We had 22+ people in attendance
                so we ran dedicated servers most of the night,
                hence the lack of demos.

                As you may notice, we're using CTF3.01 with my
                TeleWeapons v2.1 patch integrated.

                This demo starts off with 1 1/4 minutes of me
                just standing there waiting for people to join
                the game.  Go get some munchies while you wait;
                it's boring.
Playtime:       10 minutes, 53 seconds.
Level:          CTF8.  The Strongbox (gotta love it!)
...
```

The `demo1.zip` may have been initially released as `oh-1196-ctfa.zip`.

The `demo3.zip` may have been initially released as `oh-1196-ctfc.zip`.

This suggests `demo2.zip` may have been initially released as `oh-1196-ctfb.zip`.

Evidence for this can be seen in this file listing:

```text
...
	oh-1196-ctfa.txt.gz	1 KB	12/2/1996
	oh-1196-ctfa.zip	1.57 MB	12/2/1996
	oh-1196-ctfb.txt.gz	1 KB	12/2/1996
	oh-1196-ctfb.zip	2.73 MB	12/2/1996
	oh-1196-ctfc.txt.gz	1 KB	12/2/1996
	oh-1196-ctfc.zip	718 KB	12/2/1996
...
```

-- [nctuccca.edu.tw/PC/games/QUAKE/demos/j-q/](https://web.archive.org/web/19970321200124/nctuccca.edu.tw/PC/games/QUAKE/demos/j-q/) (archived)

Historical locations for `oh-1196-ctfa.zip`:

* ftp://nctuccca.edu.tw/PC/games/QUAKE/demos/j-q/oh-1196-ctfa.zip
* http://www.cdrom.com/pub/idgames2/demos/oh-1196-ctfa.zip
* http://www.gameaholic.com/deicide/download.cgi?/demos/j-q/oh-1196-ctfa.zip

Historical locations for `oh-1196-ctfb.zip`:

* ftp://nctuccca.edu.tw/PC/games/QUAKE/demos/j-q/oh-1196-ctfb.zip
* http://www.cdrom.com/pub/idgames2/demos/oh-1196-ctfb.zip
* http://www.gameaholic.com/deicide/download.cgi?/demos/j-q/oh-1196-ctfb.zip

Historical locations for `oh-1196-ctfc.zip`:

* ftp://nctuccca.edu.tw/PC/games/QUAKE/demos/j-q/oh-1196-ctfc.zip
* http://www.cdrom.com/pub/idgames2/demos/oh-1196-ctfc.zip
* http://www.gameaholic.com/deicide/download.cgi?/demos/j-q/oh-1196-ctfc.zip

**At the time of writing a copy of the original demo file releases have not been acquired.**

## Wad

A package of CTF map textures, called a WAD, was released as `ctf3wad.zip` circa November 30 1996.

Content of `ctf3wad.zip`:

```text
-rw-rw-r--  0 0      0     1209096 30 Nov  1996 ctf3.wad
-rw-rw-r--  0 0      0         977 30 Nov  1996 readthis.txt
```

Header from readme:

```text
This is a wadfile I made that contains the textures from the set
of levels for the Capture the Flag 3 patch.  If it's missing any,
I am sorry---the size of this file took me by surprise, and I had
to cut out a few textures that I found were in the base.wad,
wizard.wad, medieval.wad, and metal.wad as well as the ctf3 levels.
I did include most of the textures though.
...
```

-- readthis.txt

Some historical locations for this file:

* ftp://ftp.canvasnet.com/quake/ctf/ctf3wad.zip
* ftp://ftp.cdrom.com/pub/idgames2/graphics/texture_wads/ctf3wad.zip
* ftp://ftp.compulink.co.uk/pub/games/id/quake/graphics/texture_wads/ctf3wad.zip
* ftp://ftp.datacomm.ch/pub/idgames2/graphics/texture_wads/ctf3wad.zip
* ftp://ftp.epix.net/pub/idgames2/graphics/texture_wads/ctf3wad.zip
* ftp://ftp.gamers.org/pub/games/idgames2/graphics/texture_wads/ctf3wad.zip
* ftp://ftp.iis.com.br/pub/mirror/Quake/graphics/texture_wads/ctf3wad.zip
* ftp://ftp.powerup.com.au/pub/games/quake/graphics/texture_wads/ctf3wad.zip
* ftp://ftp.sci.fi/pub/idgames2/graphics/texture_wads/ctf3wad.zip
* ftp://ftp.sunet.se/pub/pc/games/idgames2/graphics/texture_wads/ctf3wad.zip
* ftp://ftp.task.gda.pl/pub/games/idgames2/graphics/texture_wads/ctf3wad.zip
* ftp://ftp.telepac.pt/pub/idgames2/graphics/texture_wads/ctf3wad.zip
* ftp://mirror.aarnet.edu.au/pub/idgames2/graphics/texture_wads/ctf3wad.zip
* ftp://sunsite.doc.ic.ac.uk/packages/idgames2/graphics/texture_wads/ctf3wad.zip
* http://asp.planetquake.com/dl/dl.asp?leveled/wad/ctf3wad.zip
* http://dd.networx.net.au/cgi-bin/pftp.pl?/pub/editing/wads/ctf3wad.zip
* http://ftp.gamers.org/pub/games/idgames2/graphics/texture_wads/ctf3wad.zip
* http://ftp.mancubus.net/pub/idgames2/graphics/texture_wads/ctf3wad.zip
* http://ftp.sunet.se/idgames2/graphics/texture_wads/ctf3wad.zip
* http://ftp.sunet.se/pub/pc/games/idgames2/graphics/texture_wads/ctf3wad.zip
* http://ftp.telepac.pt/pub/idgames2/graphics/texture_wads/ctf3wad.zip
* http://sunsite.doc.ic.ac.uk/Mirrors/ftp.cdrom.com/pub/quake/graphics/texture_wads/ctf3wad.zip
* http://www.cdrom.com/pub/idgames2/graphics/texture_wads/ctf3wad.zip
* http://www.gameaholic.com/deicide/download.cgi?/graphics/texture_wads/ctf3wad.zip
* http://www.gamers.org/pub/games/idgames2/graphics/texture_wads/ctf3wad.zip
* http://www.gamers.org/pub/idgames2/graphics/texture_wads/ctf3wad.zip
* http://www.globalsoft.com.au/cgi-bin/pftp.pl?/pub/editing/wads/ctf3wad.zip
* http://www.time2quake.com/filez/graphics/texture_wads/ctf3wad.zip
* https://www.quaddicted.com/files/idgames2/graphics/texture_wads/ctf3wad.zip
* https://www.quaddicted.com/files/wads/ctf3wad.zip

## v3.2

Version 3.2 was announced on BluesNews on December 3rd:

> CTF 3.2 Released, Threewave Moves\
> Big doings over at Threewave, home of Capture the Flag. First, they've moved to a new home (please update your bookmarks), as a branch off of QuakeX (all part of the PlanetQuake Empire). The QuakeX thing is a natural, since Whaleboy has been doing a lot of work for the CTF projects, and he not only is providing the space for Threewave, he did a beautiful redesign of the site. Second, CTF 3.2 has been released, which is required for servers only. The focus of version 3.2 in the words of Dave 'Zoid' Kirsch is "Expert CTF," with an added emphasis on strategy and bonuses for teamwork.
>
>> * Players now start with 50 green armor when spawned. This will let you survive at least one direct rocket hit. This is to make spawners have a chance at life and make defense more important.
>> * Weapons are *not* carried between levels. Now I know a lot of people are going to hate this, but it has to be done to make the team start on each level fair. Right now, if one team is kicking the other teams but, chances are on level change the leading team will be all stocked with ammo and weapons but the losing team will not be. This evens it out so every level, people start the same.
>
> Expert CTF mods.
>
>> * CTF will now award as assist on a capture. To get an assist frag the guy carrying your flag and return it. If your team captures in a short period of time, you will get an assist.
>> * Flag defense is now radius based (but not a large radius). It is better to kill a guy _before_ he gets your flag. There is no bonus if he gets it and then you immediately frag him.
>> * You also get a bonus for defending your flag carrier. If you blow away a guy who has harmed your carrier, you get an extra frag for it. Defend your flag carrier!

-- [https://www.bluesnews.com/archives/nov96-5.html](https://www.bluesnews.com/archives/nov96-5.html)

Links:

* http://www.planetquake.com/quakex/threewave/
* https://www.bluesnews.com/files/3wave32.zip

The release was also announced on Redwood's:

> Saw on The Void that Capture the Flag 3.2 (server source only update) is available from this site. Read what's new. Threewave also has moved to http://www.planetquake.com/quakex/threewave/ and has a new look.

-- [http://redwood.gatsbyhouse.com/quake/1296.html](https://web.archive.org/web/19970327200909/http://redwood.gatsbyhouse.com/quake/1296.html) (archived)

Links:

* http://redwood.gatsbyhouse.com/quake/files/ctf/3wave32.zip
* http://redwood.gatsbyhouse.com/quake/files/ctf/ctf32chg.txt
* http://www.planetquake.com/quakex/threewave/

Some historical locations for the release include:

* ftp://ftp.cdrom.com/pub/quake/planetquake/threewave/ctf/server/3wave32.zip
* http://bluesnews.com/files/3wave32.zip
* http://ftp.sunet.se/planetquake/threewave/ctf/server/3wave32.zip
* http://quakemecca.simplenet.com/files/downloads/3wave32.zip
* http://quakemecca.simplenet.com/files/downloads/files/downloads/3wave32.zip
* http://reality.sgi.com/rae/quake/idfiles/3wave32.zip
* http://reality.sgi.com/rae_aw/quake/idfiles/3wave32.zip
* http://redwood.gatsbyhouse.com/quake/files/ctf/3wave32.zip
* http://redwood.stomped.com/files/ctf/3wave32.zip
* http://www.bluesnews.com/files/3wave32.zip
* http://www.bluesnews.com/files/files/3wave32.zip
* http://www.cdrom.com/pub/idgames2/newstuff/3wave32.zip
* http://www.frag.com/qchq/zips/3wave32.zip
* http://www.gore.org/files/server/3wave32.zip
* http://www.planetquake.com/quakex/threewave/files/3wave32.zip
* http://www.time2quake.com/filez/threewave/ctf/server/3wave32.zip
* https://www.quaddicted.com/files/idgames2/planetquake/threewave/ctf/server/3wave32.zip
* https://www.quaddicted.com/files/mirrors/ftp.planetquake.com/threewave/ctf/server/3wave32.zip

And the CD:

* [Cream of the Crop 24](https://archive.org/details/various_cd-rom_iso_collection_2016_07)

The contents of the archive:

```text
-rw-rw-r--  0 0      0        1765  4 Oct  1996 capture.txt
-rw-rw-r--  0 0      0       31969  3 Dec  1996 server.txt
-rw-rw-r--  0 0      0         172  3 Dec  1996 autoexec.cfg
-rw-rw-r--  0 0      0        2276  3 Dec  1996 config.cfg
-rw-rw-r--  0 0      0      479048  3 Dec  1996 progs.dat
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
-rw-rw-r--  0 0      0       48880 18 Oct  1996 maps/e4m5.ent
-rw-rw-r--  0 0      0       43154 19 Oct  1996 maps/e4m6.ent
-rw-rw-r--  0 0      0       46326 21 Oct  1996 maps/e4m4.ent
-rw-rw-r--  0 0      0       11745 23 Oct  1996 maps/dm6.ent
-rw-rw-r--  0 0      0       14410 31 Oct  1996 maps/dm3.ent
-rw-rw-r--  0 0      0         108 18 Oct  1996 maps/dobsp.bat
-rw-rw-r--  0 0      0          52  4 Oct  1996 maps/dobsp.sh
-rw-rw-r--  0 0      0       14521  6 Oct  1996 src/ai.qc
-rw-rw-r--  0 0      0        1697  6 Oct  1996 src/amtest.qc
-rw-rw-r--  0 0      0       12411  6 Oct  1996 src/boss.qc
-rw-rw-r--  0 0      0        2910  6 Oct  1996 src/buttons.qc
-rw-rw-r--  0 0      0       56287 28 Nov  1996 src/client.qc
-rw-rw-r--  0 0      0        7860 27 Nov  1996 src/combat.qc
-rw-rw-r--  0 0      0       19523 28 Nov  1996 src/defs.qc
-rw-rw-r--  0 0      0        9904  6 Oct  1996 src/demon.qc
-rw-rw-r--  0 0      0        9542  6 Oct  1996 src/dog.qc
-rw-rw-r--  0 0      0       17138  6 Oct  1996 src/doors.qc
-rw-rw-r--  0 0      0       10727  6 Oct  1996 src/enforcer.qc
-rw-rw-r--  0 0      0        7208  6 Oct  1996 src/fight.qc
-rw-rw-r--  0 0      0        7747  6 Oct  1996 src/fish.qc
-rw-rw-r--  0 0      0       18298  6 Oct  1996 src/hknight.qc
-rw-rw-r--  0 0      0       34028 10 Nov  1996 src/items.qc
-rw-rw-r--  0 0      0         222  6 Oct  1996 src/jctest.qc
-rw-rw-r--  0 0      0        9684  6 Oct  1996 src/knight.qc
-rw-rw-r--  0 0      0       15088  6 Oct  1996 src/misc.qc
-rw-rw-r--  0 0      0        8996  6 Oct  1996 src/models.qc
-rw-rw-r--  0 0      0        4798  6 Oct  1996 src/monsters.qc
-rw-rw-r--  0 0      0       14657  6 Oct  1996 src/ogre.qc
-rw-rw-r--  0 0      0        9537  6 Oct  1996 src/oldone.qc
-rw-rw-r--  0 0      0        7693  6 Oct  1996 src/plats.qc
-rw-rw-r--  0 0      0       18832 23 Nov  1996 src/player.qc
-rw-rw-r--  0 0      0         614 23 Nov  1996 src/progs.src
-rw-rw-r--  0 0      0        7880  6 Oct  1996 src/shalrath.qc
-rw-rw-r--  0 0      0       12725  6 Oct  1996 src/shambler.qc
-rw-rw-r--  0 0      0        9825  6 Oct  1996 src/soldier.qc
-rw-rw-r--  0 0      0         450  6 Oct  1996 src/sprites.qc
-rw-rw-r--  0 0      0        6062  6 Oct  1996 src/subs.qc
-rw-rw-r--  0 0      0        7116  6 Oct  1996 src/tarbaby.qc
-rw-rw-r--  0 0      0       14259 19 Oct  1996 src/triggers.qc
-rw-rw-r--  0 0      0       31666  7 Nov  1996 src/weapons.qc
-rw-rw-r--  0 0      0       10663  6 Oct  1996 src/wizard.qc
-rw-rw-r--  0 0      0       11779 28 Nov  1996 src/world.qc
-rw-rw-r--  0 0      0       20108  6 Oct  1996 src/zombie.qc
-rw-rw-r--  0 0      0        2598  3 Dec  1996 src/progdefs.h
-rw-rw-r--  0 0      0       38951  3 Dec  1996 src/teamplay.qc
-rw-rw-r--  0 0      0        1560 19 Oct  1996 src/telefrag.qc
-rw-rw-r--  0 0      0         655 31 Oct  1996 src/charset.txt
-rw-rw-r--  0 0      0        8622  3 Dec  1996 src/files.dat
-rw-rw-r--  0 0      0         650 29 Oct  1996 src/log.qc
-rw-rw-r--  0 0      0        6654  4 Nov  1996 src/hook.qc
-rw-rw-r--  0 0      0        5082 26 Nov  1996 src/admin.qc
```

The header from the readme:

```text
Title    : Threewave Capture
Filename : 3wave32.zip
Version  : 3.20
Date     : 96-11-21
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
...
```

-- server.txt


## Secrets

A demo showing the location of secrets in CTF maps was released as `secrets.zip`.

Mention of the map secrets released via demos on BluesNews on December 23rd:

> Custom CTF Secrets Revealed\
> Threewave has been updated with demos of all the secrets on all the custom Threewave CTF levels. Thanks to Peter Ordal (a.k.a. Sonic) for the word.

-- [https://www.bluesnews.com/archives/dec96-3.html](https://www.bluesnews.com/archives/dec96-3.html)

Contents of `secrets.zip`:

```text
-rw-rw-r--  0 0      0       81673 20 Dec  1996 1SECRET.DEM
-rw-rw-r--  0 0      0       71381 20 Dec  1996 3SECRET.DEM
-rw-rw-r--  0 0      0      217908 20 Dec  1996 4SECRET.DEM
-rw-rw-r--  0 0      0       95132 20 Dec  1996 5SECRET.DEM
-rw-rw-r--  0 0      0       40941 20 Dec  1996 6SECRET.DEM
-rw-rw-r--  0 0      0      194426 20 Dec  1996 7SECRET.DEM
-rw-rw-r--  0 0      0      105159 20 Dec  1996 8SECRET.DEM
```


## v3.5 and QWCTF 1.0

There was mention of CTF support in QuakeWorld on BluesNews on December 5th 1996:

> QuakeWorld CTF\
> There's an update on Threewave about the conversion of Zoid's Capture the Flag patch to work in QuakeWorld. There are some differences in how Quake C works in QuakeWorld that lead to some changes in the patch. Unfortunately, QuakeWorld's client-side prediction causes the grappling hook to be unusable, so it will be axed. Also, the flag lags behind the carrier, so there probably going to make a new player model. CTF will be handled in QuakeWorld by one specialized CTF Master Server, and they're still working out what statistics it will track for each player. Zoid says "There's still some work to be done, but the bulk of the port is ready." The whole story is on Threewave, so go take a look.

-- [https://www.bluesnews.com/archives/nov96-5.html](https://www.bluesnews.com/archives/nov96-5.html)

Another mention of the QW version of CTF on BluesNews on December 15th:

> Grappling with Losing the Grappling Hook\
>A sentiment I've seen expressed in several reader emails is disappointment that Threewave Capture the Flag in QuakeWorld is not going to include the grappling hook. In a recent email Zoid dropped the hint that we might still have a grappling hook in our future in QuakeWorld CTF:
>
>> The QuakeWorld CTF conversion has gone through initial stages and is up and running. The flag lags behind the carrier pretty badly, so Whaleboy is working on a new player model that will fix this. Of course, the hook is gone. But it may appear in a future version of QuakeWorld. :)
>
> It's nice to know that Threewave CTF will be ready for the QuakeWorld release. BTW, Zoid is also the one who did all the 1.01 to 1.06 bug fixes in the Quake C for QuakeWorld.

-- [https://www.bluesnews.com/archives/dec96-2.html](https://www.bluesnews.com/archives/dec96-2.html)

The 3.5 release and CTF of QW 1.0 were announced on BluesNews on December 27:

> New Threewave CTF Releases\
> There are two new server releases on Threewave. For regular servers: Threewave CTF 3.5, and Threewave CTF 1.0 for QuakeWorld.

-- [https://www.bluesnews.com/archives/dec96-3.html](https://www.bluesnews.com/archives/dec96-3.html)

The CTF for QuakeWorld was mentioned on QuakeHole on December 27th:

> Zoid "the sheep keeper" Kirsch released QW CTF tonight. go lookie.

-- [http://www.quakehole.com/frames/oldnews.html](https://web.archive.org/web/19971210064427/http://www.quakehole.com/frames/oldnews.html) (archived)

The dual release was announced on Shake 'N Quake on December 28th:

> Threewave CTF Releases: There are two new server releases available on Threewave. For regular Net Quake servers: Threewave CTF 3.5, and Threewave CTF 1.0 for QuakeWorld CTF. As always they are here locally, for your viewing pleasure.

-- [http://www.canvasnet.com:80/quake/old/december.htm](https://web.archive.org/web/20010524021106/http://www.canvasnet.com:80/quake/old/december.htm) (archived)

With links:

* http://www.planetquake.com/quakex/threewave/
* ftp://ftp.canvasnet.com/quake/ctf/3wave35.zip
* ftp://ftp.canvasnet.com/quake/ctf/3wqw10.zip

Historical locations for `3wave35.zip`:

* ftp://ftp.canvasnet.com/quake/ctf/3wave35.zip
* ftp://ftp.cdrom.com/pub/idgames2/quakec/teamplay/ctf/3wave35.zip
* ftp://ftp.cdrom.com/pub/quake/planetquake/threewave/ctf/server/3wave35.zip
* ftp://ftp.freesoftware.com/pub/idgames2/planetquake/academy/ctf_files/3wave35.zip
* ftp://ftp.freesoftware.com/pub/idgames2/planetquake/threewave/ctf/server/3wave35.zip
* ftp://ftp.stomped.com/pub/redwood/ctf/3wave35.zip
* ftp://ftp.vision.net.au/pub/quake_stuff/extras/3wave35.zip
* http://bangg.org/files/3wave35.zip
* http://bluesnews.com/files/3wave35.zip
* http://ftp.sunet.se/planetquake/threewave/ctf/server/3wave35.zip
* http://jord.sbc.edu/dragon/files/ctf/3wave35.zip
* http://jord.sbc.edu/files/ctf/3wave35.zip
* http://quakemecca.simplenet.com/files/downloads/3wave35.zip
* http://quakemecca.simplenet.com/files/downloads/files/downloads/3wave35.zip
* http://redwood.gatsbyhouse.com/files/ctf/3wave35.zip
* http://www.bluesnews.com/files/3wave35.zip
* http://www.bluesnews.com/files/files/3wave35.zip
* http://www.cdrom.com/pub/idgames2/planetquake/academy/ctf_files/3wave35.zip
* http://www.cdrom.com/pub/idgames2/planetquake/threewave/ctf/server/3wave35.zip
* http://www.gore.org/files/server/3wave35.zip
* http://www.iceinternet.com/wilsonk/3wave35.zip
* http://www.imaxx.net/~dakota/capture/FILES/3wave35.zip
* http://www.planetquake.com/quakex/threewave/3wave35.zip
* http://www.time2quake.com/filez/threewave/ctf/server/3wave35.zip
* https://www.quaddicted.com/files/idgames2/planetquake/threewave/ctf/server/3wave35.zip
* https://www.quaddicted.com/files/mirrors/ftp.planetquake.com/threewave/ctf/server/3wave35.zip

Historical locations for `3wqw10.zip`:

* ftp://ftp.canvasnet.com/quake/ctf/3wqw10.zip
* ftp://ftp.vision.net.au/pub/quake_stuff/extras/3wqw10.zip
* http://bluesnews.com/files/3wqw10.zip
* http://ftp.sunet.se/planetquake/threewave/ctf/server/3wqw10.zip
* http://www.bluesnews.com/files/3wqw10.zip
* http://www.bluesnews.com/files/files/3wqw10.zip
* http://www.time2quake.com/filez/threewave/ctf/server/3wqw10.zip
* https://www.quaddicted.com/files/idgames2/planetquake/threewave/ctf/server/3wqw10.zip
* https://www.quaddicted.com/files/mirrors/ftp.planetquake.com/threewave/ctf/server/3wqw10.zip


The contents of the `3wave35.zip` archive:

```text
-rw-rw-r--  0 0      0        1765  4 Oct  1996 capture.txt
-rw-rw-r--  0 0      0       33447 27 Dec  1996 server.txt
-rw-rw-r--  0 0      0         180 27 Dec  1996 autoexec.cfg
-rw-rw-r--  0 0      0      271508 27 Dec  1996 progs.dat
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
-rw-rw-r--  0 0      0       48880 18 Oct  1996 maps/e4m5.ent
-rw-rw-r--  0 0      0       43154 19 Oct  1996 maps/e4m6.ent
-rw-rw-r--  0 0      0       46326 21 Oct  1996 maps/e4m4.ent
-rw-rw-r--  0 0      0       11745 23 Oct  1996 maps/dm6.ent
-rw-rw-r--  0 0      0       14410 31 Oct  1996 maps/dm3.ent
-rw-rw-r--  0 0      0         108 18 Oct  1996 maps/dobsp.bat
-rw-rw-r--  0 0      0          52  4 Oct  1996 maps/dobsp.sh
-rw-rw-r--  0 0      0         327 27 Dec  1996 src/progs.src
-rw-rw-r--  0 0      0        7312 15 Dec  1996 src/combat.qc
-rw-rw-r--  0 0      0        2910  6 Oct  1996 src/buttons.qc
-rw-rw-r--  0 0      0       57019 27 Dec  1996 src/client.qc
-rw-rw-r--  0 0      0       16302 15 Dec  1996 src/misc.qc
-rw-rw-r--  0 0      0       19674 27 Dec  1996 src/defs.qc
-rw-rw-r--  0 0      0        5601 15 Dec  1996 src/subs.qc
-rw-rw-r--  0 0      0       17138  6 Oct  1996 src/doors.qc
-rw-rw-r--  0 0      0       34028 20 Dec  1996 src/items.qc
-rw-rw-r--  0 0      0        7693  6 Oct  1996 src/plats.qc
-rw-rw-r--  0 0      0       18832 23 Nov  1996 src/player.qc
-rw-rw-r--  0 0      0       14259 19 Oct  1996 src/triggers.qc
-rw-rw-r--  0 0      0       31778 22 Dec  1996 src/weapons.qc
-rw-rw-r--  0 0      0       11779 28 Nov  1996 src/world.qc
-rw-rw-r--  0 0      0        2598 27 Dec  1996 src/progdefs.h
-rw-rw-r--  0 0      0       39616 26 Dec  1996 src/teamplay.qc
-rw-rw-r--  0 0      0        1560 19 Oct  1996 src/telefrag.qc
-rw-rw-r--  0 0      0         655 31 Oct  1996 src/charset.txt
-rw-rw-r--  0 0      0        6335 27 Dec  1996 src/files.dat
-rw-rw-r--  0 0      0         650 29 Oct  1996 src/log.qc
-rw-rw-r--  0 0      0        6654  4 Nov  1996 src/hook.qc
-rw-rw-r--  0 0      0       12106 27 Dec  1996 src/admin.qc
-rw-rw-r--  0 0      0        6093 27 Dec  1996 src/observ.qc
-rw-rw-r--  0 0      0        2368 20 Dec  1996 src/server.qc
```

The header of the `3wave35.zip` readme:

```text
Title    : Threewave Capture
Filename : 3wave35.zip
Version  : 3.50
Date     : 96-12-27
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
...
```

-- server.txt

Contents of the `3wqw10.zip` archive:

```text
-rw-rw-r--  0 0      0        1765  4 Oct  1996 capture.txt
-rw-rw-r--  0 0      0       19452 27 Dec  1996 server.txt
-rw-rw-r--  0 0      0         186 27 Dec  1996 server.cfg
-rw-rw-r--  0 0      0      232672 27 Dec  1996 progs.dat
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
-rw-rw-r--  0 0      0       48880 18 Oct  1996 maps/e4m5.ent
-rw-rw-r--  0 0      0       43154 19 Oct  1996 maps/e4m6.ent
-rw-rw-r--  0 0      0       46326 21 Oct  1996 maps/e4m4.ent
-rw-rw-r--  0 0      0       11745 23 Oct  1996 maps/dm6.ent
-rw-rw-r--  0 0      0       14410 31 Oct  1996 maps/dm3.ent
-rw-rw-r--  0 0      0         108 18 Oct  1996 maps/dobsp.bat
-rw-rw-r--  0 0      0          52  4 Oct  1996 maps/dobsp.sh
-rw-rw-r--  0 0      0       19880 14 Dec  1996 src/defs.qc
-rw-rw-r--  0 0      0        3051  4 Dec  1996 src/buttons.qc
-rw-rw-r--  0 0      0         655  4 Dec  1996 src/charset.txt
-rw-rw-r--  0 0      0       48461 19 Dec  1996 src/client.qc
-rw-rw-r--  0 0      0        7742 14 Dec  1996 src/combat.qc
-rw-rw-r--  0 0      0       30032 14 Dec  1996 src/weapons.qc
-rw-rw-r--  0 0      0       17137 14 Dec  1996 src/doors.qc
-rw-rw-r--  0 0      0        6152 27 Dec  1996 src/files.dat
-rw-rw-r--  0 0      0       38094 27 Dec  1996 src/teamplay.qc
-rw-rw-r--  0 0      0       33578  5 Dec  1996 src/items.qc
-rw-rw-r--  0 0      0       17029  4 Dec  1996 src/misc.qc
-rw-rw-r--  0 0      0        9515  4 Dec  1996 src/models.qc
-rw-rw-r--  0 0      0        8057  4 Dec  1996 src/plats.qc
-rw-rw-r--  0 0      0       17798  5 Dec  1996 src/player.qc
-rw-rw-r--  0 0      0        2541 27 Dec  1996 src/progdefs.h
-rw-rw-r--  0 0      0         200 14 Dec  1996 src/progs.src
-rw-rw-r--  0 0      0        2464  4 Dec  1996 src/server.qc
-rw-rw-r--  0 0      0         473  4 Dec  1996 src/sprites.qc
-rw-rw-r--  0 0      0        5888  4 Dec  1996 src/subs.qc
-rw-rw-r--  0 0      0       14106 14 Dec  1996 src/triggers.qc
-rw-rw-r--  0 0      0        1560  4 Dec  1996 src/telefrag.qc
-rw-rw-r--  0 0      0       11685 14 Dec  1996 src/world.qc
-rw-rw-r--  0 0      0       29316  4 Dec  1996 skins/ctfr1.pcx
-rw-rw-r--  0 0      0       29346  4 Dec  1996 skins/ctfr2.pcx
-rw-rw-r--  0 0      0       29284  4 Dec  1996 skins/ctfb1.pcx
-rw-rw-r--  0 0      0       29316  4 Dec  1996 skins/ctfb2.pcx
-rw-rw-r--  0 0      0       30449  4 Dec  1996 skins/base.pcx
```

Header for the `3wqw10.zip` readme:

```text
Title    : Threewave QuakeWorld Capture
Filename : 3wqw10.zip
Version  : 1.00
Date     : 96-12-27
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
...
```

-- server.txt

## idctf1

Tim Willits released a map for CTF. Although not a 3wave release, we'll mention it here in the history.

The release was announced on BluesNews on December 30th 1996:

> Tim Willits' CTF Map\
> Tim Willits just sent along his CTF map (772 KB) designed to work with Threewave CTF (here's the read me). This is a real treat, as Tim is a brilliant level designer. If you want to try it, he is running a server at id at:
>
> 192.246.40.121
>
> He also wants to be sure to note that this is not an official id product, just a map compatible with Zoid's modifications.
>
> While he was at it, Tim also set the record straight about his odd plan update:
>
> "I did not update my .plan, American did that crap about me liking WOOD"

-- [https://www.bluesnews.com/archives/dec96-4.html](https://www.bluesnews.com/archives/dec96-4.html)

Files:

* https://www.bluesnews.com/files/idctf1.zip
* https://www.bluesnews.com/files/idctf1.txt

The release was announced on QuakeHole on December 30th:

> Twillits CTF Map 11:35pm - 12/30/96\
> Was so busy playin the map I didnt even know Tim had released it public a couple hours ago.. here is is. you need the CTF patch from Zoid's page as well. the server (non - qw) is 192.246.40.121 have fun. I cant wait for all the other QW server to get the hook back.. man this map is cool.

-- [http://www.quakehole.com/frames/oldnews.html](https://web.archive.org/web/19971210064427/http://www.quakehole.com/frames/oldnews.html) (archived)

Links:

* http://www.quakehole.com/files/bsp/idctf1.zip

The release was also mentioned on Redwood's:

> ==December 30== 11:25p.m. CST\
> Full update to come within hours...but for now, my favorite level designer at id (Tim Willits, if you didn't already know) has released a very cool Capture the Flag level. You can get idctf1.zip (772k)from here. I'm working on a small file section right now. All the files are there, I just need to make the page *grin*. BTW, I got the file from blue's but saw the link on that cool page, The Void because blue's page is screwed again like it was Saturday. According to Quakeholio, a non-QW server is running it at 192.246.40.121 (that's at id btw). It is up, I just checked it, but nobody's there. :(. Those shelves are very cool looking. Happiness is find one Shiner Bock in the fridge and a frosted mug in the freezer to pour it in.

-- [http://redwood.gatsbyhouse.com/quake/1296.html](https://web.archive.org/web/19970327200909/http://redwood.gatsbyhouse.com/quake/1296.html) (archived)

Links:

* http://redwood.gatsbyhouse.com/quake/files/ctf/idctf1.zip

It was announced on Shake N' Quake on December 31st:

> 12-31-96, Sunday, 1:04 AM EST (F)\
> Tim Willits CTF Map: One of the most talented map designers our cooked up a little something for all of us Quakers. He took the basic map of E1M5 made it a mirror image for blue and red bases and added some enhancements. This map is on of the best CTF maps out there and even has some leet new textures done by Whaleboy. A non-QW server is running over at id, at 192.246.40.121. Download the file right here (772KB).

-- [http://www.canvasnet.com:80/quake/old/december.htm](https://web.archive.org/web/20010524021106/http://www.canvasnet.com:80/quake/old/december.htm) (archived)

Links:

* ftp://ftp.canvasnet.com/quake/levels/bsp/idctf1.zip

Historical locations for the file include:


* ftp://flinux.tu-graz.ac.at/pub/idsoftware2/idstuff/unsup/idctf1.zip
* ftp://ftp.canvasnet.com/quake/levels/bsp/idctf1.zip
* ftp://ftp.cdrom.com/pub/idgames2/idstuff/unsup/idctf1.zip
* ftp://ftp.compulink.co.uk/pub/games/id/quake/idstuff/unsup/idctf1.zip
* ftp://ftp.edu.sollentuna.se/pub/games/quake-stuff/idstuff/unsup/idctf1.zip
* ftp://ftp.ee.techpta.ac.za/pub/games/idgames2/idstuff/unsup/idctf1.zip
* ftp://ftp.epix.net/pub/idgames2/idstuff/unsup/idctf1.zip
* ftp://ftp.evildead.com/files/outgoing/quake/tf/maps/zipped/IDCTF1.zip
* ftp://ftp.gamers.org/pub/games/idgames2/idstuff/unsup/idctf1.zip
* ftp://ftp.global.co.za/pub/quake/idstuff/unsup/idctf1.zip
* ftp://ftp.hol.gr/games/idsoftware/quake/idstuff/unsup/idctf1.zip
* ftp://ftp.idsoftware.com/idstuff/unsup/idctf1.zip
* ftp://ftp.il.waw.pl/pub/quake/idstuff/unsup/idctf1.zip
* ftp://ftp.intercity.dk/pub/mirrors/quake/idstuff/unsup/idctf1.zip
* ftp://ftp.lame.org/mirrors/quake_stuff/idstuff/unsup/idctf1.zip
* ftp://ftp.lib.siu.edu/pub/mirrors/idsoftware/idstuff/unsup/idctf1.zip
* ftp://ftp.livewire.com.au/pub/idgames2/idstuff/unsup/idctf1.zip
* ftp://ftp.pioneer.wnyric.org/pub/quake/idstuff/unsup/idctf1.zip
* ftp://ftp.powerup.com.au/pub/games/quake/idstuff/unsup/idctf1.zip
* ftp://ftp.ram.net.au/pub/quake/idgames2/idstuff/unsup/idctf1.zip
* ftp://ftp.sci.fi/quake/idgames2/idstuff/unsup/idctf1.zip
* ftp://ftp.stomped.com/pub/idgames2/idstuff/unsup/idctf1.zip
* ftp://ftp.stomped.com/pub/redwood/ctf/idctf1.zip
* ftp://ftp.sunet.se/pub/pc/games/idgames2/idstuff/unsup/idctf1.zip
* ftp://ftp.telepac.pt/pub/idgames2/idstuff/unsup/idctf1.zip
* ftp://ftp.torget.se/pub/games/quake/maps/idctf1.zip
* ftp://ftp.tu-clausthal.de/pub/msdos/games/quake-mirror/idstuff/unsup/idctf1.zip
* ftp://sunsite.doc.ic.ac.uk/packages/idgames2/idstuff/unsup/idctf1.zip
* http://bluesnews.com/files/idctf1.zip
* http://ftp.digex.net/pub/idsoftware/unsup/idctf1.zip
* http://ftp.mancubus.net/pub/idgames2/idstuff/unsup/idctf1.zip
* http://ftp.planetmirror.com/pub/idgames2/idstuff/unsup/idctf1.zip
* http://ftp.sunet.se/idgames2/idstuff/unsup/idctf1.zip
* http://ftp.sunet.se/planetquake/threewave/ctf/misc/idctf1.zip
* http://ftp.sunet.se/pub/pc/games/idgames2/idstuff/unsup/idctf1.zip
* http://ftp.telepac.pt/pub/idgames2/idstuff/unsup/idctf1.zip
* http://gamers.org/pub/3dgamers/00archives/doom2/addons/idstuff/unsup/idctf1.zip
* http://gamers.org/pub/games/idgames/idstuff/unsup/idctf1.zip
* http://jord.sbc.edu/files/maps/idctf1.zip
* http://mirrors.syringanetworks.net/idgames/idstuff/unsup/idctf1.zip
* http://public.ftp.planetmirror.com/pub/idgames/idstuff/unsup/idctf1.zip
* http://quakemecca.simplenet.com/files/maps/idctf1.zip
* http://redwood.gatsbyhouse.com/files/ctf/idctf1.zip
* http://redwood.gatsbyhouse.com/quake/files/ctf/idctf1.zip
* http://redwood.stomped.com/files/ctf/idctf1.zip
* http://src.doc.ic.ac.uk/packages/idgames/idstuff/unsup/idctf1.zip
* http://sunsite.doc.ic.ac.uk/Mirrors/ftp.cdrom.com/pub/quake/idstuff/unsup/idctf1.zip
* http://sunsite.org.uk/packages/idgames2/idstuff/unsup/idctf1.zip
* http://threewave.planetquake.com/idctf1.zip
* http://wasatchfault.com/otherfiles/idctf1.zip
* http://www.bluesnews.com/files/idctf1.zip
* http://www.bluesnews.com/files/maps/idctf1.zip
* http://www.cdrom.com/pub/idgames2/idstuff/unsup/idctf1.zip
* http://www.cdrom.com/pub/idgames2/planetquake/academy/levels/idctf1.zip
* http://www.gameaholic.com/deicide/download.cgi?/idstuff/unsup/idctf1.zip
* http://www.gamers.org/pub/games/idgames/idstuff/idctf1.zip
* http://www.gamers.org/pub/games/idgames2/idstuff/unsup/idctf1.zip
* http://www.gamers.org/pub/idgames/idstuff/unsup/idctf1.zip
* http://www.gamers.org/pub/idgames2/idstuff/unsup/idctf1.zip
* http://www.gamers.org/pub/mirrors/ftp.idsoftware.com/unsup/idctf1.zip
* http://www.imaxx.net/~dakota/capture/FILES/idctf1.zip
* http://www.imaxx.net/~tabor/FILES/idctf1.zip
* http://www.minos.co.uk/idctf1.zip
* http://www.mirage.org/fanon/files/idctf1.zip
* http://www.planetquake.com/koc/files/idctf1.zip
* http://www.planetquake.com/quakex/threewave/idctf1.zip
* http://www.quakehole.com/files/bsp/idctf1.zip
* http://www.time2quake.com/filez/threewave/ctf/misc/idctf1.zip
* http://www.wasatchfault.com/otherfiles/idctf1.zip
* https://dukeworld.com/idgames/idstuff/unsup/idctf1.zip
* https://ftp.fu-berlin.de/pc/games/idgames/idstuff/unsup/idctf1.zip
* https://ftpmirror1.infania.net/pub/idgames/idstuff/unsup/idctf1.zip
* https://www.quaddicted.com/files/idgames/idstuff/unsup/idctf1.zip
* https://www.quaddicted.com/files/idgames2/idstuff/unsup/idctf1.zip
* https://www.quaddicted.com/files/idgames2/planetquake/threewave/ctf/misc/idctf1.zip
* https://www.quaddicted.com/files/maps/multiplayer/ctf/idctf1.zip
* https://www.quaddicted.com/files/mirrors/ftp.planetquake.com/threewave/ctf/misc/idctf1.zip
* https://www.quaddicted.com/files/mirrors/quakerepo.net/ctf/maps/idctf1.zip
* https://youfailit.net/pub/idgames/idstuff/unsup/idctf1.zip

The contents of the archive:

```text
-rw-rw-r--  0 0      0     1773560 30 Dec  1996 idctf1.bsp
-rw-rw-r--  0 0      0        1319 30 Dec  1996 idctf1.txt
```

The header of the readme:

```text
12-30-1996

=================================================
Title:          idctf1
File:           idctf1.bsp
Author:         Tim Willits
Email Address:  twillits@idsoftware.com
URL:            www.idsoftware.com
Description:    This map is e1m5 converted into a capture the flag level.

Additional
Credits:        Dave Kirsch (Zoid) for the CTF progs.
		Brian Cozzens (Whaleboy) for the additional GFX.
		John Cash for helpful input and beta testing
		Steve Tietze for helpful input and beta testing.
		Christain Antkow (Disruptor) for helpful input and beta
		testing.  And all the unnamed Rangers who helped test.
```

-- idctf1.txt

## QWCTF 1.1

The release was announced on BluesNews on January 2nd 1997:

> QuakeWorld CTF Grappling Hook\
> Apparently John Cash stepped up in the clutch and knocked off that last bug, so Threewave QuakeWorld CTF Server Version 1.1 has been released on Threewave. The new server includes the long awaited (well it seemed long) return of the grappling hook. This is an update to the server patch--clients do not need to download anything new.

-- [https://www.bluesnews.com/archives/dec96-4.html](https://www.bluesnews.com/archives/dec96-4.html)

Links:

* https://www.bluesnews.com/files/3wqw11.zip

It was also mentioned on QuakeHole:

> Threewave released the CTF QW server with the grappling hook!

-- [http://www.quakehole.com/frames/oldnews.html](https://web.archive.org/web/19971210064427/http://www.quakehole.com/frames/oldnews.html) (archived)

This release was announced on Shake N' Quake on January 2nd 1997 (mis-labelled 1996):

> 1-2-96, Thursday, 4:00 AM EST (O)\
> QuakeWorld CTF: Well, John Cash helped fix the bug with QW and the CTF Grappling Hook. So Threewave released QuakeWorld CTF Server v1.1 which is only the Server upgrade, the Client side does not need to be upgraded.

-- [http://www.canvasnet.com/quake/](https://web.archive.org/web/19990221161618/http://www.canvasnet.com/quake/) (archive)

Links:

* http://www.planetquake.com/quakex/threewave/
* ftp://ftp.canvasnet.com/quake/ctf/3wqw11.zip

The release was discussed on January 1st on Redwoods:

> 2:45p.m. CST\
> I saw on blue's that Zoid has one final bug in the Grappling Hook for QuakeWorld CTF that he talks about on Threewave. The bug is tough to pin down and doesn't always occur (I hate those) so he's asked id for help.

And again:

> 11:50p.m. CST
> Thanks to blue for emailing me with the info that the server code for the Grappling Hook (yep, the bug is squashed) is available. If you are just playing the game you DO NOT need this file, it's only for CTF server ops. Download 3wqw11.zip and check Threewave for more info.

-- [http://redwood.gatsbyhouse.com/quake/197.html](https://web.archive.org/web/19970327200851/http://redwood.gatsbyhouse.com/quake/197.html) (archived)

With links:

* http://redwood.gatsbyhouse.com/quake/files/ctf/3wqw11.zip

Historical locations for `3wqw11.zip` include:

* ftp://ftp.canvasnet.com/quake/ctf/3wqw11.zip
* ftp://ftp.cdrom.com/pub/quake/planetquake/threewave/ctf/server/3wqw11.zip
* ftp://ftp.stomped.com/pub/redwood/ctf/3wqw11.zip
* ftp://ftp.vision.net.au/pub/quake_stuff/extras/3wqw11.zip
* http://bluesnews.com/files/3wqw11.zip
* http://ftp.sunet.se/planetquake/threewave/ctf/server/3wqw11.zip
* http://jord.sbc.edu/dragon/files/ctf/3wqw11.zip
* http://jord.sbc.edu/files/ctf/3wqw11.zip
* http://quakemecca.simplenet.com/files/downloads/3wqw11.zip
* http://quakemecca.simplenet.com/files/downloads/files/downloads/3wqw11.zip
* http://redwood.gatsbyhouse.com/files/ctf/3wqw11.zip
* http://redwood.gatsbyhouse.com/quake/files/ctf/3wqw11.zip
* http://redwood.stomped.com/files/ctf/3wqw11.zip
* http://www.bluesnews.com/files/3wqw11.zip
* http://www.gore.org/files/qw/3wqw11.zip
* http://www.gore.org/files/server/3wqw11.zip
* http://www.imaxx.net/~dakota/capture/FILES/3wqw11.zip
* http://www.planetquake.com/quakex/threewave/3wqw11.zip
* http://www.time2quake.com/filez/threewave/ctf/server/3wqw11.zip
* https://www.quaddicted.com/files/idgames2/planetquake/threewave/ctf/server/3wqw11.zip
* https://www.quaddicted.com/files/mirrors/ftp.planetquake.com/threewave/ctf/server/3wqw11.zip

The content of the archive:

```text
-rw-rw-r--  0 0      0        1765  4 Oct  1996 capture.txt
-rw-rw-r--  0 0      0       19900  2 Jan  1997 server.txt
-rw-rw-r--  0 0      0         186 27 Dec  1996 server.cfg
-rw-rw-r--  0 0      0      243216  2 Jan  1997 progs.dat
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
-rw-rw-r--  0 0      0       48880 18 Oct  1996 maps/e4m5.ent
-rw-rw-r--  0 0      0       43154 19 Oct  1996 maps/e4m6.ent
-rw-rw-r--  0 0      0       46326 21 Oct  1996 maps/e4m4.ent
-rw-rw-r--  0 0      0       11745 23 Oct  1996 maps/dm6.ent
-rw-rw-r--  0 0      0       14410 31 Oct  1996 maps/dm3.ent
-rw-rw-r--  0 0      0         108 18 Oct  1996 maps/dobsp.bat
-rw-rw-r--  0 0      0          52  4 Oct  1996 maps/dobsp.sh
-rw-rw-r--  0 0      0       20328 31 Dec  1996 src/DEFS.QC
-rw-rw-r--  0 0      0        3051  4 Dec  1996 src/BUTTONS.QC
-rw-rw-r--  0 0      0         655  4 Dec  1996 src/CHARSET.TXT
-rw-rw-r--  0 0      0       49257  2 Jan  1997 src/CLIENT.QC
-rw-rw-r--  0 0      0        7742 14 Dec  1996 src/COMBAT.QC
-rw-rw-r--  0 0      0       33579  1 Jan  1997 src/WEAPONS.QC
-rw-rw-r--  0 0      0       17137 14 Dec  1996 src/DOORS.QC
-rw-rw-r--  0 0      0         224 28 Dec  1996 src/PROGS.SRC
-rw-rw-r--  0 0      0       38320  1 Jan  1997 src/TEAMPLAY.QC
-rw-rw-r--  0 0      0       35294  1 Jan  1997 src/ITEMS.QC
-rw-rw-r--  0 0      0       17068 29 Dec  1996 src/MISC.QC
-rw-rw-r--  0 0      0        9515  4 Dec  1996 src/MODELS.QC
-rw-rw-r--  0 0      0        8057  4 Dec  1996 src/PLATS.QC
-rw-rw-r--  0 0      0       19837 29 Dec  1996 src/PLAYER.QC
-rw-rw-r--  0 0      0       13412  1 Jan  1997 src/GRAPPLE.QC
-rw-rw-r--  0 0      0        2464  4 Dec  1996 src/SERVER.QC
-rw-rw-r--  0 0      0         473  4 Dec  1996 src/SPRITES.QC
-rw-rw-r--  0 0      0        5888  4 Dec  1996 src/SUBS.QC
-rw-rw-r--  0 0      0       15282 28 Dec  1996 src/TRIGGERS.QC
-rw-rw-r--  0 0      0        1560  4 Dec  1996 src/TELEFRAG.QC
-rw-rw-r--  0 0      0       12344 28 Dec  1996 src/WORLD.QC
-rw-rw-r--  0 0      0        2541  2 Jan  1997 src/PROGDEFS.H
-rw-rw-r--  0 0      0        6314  2 Jan  1997 src/FILES.DAT
-rw-rw-r--  0 0      0       29316  4 Dec  1996 skins/ctfr1.pcx
-rw-rw-r--  0 0      0       29346  4 Dec  1996 skins/ctfr2.pcx
-rw-rw-r--  0 0      0       29284  4 Dec  1996 skins/ctfb1.pcx
-rw-rw-r--  0 0      0       29316  4 Dec  1996 skins/ctfb2.pcx
-rw-rw-r--  0 0      0       30449  4 Dec  1996 skins/base.pcx
```

The header from the readme:

```text
Title    : Threewave QuakeWorld Capture
Filename : 3wqw11.zip
Version  : 1.10
Date     : 96-12-27
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
...
```
-- server.txt


## v4.0

Screenshots for the release were shared on the threewave homepage, announced on BluesNews on March 21st 1997:

> CTF 4.0 Screenshots\
> There are screenshots of Threewave Capture the Flag 4.0 up at Threewave. This is great looking stuff...

-- [https://www.bluesnews.com/archives/march97-3.html](https://www.bluesnews.com/archives/march97-3.html)

Which linked to:

* [http://www.planetquake.com/quakex/threewave/newstuff/index.html](https://web.archive.org/web/19970611034324/http://www.planetquake.com/quakex/threewave/newstuff/index.html) (archived)

All screenshots can be seen here:

* [http://www.planetquake.com/quakex/threewave/newstuff/full.html](https://web.archive.org/web/19970611070812/http://www.planetquake.com/quakex/threewave/newstuff/full.html) (archived)

A preparation announcement was made on BluesNews on April 15th 1997:

> CTF 4.0 Release Party\
> There is an eagerly-awaited announcement on Threewave that CTF 4.0 is going to be released tonight in an unprecedented online IRC party:
>
>> Come join the ThreeWave Gang for a online CTF4 Release party. The party starts at 6PM PST on the GamesNet IRC network. CTF4 will be released at the online gathering on channel #ThreeWave.

-- [https://www.bluesnews.com/archives/april97-2.html](https://www.bluesnews.com/archives/april97-2.html)

The release was announcement later that day on BluesNews:

> CTF 4.0
> Threewave Capture the Flag 4.0 has been released on (where else?) Threewave. Here's the Server (563 KB), and the Client (6.4 MB).

-- [https://www.bluesnews.com/archives/april97-2.html](https://www.bluesnews.com/archives/april97-2.html)

With links:

* http://www.planetquake.com/quakex/threewave/
* https://www.bluesnews.com/files/patches/threewave/3wave40.zip
* https://www.bluesnews.com/files/patches/threewave/3wctfc40.zip

The release was also announced on ShugaShack:

> 7:18pm CTF 4.0 Released!\
> Yes, it's out. go download it. I'll have it locally in a couple days when we move the pages. Check out ThreeWave to download the client or server. and YES, it has QuakeWorld 1.55 support.

-- [http://www.shugashack.com/archives/a18_a12.htm](https://web.archive.org/web/19991021234340/http://www.shugashack.com/archives/a18_a12.htm) (archived)

A huge announcement was made on Redwood's:

> 8:00p.m. CDT\
> As promised, Threewave's Capture The Flag 4.0 has been RELEASED!! You MUST have the 3.01 Client to play 4.0, as it is an add-on/upgrade. To play CTF4 on QuakeWorld servers you MUST have the QW 1.55 client. Here are the download locations:
>
> CTF 4 Servers up:
>
> 206.160.192.100 - Gatsbyhouse1-CTF 4\
> 206.160.192.101 - Gatsbyhouse2-CTF 4
>
> HTTP\
> 3WCTF 4.0 Client (6564k -Gatsbyhouse)\
> 3WCTF 4.0 Server (564k -Gatsbyhouse)\
> FTP\
> 3WCTF 4.0 Client (6564k -id sof)\
> 3WCTF 4.0 Server (564k - id soft)\
> 3WCTF 4.0 Client (6564k - Stomped)\
> 3WCTF 4.0 Server (564k - Stomped)\
> -More Download Sites\
> -3.01 Client (required)

-- [http://redwood.stomped.com/497.html](https://web.archive.org/web/20011031111944/http://redwood.stomped.com/497.html) (archived)

With many links.

Content of `3wave40.zip` archive:

```text
-rw-rw-r--  0 0      0       36218 14 Apr  1997 server.txt
-rw-rw-r--  0 0      0        1765  4 Oct  1996 capture.txt
-rw-rw-r--  0 0      0         157 13 Apr  1997 autoexec.cfg
-rw-rw-r--  0 0      0         126 13 Apr  1997 server.cfg
-rw-rw-r--  0 0      0      297480 14 Apr  1997 progs.dat
-rw-rw-r--  0 0      0      252352 14 Apr  1997 qwprogs.dat
-rw-rw-r--  0 0      0       30836 17 Sep  1996 maps/e1m1.ent
-rw-rw-r--  0 0      0       46724 19 Feb  1997 maps/e1m2.ent
-rw-rw-r--  0 0      0       52040 14 Apr  1997 maps/e1m3.ent
-rw-rw-r--  0 0      0       46337 25 Sep  1996 maps/e1m4.ent
-rw-rw-r--  0 0      0       45772 13 Apr  1997 maps/e1m5.ent
-rw-rw-r--  0 0      0       38838 23 Sep  1996 maps/e1m6.ent
-rw-rw-r--  0 0      0       39751 14 Apr  1997 maps/e1m8.ent
-rw-rw-r--  0 0      0       37653 14 Apr  1997 maps/e2m1.ent
-rw-rw-r--  0 0      0       30254 14 Apr  1997 maps/e2m2.ent
-rw-rw-r--  0 0      0       42776 14 Apr  1997 maps/e2m3.ent
-rw-rw-r--  0 0      0       45578  8 Oct  1996 maps/e2m5.ent
-rw-rw-r--  0 0      0       42672  7 Oct  1996 maps/e4m3.ent
-rw-rw-r--  0 0      0       48894 14 Apr  1997 maps/e4m5.ent
-rw-rw-r--  0 0      0       43154 19 Oct  1996 maps/e4m6.ent
-rw-rw-r--  0 0      0       46326 21 Oct  1996 maps/e4m4.ent
-rw-rw-r--  0 0      0       12603 14 Apr  1997 maps/dm6.ent
-rw-rw-r--  0 0      0       14410 31 Oct  1996 maps/dm3.ent
-rw-rw-r--  0 0      0       37621 13 Apr  1997 maps/e4m8.ent
-rw-rw-r--  0 0      0       34684 13 Apr  1997 maps/e3m7.ent
-rw-rw-r--  0 0      0       60417 28 Feb  1997 maps/e3m4.ent
-rw-rw-r--  0 0      0       55426 13 Apr  1997 maps/e2m7.ent
-rw-rw-r--  0 0      0       11376 14 Apr  1997 maps/dm5.ent
-rw-rw-r--  0 0      0       42640 25 Mar  1997 maps/e4m7.ent
-rw-rw-r--  0 0      0       68779 13 Apr  1997 maps/e3m6.ent
-rw-rw-r--  0 0      0       42952 13 Apr  1997 maps/e3m1.ent
-rw-rw-r--  0 0      0       10676 14 Apr  1997 maps/dm1.ent
-rw-rw-r--  0 0      0       20293 14 Apr  1997 maps/dm2.ent
-rw-rw-r--  0 0      0        9946 14 Apr  1997 maps/dm4.ent
-rw-rw-r--  0 0      0       15108  2 Feb  1997 maps/e1m7.ent
-rw-rw-r--  0 0      0       49057 14 Apr  1997 maps/e2m4.ent
-rw-rw-r--  0 0      0       49932 13 Apr  1997 maps/e2m6.ent
-rw-rw-r--  0 0      0       31582 13 Apr  1997 maps/e3m2.ent
-rw-rw-r--  0 0      0       35570 13 Apr  1997 maps/e3m3.ent
-rw-rw-r--  0 0      0       50483 25 Mar  1997 maps/e3m5.ent
-rw-rw-r--  0 0      0       43124 13 Apr  1997 maps/e4m1.ent
-rw-rw-r--  0 0      0       28258 25 Mar  1997 maps/e4m2.ent
-rw-rw-r--  0 0      0         108 18 Oct  1996 maps/dobsp.bat
-rw-rw-r--  0 0      0          52  4 Oct  1996 maps/dobsp.sh
-rw-rw-r--  0 0      0         409  2 Apr  1997 src/progs.src
-rw-rw-r--  0 0      0        7224  2 Apr  1997 src/combat.qc
-rw-rw-r--  0 0      0        2910  6 Oct  1996 src/buttons.qc
-rw-rw-r--  0 0      0       36589 14 Apr  1997 src/teamplay.qc
-rw-rw-r--  0 0      0       16416  2 Apr  1997 src/misc.qc
-rw-rw-r--  0 0      0       20321  7 Apr  1997 src/defs.qc
-rw-rw-r--  0 0      0        5601 15 Dec  1996 src/subs.qc
-rw-rw-r--  0 0      0       17138  6 Oct  1996 src/doors.qc
-rw-rw-r--  0 0      0       34770  9 Apr  1997 src/items.qc
-rw-rw-r--  0 0      0        7737 14 Apr  1997 src/plats.qc
-rw-rw-r--  0 0      0       18832 23 Nov  1996 src/player.qc
-rw-rw-r--  0 0      0       14259 19 Oct  1996 src/triggers.qc
-rw-rw-r--  0 0      0       11521 10 Apr  1997 src/world.qc
-rw-rw-r--  0 0      0        2598 14 Apr  1997 src/progdefs.h
-rw-rw-r--  0 0      0        1560 19 Oct  1996 src/telefrag.qc
-rw-rw-r--  0 0      0         808 31 Mar  1997 src/charset.txt
-rw-rw-r--  0 0      0        6426 14 Apr  1997 src/files.dat
-rw-rw-r--  0 0      0         650 29 Oct  1996 src/log.qc
-rw-rw-r--  0 0      0        6829 28 Mar  1997 src/hook.qc
-rw-rw-r--  0 0      0        6308 26 Mar  1997 src/observ.qc
-rw-rw-r--  0 0      0        2368 20 Dec  1996 src/server.qc
-rw-rw-r--  0 0      0        4121  2 Apr  1997 src/ctfgame.qc
-rw-rw-r--  0 0      0        1797  2 Apr  1997 src/ident.qc
-rw-rw-r--  0 0      0       16934 10 Apr  1997 src/camera.qc
-rw-rw-r--  0 0      0        5671 13 Apr  1997 src/status.qc
-rw-rw-r--  0 0      0       33574 14 Apr  1997 src/weapons.qc
-rw-rw-r--  0 0      0       52496 14 Apr  1997 src/client.qc
-rw-rw-r--  0 0      0       15417 14 Apr  1997 src/admin.qc
-rw-rw-r--  0 0      0        8204 14 Apr  1997 qwsrc/plats.qc
-rw-rw-r--  0 0      0        5888  4 Dec  1996 qwsrc/subs.qc
-rw-rw-r--  0 0      0       15316 21 Feb  1997 qwsrc/triggers.qc
-rw-rw-r--  0 0      0        4065  9 Apr  1997 qwsrc/ctfgame.qc
-rw-rw-r--  0 0      0        2541 14 Apr  1997 qwsrc/progdefs.h
-rw-rw-r--  0 0      0       12077  9 Apr  1997 qwsrc/world.qc
-rw-rw-r--  0 0      0       35890  7 Apr  1997 qwsrc/items.qc
-rw-rw-r--  0 0      0       17217 26 Feb  1997 qwsrc/doors.qc
-rw-rw-r--  0 0      0        1560  4 Dec  1996 qwsrc/telefrag.qc
-rw-rw-r--  0 0      0        3051  4 Dec  1996 qwsrc/buttons.qc
-rw-rw-r--  0 0      0         655  4 Dec  1996 qwsrc/charset.txt
-rw-rw-r--  0 0      0        7658  7 Apr  1997 qwsrc/combat.qc
-rw-rw-r--  0 0      0       21634  9 Apr  1997 qwsrc/defs.qc
-rw-rw-r--  0 0      0        6385 14 Apr  1997 qwsrc/files.dat
-rw-rw-r--  0 0      0       13284 21 Feb  1997 qwsrc/grapple.qc
-rw-rw-r--  0 0      0        9515  4 Dec  1996 qwsrc/models.qc
-rw-rw-r--  0 0      0       19879 21 Feb  1997 qwsrc/player.qc
-rw-rw-r--  0 0      0        2464  4 Dec  1996 qwsrc/server.qc
-rw-rw-r--  0 0      0         473  4 Dec  1996 qwsrc/sprites.qc
-rw-rw-r--  0 0      0       36912 13 Apr  1997 qwsrc/teamplay.qc
-rw-rw-r--  0 0      0        5495 13 Apr  1997 qwsrc/status.qc
-rw-rw-r--  0 0      0       17189 13 Apr  1997 qwsrc/misc.qc
-rw-rw-r--  0 0      0        1797  2 Apr  1997 qwsrc/IDENT.QC
-rw-rw-r--  0 0      0         263 13 Apr  1997 qwsrc/progs.src
-rw-rw-r--  0 0      0       35656 13 Apr  1997 qwsrc/weapons.qc
-rw-rw-r--  0 0      0       45359 14 Apr  1997 qwsrc/client.qc
```

Header of readme:

```text
Title    : Threewave Capture
Filename : 3wave40.zip
Version  : 4.00
Date     : 97-04-12
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
Info	 : This patch contains two versions of CTF4, for Regular Quake (1.06
	       or later) and QuakeWorld 1.55 or later.  Note that you need qwsv
           1.55 and qwcl 1.55 or later in order to play.
...
```

--- server.txt

Content of `3wctfc40.zip`:

```text
-rw-rw-r--  0 0      0    15233873 14 Apr  1997 pak1.pak
-rw-rw-r--  0 0      0        4557 14 Apr  1997 readme.txt
```

Content of readme:

```text
Title    : Threewave Capture
Filename : 3wctf40.zip
Version  : 4.00
Date     : 97-04-15
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
...
```

-- readme.txt


## v4.1

The release was announced on Redwood's on May 2nd 1997:

> :15p.m. CDT - Update by: Rob Selitto\
> CTF 4.1 Released\
> Get CTF 4.1 Now. Some of the new features are:
>
>> Server side only (clients do NOT need to download anything, just server operators). New status bar updates. There are small icons indicating the flag status (at base, carried or dropped) as well as captures, etc. There's also a new series of impulses to set the status bar position for players running in other resolutions then 320x200. Crossdressing is completely removed on the QW version (thanks onethumb!). There are also various bug fixes as well.

-- [http://redwood.stomped.com/597.html](https://web.archive.org/web/20011031112505/http://redwood.stomped.com/597.html) (archived)

Link:

* ftp://ftp.stomped.com/pub/redwood/ctf/3wave41.zip

This version was announced on BluesNews on May 3rd 1997:

> Threewave CTF 4.1\
> There's a new version of CTF on Threewave. This is a server patch only, with enhanced status bar code, and the complete elimination of cross-dressing in QuakeWorld CTF with the inclusion of OneThumb's code. Thanks TooooL.

-- [https://www.bluesnews.com/archives/may97-1.html](https://www.bluesnews.com/archives/may97-1.html)

The release was also mentioned on ShugaShack on May 3rd:

> CTF 4.1\
> Damn.. sorry Zoid, forgot to mention this yesterday. ThreeWave has a server patch with status bar stuff etc. Pretty nifty. If you dont run a server though, you dont need it.

-- [http://www.shugashack.com/archives/m3_a27.htm](https://web.archive.org/web/20010121184600/http://www.shugashack.com/archives/m3_a27.htm) (archived)

Contents of `3wave41.zip`:

```text
-rw-rw-r--  0 0      0       36523  2 May  1997 server.txt
-rw-rw-r--  0 0      0        1765  4 Oct  1996 capture.txt
-rw-rw-r--  0 0      0         161  2 May  1997 autoexec.cfg
-rw-rw-r--  0 0      0         128  2 May  1997 server.cfg
-rw-rw-r--  0 0      0      287156  2 May  1997 progs.dat
-rw-rw-r--  0 0      0      257832  2 May  1997 qwprogs.dat
-rw-rw-r--  0 0      0       30836 17 Sep  1996 maps/e1m1.ent
-rw-rw-r--  0 0      0       46724 19 Feb  1997 maps/e1m2.ent
-rw-rw-r--  0 0      0       52040 14 Apr  1997 maps/e1m3.ent
-rw-rw-r--  0 0      0       46337 25 Sep  1996 maps/e1m4.ent
-rw-rw-r--  0 0      0       45772 13 Apr  1997 maps/e1m5.ent
-rw-rw-r--  0 0      0       38838 23 Sep  1996 maps/e1m6.ent
-rw-rw-r--  0 0      0       39751 14 Apr  1997 maps/e1m8.ent
-rw-rw-r--  0 0      0       37653 14 Apr  1997 maps/e2m1.ent
-rw-rw-r--  0 0      0       30254 14 Apr  1997 maps/e2m2.ent
-rw-rw-r--  0 0      0       42776 14 Apr  1997 maps/e2m3.ent
-rw-rw-r--  0 0      0       45578  8 Oct  1996 maps/e2m5.ent
-rw-rw-r--  0 0      0       42672  7 Oct  1996 maps/e4m3.ent
-rw-rw-r--  0 0      0       48894 14 Apr  1997 maps/e4m5.ent
-rw-rw-r--  0 0      0       43154 19 Oct  1996 maps/e4m6.ent
-rw-rw-r--  0 0      0       46326 21 Oct  1996 maps/e4m4.ent
-rw-rw-r--  0 0      0       12603 14 Apr  1997 maps/dm6.ent
-rw-rw-r--  0 0      0       14410 31 Oct  1996 maps/dm3.ent
-rw-rw-r--  0 0      0       37621 13 Apr  1997 maps/e4m8.ent
-rw-rw-r--  0 0      0       34684 13 Apr  1997 maps/e3m7.ent
-rw-rw-r--  0 0      0       60417 28 Feb  1997 maps/e3m4.ent
-rw-rw-r--  0 0      0       55426 13 Apr  1997 maps/e2m7.ent
-rw-rw-r--  0 0      0       11376 14 Apr  1997 maps/dm5.ent
-rw-rw-r--  0 0      0       42640 25 Mar  1997 maps/e4m7.ent
-rw-rw-r--  0 0      0       68779 13 Apr  1997 maps/e3m6.ent
-rw-rw-r--  0 0      0       42952 13 Apr  1997 maps/e3m1.ent
-rw-rw-r--  0 0      0       10676 14 Apr  1997 maps/dm1.ent
-rw-rw-r--  0 0      0       20293 14 Apr  1997 maps/dm2.ent
-rw-rw-r--  0 0      0        9946 14 Apr  1997 maps/dm4.ent
-rw-rw-r--  0 0      0       15108  2 Feb  1997 maps/e1m7.ent
-rw-rw-r--  0 0      0       49057 14 Apr  1997 maps/e2m4.ent
-rw-rw-r--  0 0      0       49932 13 Apr  1997 maps/e2m6.ent
-rw-rw-r--  0 0      0       31582 13 Apr  1997 maps/e3m2.ent
-rw-rw-r--  0 0      0       35570 13 Apr  1997 maps/e3m3.ent
-rw-rw-r--  0 0      0       50483 25 Mar  1997 maps/e3m5.ent
-rw-rw-r--  0 0      0       43124 13 Apr  1997 maps/e4m1.ent
-rw-rw-r--  0 0      0       28258 25 Mar  1997 maps/e4m2.ent
-rw-rw-r--  0 0      0         108 18 Oct  1996 maps/dobsp.bat
-rw-rw-r--  0 0      0          52  4 Oct  1996 maps/dobsp.sh
-rw-rw-r--  0 0      0        7224  2 Apr  1997 src/combat.qc
-rw-rw-r--  0 0      0        2910  6 Oct  1996 src/buttons.qc
-rw-rw-r--  0 0      0       16416  2 Apr  1997 src/misc.qc
-rw-rw-r--  0 0      0       20321  7 Apr  1997 src/defs.qc
-rw-rw-r--  0 0      0        5601 15 Dec  1996 src/subs.qc
-rw-rw-r--  0 0      0       17138  6 Oct  1996 src/doors.qc
-rw-rw-r--  0 0      0       34770  9 Apr  1997 src/items.qc
-rw-rw-r--  0 0      0        7737 14 Apr  1997 src/plats.qc
-rw-rw-r--  0 0      0       18832 23 Nov  1996 src/player.qc
-rw-rw-r--  0 0      0       14259 19 Oct  1996 src/triggers.qc
-rw-rw-r--  0 0      0       11521 10 Apr  1997 src/world.qc
-rw-rw-r--  0 0      0        2598  2 May  1997 src/progdefs.h
-rw-rw-r--  0 0      0        1560 19 Oct  1996 src/telefrag.qc
-rw-rw-r--  0 0      0         808 31 Mar  1997 src/charset.txt
-rw-rw-r--  0 0      0        6426  2 May  1997 src/files.dat
-rw-rw-r--  0 0      0         756  1 May  1997 src/log.qc
-rw-rw-r--  0 0      0        6961 29 Apr  1997 src/hook.qc
-rw-rw-r--  0 0      0        2368 20 Dec  1996 src/server.qc
-rw-rw-r--  0 0      0        4121  2 Apr  1997 src/ctfgame.qc
-rw-rw-r--  0 0      0         282 22 Apr  1997 src/notes.txt
-rw-rw-r--  0 0      0         399  1 May  1997 src/progs.src
-rw-rw-r--  0 0      0        6162  1 May  1997 src/observ.qc
-rw-rw-r--  0 0      0       15192  1 May  1997 src/admin.qc
-rw-rw-r--  0 0      0       33876  2 May  1997 src/weapons.qc
-rw-rw-r--  0 0      0       36816  2 May  1997 src/teamplay.qc
-rw-rw-r--  0 0      0       52270  2 May  1997 src/client.qc
-rw-rw-r--  0 0      0        9190  2 May  1997 src/status.qc
-rw-rw-r--  0 0      0        1797  2 May  1997 src/ident.qc
-rw-rw-r--  0 0      0        8204 14 Apr  1997 qwsrc/plats.qc
-rw-rw-r--  0 0      0       13427 29 Apr  1997 qwsrc/grapple.qc
-rw-rw-r--  0 0      0        5888  4 Dec  1996 qwsrc/subs.qc
-rw-rw-r--  0 0      0       15316 21 Feb  1997 qwsrc/triggers.qc
-rw-rw-r--  0 0      0        4065  9 Apr  1997 qwsrc/ctfgame.qc
-rw-rw-r--  0 0      0        2541  2 May  1997 qwsrc/progdefs.h
-rw-rw-r--  0 0      0       12077  9 Apr  1997 qwsrc/world.qc
-rw-rw-r--  0 0      0       17217 26 Feb  1997 qwsrc/doors.qc
-rw-rw-r--  0 0      0        1560  4 Dec  1996 qwsrc/telefrag.qc
-rw-rw-r--  0 0      0        3051  4 Dec  1996 qwsrc/buttons.qc
-rw-rw-r--  0 0      0         655  4 Dec  1996 qwsrc/charset.txt
-rw-rw-r--  0 0      0        7658  7 Apr  1997 qwsrc/combat.qc
-rw-rw-r--  0 0      0       21634  9 Apr  1997 qwsrc/defs.qc
-rw-rw-r--  0 0      0        6385  2 May  1997 qwsrc/files.dat
-rw-rw-r--  0 0      0        9515  4 Dec  1996 qwsrc/models.qc
-rw-rw-r--  0 0      0       19879 21 Feb  1997 qwsrc/player.qc
-rw-rw-r--  0 0      0        2464  4 Dec  1996 qwsrc/server.qc
-rw-rw-r--  0 0      0         473  4 Dec  1996 qwsrc/sprites.qc
-rw-rw-r--  0 0      0       17189 13 Apr  1997 qwsrc/misc.qc
-rw-rw-r--  0 0      0         263 13 Apr  1997 qwsrc/progs.src
-rw-rw-r--  0 0      0       35913  1 May  1997 qwsrc/items.qc
-rw-rw-r--  0 0      0       35994  2 May  1997 qwsrc/weapons.qc
-rw-rw-r--  0 0      0       38101  2 May  1997 qwsrc/teamplay.qc
-rw-rw-r--  0 0      0       45600  2 May  1997 qwsrc/client.qc
-rw-rw-r--  0 0      0        9346  2 May  1997 qwsrc/status.qc
-rw-rw-r--  0 0      0        1797  2 May  1997 qwsrc/ident.qc
```

Header of readme:

```text
Title    : Threewave Capture
Filename : 3wave41.zip
Version  : 4.10
Date     : 97-05-02
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
Info	 : This patch contains two versions of CTF4, for Regular Quake (1.06
	       or later) and QuakeWorld 1.55 or later.  Note that you need qwsv
           1.55 and qwcl 1.55 or later in order to play.
...
```

-- server.txt


## v4.0 Client Update

An update to the v4.0 CTF client was released as `3wctfc.zip` on June 3rd 1997.

No announcement for the release has been located yet.

The contents of the archive:

```text
-rw-rw-r--  0 0      0     9701080 22 Nov  1996 pak0.pak
-rw-rw-r--  0 0      0    15233873 14 Apr  1997 pak1.pak
-rw-rw-r--  0 0      0        5338  3 Jun  1997 readme.txt
```

The header of the readme:

```text
Title    : Threewave Capture the Flag
Filename : 3wctfc.zip
Version  : 4.00
Date     : 97-06-02
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
...
```

-- readme.txt


## v4.2

Development of the release was announced on BluesNews on June 5th 1997:

> Zoid on QuakeWorld and CTF 4.2\
> Zoid has posted word on Threewave that he's planning a bug-fixed Threewave CTF 4.2 "soon". [...]

-- [https://www.bluesnews.com/archives/may97-5.html](https://www.bluesnews.com/archives/may97-5.html)

This was also mentioned on Redwood's:

> Zoid QW/CTF 4.2 Update\
> Zoid has updated Threewave with what he and Jack are doing on QuakeWorld and also a little about CTF 4.2. Thanks to DaKoTa for that news tip.

-- [http://redwood.stomped.com/697.html](https://web.archive.org/web/20010830150348/http://redwood.stomped.com/697.html) (archived)

This was intended to be the final release of the mod.

Zoid shared a large message on the threewave homepage detailing the history of the mod and the impact it had.

> The Final Capture\
> Server operators can download 3wave42.zip now for the Threewave CTF 4.2 upgrade.
>
> The last year has been a strange and wonderful experience for me. I've always been a game player and a programmer. But, fate had me working at ISPs instead of writing games--my favorite passion. In August '96, Quake came out and changed my life. I played some DooM, but never really did any modifications to it. Quake was different--one of my passions was multiplayer gaming. I remember playing hours and hours on an old multiline BBS system with a game called Infinity Complex (some old timers might remember this). Infinity Complex was essentially a multiplayer, text version of Quake. Since then, I had developed a deep interest in multiplayer gaming and have worked on projects related to it in the ISP field, but nothing substancial.
>
> When Quake came out, I could do real time, high action first person graphical gameplay over the Internet! The high speed action game of the future had arrived. I wanted to play and keep playing it. But something was missing.
>
> The problem, as I saw it, was either you were good and at the top of the score list, or you sucked and where at the bottom. Middle didn't count, it was the first place position that did. Due to differences in ping, skill level and other factors, it soon became boring. I had ISDN, so I tended to slaughter the modem players again and again.
>
> My first experiments were with simple teamplay. Assigning players to teams and deathmatching. But it wasn't successful--there was no coordination and it broke down into 'don't shoot guys same color as you.' There had to be something better. That something was giving a goal for the team.
>
> In two evenings, I sat down and wrote the prototype of CTF. E1M4, The Grisly Grotto was the first level I modified for CTF. I threw it up on my server and explained it to the players there. First it was just confusion, then things started getting organized. There were defenders, offensive units, rovers (middle men) and other organized teamplay units. After that first night, I came back a couple of days later and found the server full. People couldn't get enough of it (and the same level had been running for three days!). In fact, I thought people were going to get bored of the same level over and over and I tried to reset back to deathmatch for a change. All the players screamed at me to put CTF back. It was then I knew I was on to something.
>
> For history's record, the runes and the grapple were already on my server before CTF was. I installed the grapple shortly after I first saw it. It was an incredible weapon and tool and changed the game--offering unbelievable mobility. The Runes were something I invented with a friend as a variation on deathmatch. I saw them in the single player game and wanted them as part of the multiplayer game experience. Their powers grew out of their names (black for strength, hell for haste, etc).
>
> Soon I had modified E1M1: The Slipgate Complex for CTF as well. Even today it's one of my favorite maps for four on four to six on six. The bases, though quite different in design, are actually pretty balanced. I just played it again a few nights ago and it as fun as I remembered.
>
> After modifying more maps, CTF started getting more popular. I had up to three Quake servers running it in the hey day. Blue posted about it on blue's news and suddenly I saw other CTF servers appearing. My mailbox exploded with interest.
>
> I released 2.0 which added some bug fixes and support for many more maps (modified id maps, that is). 2.0 was still with the keys as flags, the vore 'ball' for the grapple with the spikes. There are people who play CTF today that have never seen the medieval keys floating in the bases. Sorry, getting nostalgic.
>
> After 2.0, I was spending time on #quakeed on IRC. There was talk of a custom version--CTF with new maps, graphics, etc. A partial TC, so to speak. I gathered some map volunteers, artists and other contributors and worked for almost two months coordinating the project. There were a few public betas (my servers got overloaded with the first beta that had three maps) and eventually the package got finally put together.
>
> On November 21th, 1996, ThreeWave CTF 3.0 was released. It contained new models, sound effects, skins, levels, textures, etc. It was the first level expansion pack released for Quake and quickly became a must-have download. The four megabyte map addon was download over 5,000 times in the first day--the response was overwhelming.
>
> With the release of Threewave CTF 3.0 and its success, I ceased working in the ISP industry to pursue a career in game development. I was involved with a few projects, but not much worked out. I continued working on CTF, releasing new versions and fixes. In Feburary, I began work on CTF4 and released it on April 4th, 1997.
>
> I had always been a big fan of Unix and the Linux community in particular. John Carmack at id software recognized my interest in this and appointed me in charge of the Unix/Linux ports of Quake. I produced a Linux client and servers for various operating systems.
>
> As for the future of CTF, I will no longer be updating CTF for Quake. 4.2 will be my last release for Quake and QuakeWorld. I have begun a contract with id software to work on the software development of Quake2 as well as integrating a CTF teamplay mode into Quake2 as well. As far as I am concerned, CTF for Quake is done and has no more evolution. Some people are working on expansion packs, derivitives (ThunderWalker CTF, the CTF Expansion Project, etc.) and other addons. To them I give my blessing. It is exciting to me to see where people are talking my product and modifying it.
>
> I am handing over the maintenance of Threewave CTF for Quake to the Xenocide Flag Academy and to Dakota in particular. The work and support they have given CTF is phenomenal and much appreciated by me. There won't be any new versions of Threewave CTF, but they will keep track of additions and new versions other people are working on.
>
> It's been a long road, almost a year now. I'd like to thank everyone in the community that has contributed to CTF (the list is very long). It is time to move onto the next step and I hope everyone will be playing Quake2 and the CTF I will be building into it.  For Updates, head over to: Xenocide Flag Academy
>
> /// Zoid.

-- [http://threewave.planetquake.com/](https://web.archive.org/web/19971224200252/http://threewave.planetquake.com/) (archived)

The release was announced on Redwood's on July 25th 1997:

> July 25, 1997 11:00 p.m. CDT - Update by: RonSolo\
> CTF 4.2\
> Zoid has announced CTF 4.2 and wrote up a neat history of CTF at Threewave. The upgrade (for server operators) is now available at cdrom.com. Download 3wave42.zip (560k - Server side patch only).

-- [http://redwood.stomped.com/797.html](https://web.archive.org/web/20011125210253/http://redwood.stomped.com/797.html) (archived)

The release was announced on BluesNews on July 26th 1997:

> CTF 4.2\
Zoid has released Threewave Capture the Flag 4.2 (559 KB) on Threewave (only required for servers). Thanks DeathMonger[MD]. According to the accompanying update, this is the final version of CTF for Quake, as Zoid will now be concentrating on the version of CTF that will be built into Quake 2. Further updates to the Threewave site will now be handled by DaKoTa of the Xenocide Flag Academy, who is clearly a fine choice for the post. As a way of commemorating the final CTF, Zoid wrote up a history of the patch from it's origination through today. It's funny that he mentioned the first posting here, because I actually remember it well (I just dug through the archives, it was October 2, 1996), as I was doing my updates from a road trip to Virginia at the time. Excuse me while I wax nostalgic...

-- [https://www.bluesnews.com/archives/july97-4.html](https://www.bluesnews.com/archives/july97-4.html)

With links:

* https://www.bluesnews.com/files/patches/threewave/3wave42.zip

The release was announced on ShugaShack on the 26th:

> CTF v4.2\
> Server admin's rejoice, the final version of ThreeWave CTF has been released. grab the file here and have a blast.

-- [http://www.shugashack.com/archives/j26_j21.htm](https://web.archive.org/web/20000816012603/http://www.shugashack.com/archives/j26_j21.htm) (archived)

Content of `3wave42.zip`:

```text
-rw-rw-r--  0 0      0       36639 24 Jul  1997 server.txt
-rw-rw-r--  0 0      0        1765  4 Oct  1996 capture.txt
-rw-rw-r--  0 0      0         161  2 May  1997 autoexec.cfg
-rw-rw-r--  0 0      0         144 12 Jul  1997 server.cfg
-rw-rw-r--  0 0      0      287564 24 Jul  1997 progs.dat
-rw-rw-r--  0 0      0      258920 24 Jul  1997 qwprogs.dat
-rw-rw-r--  0 0      0       30836 17 Sep  1996 maps/e1m1.ent
-rw-rw-r--  0 0      0       46724 19 Feb  1997 maps/e1m2.ent
-rw-rw-r--  0 0      0       52040 14 Apr  1997 maps/e1m3.ent
-rw-rw-r--  0 0      0       46337 25 Sep  1996 maps/e1m4.ent
-rw-rw-r--  0 0      0       45772 13 Apr  1997 maps/e1m5.ent
-rw-rw-r--  0 0      0       38838 23 Sep  1996 maps/e1m6.ent
-rw-rw-r--  0 0      0       39751 14 Apr  1997 maps/e1m8.ent
-rw-rw-r--  0 0      0       37653 14 Apr  1997 maps/e2m1.ent
-rw-rw-r--  0 0      0       30254 14 Apr  1997 maps/e2m2.ent
-rw-rw-r--  0 0      0       42776 14 Apr  1997 maps/e2m3.ent
-rw-rw-r--  0 0      0       45578  8 Oct  1996 maps/e2m5.ent
-rw-rw-r--  0 0      0       42672  7 Oct  1996 maps/e4m3.ent
-rw-rw-r--  0 0      0       48894 14 Apr  1997 maps/e4m5.ent
-rw-rw-r--  0 0      0       43154 19 Oct  1996 maps/e4m6.ent
-rw-rw-r--  0 0      0       46326 21 Oct  1996 maps/e4m4.ent
-rw-rw-r--  0 0      0       12603 14 Apr  1997 maps/dm6.ent
-rw-rw-r--  0 0      0       14410 31 Oct  1996 maps/dm3.ent
-rw-rw-r--  0 0      0       37621 13 Apr  1997 maps/e4m8.ent
-rw-rw-r--  0 0      0       34684 13 Apr  1997 maps/e3m7.ent
-rw-rw-r--  0 0      0       60417 28 Feb  1997 maps/e3m4.ent
-rw-rw-r--  0 0      0       55426 13 Apr  1997 maps/e2m7.ent
-rw-rw-r--  0 0      0       11376 14 Apr  1997 maps/dm5.ent
-rw-rw-r--  0 0      0       42640 25 Mar  1997 maps/e4m7.ent
-rw-rw-r--  0 0      0       68779 13 Apr  1997 maps/e3m6.ent
-rw-rw-r--  0 0      0       42952 13 Apr  1997 maps/e3m1.ent
-rw-rw-r--  0 0      0       10676 14 Apr  1997 maps/dm1.ent
-rw-rw-r--  0 0      0       20293 14 Apr  1997 maps/dm2.ent
-rw-rw-r--  0 0      0        9946 14 Apr  1997 maps/dm4.ent
-rw-rw-r--  0 0      0       15108  2 Feb  1997 maps/e1m7.ent
-rw-rw-r--  0 0      0       49057 14 Apr  1997 maps/e2m4.ent
-rw-rw-r--  0 0      0       49932 13 Apr  1997 maps/e2m6.ent
-rw-rw-r--  0 0      0       31582 13 Apr  1997 maps/e3m2.ent
-rw-rw-r--  0 0      0       35570 13 Apr  1997 maps/e3m3.ent
-rw-rw-r--  0 0      0       50483 25 Mar  1997 maps/e3m5.ent
-rw-rw-r--  0 0      0       43124 13 Apr  1997 maps/e4m1.ent
-rw-rw-r--  0 0      0       28258 25 Mar  1997 maps/e4m2.ent
-rw-rw-r--  0 0      0         108 18 Oct  1996 maps/dobsp.bat
-rw-rw-r--  0 0      0          52  4 Oct  1996 maps/dobsp.sh
-rw-rw-r--  0 0      0       36824  5 May  1997 src/teamplay.qc
-rw-rw-r--  0 0      0        2910  6 Oct  1996 src/buttons.qc
-rw-rw-r--  0 0      0       16416  2 Apr  1997 src/misc.qc
-rw-rw-r--  0 0      0        5601 15 Dec  1996 src/subs.qc
-rw-rw-r--  0 0      0       17138  6 Oct  1996 src/doors.qc
-rw-rw-r--  0 0      0       14259 19 Oct  1996 src/triggers.qc
-rw-rw-r--  0 0      0       11521 10 Apr  1997 src/world.qc
-rw-rw-r--  0 0      0        2598 24 Jul  1997 src/progdefs.h
-rw-rw-r--  0 0      0        1560 19 Oct  1996 src/telefrag.qc
-rw-rw-r--  0 0      0         808 31 Mar  1997 src/charset.txt
-rw-rw-r--  0 0      0        6426 24 Jul  1997 src/files.dat
-rw-rw-r--  0 0      0         756  1 May  1997 src/log.qc
-rw-rw-r--  0 0      0        6961 29 Apr  1997 src/hook.qc
-rw-rw-r--  0 0      0        2368 20 Dec  1996 src/server.qc
-rw-rw-r--  0 0      0        4121  2 Apr  1997 src/ctfgame.qc
-rw-rw-r--  0 0      0         282 22 Apr  1997 src/notes.txt
-rw-rw-r--  0 0      0         399  1 May  1997 src/progs.src
-rw-rw-r--  0 0      0        6162  1 May  1997 src/observ.qc
-rw-rw-r--  0 0      0       15192  1 May  1997 src/admin.qc
-rw-rw-r--  0 0      0       33876  2 May  1997 src/weapons.qc
-rw-rw-r--  0 0      0        1797  2 May  1997 src/ident.qc
-rw-rw-r--  0 0      0       18832 30 May  1997 src/player.qc
-rw-rw-r--  0 0      0        7732 21 Jun  1997 src/plats.qc
-rw-rw-r--  0 0      0        7310 22 Jun  1997 src/combat.qc
-rw-rw-r--  0 0      0       20421 12 Jul  1997 src/defs.qc
-rw-rw-r--  0 0      0       52315 12 Jul  1997 src/client.qc
-rw-rw-r--  0 0      0       35115 12 Jul  1997 src/items.qc
-rw-rw-r--  0 0      0        9190 24 Jul  1997 src/status.qc
-rw-rw-r--  0 0      0       35521 14 Jul  1997 qwsrc/weapons.qc
-rw-rw-r--  0 0      0        8199 21 Jun  1997 qwsrc/plats.qc
-rw-rw-r--  0 0      0        5888  4 Dec  1996 qwsrc/subs.qc
-rw-rw-r--  0 0      0       15261 14 Jul  1997 qwsrc/triggers.qc
-rw-rw-r--  0 0      0        4065  9 Apr  1997 qwsrc/ctfgame.qc
-rw-rw-r--  0 0      0        2541 24 Jul  1997 qwsrc/progdefs.h
-rw-rw-r--  0 0      0       12077  9 Apr  1997 qwsrc/world.qc
-rw-rw-r--  0 0      0       45602 14 Jul  1997 qwsrc/client.qc
-rw-rw-r--  0 0      0       17217 26 Feb  1997 qwsrc/doors.qc
-rw-rw-r--  0 0      0        1560  4 Dec  1996 qwsrc/telefrag.qc
-rw-rw-r--  0 0      0        3051  4 Dec  1996 qwsrc/buttons.qc
-rw-rw-r--  0 0      0       38235 20 Jun  1997 qwsrc/teamplay.qc
-rw-rw-r--  0 0      0         655  4 Dec  1996 qwsrc/charset.txt
-rw-rw-r--  0 0      0        7749 22 Jun  1997 qwsrc/combat.qc
-rw-rw-r--  0 0      0       21633 14 Jul  1997 qwsrc/defs.qc
-rw-rw-r--  0 0      0        6385 24 Jul  1997 qwsrc/files.dat
-rw-rw-r--  0 0      0       35168 12 Jul  1997 qwsrc/items.qc
-rw-rw-r--  0 0      0        9515  4 Dec  1996 qwsrc/models.qc
-rw-rw-r--  0 0      0        2464  4 Dec  1996 qwsrc/server.qc
-rw-rw-r--  0 0      0         473  4 Dec  1996 qwsrc/sprites.qc
-rw-rw-r--  0 0      0       13446 21 Jul  1997 qwsrc/grapple.qc
-rw-rw-r--  0 0      0       17189 13 Apr  1997 qwsrc/misc.qc
-rw-rw-r--  0 0      0         263 13 Apr  1997 qwsrc/progs.src
-rw-rw-r--  0 0      0        1797  2 May  1997 qwsrc/ident.qc
-rw-rw-r--  0 0      0       19937 30 May  1997 qwsrc/player.qc
-rw-rw-r--  0 0      0        9347  4 Jun  1997 qwsrc/status.qc
```


Head from readme file:

```text
Title    : Threewave Capture
Filename : 3wave41.zip
Version  : 4.10
Date     : 97-05-02
Author   : Dave 'Zoid' Kirsch
Email    : zoid@threewave.com
Info	 : This patch contains two versions of CTF4, for Regular Quake (1.06
	       or later) and QuakeWorld 1.55 or later.  Note that you need qwsv
           1.55 and qwcl 1.55 or later in order to play.
...
```

-- server.txt

## v4.21

News for the release was posted on the then official home at `http://www.captured.com/threewave/`:


> CTF4.21 Update\
> Two serious bugs have appeared recently. One in the NetQuake version to do with server logging and one in the QuakeWorld version to do with the grapple. I'm releasing a 4.21 as a very minor patch to the 4.2 code that addresses these two problems. I had no plans to make another release, but these two bugs are serious enough to warrant it. Here is the 4.21 archive (it only contains the new progs, no docs). The 3wave42.zip archive contains full documentation.

-- [http://www.captured.com/threewave/](https://web.archive.org/web/19981202093403/http://www.captured.com/threewave/) (archived)

With links:

* http://www.cdrom.com/pub/quake/planetquake/threewave/ctf/server/3wave421.zip
* http://www.cdrom.com/pub/quake/planetquake/threewave/ctf/server/3wave42.zip

The news suggests that a second version of `3wave42.zip` was released at this time with updated progs.

A copy of this updated version appears on [(Czech) Gamestar 0 (1998-10) CD](https://archive.org/details/czgamestar0cd).

This version was announced on BluesNews on December 5th 1997:

> New CTF\
Though Zoid expected to release no more versions of CTF, a couple of bugs serious enough to warrant an update popped up, so a Threewave CTF 4.21 update (354 KB, sorry about the bad zip originally, thanks Origen =Aster= for the heads up) has been released (required for the server end only). Here's this scoop straight from Threewave (thanks Dakota):
>
>> Two serious bugs have appeared recently. One in the NetQuake version to do with server logging and one in the QuakeWorld version to do with the grapple. I'm releasing a 4.21 as a very minor patch to the 4.2 code that addresses these two problems. I had no plans to make another release, but these two bugs are serious enough to warrant it. Here is the 4.21 archive (it only contains the new progs, no docs). The 3wave42.zip archive contains full documentation.

-- [https://www.bluesnews.com/archives/nov97-5.html](https://www.bluesnews.com/archives/nov97-5.html)

With link:

* https://www.bluesnews.com/files/patches/threewave/3wave421.zip

It was also mentioned on ShugaShack:

> CTF v4.21\
> Zoid has released a minor patch for CTF server admins to use. A couple of bugs have finally popped up in the code that needed to be addressed. Zoid didnt plan on releasing anymore CTF versions, but well, here it is from homeboy himself:
>
>> Two serious bugs have appeared recently. One in the NetQuake version to do with server logging and one in the QuakeWorld version to do with the grapple. I'm releasing a 4.21 as a very minor patch to the 4.2 code that addresses these two problems. I had no plans to make another release, but these two bugs are serious enough to warrant it. Here is the 4.21 archive (it only contains the new progs, no docs). The 3wave42.zip archive contains full documentation.

-- [http://www.shugashack.com/archives/d6_n30.htm](https://web.archive.org/web/20000816012328/http://www.shugashack.com/archives/d6_n30.htm) (archived)


Content of `3wave421.zip`:

```text
-rw-rw-r--  0 0      0         527  5 Dec  1997 readme.txt
-rw-rw-r--  0 0      0      287492  5 Dec  1997 progs.dat
-rw-rw-r--  0 0      0      262204  5 Dec  1997 qwprogs.dat
-rw-rw-r--  0 0      0       36824  5 May  1997 src/teamplay.qc
-rw-rw-r--  0 0      0        2910  6 Oct  1996 src/buttons.qc
-rw-rw-r--  0 0      0        9194  5 Dec  1997 src/status.qc
-rw-rw-r--  0 0      0       16416  2 Apr  1997 src/misc.qc
-rw-rw-r--  0 0      0        5601 15 Dec  1996 src/subs.qc
-rw-rw-r--  0 0      0       17138  6 Oct  1996 src/doors.qc
-rw-rw-r--  0 0      0       14259 19 Oct  1996 src/triggers.qc
-rw-rw-r--  0 0      0       11521 10 Apr  1997 src/world.qc
-rw-rw-r--  0 0      0        2598  5 Dec  1997 src/progdefs.h
-rw-rw-r--  0 0      0        1560 19 Oct  1996 src/telefrag.qc
-rw-rw-r--  0 0      0         808 31 Mar  1997 src/charset.txt
-rw-rw-r--  0 0      0        6426  5 Dec  1997 src/files.dat
-rw-rw-r--  0 0      0        6961 29 Apr  1997 src/hook.qc
-rw-rw-r--  0 0      0        2368 20 Dec  1996 src/server.qc
-rw-rw-r--  0 0      0        4121  2 Apr  1997 src/ctfgame.qc
-rw-rw-r--  0 0      0         282 22 Apr  1997 src/notes.txt
-rw-rw-r--  0 0      0         399  1 May  1997 src/progs.src
-rw-rw-r--  0 0      0        6162  1 May  1997 src/observ.qc
-rw-rw-r--  0 0      0       15192  1 May  1997 src/admin.qc
-rw-rw-r--  0 0      0       33876  2 May  1997 src/weapons.qc
-rw-rw-r--  0 0      0        1797  2 May  1997 src/ident.qc
-rw-rw-r--  0 0      0       18832 30 May  1997 src/player.qc
-rw-rw-r--  0 0      0        7732 21 Jun  1997 src/plats.qc
-rw-rw-r--  0 0      0        7310 22 Jun  1997 src/combat.qc
-rw-rw-r--  0 0      0       20421 12 Jul  1997 src/defs.qc
-rw-rw-r--  0 0      0       52315 12 Jul  1997 src/client.qc
-rw-rw-r--  0 0      0       35115 12 Jul  1997 src/items.qc
-rw-rw-r--  0 0      0         650 29 Oct  1997 src/log.qc
-rw-rw-r--  0 0      0       35567  5 Dec  1997 qwsrc/weapons.qc
-rw-rw-r--  0 0      0        8199 21 Jun  1997 qwsrc/plats.qc
-rw-rw-r--  0 0      0        2683 14 Aug  1997 qwsrc/spectate.qc
-rw-rw-r--  0 0      0        5888  4 Dec  1996 qwsrc/subs.qc
-rw-rw-r--  0 0      0       15261 14 Jul  1997 qwsrc/triggers.qc
-rw-rw-r--  0 0      0        4065  9 Apr  1997 qwsrc/ctfgame.qc
-rw-rw-r--  0 0      0        2541  5 Dec  1997 qwsrc/progdefs.h
-rw-rw-r--  0 0      0       12075 15 Aug  1997 qwsrc/world.qc
-rw-rw-r--  0 0      0       45704 15 Aug  1997 qwsrc/client.qc
-rw-rw-r--  0 0      0       17217 26 Feb  1997 qwsrc/doors.qc
-rw-rw-r--  0 0      0        1560  4 Dec  1996 qwsrc/telefrag.qc
-rw-rw-r--  0 0      0        3051  4 Dec  1996 qwsrc/buttons.qc
-rw-rw-r--  0 0      0       39965 14 Aug  1997 qwsrc/teamplay.qc
-rw-rw-r--  0 0      0         655  4 Dec  1996 qwsrc/charset.txt
-rw-rw-r--  0 0      0        7749 22 Jun  1997 qwsrc/combat.qc
-rw-rw-r--  0 0      0       21762 15 Aug  1997 qwsrc/defs.qc
-rw-rw-r--  0 0      0        6385  5 Dec  1997 qwsrc/files.dat
-rw-rw-r--  0 0      0       35210 15 Aug  1997 qwsrc/items.qc
-rw-rw-r--  0 0      0        9515  4 Dec  1996 qwsrc/models.qc
-rw-rw-r--  0 0      0        9324  5 Dec  1997 qwsrc/status.qc
-rw-rw-r--  0 0      0        2464  4 Dec  1996 qwsrc/server.qc
-rw-rw-r--  0 0      0         473  4 Dec  1996 qwsrc/sprites.qc
-rw-rw-r--  0 0      0       13446 21 Jul  1997 qwsrc/grapple.qc
-rw-rw-r--  0 0      0         276 14 Aug  1997 qwsrc/progs.src
-rw-rw-r--  0 0      0       17189 13 Apr  1997 qwsrc/misc.qc
-rw-rw-r--  0 0      0        1797  2 May  1997 qwsrc/ident.qc
-rw-rw-r--  0 0      0       19937 30 May  1997 qwsrc/player.qc
```

Content of readme:

```text
This archive contains two server prog files for NetQuake and QuakeWorld, both
updated to CTF4.21.  The NetQuake version fixes a logging bug and the
QuakeWorld version fixes a grapple bug.

Note that for logging to occur in the NetQuake version you must enable
the developer cvar (developer 1 at the console, or +developer 1 on the
command line).

Please download 4.2 for full documentation.
http://www.cdrom.com/pub/quake/planetquake/threewave/ctf/server/3wave42.zip

/// Zoid.
zoid@idsoftware.com

Dec '05/97
```

-- readme.txt


The contents of the updated `3wave42.zip` with the new (Dec 05 1997) progs:

```text
-rw-rw-r--  0 0      0       36639 24 Jul  1997 SERVER.TXT
-rw-rw-r--  0 0      0        1765  4 Oct  1996 CAPTURE.TXT
-rw-rw-r--  0 0      0         162  5 Sep  1998 AUTOEXEC.CFG
-rw-rw-r--  0 0      0         160  5 Sep  1998 SERVER.CFG
-rw-rw-r--  0 0      0      287492  5 Dec  1997 PROGS.DAT
-rw-rw-r--  0 0      0      262204  5 Dec  1997 QWPROGS.DAT
drwxrwxr-x  0 0      0           0  5 Sep  1998 MAPS/
drwxrwxr-x  0 0      0           0  5 Sep  1998 SRC/
drwxrwxr-x  0 0      0           0  5 Sep  1998 QWSRC/
-rw-rw-r--  0 0      0       30836 17 Sep  1996 MAPS/E1M1.ENT
-rw-rw-r--  0 0      0       46724 19 Feb  1997 MAPS/E1M2.ENT
-rw-rw-r--  0 0      0       52040 14 Apr  1997 MAPS/E1M3.ENT
-rw-rw-r--  0 0      0       46337 25 Sep  1996 MAPS/E1M4.ENT
-rw-rw-r--  0 0      0       45772 13 Apr  1997 MAPS/E1M5.ENT
-rw-rw-r--  0 0      0       38838 23 Sep  1996 MAPS/E1M6.ENT
-rw-rw-r--  0 0      0       39751 14 Apr  1997 MAPS/E1M8.ENT
-rw-rw-r--  0 0      0       37653 14 Apr  1997 MAPS/E2M1.ENT
-rw-rw-r--  0 0      0       30254 14 Apr  1997 MAPS/E2M2.ENT
-rw-rw-r--  0 0      0       42776 14 Apr  1997 MAPS/E2M3.ENT
-rw-rw-r--  0 0      0       45578  8 Oct  1996 MAPS/E2M5.ENT
-rw-rw-r--  0 0      0       42672  7 Oct  1996 MAPS/E4M3.ENT
-rw-rw-r--  0 0      0       48894 14 Apr  1997 MAPS/E4M5.ENT
-rw-rw-r--  0 0      0       43154 19 Oct  1996 MAPS/E4M6.ENT
-rw-rw-r--  0 0      0       46326 21 Oct  1996 MAPS/E4M4.ENT
-rw-rw-r--  0 0      0       12603 14 Apr  1997 MAPS/DM6.ENT
-rw-rw-r--  0 0      0       14410 31 Oct  1996 MAPS/DM3.ENT
-rw-rw-r--  0 0      0       37621 13 Apr  1997 MAPS/E4M8.ENT
-rw-rw-r--  0 0      0       34684 13 Apr  1997 MAPS/E3M7.ENT
-rw-rw-r--  0 0      0       60417 28 Feb  1997 MAPS/E3M4.ENT
-rw-rw-r--  0 0      0       55426 13 Apr  1997 MAPS/E2M7.ENT
-rw-rw-r--  0 0      0       11376 14 Apr  1997 MAPS/DM5.ENT
-rw-rw-r--  0 0      0       42640 25 Mar  1997 MAPS/E4M7.ENT
-rw-rw-r--  0 0      0       68779 13 Apr  1997 MAPS/E3M6.ENT
-rw-rw-r--  0 0      0       42952 13 Apr  1997 MAPS/E3M1.ENT
-rw-rw-r--  0 0      0       10676 14 Apr  1997 MAPS/DM1.ENT
-rw-rw-r--  0 0      0       20293 14 Apr  1997 MAPS/DM2.ENT
-rw-rw-r--  0 0      0        9946 14 Apr  1997 MAPS/DM4.ENT
-rw-rw-r--  0 0      0       15108  2 Feb  1997 MAPS/E1M7.ENT
-rw-rw-r--  0 0      0       49057 14 Apr  1997 MAPS/E2M4.ENT
-rw-rw-r--  0 0      0       49932 13 Apr  1997 MAPS/E2M6.ENT
-rw-rw-r--  0 0      0       31582 13 Apr  1997 MAPS/E3M2.ENT
-rw-rw-r--  0 0      0       35570 13 Apr  1997 MAPS/E3M3.ENT
-rw-rw-r--  0 0      0       50483 25 Mar  1997 MAPS/E3M5.ENT
-rw-rw-r--  0 0      0       43124 13 Apr  1997 MAPS/E4M1.ENT
-rw-rw-r--  0 0      0       28258 25 Mar  1997 MAPS/E4M2.ENT
-rw-rw-r--  0 0      0         108 18 Oct  1996 MAPS/DOBSP.BAT
-rw-rw-r--  0 0      0          52  4 Oct  1996 MAPS/DOBSP.SH
-rw-rw-r--  0 0      0       36824  5 May  1997 SRC/TEAMPLAY.QC
-rw-rw-r--  0 0      0        2910  6 Oct  1996 SRC/BUTTONS.QC
-rw-rw-r--  0 0      0       16416  2 Apr  1997 SRC/MISC.QC
-rw-rw-r--  0 0      0        5601 15 Dec  1996 SRC/SUBS.QC
-rw-rw-r--  0 0      0       17138  6 Oct  1996 SRC/DOORS.QC
-rw-rw-r--  0 0      0       14259 19 Oct  1996 SRC/TRIGGERS.QC
-rw-rw-r--  0 0      0       11521 10 Apr  1997 SRC/WORLD.QC
-rw-rw-r--  0 0      0        2598  5 Dec  1997 SRC/PROGDEFS.H
-rw-rw-r--  0 0      0        1560 19 Oct  1996 SRC/TELEFRAG.QC
-rw-rw-r--  0 0      0         808 31 Mar  1997 SRC/CHARSET.TXT
-rw-rw-r--  0 0      0        6426  5 Dec  1997 SRC/FILES.DAT
-rw-rw-r--  0 0      0         650 29 Oct  1997 SRC/LOG.QC
-rw-rw-r--  0 0      0        6961 29 Apr  1997 SRC/HOOK.QC
-rw-rw-r--  0 0      0        2368 20 Dec  1996 SRC/SERVER.QC
-rw-rw-r--  0 0      0        4121  2 Apr  1997 SRC/CTFGAME.QC
-rw-rw-r--  0 0      0         282 22 Apr  1997 SRC/NOTES.TXT
-rw-rw-r--  0 0      0         399  1 May  1997 SRC/PROGS.SRC
-rw-rw-r--  0 0      0        6162  1 May  1997 SRC/OBSERV.QC
-rw-rw-r--  0 0      0       15192  1 May  1997 SRC/ADMIN.QC
-rw-rw-r--  0 0      0       33876  2 May  1997 SRC/WEAPONS.QC
-rw-rw-r--  0 0      0        1797  2 May  1997 SRC/IDENT.QC
-rw-rw-r--  0 0      0       18832 30 May  1997 SRC/PLAYER.QC
-rw-rw-r--  0 0      0        7732 21 Jun  1997 SRC/PLATS.QC
-rw-rw-r--  0 0      0        7310 22 Jun  1997 SRC/COMBAT.QC
-rw-rw-r--  0 0      0       20421 12 Jul  1997 SRC/DEFS.QC
-rw-rw-r--  0 0      0       52315 12 Jul  1997 SRC/CLIENT.QC
-rw-rw-r--  0 0      0       35115 12 Jul  1997 SRC/ITEMS.QC
-rw-rw-r--  0 0      0        9194  5 Dec  1997 SRC/STATUS.QC
-rw-rw-r--  0 0      0       35567  5 Dec  1997 QWSRC/WEAPONS.QC
-rw-rw-r--  0 0      0        8199 21 Jun  1997 QWSRC/PLATS.QC
-rw-rw-r--  0 0      0        5888  4 Dec  1996 QWSRC/SUBS.QC
-rw-rw-r--  0 0      0       15261 14 Jul  1997 QWSRC/TRIGGERS.QC
-rw-rw-r--  0 0      0        4065  9 Apr  1997 QWSRC/CTFGAME.QC
-rw-rw-r--  0 0      0        2541  5 Dec  1997 QWSRC/PROGDEFS.H
-rw-rw-r--  0 0      0       12075 15 Aug  1997 QWSRC/WORLD.QC
-rw-rw-r--  0 0      0       45704 15 Aug  1997 QWSRC/CLIENT.QC
-rw-rw-r--  0 0      0       17217 26 Feb  1997 QWSRC/DOORS.QC
-rw-rw-r--  0 0      0        1560  4 Dec  1996 QWSRC/TELEFRAG.QC
-rw-rw-r--  0 0      0        3051  4 Dec  1996 QWSRC/BUTTONS.QC
-rw-rw-r--  0 0      0       39965 14 Aug  1997 QWSRC/TEAMPLAY.QC
-rw-rw-r--  0 0      0         655  4 Dec  1996 QWSRC/CHARSET.TXT
-rw-rw-r--  0 0      0        7749 22 Jun  1997 QWSRC/COMBAT.QC
-rw-rw-r--  0 0      0       21762 15 Aug  1997 QWSRC/DEFS.QC
-rw-rw-r--  0 0      0        6385  5 Dec  1997 QWSRC/FILES.DAT
-rw-rw-r--  0 0      0       35210 15 Aug  1997 QWSRC/ITEMS.QC
-rw-rw-r--  0 0      0        9515  4 Dec  1996 QWSRC/MODELS.QC
-rw-rw-r--  0 0      0        2464  4 Dec  1996 QWSRC/SERVER.QC
-rw-rw-r--  0 0      0         473  4 Dec  1996 QWSRC/SPRITES.QC
-rw-rw-r--  0 0      0       13446 21 Jul  1997 QWSRC/GRAPPLE.QC
-rw-rw-r--  0 0      0       17189 13 Apr  1997 QWSRC/MISC.QC
-rw-rw-r--  0 0      0         276 14 Aug  1997 QWSRC/PROGS.SRC
-rw-rw-r--  0 0      0        1797  2 May  1997 QWSRC/IDENT.QC
-rw-rw-r--  0 0      0       19937 30 May  1997 QWSRC/PLAYER.QC
-rw-rw-r--  0 0      0        9324  5 Dec  1997 QWSRC/STATUS.QC
-rw-rw-r--  0 0      0        2683 14 Aug  1997 QWSRC/SPECTATE.QC
```

## v4.21 + Docs

An updated version of the release that includes the documentation was released circa September 24th 2000 as `3wave421d.zip`.

No announcement has been located at the time of writing.

Content of `3wave421d.zip`:

```text
-rw-rw-r--  0 0      0         773 24 Sep  2000 3wave421x/readme.txt
-rw-rw-r--  0 0      0      287492  5 Dec  1997 3wave421x/progs.dat
-rw-rw-r--  0 0      0      262204  5 Dec  1997 3wave421x/qwprogs.dat
drwxrwxr-x  0 0      0           0 24 Sep  2000 3wave421x/src/
-rw-rw-r--  0 0      0       36824  5 May  1997 3wave421x/src/teamplay.qc
-rw-rw-r--  0 0      0        2910  6 Oct  1996 3wave421x/src/buttons.qc
-rw-rw-r--  0 0      0        9194  5 Dec  1997 3wave421x/src/status.qc
-rw-rw-r--  0 0      0       16416  2 Apr  1997 3wave421x/src/misc.qc
-rw-rw-r--  0 0      0        5601 15 Dec  1996 3wave421x/src/subs.qc
-rw-rw-r--  0 0      0       17138  6 Oct  1996 3wave421x/src/doors.qc
-rw-rw-r--  0 0      0       14259 19 Oct  1996 3wave421x/src/triggers.qc
-rw-rw-r--  0 0      0       11521 10 Apr  1997 3wave421x/src/world.qc
-rw-rw-r--  0 0      0        2598  5 Dec  1997 3wave421x/src/progdefs.h
-rw-rw-r--  0 0      0        1560 19 Oct  1996 3wave421x/src/telefrag.qc
-rw-rw-r--  0 0      0         808 31 Mar  1997 3wave421x/src/charset.txt
-rw-rw-r--  0 0      0        6426  5 Dec  1997 3wave421x/src/files.dat
-rw-rw-r--  0 0      0        6961 29 Apr  1997 3wave421x/src/hook.qc
-rw-rw-r--  0 0      0        2368 20 Dec  1996 3wave421x/src/server.qc
-rw-rw-r--  0 0      0        4121  2 Apr  1997 3wave421x/src/ctfgame.qc
-rw-rw-r--  0 0      0         282 22 Apr  1997 3wave421x/src/notes.txt
-rw-rw-r--  0 0      0         399  1 May  1997 3wave421x/src/progs.src
-rw-rw-r--  0 0      0        6162  1 May  1997 3wave421x/src/observ.qc
-rw-rw-r--  0 0      0       15192  1 May  1997 3wave421x/src/admin.qc
-rw-rw-r--  0 0      0       33876  2 May  1997 3wave421x/src/weapons.qc
-rw-rw-r--  0 0      0        1797  2 May  1997 3wave421x/src/ident.qc
-rw-rw-r--  0 0      0       18832 30 May  1997 3wave421x/src/player.qc
-rw-rw-r--  0 0      0        7732 21 Jun  1997 3wave421x/src/plats.qc
-rw-rw-r--  0 0      0        7310 22 Jun  1997 3wave421x/src/combat.qc
-rw-rw-r--  0 0      0       20421 12 Jul  1997 3wave421x/src/defs.qc
-rw-rw-r--  0 0      0       52315 12 Jul  1997 3wave421x/src/client.qc
-rw-rw-r--  0 0      0       35115 12 Jul  1997 3wave421x/src/items.qc
-rw-rw-r--  0 0      0         650 29 Oct  1997 3wave421x/src/log.qc
drwxrwxr-x  0 0      0           0 24 Sep  2000 3wave421x/qwsrc/
-rw-rw-r--  0 0      0       35567  5 Dec  1997 3wave421x/qwsrc/weapons.qc
-rw-rw-r--  0 0      0        8199 21 Jun  1997 3wave421x/qwsrc/plats.qc
-rw-rw-r--  0 0      0        2683 14 Aug  1997 3wave421x/qwsrc/spectate.qc
-rw-rw-r--  0 0      0        5888  4 Dec  1996 3wave421x/qwsrc/subs.qc
-rw-rw-r--  0 0      0       15261 14 Jul  1997 3wave421x/qwsrc/triggers.qc
-rw-rw-r--  0 0      0        4065  9 Apr  1997 3wave421x/qwsrc/ctfgame.qc
-rw-rw-r--  0 0      0        2541  5 Dec  1997 3wave421x/qwsrc/progdefs.h
-rw-rw-r--  0 0      0       12075 15 Aug  1997 3wave421x/qwsrc/world.qc
-rw-rw-r--  0 0      0       45704 15 Aug  1997 3wave421x/qwsrc/client.qc
-rw-rw-r--  0 0      0       17217 26 Feb  1997 3wave421x/qwsrc/doors.qc
-rw-rw-r--  0 0      0        1560  4 Dec  1996 3wave421x/qwsrc/telefrag.qc
-rw-rw-r--  0 0      0        3051  4 Dec  1996 3wave421x/qwsrc/buttons.qc
-rw-rw-r--  0 0      0       39965 14 Aug  1997 3wave421x/qwsrc/teamplay.qc
-rw-rw-r--  0 0      0         655  4 Dec  1996 3wave421x/qwsrc/charset.txt
-rw-rw-r--  0 0      0        7749 22 Jun  1997 3wave421x/qwsrc/combat.qc
-rw-rw-r--  0 0      0       21762 15 Aug  1997 3wave421x/qwsrc/defs.qc
-rw-rw-r--  0 0      0        6385  5 Dec  1997 3wave421x/qwsrc/files.dat
-rw-rw-r--  0 0      0       35210 15 Aug  1997 3wave421x/qwsrc/items.qc
-rw-rw-r--  0 0      0        9515  4 Dec  1996 3wave421x/qwsrc/models.qc
-rw-rw-r--  0 0      0        9324  5 Dec  1997 3wave421x/qwsrc/status.qc
-rw-rw-r--  0 0      0        2464  4 Dec  1996 3wave421x/qwsrc/server.qc
-rw-rw-r--  0 0      0         473  4 Dec  1996 3wave421x/qwsrc/sprites.qc
-rw-rw-r--  0 0      0       13446 21 Jul  1997 3wave421x/qwsrc/grapple.qc
-rw-rw-r--  0 0      0         276 14 Aug  1997 3wave421x/qwsrc/progs.src
-rw-rw-r--  0 0      0       17189 13 Apr  1997 3wave421x/qwsrc/misc.qc
-rw-rw-r--  0 0      0        1797  2 May  1997 3wave421x/qwsrc/ident.qc
-rw-rw-r--  0 0      0       19937 30 May  1997 3wave421x/qwsrc/player.qc
drwxrwxr-x  0 0      0           0 24 Sep  2000 3wave421x/maps/
-rw-rw-r--  0 0      0       30836 17 Sep  1996 3wave421x/maps/e1m1.ent
-rw-rw-r--  0 0      0       46724 19 Feb  1997 3wave421x/maps/e1m2.ent
-rw-rw-r--  0 0      0       52040 14 Apr  1997 3wave421x/maps/e1m3.ent
-rw-rw-r--  0 0      0       46337 25 Sep  1996 3wave421x/maps/e1m4.ent
-rw-rw-r--  0 0      0       45772 13 Apr  1997 3wave421x/maps/e1m5.ent
-rw-rw-r--  0 0      0       38838 23 Sep  1996 3wave421x/maps/e1m6.ent
-rw-rw-r--  0 0      0       39751 14 Apr  1997 3wave421x/maps/e1m8.ent
-rw-rw-r--  0 0      0       37653 14 Apr  1997 3wave421x/maps/e2m1.ent
-rw-rw-r--  0 0      0       30254 14 Apr  1997 3wave421x/maps/e2m2.ent
-rw-rw-r--  0 0      0       42776 14 Apr  1997 3wave421x/maps/e2m3.ent
-rw-rw-r--  0 0      0       45578  8 Oct  1996 3wave421x/maps/e2m5.ent
-rw-rw-r--  0 0      0       42672  7 Oct  1996 3wave421x/maps/e4m3.ent
-rw-rw-r--  0 0      0       48894 14 Apr  1997 3wave421x/maps/e4m5.ent
-rw-rw-r--  0 0      0       43154 19 Oct  1996 3wave421x/maps/e4m6.ent
-rw-rw-r--  0 0      0       46326 21 Oct  1996 3wave421x/maps/e4m4.ent
-rw-rw-r--  0 0      0       12603 14 Apr  1997 3wave421x/maps/dm6.ent
-rw-rw-r--  0 0      0       14410 31 Oct  1996 3wave421x/maps/dm3.ent
-rw-rw-r--  0 0      0       37621 13 Apr  1997 3wave421x/maps/e4m8.ent
-rw-rw-r--  0 0      0       34684 13 Apr  1997 3wave421x/maps/e3m7.ent
-rw-rw-r--  0 0      0       60417 28 Feb  1997 3wave421x/maps/e3m4.ent
-rw-rw-r--  0 0      0       55426 13 Apr  1997 3wave421x/maps/e2m7.ent
-rw-rw-r--  0 0      0       11376 14 Apr  1997 3wave421x/maps/dm5.ent
-rw-rw-r--  0 0      0       42640 25 Mar  1997 3wave421x/maps/e4m7.ent
-rw-rw-r--  0 0      0       68779 13 Apr  1997 3wave421x/maps/e3m6.ent
-rw-rw-r--  0 0      0       42952 13 Apr  1997 3wave421x/maps/e3m1.ent
-rw-rw-r--  0 0      0       10676 14 Apr  1997 3wave421x/maps/dm1.ent
-rw-rw-r--  0 0      0       20293 14 Apr  1997 3wave421x/maps/dm2.ent
-rw-rw-r--  0 0      0        9946 14 Apr  1997 3wave421x/maps/dm4.ent
-rw-rw-r--  0 0      0       15108  2 Feb  1997 3wave421x/maps/e1m7.ent
-rw-rw-r--  0 0      0       49057 14 Apr  1997 3wave421x/maps/e2m4.ent
-rw-rw-r--  0 0      0       49932 13 Apr  1997 3wave421x/maps/e2m6.ent
-rw-rw-r--  0 0      0       31582 13 Apr  1997 3wave421x/maps/e3m2.ent
-rw-rw-r--  0 0      0       35570 13 Apr  1997 3wave421x/maps/e3m3.ent
-rw-rw-r--  0 0      0       50483 25 Mar  1997 3wave421x/maps/e3m5.ent
-rw-rw-r--  0 0      0       43124 13 Apr  1997 3wave421x/maps/e4m1.ent
-rw-rw-r--  0 0      0       28258 25 Mar  1997 3wave421x/maps/e4m2.ent
-rw-rw-r--  0 0      0         108 18 Oct  1996 3wave421x/maps/dobsp.bat
-rw-rw-r--  0 0      0          52  4 Oct  1996 3wave421x/maps/dobsp.sh
-rw-rw-r--  0 0      0         146 24 Sep  2000 3wave421x/server.cfg
-rw-rw-r--  0 0      0        1765  4 Oct  1996 3wave421x/capture.txt
-rw-rw-r--  0 0      0         163 24 Sep  2000 3wave421x/autoexec.cfg
-rw-rw-r--  0 0      0       36640 24 Sep  2000 3wave421x/server.txt
drwxrwxr-x  0 0      0           0 24 Sep  2000 3wave421x/
```

Content of readme:

```text
Update Sept 2000 - 4.21 plus docs
The link on cdrom.com is no longer valid, and this archive cannot be found
there. I have included the Documentation from 4.2 to make it complete, and
available as one package.

///Casey
Sept '24/00
```

## 2 Year Anniversary

The two-year anniversary for 3wave CTF was October 02 1998.

Blue from BluesNews posted a special message:

> Out of the Blue  [4:57 AM EDT]\
> Today marks the two-year anniversary of the day the first-ever story about Threewave Capture the Flag appeared anywhere, right here on Blue's News. It really seems like the "old days" when I recall it because I was on a trip to Virginia at the time, updating on a monochrome 486SX laptop using a flaky 14.4 AOL connection. I can still remember receiving the email from Zoid that had such a strong hook (reproduced in authentic Quake Rag text):
>
>> So, I was up this morning at six AM (don't ask) and I ran QSpy. I took a look at about 300 servers. To my surprise, almost all of them were empty, *except* mine and a friend of mine who runs my patches. They were both half full.
>>
>>What is this I thought?
>>
>>Capture the Flag.
>
> I think it's safe to say that he did not know what all this would all lead to at the time... I certainly didn't. Happy Anniversary Zoid.

-- [https://www.bluesnews.com/archives/sept98-4.html](https://www.bluesnews.com/archives/sept98-4.html)

Zoid shared a message on his .plan file:

> Oct 2nd, 1998
>
> From Blue's News:
>
>> "Today marks the two-year anniversary of the day the first-ever story about
Capture the Flag appeared anywhere, right here on Blue's News. I was on
a trip to Virginia and it really seems like the "old days," because I was
updating on a monochrome 486SX laptop, using a flaky 14.4 AOL connection,
and I can still remember the email from Zoid that had such a strong hook."
>
> I remember writing that email to Blue. When I realized that CTF was going to
catch on (the sheer number of people fighting to get into my two little
twelve player servers was astounding), I wrote mail that would "sell"
the product, so to speak. I knew I built something cool and I wanted tell
everyone about it.
>
> I guess everyone heard about it by now. :)
>
> CTF has been an amazing project for me. From my humble beginings on a little
NetQuake server running a little hack with floating keys to Quake2 CTF.
It's been fun building it all, and it's going to be a challenge to continue
the tradition of simple gameplay, but addictive design.
>
> Speaking of Q2CTF, I've begun some layout plans for an addon level pak.
Players have been screaming for more "official" quality levels and I think
it's past due time for some to be made. No time line yet, but I'm hoping
to get a new pak together soon for all your CTF fanatics out there.
>
> Thanks to Blue for wishing me a Happy Anniversary and a special thanks to all
the players out there that enjoyed ThreeWave Capture the Flag and made it
what it is today. It was your feedback and desire to play a game that
drove me to build it and continue to make it better.
>
> "Zoid captured the BLUE flag!" :)

-- [http://finger.planetquake.com/qfplan.asp?userid=zoid&id=10045](https://web.archive.org/web/19990829042726/http://finger.planetquake.com/qfplan.asp?userid=zoid&id=10045) (archived)


## References

Threewave homepages:

* [http://mindlink.net/zoid/](https://web.archive.org/web/19981203003619/http://mindlink.net/zoid/)
* [http://quake.threewave.com/](https://web.archive.org/web/20020228174654/http://quake.threewave.com/)
* [http://www.planetquake.com/quakex/threewave/](https://web.archive.org/web/19980113012310/http://www.planetquake.com/quakex/threewave/)
* [http://threewave.planetquake.com/](https://web.archive.org/web/19971224200252/http://threewave.planetquake.com/)
* [http://www.captured.com/threewave/](https://web.archive.org/web/19981202093403/http://www.captured.com/threewave/)
* [http://threewave.com/](https://web.archive.org/web/19991013145630/http://threewave.com:80/)

References:

* [Capture the Flag, BluesNews](https://www.bluesnews.com/guide/ctf.htm)
* [Zoid Interview, Xenocide](https://web.archive.org/web/20010504050414fw/http://www.captured.com/academy/NEWS/zoid_interviews_body.htm) (archived)
* [Capture the Zoid, TCMag](https://web.archive.org/web/19970607042034/http://www.frag.com/tcmag/interviews/zoidint.htm) (archived)
