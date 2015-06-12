========
Software
========

:doc:`Plex <serve/plex>` is the centerpiece of my media center software. It provides access to pretty much all of my media in a nice, polished interface. That said, :doc:`Asset UPnP <serve/asset>` is my primary mechanism for accessing music.

I use :doc:`DVDFab HD Decrypter <rip/dvdfab>` and :doc:`MakeMKV <rip/makemkv>` for ripping disc contents into digital format, then :doc:`Handbrake <convert/handbrake>` for converting the ripped contents into a compatible format.

I use :doc:`Picasa <manage/picasa>` for organizing my photos and :doc:`DVD Profiler <manage/dvdprofiler>` for managing my DVD collection.

My digital music is in :doc:`iTunes <manage/itunes>` but I keep track of the combined digital and disc music collection using :doc:`Music Collector <manage/musiccollector>`.

My backup solution is :doc:`CrashPlan <system/crashplan>`, which handles both internal and off-site backup. That, combined with the workstation image-based backup of :doc:`Windows Home Server <system/whs>`, has me covered.

.. toctree::
    :maxdepth: 2

    manage/index.rst
    rip/index.rst
    convert/index.rst
    serve/index.rst
    system/index.rst
    scripts.rst
    deprecated/index.rst