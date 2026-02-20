# Lite-VRF
> [!NOTE]
> This is used to use the same ip address on a different network, but on the same router. These VRF interfaces are isolated
```cisco
ip vrf CUSTOMER1
ip vrf CUSTOMER2
do sh ip vrf
do sh ip route vrf CUSTOMER1

int g0/0
 ip vrf forwarding CUSTOMER1
 ip address 192.168.1.1 255.255.255.252
int g0/1
 ip vrf forwarding CUSTOMER1
 ip address 192.168.11.1 255.255.255.252
int g0/2
 ip vrf forwarding CUSTOMER2
 ip address 192.168.1.1 255.255.255.252
int g0/3
 ip vrf forwarding CUSTOMER2
 ip address 192.168.12.1 255.255.255.252
```