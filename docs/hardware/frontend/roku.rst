====
Roku
====

Roku 3
======

I picked up a `Roku 3 <http://www.amazon.com/dp/B00BGGDVOO?tag=mhsvortex>`_ after doing some comparison work between :doc:`Chromecast <chromecast>`, `Roku 3 <http://www.amazon.com/dp/B00BGGDVOO?tag=mhsvortex>`_, `Apple TV <http://www.amazon.com/dp/B007I5JT4S?tag=mhsvortex>`_, and `Amazon Fire TV <http://www.amazon.com/dp/B00CX5P8FC?tag=mhsvortex>`_.

.. image:: roku.jpg

While the Amazon site has `a comparison of Fire TV to Roku <http://www.amazon.com/dp/B00CX5P8FC?tag=mhsvortex>`_ and it appears to win (of course), `the majority of third-party reviews rank Roku 3 as the winner <http://www.cnet.com/news/chromecast-vs-apple-tv-vs-roku-3-which-media-streamer-should-you-buy/>`_.

`Roku has a Tablo channel <https://www.tablotv.com/blog/tablo-rockin-roku/>`_ so viewing :doc:`Tablo DVR <../server/tablo>` content is directly supported. It's very smooth and easily supports the highest quality Tablo recordings.

Roku Ultra
==========

When we upgraded to our 4K :doc:`Samsung UN65KS8000 <../tv/samsungun65ks8000>` we upgraded the Roku 3 to a Roku Ultra.

For the most part it was nice, but in around February 2017 we encountered two issues.

First, the Netflix app didn't seem to stream as fast as it should. Our Internet connection speed tested out at 150Mbps but the Netflix app internal speed test generally topped out at 30Mbps. When it dipped lower than that, we got artifacts when streaming 4K content. I don't know if there's some sort of traffic shaping going on at Comcast or what, but it was frustrating.

Second, with the February 2017 7.5.1 release of the Roku Ultra firmware things started going downhill.

- `There's a random pop/chirp noise in all channels. <https://forums.roku.com/viewtopic.php?f=28&t=98931&p=555044#p555044>`_ This appears to have been fixed with the 7.7 firmware.
- There are inconsistent HDMI handshake problems. This manifests after having the TV turned off for a period of several hours. When the TV gets turned back on, sometimes the Roku displays just fine; sometimes the picture flickers; sometimes it doesn't come back at all. In the latter two cases the only way to fix it is to reboot the Roku. The 7.7 firmware fixed most of the flickering but there's still the problem of the picture just not coming back.

In August 2017 I gave up on Roku Ultra for a while. The Roku 3 units maintained stability but I was rebooting the Roku Ultra pretty much every time I wanted to watch anything.

Once we started using the :doc:`NVIDIA Shield TV <nvidiashield>` full time, I moved the Roku Ultra upstairs to the master bedroom. It works fine for standard HD.

Plex Channel
============

With some of my HD movies the Plex channel will occasionally hang unexpectedly and just stop playing. I found that going into the Plex channel/app settings, under Transcoder, unchecking "Direct Stream" seems to fix it.

Secret Menus
============

Roku has some secret settings menus for advanced users. *Use at your own risk.* I haven't really done much with these. To reach the menus, press the keys on the remote as listed:

- Secret Menu #1: Home (x5), FF (x3), RW (x2)
- Secret Menu #2: Home (x5), Up, Right, Down, Left, Up
- Wi-Fi Menu: Home (x5), Up, Down, Up, Down, Up
- Platform Menu: Home (x5), FF, Pause, RW, Pause, FF
- Antenna Menu: Home (x5), FF, Down, RW, Down, FF
- Bit Rate Menu: Home (x5), RW (x3), FF (x2)
- Developer Menu: Home (x3), Up (x2), Left, Right, Left, Right, Left
- Network Menu: Home (x5), Right, Left, Right, Left, Right
- Reboot Device: Home (x5), Up, RW (x2), FF (x2)

There is a nice infographic of these commands `on the Lifehacker site <http://lifehacker.com/all-the-roku-secret-commands-and-menus-in-one-graphic-1779010902>`_.
