==========
Asset UPnP
==========

I picked up `Asset UPnP <http://www.dbpoweramp.com/asset-upnp-dlna.htm>`_ back `in 2009 <http://www.paraesthesia.com/archive/2009/08/11/stream-more-music-from-windows-home-server-with-asset-upnp.aspx/>`_ when I was trying desperately to figure out how to get :doc:`iTunes <../manage/itunes>` music to play natively in :doc:`Windows Media Center <../deprecated/windowsmediacenter>`.

Asset UPnP is a DLNA-compatible music streamer that can play pretty much any music format. It does a great job transcoding and seems to work well with every :doc:`front-end device <../../hardware/frontend/index>` I throw at it.

I have it running on my :doc:`Windows Home Server <../../hardware/server/hpex475>`, which is also where my music is stored.

With the updates in 2015 to the music streaming experience in :doc:`Plex <plex>` I am considering switching my music streaming over there to unify the experience rather than maintaining multiple servers. That would also let me deprecate my :doc:`Windows Home Server <../../hardware/server/hpex475>` when needed, since that's the last service it provides.

Transcoding Settings
====================

In order to allow all of my :doc:`front-end devices <../../hardware/frontend/index>` to play my music, I have the following settings in the "Advanced Settings" section of Asset UPnP:

- Force WAV Streaming
- Check the AAC, M4A, M4B, and MP4 boxes so iTunes music (including Apple Lossless) is supported everywhere.

I used to have this set to force MP3 streaming but `recent software updates <https://forum.dbpoweramp.com/showthread.php?35366-Slow-response-to-PS3-client-not-to-others>`_ in :doc:`PS3 <../../hardware/frontend/ps3>` made the WAV streaming a better choice.

As my :doc:`front-end device <../../hardware/frontend/index>` music format support improves, I may stop asking it to transcode entirely. AAC / ALAC is far more compatible now than it was several years ago when I started this.

iTunes Playlists
================

Asset supports playlists in `.m3u <http://en.wikipedia.org/wiki/M3U>`_ format, which means you can export your iTunes playlists and have them work in Asset UPnP.

1. Go get `iTunes Export <http://www.ericdaugherty.com/dev/itunesexport/>`_, a program that will export your iTunes playlists into .m3u format.
2. Close iTunes if you have it open. The exporter uses the XML version of the library and you want to make sure both that iTunes isn't locking that file and that the very latest has been written to disk so the exporter gets the right data.
3. Run the iTunes exporter.
4. Select the iTunes library XML file location.
5. Wait while the application loads the iTunes library and discovers your playlists.
6. Select the playlists that you want to export, then click "Next."
7. Select your various export options and click "Next." Make sure you...

    1. Choose "M3U" as the playlist format.
    2. Check the "Include UTF-8 BOM" and "Use Intl Extension (M3U8)" boxes. This allows you to have artist or track names that have international characters in them.
    3. For "File Types" choose "All Files" since Asset UPnP will be transcoding things so they can all be understood by the target client.
    4. In the "Music Folder (Prefix)" field, put the file path (relative to the Asset UPnP installation) where the music is stored on your server (for me, this is ``d:\Shares\Music\``) and don't forget the trailing slash. Setting that "Music Folder (Prefix)" field makes it so you don't have to do any search-and-replace later.
    5. Make a note of the "Output Directory" setting because this is where the playlists will end up.

8. The exporter will finish and you can close it.
9. Find the playlists you just exported and...

    1. Name the .M3U8 files the way you want to see them listed in Asset. For example, a playlist in iTunes called "I Love The 80's" will be exported as "I Love The 80_s.m3u" by the exporter and Asset will show that as "I Love The 80_s" - the filename, not the original title.
    2. Open each file in a text editor and remove the comment line from the top (the line that starts with a "#").

10. Put your .m3u playlists in a place Asset can find them (on the same machine as Asset). I put mine in the Public share on my Windows Home Server under a folder called "Playlists" (e.g., ``\\myhomeserver\Public\Playlists``). (Note: You can make your life a lot easier by mapping a network drive to this location so you can export your playlists directly to the shared destination from iTunes Export.)
11. Configure Asset UPnP to find the playlists you just put on the server.

    1. Open the Asset UPnP advanced settings dialog.
    2. In the top right corner you'll see a box marked "Audio Library." In it you should see the folder with your music (e.g., ``D:\Shares\Music``) listed - this is how Asset knows which folders to scan for contents. You should also see that folder is listed as "Contains: Audio Tracks."
    3. In the "Audio Library" box, click the "[Add Folder]" link.
    4. Browse to and select the location you placed your playlists. In my case, I placed them in the Public share in a "Playlists" folder, so I selected ``D:\Shares\Public\Playlists``.
    5. By default, Asset sets the folder to contain music. Click the "Contains: Audio Tracks" text next to the playlist folder and a dropdown will appear. Select "Contains: Playlists" from there.
    6. Click OK. Asset will tell you it needs to restart. That's OK. It will then rescan the library and your playlists will be included.