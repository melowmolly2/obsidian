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
![](../Assets/Pasted%20image%2020261019113109.png)![](../Assets/Pasted%20image%2020261019113145.png)![](../Assets/Pasted%20image%2020261019113226.png)![](../Assets/Pasted%20image%2020261019113658.png)![](../Assets/Pasted%20image%2020261019114806.png)![](../Assets/Pasted%20image%2020261019114936.png)v![](../Assets/Pasted%20image%2020261019115755.png)![](../Assets/Pasted%20image%2020261019115923.png)![](../Assets/Pasted%20image%2020261019120131.png)![](../Assets/Pasted%20image%2020261019120247.png)![](../Assets/Pasted%20image%2020261019120548.png)![](../Assets/Pasted%20image%2020261019120723.png)![](../Assets/Pasted%20image%2020261019120828.png)![](../Assets/Pasted%20image%2020261019121307.png)![](../Assets/Pasted%20image%2020261019213614.png)![](../Assets/Pasted%20image%2020261019213708.png)