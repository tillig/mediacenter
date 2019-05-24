=======
MakeMKV
=======

`MakeMKV <http://www.makemkv.com/>`_ is a great free tool for ripping DVD and Blu-ray content. It does no conversion like :doc:`Handbrake <../convert/handbrake>` but is good at preserving original content and cherry-picking audio tracks for later conversion.

MakeMKV has been in beta for a very long time and is free during the beta period. You do have to `re-visit the forums occasionally to get a new beta key <http://www.makemkv.com/forum2/viewtopic.php?f=5&t=1053>`_ for the product, but that's not too hard. I ended up paying since I've definitely gotten my money's worth.

Post-Conversion
===============
I found that movies ripped with MakeMKV and later converted with a tool like :doc:`Handbrake <../convert/handbrake>` will sometimes bring along metadata like the movie title. This metadata is usually not what you want and can be confusing if you try adding it to :doc:`Plex <../serve/plex>` later.

Before pushing a converted video to Plex, update the file properties to remove (or update) any metadata that was added by MakeMKV and Handbrake during the conversion process.

Playlist Obfuscation
====================
One copy protection tactic that companies may use to make it hard to rip the movie is "playlist obfuscation." When you load the movie up in MakeMKV, it may appear there are tens or hundreds of copies of the same movie. Each of these copies differs by the order of the scenes. If you rip the wrong one, the movie plays out of order and doesn't make sense.

Usually the MakeMKV forums will have someone who has already figured out the right playlist and will have posted it. However, if there's not, you can figure it out yourself with some Blu-ray player software and `Procmon <https://docs.microsoft.com/en-us/sysinternals/downloads/procmon>`_.

Fire up Procmon and set the filter to the standard exclusions (the default) and then...

- Process Name contains "dvd"
- Operation is "CloseFile"
- Path ends with ".m2ts"

Start Procmon running. Now fire up the Blu-ray player software and start playing the movie. Clear any Procmon logs right after you start playing. Then fast forward through the whole movie. As the player software moves from scene to scene, it will close the current scene file and open the next. Closing the scene file will add a log entry in Procmon. These will be numbered - 101.m2ts, 102.m2ts, etc.

When the movie is done, stop Procmon from monitoring but don't shut it down yet.

Now in MakeMKV, find the playlist that matches the numbers Procmon shows in that same order. That's the correct playlist.
