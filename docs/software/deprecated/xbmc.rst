====
XBMC
====

I was using `XBMC (now "Kodi") <http://kodi.tv>`_ as my media center front-end along with a shared database to handle synchronizing the state of the media library. I had gone from :doc:`Windows Media Center <windowsmediacenter>` to XBMC in December 2011 because Windows Media Center couldn't handle the volume of content I had and the XBMC interface is much more friendly.

While I liked the ease of use and the handling of ``VIDEO_TS`` folders, once I updated my :doc:`goals <../../requirements>` for more accessibility of media, :doc:`Plex <../plex>` seemed like a better fit for me, so I switched again.

Media Organization
==================
XBMC media organization is very similar to :doc:`Plex <../plex>` so moving wasn't too hard.

- `Movies <http://kodi.wiki/view/Movies_(Video_Library)>`_ (including `set groups <http://kodi.wiki/view/Movie_Sets>`_)
- `TV Shows <http://kodi.wiki/view/TV_Shows_(Video_Library)>`_

Advanced Configuration
======================
In order to have a shared database and proper scanning of ``VIDEO_TS`` folders, I had to do a bit of advanced configuration in XBMC.

Advanced config settings are stored in `the userdata folder <http://kodi.wiki/view/Userdata_folder>`_ in a file called `advancedsettings.xml <http://kodi.wiki/view/Advancedsettings.xml>`_

Here's what I used for my ``advancedsettings.xml`` file:

.. sourcecode:: xml

    <advancedsettings>
      <sorttokens>
        <token>the</token>
        <token>a</token>
        <token>an</token>
      </sorttokens>

      <!-- Regular expressions to match VIDEO_TS folders. -->
      <tvshowmatching append="no">
        <regexp>\[[Ss]([0-9]+)\]_\[[Ee]([0-9]+)\]?([^\\/]*)(?:(?:[\\/]video_ts)[\\/]video_ts.ifo)?</regexp>
        <regexp>[\._ \[\-\\/]([0-9]+)x([0-9]+)([^\\/]*)(?:(?:[\\/]video_ts)[\\/]video_ts.ifo)?</regexp>
        <regexp>[Ss]([0-9]+)[\.\-]?[Ee]([0-9]+)([^\\/]*)(?:(?:[\\/]video_ts)[\\/]video_ts.ifo)?</regexp>
        <regexp>[\._ \-\\/]([0-9]+)([0-9][0-9])([\._ \-][^\\/]*)(?:(?:[\\/]video_ts)[\\/]video_ts.ifo)?</regexp>
      </tvshowmatching>

      <!-- Don't show "unwatched" flags. -->
      <video>
        <playcountminimumpercent>101</playcountminimumpercent>
      </video>

      <!-- Don't recognize disc images as videos. -->
      <videoextensions>
        <!-- add>.ex1|.ex2</add -->
        <remove>.dat|.bin</remove>
      </videoextensions>

      <!-- Database sharing/synchronization. -->
      <videodatabase>
        <type>mysql</type>
        <host>192.168.XXX.XXX</host>
        <port>3306</port>
        <user>XXXXXXXX</user>
        <pass>XXXXXXXX</pass>
        <name>xbmc_video</name>
      </videodatabase>
      <musicdatabase>
        <type>mysql</type>
        <host>192.168.XXX.XXX</host>
        <port>3306</port>
        <user>XXXXXXXX</user>
        <pass>XXXXXXXX</pass>
        <name>xbmc_music</name>
      </musicdatabase>

      <!-- Central cache for thumbnails. -->
      <pathsubstitution>
        <substitute>
          <from>special://masterprofile/Thumbnails</from>
          <to>smb://illighomeserver/Public/XBMC/userdata/Thumbnails</to>
        </substitute>
        <substitute>
          <from>special://profile/Thumbnails</from>
          <to>smb://illighomeserver/Public/XBMC/userdata/Thumbnails</to>
        </substitute>
      </pathsubstitution>
    </advancedsettings>

Troubleshooting
===============
I ran into various challenges getting XBMC to properly work on my somewhat-underpowered front-end machine. I also ran into challenges getting it to start up automatically after a reboot. These notes helped get me past that.

- `Optimizing Windows 7 <http://cybernetnews.com/xbmc-optimize-windows-7/>`_ talks about updating the BIOS settings to increase the shared video RAM and disabling certain other settings that may cause issues.
- `Troubleshoot Buffering Issues <http://cybernetnews.com/xbmc-troubleshoot-buffering-issues/>`_ says video RAM and ``cachemembuffersize`` in the ``advancedsettings.xml`` may need tweaking.
- While `Windows 8.1 makes starting XBMC on boot easier <http://forum.kodi.tv/showthread.php?tid=174086>`_, there is a whole `walkthrough explaining how to do it on Windows 8 <http://cybernetnews.com/xbmc-run-boot-xbmc-startup-windows-8/>`_. You can also use `a batch file to force boot to desktop <http://forum.kodi.tv/showthread.php?tid=110132&page=2>`_ which allows this to work in Windows 8.

The "boot to desktop" batch file looks like this:

.. sourcecode:: batch

    C:\Windows\explorer.exe shell:::{3080F90D-D7AD-11D9-BD98-0000947B0257}
    "C:\Program Files (x86)\XBMC\xbmc.exe" shell:::{3080F90D-D7AD-11D9-BD98-0000947B0257}
    Exit