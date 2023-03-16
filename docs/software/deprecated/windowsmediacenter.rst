====================
Windows Media Center
====================

Microsoft Windows has a built-in media center function you can use to watch digital media and DVDs. I started using Windows Media Center with my DVDs stored on my :doc:`Windows Home Server <whs>`.

I switched away from Windows Media Center to :doc:`XBMC <xbmc>` in December 2011.

While WMC allows "media center extenders" for front ends (e.g., you can use your :doc:`Xbox 360 <../../hardware/frontend/xbox>` to access Windows Media Center content), extenders can't access all content types. I ended up getting a :doc:`Dell Studio Hybrid <../../hardware/deprecated/dellstudiohybrid>` as a dedicated Windows Media Center at my TV.

Plugins
=======
You use plugins to extend the capabilities of Windows Media Center. I looked at a few but didn't get too far into it. :doc:`XBMC <xbmc>` supports extensions a little nicer.

- `MyNetflix <https://www.anpark.com/Software.aspx>`_ - View your instant queue movies right in Windows Media Center. Looks a little more robust than `vmcNetFlix <https://myweb.cableone.net/eluttmann04/projects/vmcNetFlix/default.htm>`_. *Of course, Netflix has their own native integration now*, making this moot.
- `SecondRun.tv <https://www.secondrun.tv/>`_ - Watch Hulu video on the Windows Media Center. Interface looks similar to the DVD Library.
- `Yougle Vista <https://push-a-button.com/products/youglevista/>`_ - YouTube, Apple Trailers, and other community video sources in Windows Media Center. Has an extensibility API for adding your own custom sources.
- `tubeCore <https://tubecentric.tv/>`_ - Adds UPnP/DLNA support to Windows Media Center. Primarily geared around video.
- `RadioTime <https://radiotime.com/>`_ - A streaming audio service that lets you listen to radio from around the world. Has a plugin so you can access it through Media Center.

Configuration
=============

- You generally want to `enable auto-logon <https://support.microsoft.com/default.aspx?scid=kb;en-us;315231>`_ for a Media Center PC so you can reboot without getting prompted for a password.
- Windows Media Center shares a library with Windows Media Player. `You can delete the Windows Media Player library and force Windows Media Center to reindex everything <https://www.krunk4ever.com/blog/2007/09/16/reindexing-media-center-library/>`_ if you find things aren't up to date.
- There are a bunch of `undocumented registry settings <https://blogs.msdn.com/astebner/archive/2006/04/29/586961.aspx>`_ that help you tweak media center. You can use them to `adjust the overscan <https://thegreenbutton.com/forums/thread/17197.aspx>`_ of the display.
- The Netflix plugin left two Netflix tiles on the TV + Movies screen. I asked about it `on the Microsoft Answers forum <https://social.answers.microsoft.com/Forums/en-US/vistamedia/thread/f1bb52a0-11f1-4889-9831-358092814386>`_. It was also reported, with no solution, `on The Green Button <https://thegreenbutton.com/forums/thread/362226.aspx>`_. It eventually worked itself out with an update that came in for Windows Media Center. In case I need to directly download the plugin, `here's the link <https://go.microsoft.com/fwlink/?LinkID=147175&clcid=0x409>`_.
- I couldn't figure out how to totally stop a video and not have the little thumbnail show up in the corner. I've asked about `how to totally stop a video on the Microsoft Answers forum <https://social.answers.microsoft.com/Forums/en-US/vistamedia/thread/182adfd2-b205-46bb-b3d3-765ac3acb5f3>`_. It turns out that if you watch a web-based video, you can't totally stop it; you just have to start playing something else.
- The movie metadata (thumbnails, etc.) are stored in a folder called "DvdInfoCache." If you want to share the data across multiple machines, you can: `here's how to share DvdInfoCache <https://themetabrowser.com/userguide/sharing-dvdinfocache/>`_.

Changing the DVD Player
=======================
The idea here is that the built-in codec for playing DVDs (``VIDEO_TS`` included) isn't as good as some third-party ones. I originally looked into changing this when I didn't realize you could change the zoom/aspect ratio of playback by using the "info" button on the remote.

Most people use `MyMovies <https://www.mymovies.dk/>`_ and TheaterTek DVD player (or some other player). `I've asked what the best DVD player package is on the MyMovies forums. <https://www.mymovies.dk/forum.aspx?g=posts&t=9238>`_

There is a `utility that allows you to choose a different decoder for playing DVDs <https://mediacenterexpert.blogspot.com/2006/07/vista-media-center-decoder-utility.html>`_. (`Here's the walkthrough of the registry entries you need to update <https://mediacenterexpert.blogspot.com/2006/07/vista-media-center-changing-default.html>`_ - the tool automates the registry settings.)

- Updating the codec might make things play smoother.
- I posted a question about `improving the internal player on the AVSForums <https://www.avsforum.com/avs-vb/showthread.php?t=1069362>`_.

FFDShow integration (see below) updates the DVD player as well as adding the ability for new video formats to play.

