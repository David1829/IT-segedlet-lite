# Login Settings

>[!NOTE]
>You can use for local logins these commands

```Local
service password-encryption - coding the password
security passwords min-length 8 - sets a minimum length for password
login block-for 120 attempts 3 within 60 - blocks for 2 minutes after 3 failure within 60 seconds
exec-timeout 5 30 - the connection is going to be lost after 5 minutes 30 seconds of inactivity
enable algorithm-type {  md5 | scrypt | sha256 |  secret  } *unencrypted password* - set the encryption type for password
username Bob algorithm-type scrypt secret cisco54321 - makes a suer and set the encryption type for password
```

>[!NOTE]
>You can use these commands for VTY logins

```VTY
login block-for 120 attempts 3 within 60 - blocks for 2 minutes after 3 failure within 60 seconds
login delay 3 - sets the delay between login attempts 3 seconds
login on-success log [every login] - logs the successful logins
login on-failure log [every login] - logs the failed logins (this is equal with Router(config)# security authentication failure rate threshold-rate log)

R1(config)# ip access-list standard PERMIT-ADMIN - make an access-list for admins
R1(config-std-nacl)# remark Permit only Administrative hosts    
R1(config-std-nacl)# permit 192.168.10.10
R1(config-std-nacl)# permit 192.168.11.10
R1(config-std-nacl)# exit
R1(config)# login quiet-mode access-class PERMIT-ADMIN - enable login for the permited IP addresses, even if the router goes from normal to quiet-mode
```

