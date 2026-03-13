# AS-path Prepending

>[!NOTE]
>You make a path worse NOT better. You add more AS to the route. BGP checks this fourth when calculating

## Configuration

You need to set this to a neighbor, and make a route-map for it

```bgp
route-map prepend permit 10
    set as-path prepend 65001 65001 65001
router bgp 65001
    neighbor 10.1.0.2 remote-as 65200
    neighbor 10.1.0.2 route-map prepend out
```