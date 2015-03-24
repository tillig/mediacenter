=======
Verizon
=======

Prior to 2010 we had Verizon FiOS for phone, TV, and internet. The internet plan was 35Mbps down/35MBps up.

Speed Issues
------------
After upgrading to 35/35, on 2/25/2010 I ran a speed test to see what the results were. I got 20/15 from `SpeedTest.net <http://speedtest.net/>`_. Looking at the forums, this doesn't sound uncommon. Trying the `Verizon Speed Test <http://speedtest.verizon.net/>`_, after using the optimizer I got 35/35 on a wired connection, but 3/47(?!) on wireless.

- `One person had to get the ONT on the side of the house replaced <http://forums.verizon.com/t5/FiOS-Internet/Fios-35-35-Internet-Upgrade/m-p/159333>`_ because the older hardware didn't support the speed.
- `One person <http://forums.verizon.com/t5/FiOS-Internet/Switched-to-35-35-FIOS-plan-but-still-getting-only-25-15/td-p/149570>`_ was able to run the `Verizon Speed Optimizer <http://www.verizon.net/optimize>`_ on their machine and fix it. There was something in the network settings that needed to be changed, apparently. (That was specifically a Windows 7 thing, too.) The optimizer sets:
    - TCP 1323 Extensions - This parameter enables enhancements to the TCP/IP protocol that provide improved performance over high speed connections.
    - TCP Receive Window - This parameter specifies the number of bytes a sender (the source you are downloading from) may transmit without receiving an acknowledgment. Modifying it determines the maximum size offered by the system.
    - MTU (Maximum Transmission Units) - The MTU defines the largest single unit of data that can be transmitted over your connection. The FiOS network requires an MTU of 1492 bytes.

There is `a Microsoft KB article <http://support.microsoft.com/kb/939006>`_ talking about some issues we might run into with the Speed Optimizer. Apparently on Vista it doesn't have the permissions to write to all of the registry settings it needs to. If we have issues, or if the Speed Optimizer doesn't immediately fix things, that may be something to check. Speed Optimizer does require you to run IE as Administrator and seems to have worked for me doing so.

Conversion to Frontier
----------------------
In late 2010, Verizon sold its internet (FiOS) service to Frontier Communications, at which point we :doc:`switched to be Frontier customers <frontier>`.