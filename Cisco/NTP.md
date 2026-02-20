# NTP

>[!NOTE]
>It is important to synchronize clock all around

### Set manually the clock

`R1# clock set 16:01:00 sept 25 2020`

### Set NTP server

`R1(config)# ntp server 192.168.0.2`

### Show commands

```cisco
R1# show clock detail
21:01:34.563 UTC Fri Nov 15 2019
Time source is NTP
```

```cisco
R1# show ntp associations  
  address         ref clock       st   when   poll reach  delay  offset   disp
*~209.165.200.225 .GPS.           1     61     64   377  0.481   7.480  4.261
* sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
 
R1# show ntp status
Clock is synchronized, stratum 2, reference is 209.165.200.225
nominal freq is 250.0000 Hz, actual freq is 249.9995 Hz, precision is 2**19
ntp uptime is 589900 (1/100 of seconds), resolution is 4016
reference time is DA088DD3.C4E659D3 (13:21:23.769 PST Fri Nov 15 2019)
clock offset is 7.0883 msec, root delay is 99.77 msec
root dispersion is 13.43 msec, peer dispersion is 2.48 msec
loopfilter state is 'CTRL' (Normal Controlled Loop), drift is 0.000001803 s/s
system poll interval is 64, last update was 169 sec ago.
```