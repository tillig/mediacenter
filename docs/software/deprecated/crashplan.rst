=========
CrashPlan
=========

Evaluation
==========
Until 9/7/2009 I used `KeepVault <https://www.keepvault.com>`_ and was getting unlimited backup for $99/year, but they raised prices.

I switched to `Mozy <https://mozy.com>`_ in September 2009 with `a roundabout backup plan that I blogged <https://www.paraesthesia.com/archive/2009/08/17/backing-up-windows-home-server-to-mozyhome.aspx/>`_.

In 2012 I switched to `CrashPlan <https://www.crashplan.com/>`_. From a cost/benefit perspective, CrashPlan is a clear winner.

- Unlimited backup
- Backs up network mounted drives
- Runs on any OS (Linux for the :doc:`Synology <../../hardware/server/synologyds1010>`, Windows clients and servers, etc.)

Mounting Drives
===============
CrashPlan supports backup of mounted network drives, but getting one mounted for the ``SYSTEM`` account is easier said than done. `This StackOverflow article <https://stackoverflow.com/questions/182750/map-a-network-drive-to-be-used-by-a-service>`_ shows how to use Sysinternals ``psexec`` to mount a network drive for the ``SYSTEM`` account; but it's better to use a script to mount things using Windows Startup Scripts via group policy instead.

First, create a batch file like this that creates a log (for troubleshooting) and mounts the drives via the ``net use`` command.

.. sourcecode:: batch

    echo %date% %time% : "%cd%\mount_crashplan_shares.bat" >> C:\Windows\Temp\mount.log 2>&1
    net use V: "\\diskstation\video\Home Videos" /USER:DISKSTATION\admin password >> C:\Windows\Temp\mount.log 2>&1

Now set up Local Computer Policy so the script runs at Windows startup:

.. image:: startupscript.png

CrashPlan is set up on the Windows Home Server to back up all shares on the home server. It also has mapped drives for:

- Home Videos - ``V:`` @ ``\\diskstation\video\Home Videos``
- Plex Database - ``W:`` @ ``\\megaplex\Plex``
