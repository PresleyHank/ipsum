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

**Important:** If you are planning to use `git` to get the content of this repository do it like `git clone --depth 1 https://github.com/stamparm/ipsum.git`

Wall of shame (2019-05-09)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
171.25.193.20|tor-exit0-readme.dfri.se|11
171.25.193.25|tor-exit5-readme.dfri.se|11
197.231.221.211|exit1.ipredator.se|11
89.234.157.254|marylou.nos-oignons.net|10
171.25.193.77|tor-exit1-readme.dfri.se|10
80.82.77.139|dojo.census.shodan.io|10
171.25.193.235|tor-exit3-readme.dfri.se|10
80.82.77.33|sky.census.shodan.io|9
178.73.215.171|178-73-215-171-static.glesys.net|9
223.111.139.239|promote.cache-dns.local|9
183.230.146.26|-|9
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|9
77.247.181.162|chomsky.torservers.net|9
65.19.167.131|-|9
31.220.40.54|exit4.tor-network.net|9
62.102.148.67|-|9
185.244.25.205|-|9
178.128.96.131|-|8
192.160.102.170|ogopogo.relay.coldhak.com|8
209.141.35.22|thessia.mtomwing.com|8
222.187.225.9|-|8
213.213.194.116|host-213-213-194-116.dynamic.voo.be|8
176.31.208.193|tor-exit1.netnik.xyz|8
171.25.193.78|tor-exit4-readme.dfri.se|8
194.105.205.42|-|8
185.220.101.3|-|8
202.150.142.38|host38.subnet142.comnet.net.id|8
71.6.146.185|pirate.census.shodan.io|8
81.215.200.232|81.215.200.232.dynamic.ttnet.com.tr|8
27.184.49.9|-|8
222.187.254.14|-|8
185.220.101.28|-|8
153.37.165.220|-|8
199.87.154.255|tor.les.net|8
185.220.101.25|-|8
73.136.221.190|c-73-136-221-190.hsd1.tx.comcast.net|8
166.70.207.2|this.is.a.tor.node.xmission.com|8
115.238.245.4|-|8
185.220.102.8|-|8
18.85.192.253|wholesomeserver.media.mit.edu|8
115.238.245.2|-|8
27.92.117.238|KD027092117238.ppp-bb.dion.ne.jp|8
185.220.101.46|-|8
122.226.181.165|-|8
122.226.181.164|-|8
122.226.181.167|-|8
122.226.181.166|-|8
223.111.139.203|promote.cache-dns.local|8
192.81.219.158|-|8
185.193.125.42|tor-exit2.0day.to|8
222.187.232.212|-|8
31.220.0.225|exit3.tor-network.net|8
222.187.238.32|-|8
222.187.221.202|-|8
222.187.221.72|-|8
80.67.172.162|algrothendieck.nos-oignons.net|8
82.196.9.232|crawler3.systalker.org|8
222.187.221.222|-|8
87.120.36.157|no-rdns.mykone.info|8
5.199.130.188|tor.piratenpartei-nrw.de|8
77.247.181.165|politkovskaja.torservers.net|8
89.248.167.131|mason.census.shodan.io|8
185.129.62.63|tor02.zencurity.dk|8
185.129.62.62|tor01.zencurity.dk|8
122.228.19.79|-|8
185.220.101.33|-|8
188.166.150.136|-|8
206.189.152.215|randisgb.nolepstore.id|8
89.197.161.164|89-197-161-164.virtual1.co.uk|8
