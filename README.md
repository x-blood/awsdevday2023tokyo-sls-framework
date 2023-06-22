# awsdevday2023tokyo-sls-framework

## Result of K6

```
     data_received..................: 1.2 MB 275 kB/s
     data_sent......................: 168 kB 40 kB/s
     http_req_blocked...............: avg=230.91ms min=161.22ms med=208.77ms max=353.86ms p(90)=319.61ms p(95)=327.94ms
     http_req_connecting............: avg=14.48ms  min=5.52ms   med=13.23ms  max=25.53ms  p(90)=21.59ms  p(95)=22.78ms 
     http_req_duration..............: avg=2.6s     min=2.36s    med=2.6s     max=2.99s    p(90)=2.71s    p(95)=2.73s   
       { expected_response:true }...: avg=2.6s     min=2.36s    med=2.6s     max=2.99s    p(90)=2.71s    p(95)=2.73s   
     http_req_failed................: 0.00%  ✓ 0         ✗ 200  
     http_req_receiving.............: avg=242.91µs min=7µs      med=26µs     max=2.26ms   p(90)=1.06ms   p(95)=1.26ms  
     http_req_sending...............: avg=47.03µs  min=22µs     med=37µs     max=300µs    p(90)=66.5µs   p(95)=93.14µs 
     http_req_tls_handshaking.......: avg=192.61ms min=130.95ms med=169.43ms max=317.72ms p(90)=286.86ms p(95)=293.71ms
     http_req_waiting...............: avg=2.6s     min=2.36s    med=2.6s     max=2.99s    p(90)=2.71s    p(95)=2.73s   
     http_reqs......................: 200    47.089626/s
     iteration_duration.............: avg=3.83s    min=3.6s     med=3.84s    max=4.24s    p(90)=3.93s    p(95)=3.97s   
     iterations.....................: 200    47.089626/s
     vus............................: 10     min=10      max=200
     vus_max........................: 200    min=200     max=200
```

## Result of CloudWatch Logs Insights

```
filter @type="REPORT" and ispresent(@initDuration)
| stats count() as coldStarts, avg(@maxMemoryUsed), avg(@duration + @initDuration) as totalDuration_avg, avg(@duration), avg(@initDuration), min(@initDuration), max(@initDuration) by bin(10m)
```
---
| coldStarts | avg(@maxMemoryUsed) | totalDuration_avg | avg(@duration) | avg(@initDuration) | min(@initDuration) | max(@initDuration) |
|------------|---------------------|-------------------|----------------|--------------------|--------------------|--------------------|
| 200        | 173695000           | 2329.8446         | 87.4972        | 2242.3474          | 2032.61            | 2561.5             |
---
