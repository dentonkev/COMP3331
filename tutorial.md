## Tutorial 1
### Exercise 1: nslookup (Not Marked)
1. `nslookup www.telstra.com.au` 

```
Non-authoritative answer:
www.telstra.com.AU	canonical name = d2l3pjybjlbg0l.cloudfront.net.
Name:	d2l3pjybjlbg0l.cloudfront.net
Address: 65.8.134.47
Name:	d2l3pjybjlbg0l.cloudfront.net
Address: 65.8.134.89
Name:	d2l3pjybjlbg0l.cloudfront.net
Address: 65.8.134.9
Name:	d2l3pjybjlbg0l.cloudfront.net
Address: 65.8.134.70
```

2. `nslookup 127.0.0.1`

```
1.0.0.127.in-addr.arpa	name = localhost.
```

### Exercise 2: Use ping to test host reachability (2 marks. 0.2 per each host)

1. `ping www.google.co.uk`

```
PING www.google.co.uk (142.250.204.3) 56(84) bytes of data.
64 bytes from syd09s25-in-f3.1e100.net (142.250.204.3): icmp_seq=1 ttl=116 time=1.28 ms
64 bytes from syd09s25-in-f3.1e100.net (142.250.204.3): icmp_seq=2 ttl=116 time=1.57 ms
^C
--- www.google.co.uk ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.275/1.423/1.572/0.148 ms
```
**ttl** - time to live: after 116 seconds the packet will be deleted off your server  
**time** - round trip time

2. `ping ec.ho`
```
ping: ec.ho: Name or service not known
```

3. `ping defence.gov.au`
```
PING defence.gov.au (54.206.239.18) 56(84) bytes of data.
^C
--- defence.gov.au ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2033ms
```

Website is reachable but since it is a government website the packets are blocked.

### Exercise 3: Use traceroute to understand the network topology (4 marks)

1. Run traceroute (s) on your machine to ufac.br

a) `traceroute ufac.br`  

