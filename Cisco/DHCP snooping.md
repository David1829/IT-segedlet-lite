# DHCP snooping
> [!NOTE]
> Enables the dhcp snooping globally
```cisco
ip dhcp snooping
```
> [!NOTE]
> Make dhcp snooping on a vlan
```cisco
ip dhcp snooping vlan *vlan-number*
```
> [!NOTE]
> Makes a port trusted (make only the uplink ports)
```cisco
int g0/0/0
 ip dhcp snooping trust
```
> [!NOTE]
> This is needed on all switches (not relay agents) to not flag with dhcp option 82
```cisco
no ip dhcp snooping information option
```
> [!NOTE]
> Limit how much dhcp packet can be transfered from an untrusted port (if more than the limit, the port goes to err-disable)
```cisco
ip dhcp snooping limit rate *packets-per-second*
```
> [!NOTE]
> Err-disable recovery
```cisco
errdisable recovery cause dhcp-rate-limit
```