![](../Assets/Pasted%20image%2020261018205518.png)![](../Assets/Pasted%20image%2020261018205527.png)![](../Assets/Pasted%20image%2020261018205536.png)
![](../Assets/Pasted%20image%2020261018210138.png)![](../Assets/Pasted%20image%2020261018210829.png)![](../Assets/Pasted%20image%2020261018210854.png)
![](../Assets/Pasted%20image%2020261018211059.png)```

```
C:\Users\Acer>tracert -h 50 gaia.cs.umass.edu

Tracing route to gaia.cs.umass.edu [128.119.245.12]
over a maximum of 50 hops:

  1     3 ms    <1 ms    <1 ms  192.168.10.1
  2     2 ms     1 ms     1 ms  192.168.1.1
  3     3 ms    21 ms     2 ms  100.123.0.132
  4     *        *        *     Request timed out.
  5     3 ms     2 ms     3 ms  42.114.244.86
  6     4 ms     2 ms     2 ms  42.116.170.142
  7     *        *        *     Request timed out.
  8    11 ms    11 ms    13 ms  118.69.189.84
  9     2 ms     4 ms     2 ms  169.254.205.1
 10     *        3 ms     2 ms  42.112.2.1
 11     *        *        *     Request timed out.
 12    19 ms    21 ms    23 ms  118.69.253.83
 13    21 ms    21 ms    20 ms  118.69.131.101
 14    42 ms    42 ms    44 ms  gi100-0-0-7.br04.hkg15.as3491.net [63.217.16.77]
 15    42 ms     *        *     BE42.br04.hkg12.as3491.net [63.218.174.134]
 16     *        *        *     Request timed out.
 17   202 ms   202 ms   199 ms  be2414.ccr21.hkg02.atlas.cogentco.com [154.54.88.49]
 18   203 ms   203 ms   203 ms  be3701.ccr21.pdx01.atlas.cogentco.com [154.54.87.121]
 19     *        *        *     Request timed out.
 20   215 ms   216 ms   222 ms  be9527.ccr81.slc03.atlas.cogentco.com [154.54.85.198]
 21     *        *      214 ms  be2353.ccr81.den01.atlas.cogentco.com [154.54.5.101]
 22   225 ms   225 ms   225 ms  be6904.ccr31.oma02.atlas.cogentco.com [154.54.95.98]
 23   234 ms   236 ms   236 ms  be5214.ccr41.ord01.atlas.cogentco.com [154.54.165.134]
 24   252 ms   252 ms   252 ms  port-channel2717.ccr91.cle04.atlas.cogentco.com [154.54.6.222]
 25   255 ms   255 ms   255 ms  be8022.ccr21.alb02.atlas.cogentco.com [154.54.169.186]
 26   254 ms   255 ms   257 ms  be8027.rcr71.orh02.atlas.cogentco.com [154.54.169.213]
 27   256 ms   255 ms   255 ms  be2191.rcr71.orh01.atlas.cogentco.com [154.54.160.70]
 28   240 ms   240 ms   240 ms  38.32.33.83
 29   249 ms   248 ms   252 ms  69.16.0.9
 30   247 ms   249 ms   249 ms  69.16.3.0
 31   245 ms   246 ms   245 ms  core1-rt-et-4-3-0.gw.umass.edu [192.80.83.101]
 32   247 ms   248 ms   249 ms  n5-rt-1-1-et-0-0-0.gw.umass.edu [128.119.0.8]
 33   252 ms   253 ms   252 ms  128.119.77.235
 34     *        *        *     Request timed out.
 35   254 ms   272 ms   270 ms  cics-rt-xe-0-0-0.gw.umass.edu [128.119.3.32]
 36     *        *        *     Request timed out.
 37   246 ms   246 ms   245 ms  gaia.cs.umass.edu [128.119.245.12]

Trace complete.
```