PowerDVD
--------
You can `set up PowerDVD, for example, using registry settings <https://www.mymovies.dk/forum.aspx?g=posts&t=8804>`_. Several folks recommend using the PowerDVD codec over VMC one.

There are `different options for integrating PowerDVD <https://www.avsforum.com/avs-vb/archive/index.php/t-924118.html>`_. Primarily people use the PowerDVD codec for playback rather than the built-in one.

You can `integrate PowerDVD as an external application <https://thegreenbutton.com/blogs/mike/archive/2007/01/14/158640.aspx>`_ using an "mcl" file. (This is how you get HD DVD and Blu-ray playback to work.) There's an article about `extending Media Center with XML files <https://mediacenterexpert.blogspot.com/2006/07/vista-media-center-decoder-utility.html>`_.

There is `a launching application for PowerDVD <https://thegreenbutton.com/forums/thread/279556.aspx>`_ that someone wrote. Might do what needs to be done. Looks like it can launch any app, not just PowerDVD. That said, it doesn't add a button to each movie, it just lets you launch the app.

TotalMedia Theatre
------------------
ArcSoft TotalMedia Theatre seems to be growing on people.

- `Remove the "which player do you want to use" setting <https://www.mymovies.dk/forum.aspx?g=posts&t=8874>`_ and let MyMovies handle it.
- `I'd just need the TotalMedia Theatre <https://www.mymovies.dk/forum.aspx?g=posts&t=8820>`_, NOT the Extreme version.

`ArcSoft Total Media Theater <https://www.arcsoft.com/products/totalmediatheatre/>`_ integrates with Media Center via a plugin. `There is a review of it here with screen shots. <https://www.missingremote.com/index.php?option=com_content&task=view&id=2822&Itemid=1&limit=1&limitstart=2>`_

FFDShow Integration
-------------------
FFDShow updates the DVD player as well as adding new video format support. `Media Control <https://damienbt.free.fr/index.php>`_ integrates FFDShow codecs into Media Center, however, `it doesn't look like it's really well supported <https://damienbt.free.fr/phpBB2/viewtopic.php?t=33&highlight=dvd>`_. You may be able to get results `if you switch the default MPEG2 decoder <https://damienbt.free.fr/phpBB2/viewtopic.php?t=440&start=0&postdays=0&postorder=asc&highlight=dvd>`_, but in general, it appears that `launching DVD Library titles with FFDShow may be experimental <https://damienbt.free.fr/phpBB2/viewtopic.php?t=271&highlight=dvd>`_.

Enabling iTunes
===============
My original thought was to try to get Windows Media Center to serve :doc:`iTunes <../manage/itunes>` (AAC/M4A) music natively. **It turns out that's very hard.**

**I never did get this working.** Instead I went to :doc:`Asset UPnP <../serve/asset>` to serve my music and it's been awesome.

But, for folks interested in some of the notes/travails, here you go.

Objectives
----------
Originally, I wanted a seamless music experience where I don't have to leave Windows Media Center and run iTunes separately.

- I've seen this done through `MCETunes <https://www.mcetunes.com/>`_, but there appears to be a lot of moving parts with that and, reading through the forums, it appears there's some weirdness around gaps between songs... like MCETunes is just "wrapping" iTunes through the COM interface.
- Instead, I wanted to get WindowsMediaCenter natively understanding AAC/M4A songs.

    - Apple Lossless, MP4/AAC/M4A is all included.
    - I don't care if it doesn't play "licensed" music since Apple's moving away from that anyway.
    - It does need to read the song metadata and correctly display artist/album/track info (at a minimum). It'd be nice to get playlists in there, too, as well as ratings and album art, but I'm not going to be picky.

As part of doing that, the iTunes metadata (particularly album art) would need to be cleaned up. That part of the project is the remaining important part.

Plan
----

- Install the DSP-worx plugin on laptop.
- Install the tag extender on laptop.
- Update album artist tags via iTunes. Using "Various Artists" for albums that are compilations or otherwise have lots of contributors.
- Allow Media Player to retrieve information from the internet for tracks - see if those Album{GUID} tracks are showing up, verify tracks are still playable in iTunes if info is downloaded. (Putting Folder.jpg into the folder with the music handles the Album Art issue.)
- Play music in Windows Media Center. (Does this involve setting up folder monitoring for the Music share? Yes, it does.)
- Get the album art updated on all tracks.
- Write a script to get rid of all of the automatic album art in the folders.
- Write a script to delete any empty folders.
- Write a script to set any downloaded artwork right on the track so metadata readers can get it, then clear the downloaded artwork.
- Write a script to get Folder.jpg into the folders based on the metadata art.
- Write a script to make a playlist from all songs where artist != album artist AND album artist != "Various Artists". That list will contain a set of tracks that may have album artist incorrectly set.
- Clean up the filesystem (run the scripts):

    - Set the downloaded artwork to be part of the track.
    - Delete the Folder.jpg files.
    - Clear out empty folders.
    - Set Folder.jpg for all folders based on track artwork.

