![](../Assets/Pasted%20image%2020261018205518.png)![](../Assets/Pasted%20image%2020261018205527.png)![](../Assets/Pasted%20image%2020261018205536.png)
![](../Assets/Pasted%20image%2020261018210138.png)![](../Assets/Pasted%20image%2020261018210829.png)![](../Assets/Pasted%20image%2020261018210854.png)
![](../Assets/Pasted%20image%2020261018211059.png)```

```
C:\Users\Acer>   tracert -w 5000 -h 50 gaia.cs.umass.edu

Tracing route to gaia.cs.umass.edu [128.119.245.12]
over a maximum of 50 hops:

  1     1 ms     1 ms     1 ms  192.168.10.1
  2     2 ms     1 ms     1 ms  192.168.1.1
  3     5 ms     5 ms     6 ms  100.123.0.132
  4     *        *        *     Request timed out.
  5     3 ms     3 ms     2 ms  42.114.244.86
  6     2 ms     2 ms     2 ms  42.116.170.142
  7     *        *        *     Request timed out.
  8     3 ms     2 ms     2 ms  118.69.189.84
  9     3 ms     2 ms     2 ms  169.254.205.1
 10     *        *        3 ms  42.112.2.1
 11     *        *        *     Request timed out.
 12    19 ms    19 ms    19 ms  118.69.253.83
 13    21 ms    20 ms    20 ms  118.69.131.101
 14    42 ms    42 ms    42 ms  gi100-0-0-7.br04.hkg15.as3491.net [63.217.16.77]
 15     *        *        *     Request timed out.
 16     *        *        *     Request timed out.
 17   198 ms   199 ms   198 ms  be2414.ccr21.hkg02.atlas.cogentco.com [154.54.88.49]
 18   202 ms   205 ms   203 ms  be3701.ccr21.pdx01.atlas.cogentco.com [154.54.87.121]
 19     *      197 ms     *     be9851.ccr81.sea08.atlas.cogentco.com [154.54.26.166]
 20   216 ms   214 ms   238 ms  be9527.ccr81.slc03.atlas.cogentco.com [154.54.85.198]
 21     *      213 ms   214 ms  be2353.ccr81.den01.atlas.cogentco.com [154.54.5.101]
 22   225 ms   224 ms   225 ms  be6904.ccr31.oma02.atlas.cogentco.com [154.54.95.98]
 23   233 ms   239 ms   281 ms  be5214.ccr41.ord01.atlas.cogentco.com [154.54.165.134]
 24   319 ms   256 ms   252 ms  port-channel2717.ccr91.cle04.atlas.cogentco.com [154.54.6.222]
 25   256 ms   255 ms   255 ms  be8022.ccr21.alb02.atlas.cogentco.com [154.54.169.186]
 26   255 ms   255 ms   254 ms  be8027.rcr71.orh02.atlas.cogentco.com [154.54.169.213]
 27   256 ms   255 ms   256 ms  be2191.rcr71.orh01.atlas.cogentco.com [154.54.160.70]
 28   240 ms   240 ms   239 ms  38.32.33.83
 29   248 ms   250 ms   263 ms  69.16.0.9
 30   245 ms   246 ms   246 ms  69.16.3.0
 31   246 ms   245 ms   248 ms  core1-rt-et-4-3-0.gw.umass.edu [192.80.83.101]
 32   246 ms   245 ms   247 ms  n5-rt-1-1-et-0-0-0.gw.umass.edu [128.119.0.8]
 33   252 ms   252 ms   252 ms  128.119.77.235
 34     *        *        *     Request timed out.
 35   251 ms   252 ms   252 ms  cics-rt-xe-0-0-0.gw.umass.edu [128.119.3.32]
 36     *        *        *     Request timed out.
 37   246 ms   245 ms   324 ms  gaia.cs.umass.edu [128.119.245.12]

