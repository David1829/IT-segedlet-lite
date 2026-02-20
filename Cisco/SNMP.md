# SNMP

>[!NOTE]
>You can use "ManageEngine MibBrowser Free Tool

> [!NOTE]
> Set up connection to your SNMP server.

```cisco
snmp-server group ADMIN v3 priv
snmp-server user ADMIN ADMIN v3 auth md5 Passw0rd priv aes 256 Passw0rd
snmp-server location  <XYZ>
```

### Other example

```cisco
R1(config)# ip access-list standard PERMIT-ADMIN
R1(config-std-nacl)# permit 192.168.1.0 0.0.0.255  
R1(config-std-nacl)# exit
R1(config)# snmp-server view SNMP-RO iso included
R1(config)# snmp-server group ADMIN v3 priv read SNMP-RO access PERMIT-ADMIN  
R1(config)# snmp-server user BOB ADMIN v3 auth sha cisco12345 priv aes 128 cisco54321  
R1(config)# end
```

### Show commands

```cisco
R1# show snmp user  
 
User name: BOB
Engine ID: 80000009030030F70DA30DA0
storage-type: nonvolatile active
Authentication Protocol: SHA
Privacy Protocol: AES128
Group-name: ADMIN
```