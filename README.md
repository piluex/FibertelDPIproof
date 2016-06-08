# Fibertel DPI proof

Proof of Fibertel DPI (https://en.wikipedia.org/wiki/Deep_packet_inspection) for peak hour packet filtering.

This is just a bunch of stuff I used to test my ISP for DPI packet filtering on peak hours. I've suspected something was wrong when some https connections went really fast and my video streaming/torrent downloading/skype calls were so slow... 

So I did the regular, started a ssh tunnel on a 443 port (my isp as a lot of isp's tend to filter by port number) but that wasn't enough, still slow... Then tried OpenVPN with TLS on 443 and a bunch of other ports, TCP, UDP, nothign... super slow... So I setup a https server on the same machine, just for the sake of it and generated random data files to download and... FAST! So.. hey? same port? always encrypted data but different results... My ISP got smarter at fucking my! some wiki reading and found it, DPI (deep packet inspection). They were checking the headers and if it's a "legit" https stream, it goes fast, if not you're f**d... I needed to find a simpler way to show this and to make it useless, just fight fire with fire, as Metallica tought me. 

And here it's a OpenVPN tunneled with stunnel which perfectly emulates https traffic to navigate internet freely... and with a little more privacy... Who knows what else are they looking with DPI. 

To make some sense of this, I ran some tests (check testing.txt) on a typical Windows 10 machine, no VMs, no strange stuff, a "standard client setup" (I hate Windows 10... but it's what the people uses today). The tests were all directed to a NYC server with and the VPN and tunnel are set up on a NYC virtual machine on Digital Ocean's servers.

The video showing the legitimacy of the tests: https://youtu.be/--y2S0syxVI