**Answer**: 
- 25 routers between my current workstation and `ufac.br`  
- Each of these are routers and the earlier routers are the UNSW routers
- Use `whois` to determine more information about a particular IP address `whois 129.94.39.17`
- Routers 1 and 2 are part of UNSW network. Routers 3 and 4 are private routers (unsure if they are part of UNSW). Router 5 is not part of UNSW. 
```
traceroute to ufac.br (200.129.173.47), 30 hops max, 60 byte packets
 1  cserouter1-server.orchestra.cse.unsw.EDU.AU (129.94.242.251)  0.053 ms  0.058 ms  0.075 ms
 2  129.94.39.17 (129.94.39.17)  0.726 ms  1.303 ms  0.724 ms
 3  172.17.47.11 (172.17.47.11)  1.796 ms  1.275 ms  1.279 ms
 4  172.17.17.49 (172.17.17.49)  0.949 ms 172.17.17.13 (172.17.17.13)  0.808 ms  0.735 ms
 5  138.44.5.0 (138.44.5.0)  1.677 ms 172.17.17.33 (172.17.17.33)  0.929 ms 138.44.5.0 (138.44.5.0)  1.618 ms
 6  et-1-1-0.pe1.mcqp.nsw.aarnet.net.au (113.197.15.4)  2.107 ms  1.713 ms  1.713 ms
 7  * * et-1-1-0.pe1.mcqp.nsw.aarnet.net.au (113.197.15.4)  1.629 ms
 8  138.44.228.5 (138.44.228.5)  185.440 ms et-0_0_2.bdr1.guam.gum.aarnet.net.au (113.197.14.137)  71.645 ms  71.283 ms
 9  138.44.228.5 (138.44.228.5)  185.376 ms fourhundredge-0-0-0-20.4079.core2.losa.net.internet2.edu (163.253.1.49)  232.023 ms fourhundredge-0-0-0-21.4079.core2.losa.net.internet2.edu (163.253.1.51)  232.254 ms
10  fourhundredge-0-0-0-19.4079.core2.losa.net.internet2.edu (163.253.1.47)  232.225 ms fourhundredge-0-0-0-0.4079.core2.elpa.net.internet2.edu (163.253.1.202)  231.342 ms  231.343 ms
11  fourhundredge-0-0-0-23.4079.core1.elpa.net.internet2.edu (163.253.1.74)  232.674 ms * fourhundredge-0-0-0-0.4079.core2.elpa.net.internet2.edu (163.253.1.202)  232.330 ms
12  fourhundredge-0-0-0-0.4079.core1.hous.net.internet2.edu (163.253.2.39)  230.643 ms  230.560 ms  230.539 ms
13  fourhundredge-0-0-0-0.4079.core1.houh.net.internet2.edu (163.253.2.24)  232.197 ms fourhundredge-0-0-0-0.4079.core1.hous.net.internet2.edu (163.253.2.39)  232.173 ms fourhundredge-0-0-0-0.4079.core1.houh.net.internet2.edu (163.253.2.24)  232.095 ms
14  fourhundredge-0-0-0-0.4079.core1.houh.net.internet2.edu (163.253.2.24)  231.667 ms fourhundredge-0-0-0-0.4079.core1.pens.net.internet2.edu (163.253.2.35)  231.644 ms  230.668 ms
15  fourhundredge-0-0-0-0.4079.core1.jack.net.internet2.edu (163.253.1.0)  233.181 ms  232.741 ms fourhundredge-0-0-0-0.4079.core1.pens.net.internet2.edu (163.253.2.35)  230.769 ms
16  fourhundredge-0-0-0-0.4079.core1.jack.net.internet2.edu (163.253.1.0)  232.482 ms  232.576 ms 64.57.28.62 (64.57.28.62)  340.756 ms
17  mia2-mia1.bkb.rnp.br (200.143.252.26)  341.247 ms  341.519 ms 64.57.28.62 (64.57.28.62)  340.722 ms
18  mia2-mia1.bkb.rnp.br (200.143.252.26)  340.918 ms cce2-mia2-monet.bkb.rnp.br (170.79.213.46)  341.205 ms  341.375 ms
19  cce2-mia2-monet.bkb.rnp.br (170.79.213.46)  341.332 ms cdf2-ce2-tlbrs.bkb.rnp.br (200.143.253.81)  344.029 ms cce2-mia2-monet.bkb.rnp.br (170.79.213.46)  343.423 ms
20  cmt1-cdf2-telebras.bkb.rnp.br (170.79.213.185)  359.520 ms  358.675 ms  358.654 ms
21  mxro-cmt1-infobarra.bkb.rnp.br (170.79.213.201)  372.317 ms  372.470 ms cmt1-cdf2-telebras.bkb.rnp.br (170.79.213.185)  358.855 ms
22  mxac-mxro-3g-allo.bkb.rnp.br (170.79.213.242)  379.217 ms  378.903 ms mxro-cmt1-infobarra.bkb.rnp.br (170.79.213.201)  372.406 ms
23  mxac-mxro-3g-allo.bkb.rnp.br (170.79.213.242)  379.373 ms  378.998 ms  378.895 ms
24  200.139.4.122 (200.139.4.122)  379.618 ms  380.821 ms *
25  www.ufac.br (200.129.173.47)  379.036 ms !X  378.980 ms !X  378.870 ms !X
```

b) First router out of Australia
- this can be done using roundtrip time (longer physical distance between source and router)
- 7 is 1.629 ms and 8 is 71.283 ms
- **Answer**: router 8

c) First router in USA

### Exercise 4: Use ping to gain insights into network performance (4 marks)

1. Find the distance using google maps then do $t = \frac{d}{c}$ to calculate time 
2. a
3. 
- There are more type of delays apart from propogation delays
- Distance calculated is not exact from google maps
- Packets are not transmistted at the speed of light