Hexenwail compiled gamecode (progs.dat)
=======================================

There is nothing to install.  The engine already loads these.

They are the Hexen II game logic, rebuilt from the HexenC sources in this
project.  They carry bug fixes that are not in Raven's 1997 progs.dat -- most
notably a fix for dropped backpacks silently vanishing in co-op and
deathmatch.  Nothing else in this download changes game behaviour; these files
do.

Hexenwail carries its own copy of them next to the engine and prefers it to
the one in your Hexen II folder.  That is true on Linux and on Windows alike,
straight out of the zip: nothing is copied, nothing of yours is overwritten,
and there is no step you have missed.

So this gamecode/ folder is not a job waiting for you.  On Windows it IS the
copy the engine loads -- it sits beside glh2.exe, which is where the engine
looks first.  On Linux the engine loads its own from the platform directory
and this folder is a spare.  Either way, read on only if you want to check
what you are running, turn it off, or use these files somewhere else.

WHICH GAMECODE AM I RUNNING?
----------------------------
The engine says so.  Whenever it loads gamecode it prints one line to the
console naming the exact file:

  Gamecode: progs.dat from <full path to the file> (<version>, file crc <n>)

If that path has gamecode or share/hexenwail in it, you are running ours.  If
it points inside your Hexen II folder, you are running the one that came with
the game.  Quote the whole line in bug reports; the crc identifies the file
exactly, which a filename cannot.

One exception worth knowing: our gamecode is built from the v1.11 sources, so
the engine declines to substitute it on the shareware demo, the OEM release
and mix-and-match installs -- those are different versions of the game.  There
you get the gamecode your install came with, and the line above will say so.

TURNING IT OFF
--------------
Launch the engine with -vanillaprogs.  It then ignores its own copy entirely
and uses whatever gamecode your Hexen II install provides.

Nothing is moved or deleted, so this is a per-launch decision -- drop the
switch and you are back on ours.  Use it when you want Raven's 1997 behaviour,
and when you are reporting a bug and want to say whether it happens both ways.

RUNNING SOME OTHER GAMECODE
---------------------------
A translation, a balance patch, your own build.

Linux, macOS, BSD -- put it in your Hexen II user directory.  The engine
creates it the first time you run it, and it is where your config and
savegames already live:

  ~/.hexen2/data1/progs.dat
  ~/.hexen2/data1/progs2.dat
  ~/.hexen2/portals/progs.dat

The order is: your user directory beats the engine's own copy, which beats
your Hexen II folder.  ~/.hexen2 is therefore the one place that wins
outright, and it is why a progs.dat dropped into <your Hexen II folder>/data1/
has no effect -- the engine's copy is preferred to it.

Two more reasons it is the right place, both about being able to undo it:

  - Nothing of Raven's is overwritten.  Retail Hexen II keeps progs.dat as a
    loose file and there is NO copy inside pak0.pak/pak1.pak/pak3.pak to fall
    back on, so overwriting it in the game folder cannot be undone.

  - Uninstalling is deleting files you put there yourself, in a directory you
    own.  The game folder is never touched, so there is nothing to restore.

Windows -- there is no user directory, so replace the files inside the
gamecode\ folder beside glh2.exe instead:

  gamecode\data1\progs.dat
  gamecode\data1\progs2.dat
  gamecode\portals\progs.dat

Those are our files, not Raven's, so nothing irreplaceable is at risk --
re-extracting the zip puts them back.

USING THESE WITH A DIFFERENT ENGINE
-----------------------------------
This is the one case that calls for copying anything.  The original glhexen2,
or another port, will not know to look beside its own executable, so it wants
the files in the game folder:

  gamecode\data1\progs.dat    ->  <your Hexen II folder>\data1\progs.dat
  gamecode\data1\progs2.dat   ->  <your Hexen II folder>\data1\progs2.dat
  gamecode\portals\progs.dat  ->  <your Hexen II folder>\portals\progs.dat

BACK UP FIRST.  That overwrites Raven's files, and as above no .pak holds a
copy to fall back on, so your backup is the only way back.  Put your existing
data1\progs.dat, data1\progs2.dat and portals\progs.dat somewhere safe before
you copy over them.  To undo it, restore those backups -- nothing else is
needed.

None of this is required to play Hexenwail, and doing it changes what that
other engine runs, not what Hexenwail runs.

Whichever engine you are feeding, copy progs.dat and progs2.dat TOGETHER.
Five maps use progs2.dat and the rest use progs.dat: rider1a, rider2c, meso9,
romeric6 and eidolon -- the boss arenas at the end of each hub, and Eidolon's
lair.  Installing one file without the other leaves the game running new
gamecode on those five maps and 1997 gamecode everywhere else.

Include portals/progs.dat if you have the Portal of Praevus mission pack.
When the mission pack is active it takes priority over data1 completely, so
without this file you get none of the fixes.

WHAT CHANGES
------------
Crusader's Glyph of the Ancients (Portal of Praevus).  The glyph detonates on
whoever touches it for real damage -- 50 in deathmatch, 37 otherwise -- and
that includes YOU, the caster.  Do not walk into your own glyph.

This is Raven's original behaviour, so nothing about the glyph changes if you
are coming from a stock progs.dat.  It is called out because Hexenwail's own
gamecode briefly did something else: builds made from source for a while let
the glyph pass harmlessly through the caster.  That exemption is gone -- it was
never how the game worked.

"Vanilla" now means two things.  A Hexenwail build runs our gamecode unless
you asked otherwise, so it will differ from Raven's in ways that are not
engine bugs.  If you report a bug, paste the Gamecode: line, or say whether
-vanillaprogs changes what you see -- that is the fastest way to tell whether
a problem is ours or Raven's, and it deletes nothing.
