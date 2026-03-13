# Local Preference

>[!NOTE]
>This is the second that BGP watches when calculates best path, you can use this on iBGP

## Change for a whole router

You are able to change the local-preference for a whole router, for example from R4 you want LocPrf 400, then you write the next commands on R4

```bgp
R4(config)#router bgp 50
R4(config-router)#bgp default local-preference 300
```

## Change only for a prefix

When you have 2 different networks, but you only want to change only for one network, then you need to use routemap for that (for example 1.1.1.0/24 and 2.2.2.0/24)

```bgp
R4(config)# ip access-list standard LP_MATCH
R4(config-std-nacl)# permit 1.1.1.0

R4(config)# route-map LOCALPREF permit 10
R4(config-route-map)# match ip address LP_MATCH
R4(config-route-map)# set local-preference 300

R4(config)# router bgp 50
R4(config-router)# neighbor 10.10.21.1 route-map LOCALPREF in
```