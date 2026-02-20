# Symmetric_encryption
## GNU Privacy Guard
>[!NOTE]
>The *CIPHER* is the encryption algorithm check algorithms: gpg --version

>[!IMPORTANT]
>To store the key on ASCII characters, you need to add --armor on the command
```GPG
gpg --symmetric --cipher-algo *CIPHER* message.txt
gpg --armor --symmetric --cipher-algo *CIPHER* message.txt
```
>[!NOTE]
>Decrypt the message
```GPG
gpg --output original_message.txt --decrypt message.pgp
```
## OPENSSL Project
>[!NOTE]
>This uses AES-256 on this command, the second one is more secure, it is against bruteforce, in it you use the Password-Base Key Derivation Function 2 (pbkdf2) and you can specify the number of iterations on the password to derive the encrypt (-iter *NUMBER*)
```OpenSSL
openssl aes-256-cbc -e -in message.txt -out encrypted_message

openssl aes-256-cbc -pbkdf2 -iter 10000 -e -in message.txt -out encrypted_message
```
>[!NOTE]
>Decrypt the message
```OpenSSL
openssl aes-256-cbc -d -in encrypteg_message -out original_message.txt

openssl aes-256-cbc -pbkdf2 -iter 10000 -d -in encrypted_message -out original_message.txt
```