I had previously set up all the tests with the DSP-worx plugin on my primary laptop before I upgraded from Windows Vista to Windows 7. Post-upgrade, I did not re-introduce these elements as, by that time, I had already decided to skip getting this working in media center. I have too many other devices that understand DLNA/UPnP streaming just fine so I decided to reduce the moving pieces and just use those.

Notes
-----

- `DSP-worx <https://www.dsp-worx.de/>`_ has a January 8, 2007 entry talking about playing Apple Lossless in Media Player. That might also work for Media Center. `There is a bit of discussion on getting this working <https://www.eggheadcafe.com/software/aspnet/32790282/play-apple-lossless-on-wi.aspx>`_. It seems this is a common (and the only solution). An even better discussion on getting it set up is here. `Hydrogenaudio has a forum on it as well. <https://www.hydrogenaudio.org/forums/index.php?s=aa0c34bbe6db4a90a18f904c50b0327b&showtopic=46551&st=75>`_

    - `Install the plugin. <https://files.dsp-worx.de/dsmp3source_aac_alac.zip>`_ It may not work if the directory it's registered from `has spaces in it <https://www.hydrogenaudio.org/forums/index.php?showtopic=46551&st=50>`_.
    - Install the tag extender.

- If the DSP-works one doesn't work, `here's a registry patch that lets Media Center play AAC <https://a8t8.spaces.live.com/blog/cns%212518DD508BB713E8%21156.entry>`_.
- Album Art!

    - It may be that the auto-downloading behavior of Windows Media Player will overwrite Folder.jpg files. If that's how it is, set WMP to not auto-download.
    - `Put a Folder.jpg in the folder with the songs. <https://dalepreston.com/Blog/2007/11/more-windows-media-player-album-art.html>`_ That will get album art in, at least for each album if not for each individual song.
    - I can use a script to extract the art from one song on each album and dump it to Folder.jpg.
    - `Clearing out the library <https://www.krunk4ever.com/blog/2007/09/16/reindexing-media-center-library/>`_ may come in handy if things go wrong.

`The article here is the most concise and basically accurate description of what needs to be done. <https://www.technologyquestions.com/technology/windows-media/133228-displaying-m4a-media-player-11-library-media-center-vista.html>`_

Getting DSP-worx to work allows you to play the songs in WMP but the metadata isn't displayed.

- Download the plugin.
- Unzip in ``C:\DSP-worx`` (or a folder that doens't have spaces in it).
- Run the ``register.bat`` file.
- Reboot.
- You should be able to add .m4a files to a playlist and play them in WMP now.

To get the metadata displayed, you need to install the tag extender.

- Set up your library. Particularly if you're sharing between iTunes and WMP, you don't want removing the file from one to impact the other. In Options...

    - Player tab:

        - The "Add media files to library when played" option doesn't seem to make a difference - they always get added to the library.

    - Library tab:

        - Under "Update library by monitoring folders," uncheck "Delete files from computer when deleted from library" if you're sharing with iTunes.
        - Under "Automatic media information updates for files" uncheck everything but "Maintain my star ratings as global ratings in files." If you don't uncheck the rename/rearrange options, your music files will get moved around. Leaving the "Retrieve additional information from the Internet" will download album art and other metadata and modify the tags in your files. You may not want that. (If you do, **it's recommended you fill in "Album Artist" on ALL tracks**. That's how album art is keyed.)

    - Privacy tab:

        - Under "Enhanced Playback and Device Experience," you may want to uncheck "Update music files by retrieving media info from the Internet." This also gets metadata and updates the tags on the files.

- Install the tag extender.
- Reboot.
- Adding things to the "Now Playing" list seems to add them to your library. You won't see the tags if you just drag them into "Now Playing,"  but if you play them from the library, everything comes up.

Scripts
-------

Powershell to get rid of all ``.jpg`` files in a folder tree, hidden or otherwise:

.. sourcecode:: ps1

    get-childitem -recurse -force | where-object { $_.Extension -eq ".jpg" } | remove-item -force

Powershell to remove empty folders (``Remove-EmptyDirectory.ps1``):

.. sourcecode:: ps1

    if($args.length -ne 1)
    {
        Write-Error "You must specify the start location."
    }
    Function Remove-EmptyDirectory
    {
        param($target)

        Begin
        {
            if($target -eq $null)
            {
                Break;
            }
            if($target.GetType().FullName -ne "System.IO.DirectoryInfo")
            {
                Break;
            }
        }
        Process
        {
            $target.GetDirectories() | foreach { Remove-EmptyDirectory $_ };
            $count = $target.GetDirectories().Length + $target.GetFiles().Length;
            if($count -lt 1)
            {
                Write-Host "Deleting " $target.FullName;
                Remove-Item $target.FullName;
            }
        }
        End
        {
        }
    }
    Get-ChildItem -force $args[0] | ForEach{ Remove-EmptyDirectory $_ }
