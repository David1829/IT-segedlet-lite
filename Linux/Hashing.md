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

## Crack the Hashes that uses salt

### Hashcat

>[!NOTE]
>This uses GPU for cracking </br > -m <hash_type> specifies the hash-type in numeric format. For example, -m 1000 is for NTLM. Check the official documentation (man hashcat) and https://hashcat.net/wiki/doku.php?id=example_hashes to find the hash type code to use.</br > -a <attack_mode> specifies the attack-mode. For example, -a 0 is for straight, i.e., trying one password from the wordlist after the other. </br > hashfile is the file containing the hash you want to crack. </br > wordlist is the security word list you want to use in your attack.

```Hashcat
hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
```

### John

>[!NOTE]
>If you need to identify a hash you can use https://gitlab.com/kalilinux/packages/hash-identifier/-/tree/kali/master (start it with python3 hash-id.py), to check the supported formats use: *john --list=formats*

```John
john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt
```

>[!IMPORTANT]
>On UNIX based systems u need first unshadow a file. </br > On Windows like operation systems u need format NTLM/NTHash but you can use other tool such like Mimikatz or the AD database (NTDS.dit). With this u can perform a pass the hash attack

```unshadow
unshadow [path to passwd] [path to shadow]
```

>[!NOTE]
>If you want you can us GECOS (after the fifth : on /etc/shadow file) to get the list from the office number, telephone number, etc. You need to use the --single variable to use single hash-cracking mode. 

>[!IMPORTANT]
>You need to add the username of the user before the hash </br > **Example** </br > 9cb1972dceedce77713b52f8da0b9c03272a5edd9a42b5885f98a9fffd863d6f </br > username:9cb1972dceedce77713b52f8da0b9c03272a5edd9a42b5885f98a9fffd863d6f

```GECOS
john --single --format=[format] [path to file]
```

>[!NOTE]
>You are able to add rules for the cracking

```Rules
john --wordlist=[path to wordlist] --rule=MyRule [path to file]
```

| Rule Component | Modifier | Description | Example Character Set |
|----------------|----------|-------------|----------------------|
| Name           | `[List.Rules:MyRule]` | Defines the name of your rule, used as a John argument | `[List.Rules:MyRule]` |
| Append         | `Az`     | Appends characters to the word | `"abc"` → adds `abc` to the end of the word |
| Prepend        | `A0`     | Prepends characters to the word | `"xyz"` → adds `xyz` to the beginning of the word |
| Capitalize     | `c`      | Capitalizes the character positionally | `c1` → capitalizes the first character |
| Character Sets | `[0-9]`  | Includes numbers 0-9 | `[0-9]` |
|                | `[0]`    | Includes only the number 0 | `[0]` |
|                | `[A-z]`  | Includes both upper and lowercase letters | `[A-z]` |
|                | `[A-Z]`  | Includes only uppercase letters | `[A-Z]` |
|                | `[a-z]`  | Includes only lowercase letters | `[a-z]` |
|                | `[a]`    | Includes only the letter "a" | `[a]` |
|                | `[!£$%@]`| Includes the symbols `!`, `£`, `$`, `%`, `@` | `[!£$%@]` |

>[!NOTE]
>You are able to crack zip/rar files or ssh private keys (id_rsa), first you nee to make a hash from it (first, second and third command), then crack it (fourth command).

```ZIP
zip2john [options] [zip file] > [output file]

rar2john [rar file] > [output file]

ssh2john [id_rsa private key file] > [output file]

john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
```