Trace complete.
```
![](../Assets/Pasted%20image%2020261018213457.png)
![](../Assets/Pasted%20image%2020261018213526.png)
![](../Assets/Pasted%20image%2020261018213701.png)**Answers: 1 → C, 2 → A, 3 → B**

**1. Average 2.1 Mbps, 15 Mbps when transmitting: C (neither works well)**

The total average demand already exceeds the channel capacity:

$$5 \times 2.1 = 10.5 \text{ Mbps} > 10 \text{ Mbps}$$

Circuit switching can't give each user their average rate. Packet switching has queues that grow without bound, causing long delays and loss.

**2. Average 2 Mbps, 2 Mbps when transmitting: A (circuit switching)**

The traffic is constant and fits the channel exactly:

$$5 \times 2 = 10 \text{ Mbps} = 10 \text{ Mbps}$$

Each user gets a dedicated $10/5 = 2$ Mbps circuit, which is fully used. Packet switching would add queueing delay and variability with no benefit, since there is no burstiness to exploit.

**3. Average 0.21 Mbps, 15 Mbps when transmitting: B (packet switching)**

The traffic is very bursty, and the total average demand is small:

$$5 \times 0.21 = 1.05 \text{ Mbps} \ll 10 \text{ Mbps}$$

A circuit would give each user only $2$ Mbps, far below their $15$ Mbps burst rate, and that capacity would sit idle most of the time. With packet switching, a user who is transmitting can use the whole channel, and it is unlikely that several users burst at once.
![](../Assets/Pasted%20image%2020261018214003.png)![](../Assets/Pasted%20image%2020261018214028.png)![](../Assets/Pasted%20image%2020261019102429.png)![](../Assets/Pasted%20image%2020261019102812.png)![](../Assets/Pasted%20image%2020261019103638.png)![](../Assets/Pasted%20image%2020261019103733.png)![](../Assets/Pasted%20image%2020261019104229.png)![](../Assets/Pasted%20image%2020261019104501.png)![](../Assets/Pasted%20image%2020261019104634.png)![](../Assets/Pasted%20image%2020261019104803.png)![](../Assets/Pasted%20image%2020261019104928.png)![](../Assets/Pasted%20image%2020261019105112.png)![](../Assets/Pasted%20image%2020261019105224.png)
![](../Assets/Pasted%20image%2020261019111510.png)vv![](../Assets/Pasted%20image%2020261019112112.png)![](../Assets/Pasted%20image%2020261019112131.png)v![](../Assets/Pasted%20image%2020261019112147.png)![](../Assets/Pasted%20image%2020261019112222.png)![](../Assets/Pasted%20image%2020261019112232.png)![](../Assets/Pasted%20image%2020261019112237.png)![](../Assets/Pasted%20image%2020261019112241.png)![](../Assets/Pasted%20image%2020261019112245.png)![](../Assets/Pasted%20image%2020261019113008.png)
![](../Assets/Pasted%20image%2020261019113109.png)![](../Assets/Pasted%20image%2020261019113145.png)![](../Assets/Pasted%20image%2020261019113226.png)![](../Assets/Pasted%20image%2020261019113658.png)![](../Assets/Pasted%20image%2020261019114806.png)![](../Assets/Pasted%20image%2020261019114936.png)v![](../Assets/Pasted%20image%2020261019115755.png)![](../Assets/Pasted%20image%2020261019115923.png)![](../Assets/Pasted%20image%2020261019120131.png)![](../Assets/Pasted%20image%2020261019120247.png)![](../Assets/Pasted%20image%2020261019120548.png)![](../Assets/Pasted%20image%2020261019120723.png)![](../Assets/Pasted%20image%2020261019120828.png)![](../Assets/Pasted%20image%2020261019121307.png)![](../Assets/Pasted%20image%2020261019213614.png)![](../Assets/Pasted%20image%2020261019213708.png)![](../Assets/Pasted%20image%2020261019213829.png)![](../Assets/Pasted%20image%2020261019213947.png)![](../Assets/Pasted%20image%2020261019214027.png)![](../Assets/Pasted%20image%2020261019214207.png)![](../Assets/Pasted%20image%2020261019214223.png)![](../Assets/Pasted%20image%2020261019214507.png)![](../Assets/Pasted%20image%2020261027143359.png)![](../Assets/Pasted%20image%2020261027143411.png)![](../Assets/Pasted%20image%2020261027143441.png)![](../Assets/Pasted%20image%2020261027143521.png)**The requests at t=0, t=1, and t=30 take 8 time units.**

A full iterative resolution takes 8 units: host to local server (1), then local server to root and back (2), to TLD and back (2), to authoritative and back (2), and finally local server to host (1). Cached entries let you skip steps. Each entry lasts 20 time units.

|Request|Cache state|Time units|
|---|---|---|
|t=0, gaia.cs.umass.edu|Cache is empty, so a full resolution is needed.|**8**|
|t=1, icann.org|Only .edu information is cached, so the root must be asked for the .org TLD.|**8**|
|t=5, cs.umd.edu|The .edu TLD server was cached around t=2, so the root is skipped. The remaining steps are host to local (1), local to TLD and back (2), local to authoritative and back (2), and local to host (1).|6|
|t=10, gaia.cs.umass.edu|The IP address was cached around t=6, so only host to local server and back is needed.|2|
|t=12, cs.mit.edu|The .edu TLD server is still cached, so the root is skipped.|6|
|t=30, gaia.cs.umass.edu|Everything from the first request has expired. The .edu TLD entry (cached around t=2) expired around t=22, and the umass.edu authoritative and IP entries expired around t=24 and t=26.|**8**|

The t=5 and t=30 requests are the tricky ones. At t=5 the .edu TLD cache from the first request still helps, while at t=30 the same name needs a full resolution again because all cached entries have expired.

![](../Assets/Pasted%20image%2020261027143625.png)**The first and third statements are true.**

1. **True.** The local DNS server caches results, so a repeated or partially overlapping query can be answered without going through the root, TLD, and authoritative servers. This is what made the t=10 request in the previous problem take only 2 time units.
2. **False.** The local host always contacts its local DNS server first. The local server is the one that queries the DNS hierarchy on the host's behalf, so the host never contacts it only as a fallback.
3. **True.** The local server's cached record can be out of date. If the authoritative server changes a record before the cached copy's time-to-live expires, the local server may still hand out the old record until its cache entry expires.
4. **False.** Local DNS servers can cache other record types too, such as MX, NS, and CNAME records, not only hostname-to-IP mappings.
![](../Assets/Pasted%20image%2020261027143921.png)

**Only the second statement is correct.**

5. **False.** Providing a list of TLD servers is the job of the root servers, not an authoritative server.
6. **True.** An authoritative name server holds the actual DNS records for the names in its own domain, so it gives the definitive answer for those names.
7. **False.** This describes the local DNS server. A cache is not authoritative, because its entries can be stale, and an authoritative server is not necessarily local to the querying host.
8. **False.** Pointing the resolver to the server that can give the definitive answer is the job of the TLD servers, which return the address of the authoritative server. By the time a query reaches the authoritative server, it answers directly.

![](../Assets/Pasted%20image%2020261027144048.png)

**The two checked answers are correct: HTTP local web caching and local DNS server caching.**

- **HTTP local web caching (checked):** A local web cache (proxy server) is shared by many users on the same network. If another user recently requested an object, its copy is already stored, so your request can be served from the cache without going to the origin server.
- **HTTP browser caching (unchecked):** A browser cache lives on your own machine and only holds items that you requested. Other users' requests never populate it, so it doesn't help you in that way.
- **Local DNS server caching (checked):** The local DNS server serves many hosts. If another host recently resolved a name, or one of the TLD or authoritative server lookups along the way, those cached results speed up your own resolution too. The t=1 and t=5 requests in the earlier problem showed the same effect, where cached TLD information made later requests faster.
![](../Assets/Pasted%20image%2020261027144150.png)
**The first option is correct: a manifest file lets a client know where it can retrieve different video segments, encoded at different rates.**

In DASH (Dynamic Adaptive Streaming over HTTP), the video is split into short chunks, and each chunk is encoded at several bitrates. The server provides a manifest file listing the URLs of these chunks for each encoding rate. The client downloads the manifest first, then requests chunks one at a time, choosing the rate that fits its current network conditions.

The other options are wrong:

- **Telling the server which video the client wants:** The client already does this by requesting the manifest's URL.
- **Logging the video and server:** Logging is not the manifest's purpose.
- **Reserving bandwidth along a path:** Streaming over HTTP involves no bandwidth reservation. Adaptive bitrate selection is the client's way of coping with the bandwidth it actually gets.
![](../Assets/Pasted%20image%2020261027144222.png)**The third option, which is already selected, is correct: store and serve multiple copies of videos at multiple geographically distributed sites.**

A CDN (content distribution network) places servers at many locations, either in large data centers near major network hubs or inside access ISPs close to users. Each client is directed to a nearby server holding a copy of the content. This gives three benefits:

- **Lower delay:** The path from server to client is shorter.
- **Load spreading:** No single server or link has to carry all the traffic.
- **Fewer bottlenecks:** Traffic doesn't all cross the same long-haul links.

The other options are wrong:

- **Single mega-server:** This is a single point of failure, the path to distant clients is long, and the server's outgoing link would be a bottleneck for hundreds of thousands of users.
- **Pushing videos to clients with machine learning:** Prediction-based prefetching can supplement a CDN but is not its core approach.
- **Clients sending content to each other:** This is peer-to-peer distribution, which is a different architecture from a CDN.

