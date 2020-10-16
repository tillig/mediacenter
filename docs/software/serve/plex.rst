====
Plex
====
`Plex is a media server and associated set of client apps. <https://plex.tv>`_ I switched to use Plex for things due to the ability to access my media in more places. That means no more storage of full DVD image rips, but that's OK because :doc:`the Synology DS1010+ <../../hardware/server/synologyds1010>` was running out of space and we didn't watch the extra features anyway. The added flexibility of the media is awesome.

I bought a lifetime `Plex Pass subscription <https://plex.tv/subscription/about>`_ in September 2014 for $75 before they doubled the price to $150. This lets me get the latest server packages early and try out new features, plus I'm happy to support the development effort.

Server Requirements
===================
The Synology DiskStation Manager has a Plex server package but **the physical machine is not powerful enough to transcode HD video**. Trying to watch home movies proved difficult because they're all HD.

For `a standalone server <https://support.plex.tv/hc/en-us/articles/200375666-Stand-Alone-Server>`_ that serves data off the network and can transcode the HD video you need:

- Intel Core 2 Duo 2.4GHz or better (better if you want more than one transcode op to run at once)
- 2+ GB RAM
- `Network resources properly mounted as drives <https://support.plex.tv/hc/en-us/articles/201122318-Mounting-Network-Resources>`_

I addressed this during :doc:`my plan to cut cable <../../plans/cuttingthecable>` by building :doc:`my Megaplex server <../../hardware/server/megaplex>`, which was researched/built to handle HD video with ease and hopefully be fairly future-proof.

Running as a Service
====================
**Plex doesn't run as a service** - it's interactive (except when run on the Synology). There are various forum posts about how to get Plex to run as a service or otherwise always start up after rebooting but there's no official solution.

`There is a PmsService package <https://github.com/cjmurph/PmsService>`_ that allows you to wrap Plex with a service. `This topic in the Plex forums explains how to use PmsService <https://forums.plex.tv/index.php/topic/93994-pms-as-a-service/>`_ to host Plex.

Windows Server TCP Settings
===========================
There's a reasonably well-known issue where some devices like Xbox One, iPhone, and others seem to buffer a lot even on the local network. `This Plex forum post <https://forums.plex.tv/t/enhanced-video-player-on-apple-tv-4k-creating-buffering-issues/536483/87>`_ has an answer - by changing some settings on the server, you can fix the constant buffering.

.. sourcecode:: powershell

    # Show the current TCP settings.
    Get-NetTCPSetting | ft -AutoSize

    # Update the problem settings. These are initially 20, not 300.
    Set-NetTCPSetting -SettingName "DatacenterCustom" -MinRtoMs 300
    Set-NetTCPSetting -SettingName "Datacenter" -MinRtoMs 300

If you want to totally reset the settings, you can do ``netsh int tcp reset``

Migrating Servers
=================
When I moved Plex from :doc:`my Synology <../../hardware/server/synologyds1010>` over to :doc:`Megaplex <../../hardware/server/megaplex>` I had to migrate the library from one machine to another.

Luckily, `Plex has a help topic explaining how to migrate your library <https://support.plex.tv/hc/en-us/articles/201370363-Move-an-Install-to-Another-System>`_ so I followed those instructions. *Be warned that this takes forever.* My library consisted of over 200,000 individual, tiny files (e.g., the posters and such for each title) and copying that from one place to another is super time-consuming. Be prepared to invest a couple of hours or more in moving from one server to another.

DTS-HD MA
=========
When converting my HD movies for Plex, I kept the lossless audio tracks - the DTS-HD MA format tracks - for the future. The format DTS-HD is backwards compatible with standard DTS, which Plex handles well.

I did find that sometimes this format can trip Plex up. Watching `Oblivion <http://www.amazon.com/Oblivion-Blu-ray-Digital-Copy-UltraViolet/dp/B008JFUO4U/ref=sr_1_2?s=movies-tv&ie=UTF8&qid=1435238947&sr=1-2&keywords=oblivion&tag=mhsvortex>`_, for example, the sound would just cut out after a few minutes and never return. If I fast-forwarded the movie by a second or two, the sound would be back. It was sort of like Plex lost track of where it was so decided to just not play sound, but the fast-forward operation would get it back.

When I found this, I re-converted the movie with :doc:`Handbrake <../convert/handbrake>` to only include the DTS audio and not the DTS-HD. You get a much smaller movie file and Plex no longer has the audio tracking problem.

Getting Support
===============
`Plex has some great support and documentation. <https://support.plex.tv/hc/en-us>`_ The folks in `the Plex forums <https://forums.plex.tv/>`_ are cool and ready to help.

However, when you post for help, particularly in crash situations, `you have to be aware of some stuff <https://forums.plex.tv/index.php/topic/23452-diagnosing-heap-corruption-on-windows/>`_ or you'll be asked to provide additional details before getting help.

`This page on handling crashes in Plex Media Server is the place to start. <https://support.plex.tv/hc/en-us/articles/201455336-Crash-Logs-Plex-Media-Server>`_ It has instructions on how to set up your machine to handle crash dumps and explains where the logs are. Make sure you've read through this and have things set up.
