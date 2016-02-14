=========================
Windows Server Essentials
=========================

In February 2016 I upgraded my :doc:`HP EX475 Windows Home Server <../../hardware/server/hpex475>` from :doc:`Windows Home Server v1 <../deprecated/whs>` to Windows Server 2012 R2 with Windows Server Essentials.

What's interesting is how Windows Server Essentials is so much "the evolution" of Windows Home Server. Except for the more "media-centric" sharing that was present in WHS, WSE has pretty much the same feature set - client backups, shared folders, user account management.

Active Directory
================

I wasn't really looking to run an Active Directory at home but WSE requires it - it *is* your domain controller. I saw some docs on how to handle things if you wanted to join it to a domain or something, but since I didn't already have a domain set up, I did this.

Storage
=======

I *wanted* to use Storage Spaces to span the disks in the HP EX475 but found that Storage Spaces are *not compatible with RAID controlled disks*. The HP EX475 disks are seen as RAID, so I went with RAID 5 across the three storage disks.

Backups
=======

I have an external 1TB hard drive set as a local backup destination for the shared data content using :doc:`Crashplan <crashplan>`.

I found that you can't use the same hard drive for the built-in server backup as well as other backup types or other storage, so I need a second external drive for server OS backups.

Networking
==========

If you install the Windows Server Essentials Connector (by visiting ``http://servername/connect`` on your server), it adds a few services that not only help backup your computer and monitor settings... but it also enforces that the DNS server is always set to the WSE machine. Normally this works fine and correctly forwards to your router or whatever, except in the case of things like ``routerlogin.net`` used by Netgear routers. I had to add a DNS forwarding zone for ``routerlogin.net`` with a single A record pointing to ``192.168.1.1`` to get my router UI back up and running.