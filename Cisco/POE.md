# POE
> [!NOTE]
> Default is disable the port and send syslog message, you need to reenable the port with sh and no sh
```cisco
power inline police
power inline police action err-disable (equivalent with the command above)
```
> [!NOTE]
> Just for logging and not shutdowning the port
```cisco
power inline police action log
```
> [!NOTE]
> Check the interface POE settings
```cisco
show power inline police g0/0
```