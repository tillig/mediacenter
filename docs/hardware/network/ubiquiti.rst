================
Ubiquiti Devices
================

In late 2019 we had some hiccups with the :doc:`Frontier network <../../network/providers/frontier>`. We fought with it for a while but the :doc:`Netgear R8000 router <../deprecated/netgearr8000>` was seen to be the problem since it had been around for a while.

[As it turns out, the problem was a bad card in a Frontier substation that would intermittently cause failures. It was affecting multiple customers, we were just the only ones to report it.]

I updated the whole network with Ubiquiti UniFi equipment. I'd sort of been researching this for a while, ended up just doing it.

- UniFi Security Gateway
- UniFi Cloud Key
- UniFi long range access point (UAP-LR)
- UniFi standard access point (UAP)

I found a few things that weren't obvious when setting this up, so I have notes here.

Initial Setup
=============

Once you set up a username and password for the Cloud Key (e.g., "ubnt-admin") the original ubnt/ubnt credential set is replaced.

When you adopt a Security Gateway you'll have to set up a "device authentication" credential set ("admin" with a password by default). This is the new username/password for logging into the Security Gateway directly. It won't use the same password as the controller.

Reserved DHCP Addresses
=======================

Go to the client list and select the client that should have a reservation. Under "network" you should select "fixed IP address" and that's the reservation.

Wireless Network
================

It appears best if you can set the channel and power on wireless yourself. There are `some articles <https://community.ui.com/questions/Clients-still-connecting-at-2G-not-5G-/ca738b92-5a85-4bc9-b112-72c966d47197>`_ on `the forums <https://community.ui.com/questions/No-5ghz-on-AP-AC-LR/5b57f50f-2f0b-410a-aee6-19b7e8478405>`_ that indicate this.

Some devices don't like certain higher channels on 5GHz. For example, auto selected channels in the higher range didn't allow the Google Home devices to connect, but when I switched to 36 manually they started connecting to 5GHz.

Set the 2GHz power to medium and the 5GHz to high to compensate for the differences in the bandwidth power. Use "bandwidth steering" to "prefer 5GHz" and more devices will start to use the 5GHz.

Some devices may just never connect to 5GHz. Folks report you may need to set up two different SSIDs and manually force the issue.

Enable "advanced features" on the Cloud Key (under "Settings"), then on the access point enable "bandwidth steering" to "prefer 5GHz."
