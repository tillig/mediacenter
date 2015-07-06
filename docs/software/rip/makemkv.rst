=======
MakeMKV
=======

`MakeMKV <http://www.makemkv.com/>`_ is a great free tool for ripping DVD and Blu-ray content. It does no conversion like :doc:`Handbrake <../convert/handbrake>` but is good at preserving original content and cherry-picking audio tracks for later conversion.

MakeMKV has been in beta for a very long time and is free during the beta period. You do have to `re-visit the forums occasionally to get a new beta key <http://www.makemkv.com/forum2/viewtopic.php?f=5&t=1053>`_ for the product, but that's not too hard.

I use both this and :doc:`DVDFab HD Decrypter <dvdfab>` for ripping content. MakeMKV is great at grabbing individual MKV files based on disc titles, but DVDFab HD Decrypter is sometimes easier to use when it comes to complex copy protection and more one-click operation. I will usually start with MakeMKV and, if there's trouble getting a good rip of a movie, will fall back to DVDFab.

Post-Conversion
===============
I found that movies ripped with MakeMKV and later converted with a tool like :doc:`Handbrake <../convert/handbrake>` will sometimes bring along metadata like the movie title. This metadata is usually not what you want and can be confusing if you try adding it to :doc:`Plex <../serve/plex>` later.

Before pushing a converted video to Plex, update the file properties to remove (or update) any metadata that was added by MakeMKV and Handbrake during the conversion process.