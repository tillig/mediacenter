===================
HP EX475 MediaSmart
===================

I bought an HP EX475 MediaSmart server with :doc:`Windows Home Server v1 <../../software/deprecated/whs>` on it as my first foray into serving media and general media storage. In February 2016 I switched the OS to be :doc:`Windows Server 2012 with Windows Server Essentials <../../software/system/wse>`.

- 2GB RAM (upgraded)
- AMD Sempron Processor 3400+ (upgraded)

Storage
=======

Current drive mappings (model / serial) - helpful in debugging issues:

- WD10EADS-00L5B1 / WCAU45460755 1TB WD Green Drive
- WD10EADS-00L5B1 / WCAU46152093 1TB WD Green Drive
- WD10EADS-00L5B1 / WCAU48489215 1TB WD Green Drive
- 500GB Samsung system drive

There is a defect in WHS where the serial number of the drives inside the EX475 gets misreported. Number pairs get transposed. For example:

- Real serial number: 12345678
- Reported serial number: 21436587

RAID Controller
---------------
I discovered while setting up :doc:`Windows Server 2012 with Windows Server Essentials <../../software/system/wse>` that the OS actually sees the drives as a RAID-controlled array to be provisioned, not as separate SATA disks. **This makes it incompatible with Storage Spaces.** You can't allocate RAID disks into a Storage Space - you have to use RAID instead. I ended up putting the three 1TB drives into a RAID 5 configuration to balance storage and resilience.

WD Green Drives
---------------
I stumbled upon WD Green hard drives and they appeared to not only be affordable but also provide power saving benefits.

**Bad, bad news. In general, I've found these drives to be horrible performers.**

I added a bunch of `WD Green 1TB drives <http://www.newegg.com/Product/Product.aspx?Item=N82E16822136317>`_ and `one WD Green 2TB drive <http://www.newegg.com/Product/Product.aspx?Item=N82E16822136344>`_. However, doing so I ran into problems with PerfectDisk and defragmentation where the system would hang or blue screen, leaving errors in the event log around the storage or Marvell drivers causing issues. Further research found that *there are only two good WD Green model numbers*:

- WD10EADS-00L5B1
- WD20EADS-00R6B0

Unfortunately, about half of the drives I bought, including the 2TB drive, were not the right models. After moving data off the home server, I removed the drives with the incorrect model numbers and enabled PerfectDisk. The performance problems and I/O errors went away.

There are several drives that are known to be problematic with Windows Home Server. The WD drives that use "advanced formatting" are problematic and have an "EARS" product code like "WD20EARS." I lucked out and got the original/older format with an "EADS" code like "WD20EADS." The problem is that it requires a special utility to "align" the drives on older systems like the WHS operating system `but the utility isn't compatible with WHS <http://forum.wegotserved.com/index.php?/topic/11681-wd-green-2tb-drives-should-we-use-wd-align/?s=8d3464c66fdadf5643f991d5ef385c92>`_. I also tried a 2TB Samsung SpinPoint drive but `it turns out those are also known to have issues with WHS <http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01368548&lc=en&cc=us&dlc=en&product=3548165>`_.

eSATA Port Multiplier
---------------------
I have a Rosewill RSV-S5 5-bay eSATA port multiplier. While it can support RAID configurations, I use it as JBOD ("Just a Bunch Of Disks"). There is `a review of a Sans Digital port multiplier similar to what I have here <http://www.mediasmartserver.net/2009/01/15/review-sans-digital-towerraid-tr5m-esata-storage-enclosure/>`_ and it says the EX475 will only recognize four of the five drives in a five-drive multiplier while the EX495 will see all five. I never put more than four drives in it so I can't say.

After moving the big storage to the :doc:`Synology DS1010+ <synologyds1010>` I disconnected the port multiplier because it wasn't needed anymore, it was a tad noisy, and it ate power.


CPU / RAM
=========
I upgraded the RAM and it's works great, no issues. I considered upgrading the CPU on it, but `according to these CPU upgrade instructions <http://www.homeserverhacks.com/2008/03/add-performance-to-your-hp-ex470-with.html>`_, that doesn't really help with file access time (which was my big bottleneck) so it wasn't really worth the risk. Several folks in comments report problems, though several others say it went off without a hitch.

Drivers
=======

Marvell SATA Driver
-------------------
The stock Marvell SATA controller driver is 1.2.0.46. I tried upgrading the "Marvell Virtual Device" driver through Windows Update to 1.2.0.57 but the "Marvell 61xx Marvell RAID Controller" still read 1.2.0.46. I'm not sure how the two are related. Either way, it didn't fix the issue I saw with the WD Green drives.

**I intentionally never updated to driver 1.2.0.60.** Alex Kuretz (from MediaSmartServer.net) has said the newer drivers can render a port mutliplier inoperable. On the other hand, ymboc (the guy behind lots of low-level hacks on WHS), `says the 1.2.0.68 drivers help a lot <http://www.mediasmartserver.net/forums/viewtopic.php?f=2&t=4675>`_.

