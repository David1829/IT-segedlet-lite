# Assymetrical Keys
>[!IMPORTANT]
>Here is how RSA key works: </br > 1. Bob chooses two prime numbers: p = 157 and q = 199. He calculates N = 31243. </br > 2. With ϕ(N) = N − p − q + 1 = 31243 − 157 − 199 + 1 = 30888, Bob selects e = 163 and d = 379 where e × d = 163 × 379 = 61777 and 61777 mod 30888 = 1. The public key is (31243,163) and the private key is (31243,379). </br > 3. Let’s say that the value to encrypt is x = 13, then Alice would calculate and send y = x<sup>e</sup> mod N = 13<sup>163</sup> mod 31243 = 16341. </br > 4. Bob will decrypt the received value by calculating x = y<sup>d</sup> mod N = 16341<sup>379</sup> mod 31243 = 13.

## OpenSSL
### Generate private key
>[!NOTE]
>genrsa - generate an RSA private key. -out - the name of the private key. 2048 - the size of the key in bits
```OpenSSL
openssl genrsa -out private-key.pem 2048
```
### Generate public key from private key
>[!NOTE]
>rsa - the used algorithm. -pubout - we need the public key out from this key. -in set the private key. -out define a name for the public key
```OpenSSL
openssl rsa -in private-key.pem -pubout -out public-key.pem
```
### Check the RSA variables from private key
>[!NOTE]
> The values of p, q, N, e, and d are prime1, prime2, modulus, publicExponent, and privateExponent, respectively.
```OpenSSL
openssl rsa -in private-key.pem -text -noout
```
### Encrypt with the public key
```OpenSSL
openssl pkeyutl -encrypt -in plaintext.txt -out ciphertext -inkey public-key.pem -pubin
```
### Decrypt with the private key
```OpenSSL
openssl pkeyutl -decrypt -in ciphertext -inkey private-key.pem -out decrypted.txt
```

### Diffie-Hellman

>[!IMPORTANT]
>Here is how Diffie-Hellman works: 1. Alice and Bob agree on q and g. For this to work, q should be a prime number, and g is a number smaller than q that satisfies certain conditions. (In modular arithmetic, g is a generator.) In this example, we take q = 29 and g = 3. </br > 2. Alice chooses a random number a smaller than q. She calculates A = (g<sup>a</sup>) mod q. The number a must be kept a secret; however, A is sent to Bob. Let’s say that Alice picks the number a = 13 and calculates A = 3<sup>13</sup>%29 = 19 and sends it to Bob. </br > 3. Bob picks a random number b smaller than q. He calculates B = (g<sup>b</sup>) mod q. Bob must keep b a secret; however, he sends B to Alice. Let’s consider the case where Bob chooses the number b = 15 and calculates B = 3<sup>15</sup>%29 = 26. He proceeds to send it to Alice. </br > 4. Alice receives B and calculates key = B<sup>a</sup> mod q. Numeric example key = 26<sup>13</sup> mod 29 = 10.</br > 5. Bob receives A and calculates key = A<sup>b</sup> mod q. Numeric example key = 19<sup>15</sup> mod 29 = 10.

>[!NOTE]
>We can get the p and g from the key
```OpenSSL
openssl dhparam -in dhparams.pem -text -noout
```

## GPG

### Generate assymetric key interactively (Not protected with passphrase)

```GPG
gpg --full-gen-key
```

### Backup from a backupkey

```GPG
gpg --import backup.key
```

### Decrypt messages

```GPG
gpg --decrypt message.gpg
```

## SSH-keygen

>[!NOTE]
>For ssh u can use ssh-keygen