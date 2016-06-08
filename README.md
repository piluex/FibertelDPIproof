# Fibertel DPI proof

Proof of Fibertel DPI (https://en.wikipedia.org/wiki/Deep_packet_inspection) for peak hour packet filtering.

# Short story

I found I can counter my ISP measures creating a stunnel-ed- OpenVPN connection to the internet, I've used port 443 but I think as they're using DPI it doesn't matter. I used it to make sure I didn't hit a second filtering mechanism. If the traffic looks like HTTPs it goes uncapped (only capped to the speed you pay for) if looks like something else then you're a capped level 1 (http and who knows what else) and a second slower cap, level 2 internet fucking, for everything else (torrents, video calls, regular vpn connections, etc).

I ran some tests on video, the results are in testing.txt, the video: https://youtu.be/--y2S0syxVI

On the test I got a generous 4mbps vs the supposed 25mbps, on my previous private tests it goes as slow as 1.5mbps... So don't feel bad if you're getting that, me too. 

# Long story

So this is just a bunch of stuff I used to test my ISP for DPI packet filtering on peak hours. I've suspected something was wrong when some https connections went really fast and my video streaming/torrent downloading/skype calls were so slow... 

So I did the regular, started a ssh tunnel on a 443 port (my isp as a lot of isp's tend to filter by port number) but that wasn't enough, still slow... Then tried OpenVPN with TLS on 443 and a bunch of other ports, TCP, UDP, nothign... super slow... So I setup a https server on the same machine, just for the sake of it and generated random data files to download and... FAST! 

So.. hey? same port? always encrypted data but different results... My ISP got smarter at fucking me!!! after some wiki reading a possible culprit was found, DPI (deep packet inspection). They were checking the headers of at least all my connection starting packets and if it's a "legit" https stream, it goes fast, if not you're f**d... I needed to find a simpler way to show this and to make it useless, just fight fire with fire, as Metallica tought me. 

And here it's a OpenVPN tunneled with stunnel which perfectly emulates https traffic to navigate internet freely... and with a little more privacy... Who knows what else are they looking with DPI. 

To make some sense of this, I ran some tests (check testing.txt) on a typical Windows 10 machine, no VMs, no strange stuff, a "standard client setup" (I hate Windows 10... but it's what the people uses today). The tests were all directed to a NYC server with and the VPN and tunnel are set up on a NYC virtual machine on Digital Ocean's servers.

# Future goals

Make better instructions in english and spanish so everybody can go over DPI. If you're a lawyer interested in net-neutrality stuff I can help with the technical part! contact me. 