`This site says the EX470 (same internals as EX475, different drive configuration out of the box) has a Marvell 88SE6111 SATA controller <http://www.smallnetbuilder.com/content/view/30135/75/1/2/>`_, so I thought I'd be looking for drivers for that, but `this upgrade tutorial <http://www.homeserverhacks.com/2008/11/update-marvell-6121-esata-driver.html>`_ uses the 6121 drivers and even provides a link to 1.2.0.57. `This article also uses the 1.2.0.57 drivers <http://viztaview.wordpress.com/2009/03/05/drivers-for-hp-ex-47-mediasmart-servers/>`_. Most times we're looking at the WinXP 32-bit drivers for upgrade.

I stopped fussing with the Marvell SATA drivers when I moved storage to the :doc:`Synology DS1010+ <synologyds1010>`.

WNAS Driver
-----------
There appears to be a defect with the WNAS driver where it reports high heat on the VRM (voltage regulator module). It's been ongoing since I got the machine. All drives in the system seem to work fine and the system generally reports healthy. I verified it had nothing to do with eSATA or the port multiplier. I've read on forums where a couple of people have seen this and it always comes out that there is some sort of misreporting problem going on.

The WNAS driver also appears to be what controls the lights on the HP EX475. After updating to :doc:`Windows Server 2012 with Windows Server Essentials <../../software/system/wse>` the lights on the drives and the system health light no longer functioned as they did in the Windows Home Server world.

I found `a forum where someone reverse-engineered the driver for WHS 2011 <http://forum.wegotserved.com/index.php?/topic/18458-hp-ex48x-lights-management-driver-for-whs-2011/>`_ but it doesn't support the HP EX475. They claim they did it by reverse-engineering the WNAS driver. At some point I may look into this.

HP Software Updates
===================
The machine came with a 2.x version of the HP home server software (some custom stuff on top of :doc:`Windows Home Server v1 <../../software/deprecated/whs>`). A 3.0 update came out but I never installed it.

To install the update, it's sort of a "server recovery model" - basically it keeps storage but wipes the system drive. If you have folder duplication running, any data that was stored on the system drive will be duplicated to another drive in the pool.

- Make sure folder duplication is running.
- Consider doing a file list dump to see if anything in storage is lost after the update.
- Be prepared to lose the backup database. You may need to do the full reset on that after updating.
- First thing after the update, run Windows Update to get WHS Power Pack 3. PP3 is not included on the disc.
- Leave it for a night before installing additional add-ins. There will be churn as it re-discovers files in storage.
- You will need to re-create all of the user accounts, but you won't have to re-create the user-specific folders.

I ordered the update on 2/26/10 for $27.95 and received the discs in early April.

`There is a blog entry from a guy who has done the 3.0 update <http://usingwindowshomeserver.com/2010/02/27/replacing-the-system-drive-on-the-hp-mediasmart-ex47x-series-and-performing-the-3-0-software-update/>`_ and swapped out the system drive at the same time. This apparently worked well. That said, `he had trouble running the update from Windows 7 <http://usingwindowshomeserver.com/2010/02/27/experiences-and-issues-upgrading-to-the-hp-mediasmart-server-3-0-software-release/>`_ so if I run into that I should try from an XP or Vista machine (VM?).

The 3.0 update does not contain any updated drivers.

Upgrade to Windows Server 2012 Essentials
=========================================
January 8, 2013 was the last day of support for :doc:`Windows Home Server v1 <../../software/deprecated/whs>`. In February 2016 I upgraded to :doc:`Windows Server 2012 with Windows Server Essentials <../../software/system/wse>`.

I basically followed `this article another person wrote on upgrading <http://www.wegotserved.com/2012/10/12/install-windows-server-2012-essentials-hp-mediasmart-server/>`_. I even made my own debug cable `rather than buying one <http://www.mediasmartserver.net/forums/viewtopic.php?f=6&t=8066>`_.

I thought I might have to upgrade the processor `which sounds painful <http://www.mediasmartserver.net/forums/viewtopic.php?f=2&t=1102>`_ because you need to modify the BIOS to support it... but it turned out the processor upgrade I already did supports WSE just fine.

I did find that Windows Storage Spaces, which I wanted to use, isn't compatible with RAID drive arrays. The HP EX475 registers drives as controlled by a hardware RAID array, so I was stuck on Storage Spaces and instead had to use RAID 5.

This upgrade really showed me how close to end-of-life this hardware is. Fighting with the debug cable just added a whole level of pain to everything. I realize I could probably put some form of Linux on there, but then we get out of "appliance I don't have to pay attention to" and into "something I have to fiddle with." I don't want to fiddle with it, I just want it to work.

Deprecation
===========
In June 2016, I noticed things were starting to run really slow. CrashPlan backups were taking days to finish (even when there was nothing new to back up). I couldn't do anything but file sharing on the server because everything else took too much toll on the CPU and RAM. I tried running an error scan on the system OS drive and it took two days to finish. A long-time issue with one of the cooling fans rattling came back.

All of that along with the fact that this thing is headless... I lost confidence in the machine. It stopped behaving like an appliance.

I started the process of moving all the data off the WHS machine and onto the :doc:`Synology DS1010+ <synologyds1010>`. I will probably keep it around for workstation backups but will move CrashPlan to a different machine.