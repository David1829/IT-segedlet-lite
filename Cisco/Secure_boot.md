# Secure boot

>[!NOTE]
>You are able to set the IOS and the current state of config on Cisco devices

```cisco
R1(config)# secure boot-config
R1(config)# secure boot-image
```

### To see if you have an archived file write the next command

`R1# show secure bootset`

>[!NOTE]
>First of all get the filename in rommon mode, then write the next  (You can add any flash number after it, where. You need to add where the file is it)

`rommon 1 > boot flash0:*filename*`

>[!NOTE]
>Boot from the secured config

`rommon 1 > secure boot-config restore`

## Get a file via SCP

>[!IMPORTANT]
>It relies on AAA and SSH, and use the next commands to config

```cisco
R1(config)# ip domain-name span.com
R1(config)# crypto key generate rsa general-keys modulus 2048
R1(config)# username Bob privilege 15 algorithm-type scrypt secret cisco12345
R1(config)# aaa new-model                          
R1(config)# aaa authentication login default local
R1(config)# aaa authorization exec default local  
R1(config)# ip scp server enable
```

>[!NOTE]
>You can use security against password recovery from rommon mode, if you want to go to rommon mode then you are get prompted twice, then it boots with the factory new configs

`R1(config)# no service password-recovery`