# HSRP with IP SLA

## HSRP

First of all you need to define a HSRP on routers

```hsrp
int g0/0
    ip add 192.168.10.1 255.255.255.0
    standby 10 ip 192.168.10.254
    standby 1 priority 110
    standby 1 preempt
```

## IP SLA for Monitoring

You need to create an IP SLA operation, then choose an operation type (in our example ICMP echo) to monitor the target

### Make the SLA

```sla
ip sla 1
    icmp-echo 100.100.100.2 source-ip 100.100.100.1
    threshold 1000
    timeout 1000
    frequency 1
```

### Schedule the SLA

Then you need to schedule the SLA operation

```sched
ip sla schedule 1 life forever start-time now
```

### Track objects for Dynamic Routing

```track
track 1 ip sla 1 reachability
```

>[!NOTE]
>You are able to add more active tracks to one and make a boolean to "and" or "or". If any of them stopped working and then needs to decrement, then you need "and" and if one of them failing but don't need to decrement, then you need "or"

```tracko
track 30 list boolean or
    object 1
    object 2
```

### Set the SLA to decrement HSRP value on failing

You can set the list track (30 in our case) or the single tracks for it. Now our standby decrements 20, so from priority 110 it gets to 90.

```strack
standby 1 track 1 decrement 20
```

## Show commands for SLA

`show track`

`show ip sla summary`
