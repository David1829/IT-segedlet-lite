# QOS
> [!NOTE]
> class-maps for define a protocol for a "name"
```
class-map HTTPS_MAP
 match protocol https

class-map HTTP_MAP
 match protocol https
```
> [!NOTE]
> policy-maps are for define a policy with the defined class-maps and how these class-maps need to work
```cisco
policy-map g0/0/0_OUT
 class HTTPS_MAP
  set ip dscp AF31
  priority precent 10
 class HTTP_MAP
  set ip dscp AF32
  bandwith precent 10
```
> [!NOTE]
> You add the defined policy-maps for an interface
```cisco
service-policy output G0/0/0_OUT
```