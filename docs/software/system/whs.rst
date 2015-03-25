===================
Windows Home Server
===================

Media Sharing
=============
Windows Home Server uses Windows Media Connect 2.0 to do its built-in sharing.

Windows Media Connect is the way Windows did DLNA style media sharing prior to Windows Media Player 11. None of the formats from :doc:`Handbrake <../convert/handbrake>` are recognized by Windows Media Connect. Even the AVI format it supports is ripped with a codec that Windows Media Connect doesn't understand. I tried all of them, even the Xbox 360 preset.

`Windows Media Connect understands <http://blogs.msdn.com/alan_ludwig/archive/2006/02/01/522092.aspx>`_:

- ``.wmv``
- ``.dvr-ms``
- ``.avi``
- ``.mpeg``, ``.mpg`` - MPEG-1
- ``.mp2``, ``.mpeg``, ``mpg`` - MPEG-2

That product has been discontinued and the replacement is the Media Sharing feature of Windows Media Player 11. `There is a good forum here explaining how to update WHS to incorporate WMP11 sharing <http://social.microsoft.com/forums/en-US/whssoftware/thread/82fd0c09-86e0-45a8-b49e-762f89ede333>`_, but **I DIDN'T DO IT**. Several accounts of people losing media sharing entirely are there as well as the fact that it takes the automatic sharing setup out of the console. Not good, and they never did come out with an official update (other than Windows Home Server v2).

Instead of using the *weak* media sharing capabilities on Windows Home Server, I put :doc:`Asset UPnP <../serve/asset>` on to serve my music and I've switched to :doc:`Plex <../serve/plex>` for video. For a short time while I was trying to get :doc:`Windows Media Center <../deprecated/windowsmediacenter>` to work, I considered using `My Movies <http://www.mymovies.dk/>`_ for WHS. I never went down that road.

Storage
=======

Defragmenting
-------------
You can't just use any standard defrag program because it won't understand the WHS filesystem.

- `PerfectDisk 10 <http://www.perfectdisk.com/products/home-perfectdisk10-windows-home-server/learn-more>`_ is what I use because it's comparable to other solutions, has a nice interface in the WHS console, and costs half of Diskeeper.
- `Diskeeper 2009 <http://www.diskeeper.com/Diskeeper/home/homeserver.aspx>`_ is another option that is fairly popular but is expensive and doesn't have anything compelling over PerfectDisk.

I noticed after running PerfectDisk for a month or so that I was getting health warnings on my system drive roughly once or twice a week. I disabled defragmentation of the system drive and these warnings stopped. (The drive works really well, not sure what this was about.)

In December 2009 my trouble with the aforementioned WD Green drives started. It was discovered when I introduced PerfectDisk into the system (though it was a drive problem, not a PerfectDisk problem).

- December 2009: Started getting file conflict errors. I disabled PerfectDisk and the errors stopped.
- January 26, 2010: Contacted PerfectDisk support. PerfectDisk support says they think it's a hardware issue. I also contacted Rosewill support, who passed me on to Sans Digital support because my port multiplier is made and supported by them. Sans Digital support said I need to upgrade the drivers for my Marvell controller. They haven't seen this exact issue, but most of their customers have all their problems go away with a driver update.
- February 3, 2010: Re-enabled PerfectDisk to verify problems still happen.
- February 4, 2010: Disabled PerfectDisk after system lockup.
- April 28, 2010: Updated Marvell drivers to 1.2.0.57 and re-enabled PerfectDisk.
- April 29, 2010: Disabled PerfectDisk after a blue screen and errors indicating "disk not ready for access."

After purging the system of some potentially problematic WD drives, I re-enabled PerfectDisk and haven't seen any issues. Definitely the WD Green drives at fault.

Checking for Drive Issues
-------------------------
You can run a special batch file (``checkall.cmd``) to run ``CHKDSK`` on all drives. Don't bother waiting to see them all pass; you should see errors in the event log if there are issues. That said, wait until the system drive is done because you may be prompted to answer a question before all the other drives start running.

