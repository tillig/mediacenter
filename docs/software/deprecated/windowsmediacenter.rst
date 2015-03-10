====================
Windows Media Center
====================

Microsoft Windows has a built-in media center function you can use to watch digital media and DVDs. I started using Windows Media Center with my DVDs stored on my :doc:`Windows Home Server <../system/whs>`.

I switched away from Windows Media Center to :doc:`XBMC <xbmc>` in December 2011.

While WMC allows "media center extenders" for front ends (e.g., you can use your :doc:`Xbox 360 <../../hardware/frontend/xbox360>` to access Windows Media Center content), extenders can't access all content types. I ended up getting a :doc:`Dell Studio Hybrid <../../hardware/frontend/dellstudiohybrid>` as a dedicated Windows Media Center at my TV.

Plugins
=======
You use plugins to extend the capabilities of Windows Media Center. I looked at a few but didn't get too far into it. :doc:`XBMC <xbmc>` supports extensions a little nicer.

- `MyNetflix <http://www.anpark.com/Software.aspx>`_ - View your instant queue movies right in Windows Media Center. Looks a little more robust than `vmcNetFlix <http://myweb.cableone.net/eluttmann04/projects/vmcNetFlix/default.htm>`_. *Of course, Netflix has their own native integration now*, making this moot.
- `SecondRun.tv <http://www.secondrun.tv/>`_ - Watch Hulu video on the Windows Media Center. Interface looks similar to the DVD Library.
- `Yougle Vista <http://push-a-button.com/products/youglevista/>`_ - YouTube, Apple Trailers, and other community video sources in Windows Media Center. Has an extensibility API for adding your own custom sources.
- `tubeCore <http://tubecentric.tv/>`_ - Adds UPnP/DLNA support to Windows Media Center. Primarily geared around video.
- `RadioTime <http://radiotime.com/>`_ - A streaming audio service that lets you listen to radio from around the world. Has a plugin so you can access it through Media Center.

Configuration
=============

- You generally want to `enable auto-logon <http://support.microsoft.com/default.aspx?scid=kb;en-us;315231>`_ for a Media Center PC so you can reboot without getting prompted for a password.
- Windows Media Center shares a library with Windows Media Player. `You can delete the Windows Media Player library and force Windows Media Center to reindex everything <http://www.krunk4ever.com/blog/2007/09/16/reindexing-media-center-library/>`_ if you find things aren't up to date.
- There are a bunch of `undocumented registry settings <http://blogs.msdn.com/astebner/archive/2006/04/29/586961.aspx>`_ that help you tweak media center. You can use them to `adjust the overscan <http://thegreenbutton.com/forums/thread/17197.aspx>`_ of the display.
- The Netflix plugin left two Netflix tiles on the TV + Movies screen. I asked about it `on the Microsoft Answers forum <http://social.answers.microsoft.com/Forums/en-US/vistamedia/thread/f1bb52a0-11f1-4889-9831-358092814386>`_. It was also reported, with no solution, `on The Green Button <http://thegreenbutton.com/forums/thread/362226.aspx>`_. It eventually worked itself out with an update that came in for Windows Media Center. In case I need to directly download the plugin, `here's the link <http://go.microsoft.com/fwlink/?LinkID=147175&clcid=0x409>`_.
- I couldn't figure out how to totally stop a video and not have the little thumbnail show up in the corner. I've asked about `how to totally stop a video on the Microsoft Answers forum <http://social.answers.microsoft.com/Forums/en-US/vistamedia/thread/182adfd2-b205-46bb-b3d3-765ac3acb5f3>`_. It turns out that if you watch a web-based video, you can't totally stop it; you just have to start playing something else.
- The movie metadata (thumbnails, etc.) are stored in a folder called "DvdInfoCache." If you want to share the data across multiple machines, you can: `here's how to share DvdInfoCache <http://themetabrowser.com/userguide/sharing-dvdinfocache/>`_.

Changing the DVD Player
=======================
The idea here is that the built-in codec for playing DVDs (``VIDEO_TS`` included) isn't as good as some third-party ones. I originally looked into changing this when I didn't realize you could change the zoom/aspect ratio of playback by using the "info" button on the remote.

