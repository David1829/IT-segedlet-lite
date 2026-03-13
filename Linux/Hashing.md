# Hashing

>[!NOTE]
>There are several hash methods such as sha224, sha256, sha384, sha512, ripemd160

## Checking the hash with sha256sum
```sha
sha256sum asd.txt
```
## Check the file with hex values
```hex
hexdump asd.txt -C
```
## HMAC 

>[!IMPORTANT]
>This uses a key too, this needed to be the same to get the same result

>[!NOTE]
>There are several HMAC methods such as hmac256, sha224mac, sha256hmac, sha384hmac, sha512hmac
```HMAC
hmac256 s!k34 asd.txt

sha256mac asd.txt --key s1k34
``` 