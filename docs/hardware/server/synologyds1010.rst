====================
Synology DS1010+ NAS
====================

The `Synology DS1010+ <https://www.amazon.com/dp/B0031ZKX5I?tag=mhsvortex>`_ is my primary storage server for video content. It has since been superseded by the `DS1515+ <https://www.amazon.com/dp/B00PTGQJL4?tag=mhsvortex>`_ but I've not seen any reason I need to upgrade. This DS1010+ serves me well and has really great performance and flexibility. I picked it up based on my :doc:`NAS research <../../plans/nas>`.

.. image:: synologyds1010.jpg
   :target: https://www.amazon.com/dp/B0031ZKX5I?tag=mhsvortex

:doc:`Diskstation Manager (DSM) <../../software/system/dsm>` is the operating system that runs Synology NAS devices. It supports installation of packages that provide additional functionality (beyond just storage) from the device. Anything from Git to MySQL to :doc:`Plex <../../software/serve/plex>` can be run as a DSM package.

Plex Support
============
:doc:`Plex <../../software/serve/plex>` does have a package to allow you to run right on the Diskstation via DSM.

**The problem I ran into with Plex on the DS1010+ was transcoding support.**

Whenever you play a video that doesn't natively play on a device or can't handle the throughput, Plex transcodes the video to something the device can handle. For example, if I'm on a phone I might easily have the bandwidth to accommodate SD content, but I might not be able to accommodate HD content (or my phone's screen might have a lower resolution that can't display full HD), so Plex will try to step it down to accommodate the restrictions.

**The DS1010+ doesn't have enough CPU power to handle transcoding HD video with Plex, full stop.** I tried to configure the server and my various devices to avoid messing with transcoding but never could get the right setup. I'd get one :doc:`front-end device <../frontend/index>` working and it would cause some other device to start requiring transcoding. SD video? Great. HD? Nope.

This lack of power is why I built the :doc:`Megaplex custom server <megaplex>` to handle :doc:`Plex <../../software/serve/plex>` for me. I keep the storage on the DS1010+, I still run other packages and services, but Plex is specifically offloaded ot the dedicated machine to enable a smooth viewing experience.

Aside: Synology does provide a "Video Station" package that has similar functionality to Plex - serving video to different devices, transcoding, etc. - and it does allow the DS1010+ to transcode HD streams. It does this because it's very specifically tailored to the Synology DSM environment. Plex, serving a much wider range of hardware, doesn't include those customizations and there is no intention of doing so to my knowledge. This has seen a lot of discussion `on the Plex forums <https://forums.plex.tv/index.php/forum/133-synology/>`_. Note I didn't choose "Video Station" over Plex because Plex has a wider array of client support and a far nicer experience in general.

Storage
=======

    - I have a bunch of WD Green drives I pulled out of my :doc:`Windows Home Server <../deprecated/hpex475>`. Synology forums have some posts about this. `This one says that some of the drives work fine while others don't <https://forum.synology.com/enu/viewtopic.php?f=151&t=19131>`_; `this one is about someone who is trying to avoid issues by switching away from WD Green <https://forum.synology.com/enu/viewtopic.php?f=124&t=23719>`_. I decided not to use these and instead go with some other drives.
    - `I should get the latest firmware off the website <https://www.synology.com/support/download.php?lang=enu>`_ for initial install. This will make sure everything is compatible with newer disks.
    - `There is a hardware compatibility list for supported drives <https://www.synology.com/support/faq_show.php?q_id=130>`_ on Synology devices.

Of the 2TB drives listed as directly supported, these seem reasonably viable. Others are rated far too slow or are way beyond the $250/drive range (as of ~2010)...

    - Seagate Barracuda ST32000542AS is 5900RPM, 3Gb/s, 32MB cache. `$130 at NewEgg <https://www.newegg.com/Product/Product.aspx?Item=N82E16822148413&Tpk=ST32000542AS>`_, `$120 at Amazon <https://www.amazon.com/dp/B0028Y4CY6?tag=mhsvortex>`_. `A very favorable review here <https://hardwarelogic.com/articles.php?id=5578>`_ shows it outperforms an older performance-oriented model on all sorts of benchmarks, so spin speed isn't everything.
    - Seagate Barracuda XT ST32000641AS is 7200RPM, 6Gb/s, 64MB cache. `$250 at NewEgg <https://www.newegg.com/Product/Product.aspx?Item=N82E16822148506&Tpk=ST32000641AS>`_, `$270 at Amazon <https://www.amazon.com/dp/B002RWJHBM?tag=mhsvortex>`_.
    - Samsung Spinpoint HD203WI is 5400 RPM, 3Gb/s, 32MB cache. `$140 at NewEgg <https://www.newegg.com/Product/Product.aspx?Item=N82E16822152202&Tpk=HD203WI>`_, not at Amazon.

In June 2016 I replaced the 2TB drives with 3TB drives so I could deprecate the :doc:`Windows Home Server <../deprecated/hpex475>` which had started getting finicky. I picked up five `WD Blue 3TB WD30EZRZ drives <https://amzn.to/28NCIKi>`_ (5400RPM, 64MB cache, $89 each) and went through the process of replacing one drive at a time. I went from an array of (7.15TB capacity / 5.8TB used / 1.35TB available) to (10.73 capacity / 5.8TB used / 4.93TB available) in a RAID 5 configuration.

Fan Upgrade
===========

In September 2019 I was working more in my office and having to sit right next to the Synology for longer periods of time. White noise from fans was bugging me. The Synology has two 80mm cooling fans that I ended up replacing with "be quiet! Pure Wings 2" silent fans.

As part of that, I did have to disable the fan beep. It seems to be a well-known thing that Synology uses fans that aren't standard. If you replace it with a nice, standard fan, the system thinks the fan has stopped and does all sorts of alerting, eventually shutting down for safety.

I did that by connecting via ``ssh root@diskstation`` using the admin user's password and then:

.. sourcecode:: sh

    # Find the location of the fan settings
    # For me this was /sys/module/pineview_synobios/parameters/check_fan
    find /sys -name *fan*

    # Create a startup script to turn off the beep
    vi /usr/syno/etc.defaults/rc.d/S99_beep_fan_disable.sh

In the script:

.. sourcecode:: sh

    echo 0 > /sys/module/pineview_synobios/parameters/check_fan

Finally, set it to execute.

.. sourcecode:: sh

    chmod +x /usr/syno/etc.defaults/rc.d/S99_beep_fan_disable.sh

Before you reboot, go into the DSM control panel. Under "Notifications," disable all the "server fan" notifications. CPU and expansion unit fan notifications should still be fine. Now reboot.

I found `one person who did a hardware hack to make a standard fan simulate what Synology wants <https://www.askrprojects.net/other/synofan/index.html>`_. I haven't gone to those lengths. Honestly, the person could probably make a mint selling little fan adapters that would hook inline with a standard fan.
