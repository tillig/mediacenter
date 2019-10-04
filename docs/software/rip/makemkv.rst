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

If there are a lot of playlists, you can use the MakeMKV console app to dump them to a file and search:

.. sourcecode:: bat

    "C:\Program Files (x86)\MakeMKV\makemkvcon.exe" --robot --messages=C:\Users\YourUserName\Desktop\MakeMKVOutput.txt info disc:0

You'll get a lot of results that have messages like this::

    TINFO:385,2,0,"John Wick 3: Parabellum"
    TINFO:385,8,0,"16"
    TINFO:385,9,0,"2:10:45"
    TINFO:385,10,0,"32.0 GB"
    TINFO:385,11,0,"34411984896"
    TINFO:385,16,0,"00957.mpls"
    TINFO:385,25,0,"19"
    TINFO:385,26,0,"518,512,514,510,515,506,520,511,516,505,501,504,502,519,507,508,509,503,517"
    TINFO:385,27,0,"John Wick 3- Parabellum_t385.mkv"

This shows that title 385 is playlist 00957.mpls along with the associated segment list. Use a text editor to find the segment list that you determined with Procmon.
