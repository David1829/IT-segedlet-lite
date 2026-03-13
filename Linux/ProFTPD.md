# ProFTPD

## Dependencies install

`sudo apt install proftpd proftpd-mod-crypto`

## Set config

You need to set all of these on /etc/proftpd/proftpd.conf

### Message

You can set message for accepted and for denied sessions
`AccessGrantMsg "Welcome"`
`AccessDenyMsg "Not welcome"`

### Root

You are able to set the root for all users, or you can set various folder for various user, in our example `ftpuser`

`DefaultRoot ~`

`DefaultRoot /tmp/ftpuser ftpuser`

### Servername

Set the server name

`ServerName "Myserver"`

### Port

Set a different port

`Port [port]`

### TLS

First of all enable tls module on /etc/proftpd/modules.conf

`LoadModule mod_tls.c`

Then you need to enable it on the default conf (/etc/proftpd/proftpd.conf)

`Include /etc/proftpd/tls.conf`

Lastly you need to set the followings ont /etc/proftpd/tls.conf
```TLS
TLSEngine                               on
TLSLog                                  /var/log/proftpd/tls.log
TLSProtocol                             SSLv23
TLSRSACertificateFile                   /etc/ssl/certs/proftpd.crt
TLSRSACertificateKeyFile                /etc/ssl/private/proftpd.key
TLSOptions                              NoSessionReuseRequired
TLSVerifyClient                         off
```