=======================
Frontier Communications
=======================

We switched from :doc:`Verizon <verizon>` to Frontier after they purchased Verizon FiOS in 2010.

Frontier hosed things up on my network constantly by remotely pushing policy and configuring the router. To repair:

- Reset the router to defaults.
- Set the admin password.
- Disable wireless (at the time we were using the :doc:`DAP-1522 <../../hardware/deprecated/dap1522>` for wireless).
- On Advanced -> System Setttings, change the local domain name to "home" if it's not that already. (Frontier conveniently remotely made it "ftrdhcpuser.net" and now some domain names try to resolve on the internet.)
- Log into the :doc:`Windows Home Server <../../software/deprecated/whs>` remotely and verify access. If you can't get to it, log into the WHS console, Settings -> Remote Access, and click "Repair" to update the router via UPnP.

We left Verizon/Frontier FIOS in June 2011 and switched to :doc:`Comcast <comcast>`. The price was better, the service was better, the TV and phone features were better. We didn't get the same speed network as we had with FIOS, and we started out with a 250GB monthly cap (later lifted), but it's a small price to pay for better service and folks not constantly remote-pushing changes to my network.

In June 2019 we switched back to Frontier because the Comcast internet, while nice, was getting spendy. We had cut the cord and had internet-only service, and even then we got Frontier at half the price for the same service. Frontier appears to have gotten their act in gear since we last had them and it's been reasonably stable.

Late 2019 we had some networking hiccups where the network was going down intermittently. It turns out the ONT on the house was of a particular model that interacted poorly with one of the cards at the local substation. The card would think it was getting flooded and shut down, then ramp back up. This appeared from our end to be a network outage. Our router was blamed, so we bought new equipment (Ubiquiti) but then they located the bad card after all the new equipment was in place. Sigh.
