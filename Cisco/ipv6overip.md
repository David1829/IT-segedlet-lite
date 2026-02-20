# IPv6overIP
> [!NOTE]
> You need to config the ip and ipv6 addresses first
> JUST REMEMBER TO USE IPV6 UNICAST-ROUTING

```cisco
int tunnel 0
 ipv6 address *The ipv6 address on the tunnel* example: fb::1
 tunnel source *The source interface, where you have the ipv6* example: g0/0/0
 tunnel destination *The destination ip address where is the other half of the ipv6* example: 192.168.3.1
 tunnel mode ipv6ip
exit
```
> [!NOTE]
> Add the route to the other ipv6
```cisco
ipv6 route fa::0/64 fb::1
```