.. sourcecode:: batch

    net stop pdl
    net stop whsbackup
    chkdsk D: /x /r
    chkdsk C: /x /r
    for /d %%1 in (C:\fs\*) do start chkdsk /x /r %%1

Computer Image Backup
=====================
Windows Home Server has a full image backup for Windows machines built in. It works pretty well.

On 10/26/2013 I upgraded the computers to Windows 8.1. All the other computers worked great, but one laptop failed backup because the System Reserved Partition (350MB) had only 27MB free after the upgrade. The error message I saw on the failed backup told me that I needed to run ``chkdsk`` on all the drives, but on looking at the event logs and doing some research, **the problem is the Volume Shadow Copy Service** - it's used in backups and it requires 40MB of free space. **This is common for all backup software failures** - it's not specific to WHS backup.

As a workaround I had to stop backing up the System Reserved Partition on Inspiron. I'll have files, but if things break I'll need to do a clean Windows install (with a 400MB or 500MB System Reserved Partition).

**WHS backs up all of my client computers nightly.** This works in conjunction with :doc:`CrashPlan <crashplan>` to keep my data safe.

In January 2010 I started getting weekly "backup database corrupt" errors after the weekly automatic backup cleanup run. Looking at the backup database, it was reporting 225GB used - far more than the combined capacity of all of my client computers twice over. `After posting to the Microsoft forums <http://social.microsoft.com/Forums/en/whssoftware/thread/1e25eb79-eb04-4385-83a6-f5a20b0d09bf>`_, I decided to reset the backup database manually and start from scratch.

1. Exit then uninstall the connector software on all clients.
2. RDP to the WHS desktop and run the WHS console from there.
3. In the Computers and Backups section, remove all clients. This will claim to delete the backups from the database but it won't.
4. Open Windows Explorer and navigate to ``D:\folders\{00008086-058D-4C89-AB57-A7F909A47AB4}``
5. Manually delete all files.
6. Reboot WHS.
7. RDP to the WHS desktop and run the WHS console from there.
8. Select Settings -> Backups and run "Cleanup Now" to reset the database consistency.
9. From each client, navigate to ``\\YOURSERVER\Software\Home Server Connector Software`` and run ``setup.exe`` to reinstall the connector software. Reconfigure the backups for each client as you reinstall.

You may be able to run ``C:\Program Files\Windows Home Server\discovery.exe`` on each of the clients rather than uninstall/reinstall of the connector. I tried this and it didn't work. It probably requires you to shut down all clients and I didn't do that.

Server Recovery
===============

Reference Links
---------------

- `How to replace the system drive <http://social.microsoft.com/Forums/en-US/whsfaq/thread/cdb387f1-9baa-4ae3-a74b-ff351dc1c0bf>`_ (Microsoft Forums)
- `Server reinstall fails and can't attempt again <http://social.microsoft.com/Forums/en-US/whssoftware/thread/7f224a0c-f724-4b0c-b828-01104610115a>`_ (Microsoft Forums)
- `HP MediaSmart Server - Recovering or Resetting the Server <http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01213390&tmp_track_link=ot_recdoc/c01213383/en_us/c01213390/loc:1&lc=en&dlc=en&cc=us>`_ (HP Support)
- `HP MediaSmart Server - Using Server Recovery and Factory Reset <http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c01213383&dlc=en>`_ (HP Support)
- `HP MediaSmart Server - Replacing the System Drive <http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01212953&tmp_track_link=ot_recdoc/c01213383/en_us/c01212953/loc:2&lc=en&dlc=en&cc=us>`_ (HP Support)
- `Can you recover a system drive using a different Power Pack? <http://social.microsoft.com/Forums/en-US/whssoftware/thread/3ae8b7f8-5898-4824-b389-7ba7795786aa>`_ (Microsoft Forums) - I asked this because the HP recovery disk doesn't have PP2 or PP3 on it. You do need to restore from the original disk, then just do "Update Now..." over and over to reinstall the power packs.
- If you can't remove a drive, `you may have to do some RoboCopy fanciness <http://bradwilson.typepad.com/blog/2009/12/rescuing-data-from-windows-home-server.html>`_ to get it to work like Brad Wilson did.
- `You can upgrade the system drive by cloning it <http://www.mediasmartserver.net/2010/01/17/forum-spotlight-how-to-successfully-clone-and-upgrade-a-whs-system-drive/>`_.

