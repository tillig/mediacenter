====================
Synology DS1010+ NAS
====================

:doc:`Diskstation Manager (DSM) <../../software/system/dsm>` is the operating system that runs Synology NAS devices.

Storage
=======

    - I have a bunch of WD Green drives I pulled out of my :doc:`Windows Home Server <hpex475>`. Synology forums have some posts about this. `This one says that some of the drives work fine while others don't <http://forum.synology.com/enu/viewtopic.php?f=151&t=19131>`_; `this one is about someone who is trying to avoid issues by switching away from WD Green <http://forum.synology.com/enu/viewtopic.php?f=124&t=23719>`_. I should check and see which model numbers I have - I may have some bum drives that are known to be slow.
    - `I should get the latest firmware off the website <http://www.synology.com/support/download.php?lang=enu>`_ for initial install. This will make sure everything is compatible with newer disks.
    - `There is a hardware compatibility list for supported drives <http://www.synology.com/support/faq_show.php?q_id=130>`_ on Synology devices.

Of the 2TB drives listed as directly supported, these seem reasonably viable. Others are rated far too slow or are way beyond the $250/drive range (as of ~2010)...

    - Seagate Barracuda ST32000542AS is 5900RPM, 3Gb/s, 32MB cache. `$130 at NewEgg <http://www.newegg.com/Product/Product.aspx?Item=N82E16822148413&Tpk=ST32000542AS>`_, `$120 at Amazon <http://www.amazon.com/dp/B0028Y4CY6?tag=mhsvortex>`_. `A very favorable review here <http://hardwarelogic.com/articles.php?id=5578>`_ shows it outperforms an older performance-oriented model on all sorts of benchmarks, so spin speed isn't everything.
    - Seagate Barracuda XT ST32000641AS is 7200RPM, 6Gb/s, 64MB cache. `$250 at NewEgg <http://www.newegg.com/Product/Product.aspx?Item=N82E16822148506&Tpk=ST32000641AS>`_, `$270 at Amazon <http://www.amazon.com/dp/B002RWJHBM?tag=mhsvortex>`_.
    - Samsung Spinpoint HD203WI is 5400 RPM, 3Gb/s, 32MB cache. `$140 at NewEgg <http://www.newegg.com/Product/Product.aspx?Item=N82E16822152202&Tpk=HD203WI>`_, not at Amazon.

Remote Shutdown
===============
I have multiple UPS units, but when I only had one, I wanted to tie my :doc:`Windows Home Server <hpex475>` to the UPS and have it trigger other servers to shut down when the UPS went into a critical battery mode. I researched how to do remote shutdown on the Synology so I could potentially implement it, but I never did because I ended up adding a second UPS and tied one server to each.

If I set up SSH on the machine along with public key authentication, `I can use SSH to remote shutdown the Diskstation <http://forum.synology.com/enu/viewtopic.php?f=19&t=32549&p=129019#p129019>`_:

``ssh root@diskstation poweroff``

Basic Commands
==============
There are some `basic commands for managing the Synology Diskstation via command line <http://forum.synology.com/wiki/index.php/Basic_commands>`_.

Note that you have to `enable command-line access through SSH <http://forum.synology.com/wiki/index.php/Enabling_the_Command_Line_Interface>`_. Here's some info on setting up `secure key authentication with SSH <http://blog.bobpeers.com/2008/05/30/ssh-into-a-synology-disk-station-using-secure-keys/>`_ on the Diskstation. I'll want to make sure I've got the latest DSM installed before doing this. (Don't go beta, though, `betas seem to break stuff <http://forum.synology.com/enu/viewtopic.php?f=168&t=32772>`_.)
