=============
Configuration
=============

Jumbo Frames
============
Jumbo frames are a gigabit Ethernet thing that can increase throughput but *you have to have all devices running gigabit and they all have to support the same jumbo frame size*. `Here's a good article talking about what it all means. <https://www.smallnetbuilder.com/lanwan/lanwan-features/30201>`_

**I haven't moved to jumbo frames** because if all the devices on your network don't all line up with the frame size (and if they're not all wired) then you start dropping network packets. You can fix that by setting up managed switches (spendy) and set up VLANs that segregate the jumbo frames traffic from the rest of the network... but that's really more than I'm interested in getting into.

Setting the Name / Type
=======================
After switching routers, my Windows machines started thinking the "new network" was a public network and stopped doing network discovery on things. It was also called "Network 3" or something like that and that didn't help much.

You can run ``secpol.msc`` and update the name/type of the network from there.
