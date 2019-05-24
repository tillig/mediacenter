==========================
Video/Movie Intake Process
==========================

This is the process I go through when I get new movies or TV shows for my collection. Following this process helps me keep track of what I have (both for insurance purposes and so I don't buy duplicate stuff); and it makes sure I get everything into the system so it can be consumed by all of my devices.

Note that currently I don't buy digital-only movies - I only buy discs. While some of those discs may come with DRM-laden digital copies (which I do claim), there isn't a process for bringing in digital-only video because I don't really have any.

1. Add the disc/set to :doc:`DVD Profiler <../software/manage/dvdprofiler>` by UPC.
2. Synchronize the DVD Profiler local database with `my online video database <http://www.invelos.com/dvdcollection.aspx/tillig>`_.
3. Back up the local DVD Profiler database. This is a more thorough backup than the online collection and would be used in favor of the online sync backup if available.
4. Claim any digital copy codes. If the disc comes with a "digital copy," I'll claim it. I prefer iTunes over Vudu because the primary use case for my digital copy movies is traveling with an iPad and it makes for a simpler sync. If I have an internet connection, I'll just use Plex.
5. Rip the video. I use :doc:`MakeMKV <../software/rip/makemkv>` to rip just the main movie or TV episode(s).
6. Convert the video. I use :doc:`Handbrake <../software/convert/handbrake>` to convert the video from the ripped format into :doc:`MP4 format <../formats/video>`.
7. Store the converted video. I put the movie or TV episodes into a shared folder on my :doc:`Synology DS1010+ <../hardware/server/synologyds1010>`. I use `the naming conventions and folder structures outlined by Plex <https://support.plex.tv/hc/en-us/categories/200028098-Media-Preparation>`_. Once on the DS1010+, my :doc:`MegaPlex server <../hardware/server/megaplex>` automatically finds it and adds it to :doc:`Plex <../software/serve/plex>` so it is available to all of my devices.
8. File the discs.

    1. If it's a TV series - DVD or Blu-ray - I put them upstairs on some shelves we have specifically for this purpose. It's kind of fun to see all the TV series in one place, though admittedly it's getting pretty cramped.
    2. If it's a DVD, I use `Odyssey CD Storage Cases <http://www.sleevecityusa.com/Odyssey-CD-Storage-Case-for-65-Jewel-Cases-p/3strody65.htm>`_, each DVD in a `Diskeeper sleeve <http://www.sleevecityusa.com/diskeeper-anti-static-cd-dvd-sleeve-p/3cdrice.htm>`_. I store liner notes and any other paperwork in an expandable envelope.
    3. If it's a Blu-ray, I use `DiscSox HiDef Pro sleeves <http://www.amazon.com/dp/B002LDBZM6?tag=mhsvortex>`_ in `a case specifically for those sleeves <http://mmdesign.com/products/decorative-case-gunny-dvd-pro.php>`_.

The Odyssey box for DVDs looks like this:

.. image:: odysseybox.jpg
   :target: http://www.sleevecityusa.com/Odyssey-CD-Storage-Case-for-65-Jewel-Cases-p/3strody65.htm

DiscSox HiDef Pro sleeves look like this:

.. image:: discsox.jpg
   :target: http://www.amazon.com/dp/B002LDBZM6?tag=mhsvortex

The case for the DiscSox sleeves looks like this and sits nicely in my living room:

.. image:: discsox_case.jpg
   :target: http://mmdesign.com/products/decorative-case-gunny-dvd-pro.php
