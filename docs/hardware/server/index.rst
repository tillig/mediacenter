=======
Servers
=======

.. toctree::
    synologyds1010.rst
    hpex475.rst
    megaplex.rst
    tablo.rst

Network Attached Storage Research
=================================
I looked at different NAS devices around 2010 to see if they would be more appropriate than :doc:`my Windows Home Server <hpex475>` for video storage. After research, I ended up with a :doc:`Synology Diskstation DS1010+ <synologyds1010>`.

Requirements
------------

- **Performance**: WHS is a little slow on the I/O - I think this is the overhead of the drive extender and such.
- **Reliability**: I can't duplicate my DVD rips in WHS because I'd need double storage. A RAID solution would allow me to have fault tolerance with much less overhead.
- **Scalability**: Four drives is a minimum. Since I need around 6TB of space, the ability to add drives is important.

RAID
----

The way that RAID gets expanded depends on which RAID type you choose (per the Synology documentation):

- **No RAID, Basic, RAID 0**: Backup the data, replace the drive, put the data back on the system.
- **RAID 1, 5, 5+Spare, 6, 10**: Remove and replace one drive at a time, allowing the system to rebuild the array with each replacement.

Notes
-----

- `PCWorld has some reviews on various NAS devices. <http://www.pcworld.com/reviews/collection/1651/top_10_network_attached_storage_devices.html>`_ Synology devices seem to be rated consistently higher than Western Digital and Seagate, and performance is always top marks.
- `Synology has the DS1010+ <http://www.synology.com/us/products/DS1010+/index.php>`_ that has five bays and an extension that allows for five more bays. The performance numbers listed look good and it supports RAID 5 so this would be a good solution, but it's expensive (~$1000 for a diskless system). Synology offers a "Hybrid RAID" solution that allows you to combine multiple disks of different sizes - normally all the volumes in an array have to be the same size.
    - `Here is a good overview of the functions and a review. <http://www.ntm1275.f2s.com/synology/synology1010.htm>`_ The reviewer set up jumbo frames on his network to improve speed, which isn't something I have running.
    - Read speed is 116MB/sec, write speed is 103MB/sec (under RAID 5).
- `Drobo <http://www.drobo.com/>`_ makes a five-bay system (`the Drobo S <http://www.drobo.com/products/drobo-s.php>`_) and has eSATA. It appears you can add drives to the bays just like WHS, but various reviews show it doesn't have the speed of a regular RAID system.
- `Netgear ReadyNAS NVX <http://www.netgear.com/Products/Storage/ReadyNASNVXPE.aspx?for=Home+Networking>`_ has four bays and a 75MB/sec read/write time.
    - It is not expandable via eSATA or USB so you're limited to the four bays.
    - ~$750 for the diskless system.
    - It gets decent reviews on various websites, but there is one note that a guy had problems getting it to work with his D-Link DIR-655 router. I don't know if that means I'd have similar issues with our D-Link wireless access point.
    - Has an "X-RAID2" technology that lets you expand the RAID array without having to move data off the array.
- Not investigated:
    - Iomega
    - LaCie
- Removed from consideration:
    - Seagate BlackArmor: Several reviews talk about slow performance and confusing operation.
    - Dell: They offer some nice file servers, but they're huge towers or rack mounts and they're expensive.
    - Western Digital: The ShareSpace models are the only ones that fit close to my requirements and they're slow. Plus you can only use WD drives, which is limiting.
    - Cavalry: They have only one four-bay model and, while there's not much info out there on it, that info says performance was lacking.
    - Buffalo: Reviews show slow performance and really, really horrible support. No thank you.
    - D-Link: Their four-bay device gets pretty poor reviews and their five-bay diskless device is $1500 - a full file server. There's nothing in between.

Result
------

I settled on the :doc:`Synology DS1010+ <synologyds1010>` and the Seagate ST32000542AS drives. I ordered it all on 5/16/10.

The DS1010+ gets rave reviews on every site particularly around performance, it's expandable, and appears easy to administer.

The Seagate drives are specifically on the supported list and also get reasonably good reviews, though the negative ones are around "click of death" and sector errors. I'll have to watch for this. If it turns out there are problems, I'll replace with the better (more expensive) drives.
