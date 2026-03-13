# Syslog

## Default commands

> [!NOTE]
> Sending system log messeages to a server.

```cisco
logging trap debugging
logging facility local6
logging 10.1.21.12
```
## More advanced commands

>[!IMPORTANT]
>You need to enable timestamps, it is not automatically shows

`service timestamps log datetime`

### Set the syslog server

`R1(config)# logging 192.168.0.10`

### (Optional) Set the log severity (trap) level

`R1(config)# logging trap informational`

### (Optional) Set the source interface

`R1(config)# logging source-interface lo0`

### (Optional) Enable logging to all enabled destinations

`R1(config)# logging on`