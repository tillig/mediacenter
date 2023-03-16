===================
DiskStation Manager
===================

`The Synology DiskStation Manager <https://www.synology.com/en-us/dsm>`_, or "DSM," is the administrative interface for Synology NAS products. For example, when working with my :doc:`Synology DS1010+ <../../hardware/server/synologyds1010>`, this is the interface I use to install and configure various packages.

Remote Shutdown
===============
I have multiple UPS units, but when I only had one, I wanted to tie my :doc:`Windows Home Server <../../hardware/deprecated/hpex475>` to the UPS and have it trigger other servers to shut down when the UPS went into a critical battery mode. I researched how to do remote shutdown on the Synology so I could potentially implement it, but I never did because I ended up adding a second UPS and tied one server to each. I have since deprecated my Windows Home Server.

If I set up SSH on the machine along with public key authentication, `I can use SSH to remote shutdown the Diskstation <https://forum.synology.com/enu/viewtopic.php?f=19&t=32549&p=129019#p129019>`_:

``ssh root@diskstation poweroff``

Basic Commands
==============
There are some `basic commands for managing the Synology Diskstation via command line <https://forum.synology.com/wiki/index.php/Basic_commands>`_.

Note that you have to `enable command-line access through SSH <https://forum.synology.com/wiki/index.php/Enabling_the_Command_Line_Interface>`_. Here's some info on setting up `secure key authentication with SSH <https://blog.bobpeers.com/2008/05/30/ssh-into-a-synology-disk-station-using-secure-keys/>`_ on the Diskstation. I'll want to make sure I've got the latest DSM installed before doing this. (Don't go beta, though, `betas seem to break stuff <https://forum.synology.com/enu/viewtopic.php?f=168&t=32772>`_.)