If I have to do a recovery, I may want to upgrade to MediaSmart 3.0 at the same time. It's offered only as a "recovery option" so I'd have to "recover in place" even if I wasn't replacing the drive.

Recovery Steps
--------------
I copy/pasted it here so I don't go panicking searching for it since it has disappeared from various sources already. I didn't get the pictures saved in time, but the reference links above still have some images and the text descriptions are pretty good.

**This document applies to HP MediaSmart Server EX470 and EX475.**

Replacing the internal system drive consists of four parts:

1. Removing the system drive
2. Re-installing the new system drive
3. Resetting the System. See Using Server Recovery and Factory Reset below.
4. Reinstall the software on each computer. See Installing the Software on Additional Home Computers via Installation disc, Window XP or Windows Vista below.

**CAUTION:** The system drive contains the Microsoft Windows Home Server operating system. The server cannot operate while the system drive is removed and must be re-installed via the Server Recovery Disc or factory reset. See Using Server Recovery and Factory Reset on page 7-7.

Removing the System Drive
~~~~~~~~~~~~~~~~~~~~~~~~~
The following figure shows the location of the system hard drive. (It's the BOTTOM drive in the server.)

1. Hold in the Power button for at least 4 seconds to force the server to shutdown.
2. Open the door on the front of the server.
3. Using a coin, turn the security knob clockwise to unlock the drive.
4. On the bottom drive, press down the lever to unlock the handle.
5. Lift the handle all the way up.
6. Gently pull the hard-drive tray from the hard drive bay.
7. Flex the back of the right side-rail, and then withdraw the back pin from the hard drive by gently pulling the side-rail down and away.
8. Flex the front of the right side-rail and withdraw the front pin from the hard drive by gently pulling the side-rail down and away.
9. Remove the drive from the hard-drive tray.

Installing the New System Drive
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Insert the new system drive into the left side of the hard-drive tray, making sure that the pins go into the hard drive's mounting holes.
2. Flex the front of the right side-rail and insert the pin into the hard drive’s mounting hole, and then flex the back of the right side-rail and insert the pin into the other mounting hole.
3. With the handle up, slide the hard-drive tray and drive into the system bay. **NOTE:** Don’t push on the handle; the tray won’t slide in.
4. Press down on the handle on the hard-drive tray until it locks.
5. Using a coin, turn the security knob counterclockwise to lock system drive in its bay.
6. Close the door on the front of the server.
7. Power on the server. The Health indicator light is initially purple and then blinks blue and red.
8. Perform a Factory Reset to initiate the drive. See Using Server Recovery and Factory Reset below.

Recovering or Resetting the Server
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**CAUTION:** Steps for performing a Server Recovery or Factory Reset. To recover or reset the server Use the Server Recovery Disc from a computer using a wired connection to the router (or switch). A wireless connection is not recommended. Additionally, if the server is some distance from the computer you are using for Server Recovery or Factory Reset, it may be more convenient to move the server near the computer.

1. If the HP MediaSmart Server Control Center is open on your computer, close it before proceeding.
2. Insert the Server Recovery Disc into a DVD drive in a computer connected to the network by an Ethernet cable. The Server Recovery program automatically starts.
3. Click Next.
4. Uninstall HP MediaSmart Server and Windows Home Server Connector:

    a. Click Start, Control Panel and select Add or Remove Programs.
    b. Click on HP MediaSmart Server, click Remove.
    c. Click on Windows Home Server Connector, click Remove.

5. Prepare the server for recovery or reset:

    a. On the back of the server, hold in the Power button for at least 4 seconds to force the server to shutdown.
    b. After the server is completely off, locate the recessed Status/Recovery button on the front of the server and prepare to press this button with a paper clip.
    c. On the back of the server, press the Power button to restart.
    d. While the Health indicator is blinking blue and red, use a paper clip to press the recessed Status/Recovery button until it clicks. Recovery mode is initiated.
    e. If recovery mode is successfully initiated, the Health indicator light blinks purple and red repeating.

6. On the Rebooting your server into recovery mode dialog box, click Next, and then follow the instructions on each dialog box. During the recovery process, the following may happen:

    a. If the recovery program cannot find the server, see No server found (below).
    b. If the Server Recovery cannot recover the partition data, the progress bar will go to 100% and then back to zero and start over.
    c. If the recovery fails, see Recovery fails (below).

7. After the Server Recovery or Factory Reset completes, the server automatically restarts. Before taking the next step wait until the Health indicator light is solid blue.
8. **You must reinstall the software on each of your computers, including the computer that you used to perform the recovery** - otherwise, you won’t be able to use the server.
9. Click Finish on the Server recovery complete dialog box. The HP MediaSmart Server software will automatically be installed on the computer where you performed the Server Recovery or Factory Reset.

**CAUTION:** If you did not close the HP MediaSmart Server Control Center, as indicated in step 1, you may see a message asking you to reboot your computer. If you see this message, choose to reboot later. Otherwise, rebooting may leave the server in a state where it cannot be configured, and you will have to repeat the recovery or reset process.

**NOTE:** It takes a few minutes for the server to go through the finishing process. Please be patient.

**PERSONAL NOTE**: I may need to run a Windows Update after recovery - but before reinstalling the connector on my computers - since Power Pack 2 was installed after I bought the server.

Troubleshooting
~~~~~~~~~~~~~~~

No Server Found
:::::::::::::::

If the recovery program cannot find the server, the most likely causes are:

- The Recovery Mode was not successfully initiated—repeat step 5 if you did not push the Status/Recovery button while the Health indicator lights was blinking red and blue.
- A firewall is blocking the connection - configure the firewall to allow the Windows Home Server Recovery application or to allow connections over TCP port 8192 and UDP port 8192. If opening these ports, be sure to close them after the recovery has completed. For more information, see the vendor’s documentation.
- The network connection is not working.

Recovery Fails
::::::::::::::

If the recovery fails, one of the following messages will be displayed:

- The server disks could not be reformatted
- The partition data on the server could not be written
- The primary volume on the server could not be written
- The recovery image could not be loaded

The most likely causes of these messages is a connection failure.

1. Make sure that you are using a wired connection to the server from the computer you are using to do the recovery.
2. Check network connections
3. Repeat the recovery or reset.

Recovery Fails and you Can't Try Again
::::::::::::::::::::::::::::::::::::::

Unfortunately, once a Server Reinstallation fails, there seems to be no way to attempt it again.  I think you're only option at this point is to do a New Installation.  What you need to do is unplug all of your secondary drives (so the data will stay there).  Then, I would remove the primary drive (the one with the OS installed) and hook it up to another computer.  Browse to ``D:\DE\shares`` and copy all of the data that's in there that was not in a share with Folder Duplication to another computer (or, for extra protection, copy all data in that location regardless of Duplication).  Once you are 100% sure you have pulled everything from that location that you want/need, put the drive back in the server and do a New Installation on to that drive.  (Again, make sure it is the **only drive** hooked up at this point.)  Once the installation is complete, do the WHS Shuffle:

1. Login to the server desktop
2. Hook one of your other drives up to the server, but do not add it to the storage pool
3. Move data from that drive (path is ``X:\DE\shares``, where ``X`` is the drive letter of the drive you hooked up) to the network shares using the icon on the desktop (do not move the data to ``D:\shares``)
4. Once all of the data is off of that drive and on the server, add that drive to the storage pool and wait for balancing
5. Continue to do steps 2-4 for each other secondary drive
