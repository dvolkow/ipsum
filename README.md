![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-Public_domain-red.svg)](https://wiki.creativecommons.org/wiki/Public_domain)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt-get -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of shame (2020-07-25)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
54.38.81.231|ns31251136.ip-54-38-81.eu|9
171.25.193.77|tor-exit1-readme.dfri.se|8
171.25.193.78|tor-exit4-readme.dfri.se|8
51.75.144.58|ns3129522.ip-51-75-144.eu|8
162.247.72.199|-|8
185.220.102.8|185-220-102-8.torservers.net|8
89.234.157.254|marylou.nos-oignons.net|8
51.77.135.89|ns31066279.ip-51-77-135.eu|8
51.75.144.43|ns3129517.ip-51-75-144.eu|8
185.220.101.207|-|8
51.158.111.157|157-111-158-51.instances.scw.cloud|8
85.209.0.103|-|7
51.38.10.45|ip45.ip-51-38-10.eu|7
178.32.123.182|ip182.ip-178-32-123.eu|7
150.129.8.19|-|7
217.182.192.217|ns3073700.ip-217-182-192.eu|7
51.77.52.11|ns3138321.ip-51-77-52.eu|7
145.239.92.26|relay3.tor.ian.sh|7
192.42.116.24|this-is-a-tor-exit-node-hviv124.hviv.nl|7
87.98.151.169|ip169.ip-87-98-151.eu|7
178.32.124.62|ip62.ip-178-32-124.eu|7
51.15.43.205|tor4thepeople3.torexitnode.net|7
18.27.197.252|wholesomeserver.media.mit.edu|7
87.98.152.111|ip111.ip-87-98-152.eu|7
178.32.123.204|ip204.ip-178-32-123.eu|7
178.32.123.203|ip203.ip-178-32-123.eu|7
51.75.64.187|relay4.tor.ian.sh|7
31.220.2.100|-|7
145.239.252.197|ns3100067.ip-145-239-252.eu|7
185.10.68.152|152.68.10.185.ro.ovo.sc|7
54.38.75.42|ip42.ip-54-38-75.eu|7
54.38.75.44|ip44.ip-54-38-75.eu|7
185.130.44.108|tor-exit-se1.privex.cc|7
193.218.118.131|131.118.218.193.urdn.com.ua|7
77.247.181.165|politkovskaja.torservers.net|7
77.247.181.162|chomsky.torservers.net|7
51.195.148.18|relay2.tor.ian.sh|7
176.10.104.240|tor1e1.digitale-gesellschaft.ch|7
185.213.155.169|-|7
185.220.102.4|communityexit.torservers.net|7
87.98.152.180|ip180.ip-87-98-152.eu|7
193.228.91.108|-|7
145.239.7.56|ns3083371.ip-145-239-7.eu|7
178.33.42.215|ip215.ip-178-33-42.eu|7
51.83.69.84|welcome-europe.website|7
36.67.200.85|-|7
185.220.102.254|tor-exit-relay-8.anonymizing-proxy.digitalcourage.de|7
185.220.102.253|tor-exit-relay-7.anonymizing-proxy.digitalcourage.de|7
87.98.139.44|ip44.ip-87-98-139.eu|7
87.98.155.50|ip50.ip-87-98-155.eu|7
178.32.124.74|ip74.ip-178-32-124.eu|7
217.182.194.103|ns3075283.ip-217-182-194.eu|7
54.39.16.73|ns555166.ip-54-39-16.net|7
145.239.1.182|ns3084826.ip-145-239-1.eu|7
51.75.52.118|ns3130898.ip-51-75-52.eu|7
209.141.47.92|-|7
87.98.152.54|ip54.ip-87-98-152.eu|7
194.180.224.130|-|7
79.137.79.167|tor-exit.talyn.se|7
62.210.105.116|62-210-105-116.rev.poneytelecom.eu|7
87.98.155.123|ip123.ip-87-98-155.eu|7
185.100.87.206|geri.enn.lu|7
185.100.87.207|freki.enn.lu|7
