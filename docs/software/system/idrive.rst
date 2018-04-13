======
iDrive
======

:doc:`CrashPlan <../deprecated/crashplan>` decided to get out of the consumer backup business in 2017 so I had to find a new backup option. I ended up going with `iDrive <https://www.idrive.com/>`_ for a couple of reasons:

- Reasonable price. It's not unlimited storage, but you can get 2TB for about the same price as what CrashPlan was running yearly. I didn't have that much backed up so that was fine.
- Direct integration with :doc:`Synology <dsm>` and my :doc:`DS1010+ <../../hardware/server/synologyds1010>`. No need to mount the NAS as an external drive.

There are three downsides to iDrive that I've found:

- It can't back up network drives, so if I need to get things backed up they absolutely need to be on the :doc:`DS1010+ <../../hardware/server/synologyds1010>`.
- It doesn't have a great retention policy configuration. Basically it just keeps adding files forever and you have to manually initiate a cleanup.
- It doesn't have history. A new version of a file will overwrite the old version that was backed up, so if a file gets corrupted and that corrupt file gets backed up, you're done.
