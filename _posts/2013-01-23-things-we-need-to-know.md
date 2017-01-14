---
layout: post
title: Things we need to know
date: 2013-01-11 17:15:36 +0800
tags: [technote]
---

**Prerequisite**

* OpenVPN account, please do yourself a favor, choose a stable/paid provider :-)


**Software & Script**

* [TunnelBlick](http://code.google.com/p/tunnelblick/): OpenVPN Client on Mac. ([Tutorial](http://strongvpn.com/setup_macosx_openvpn_tunnelblick.shtml))
* [chnroutes](http://code.google.com/p/chnroutes/): Fetching the updated routes & scripts for China mainland.


**Create Routes for TunnelBlick**

```bash
curl -o chnroutes.py
python chnroutes.py -p mac
chmod a+x ip-up ip-down
mv ip-* ~/Library/Application\ Support/Tunnelblick/Configurations/
echo ‘up ip-up’ >> ~/Library/Application\ Support/Tunnelblick/Configurations/<your-config>
echo ‘down ip-down’ >> ~/Library/Application\ Support/Tunnelblick/Configurations/<your-config>
```


**Unset nameserver from account settings**

* TunnelBlick => VPN Details => => Settings => Set DNS/WINS => Do not set nameserver.
* Good to go now :-)


**Update Routes for TunnelBlick Monthly**

* repeat listed commands from line 2, 3, 4 above.


**OPTIONAL** Life is short, use 8.8.8.8, 8.8.4.4
