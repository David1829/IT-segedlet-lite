# DAI
> [!NOTE]
> The all interfaces all untrusted in default, you need to configure like this
```cisco
ip arp inspection vlan 1
int range g0/0-1
 ip arp inspection trust
```
> [!NOTE]
> Check trusted interfaces, and other specificiations
```cisco
show ip arp inspection interfaces
show ip arp inspection
```
> [!NOTE]
> Limiting how many packets (limit rate) per how many seconds (burst interval) (x packets per y seconds)
```cisco
int range g0/1-2
 ip arp inspection limit rate 25 burst interval 2
```
> [!NOTE]
> Validate the arp packets via dst-mac, ip and src-mac (IF YOU WANT TO ENABLE MULTIPLE, THEN DO IT ON ONE COMMAND)
```cisco
ip arp inspection validate dst-mac
ip arp inspection validate ip
ip arp inspection validate src-mac
```
> [!NOTE]
> The DAI works with ip dhcp snooping binding table, you need to add staticly if there is no DHCP on that port (example a server)
```cisco
arp access-list ARP-ACL-1
 permit ip host 192.168.0.200 mac host 0c29.2f1e.7700
 ip arp inspection filter ARP-ACL-1 vlan 1
```