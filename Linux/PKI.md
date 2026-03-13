# PKI

>[!IMPORTANT]
>It is works with CSRs and CAs. The CSR is the signing request, that you need to send to a CA.

## Make a private key with a CSR

>[!NOTE]
> req -new - create a new certificate signing request </br > -nodes - save private key without a passphrase </br > -newkey - generate a new private key </br > rsa:4096 - generate an RSA key of size 4096 </br > -keyout - specify where to save the private key </br > -out - save the certificate signing request

```OpenSSL
openssl req -new -nodes -newkey rsa:4096 -keyout /keys/key.pem -out cert.csr
```

## Sign a cert for yourself

>[!NOTE]
></br > -x509 - we generate a self signed cert request </br > -sha256 - specifies the use of SHA256 </br > -days 365 - Valid for one year </br > -out - specify where to save the public key

```OpenSSL
openssl req -x509 -newkey -nodes rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365
```

## Certificate Formats
>[!IMPORTANT]
>Certificates are used for a variety of use cases, and come in a different flavour fitting for each case.

- PFX (Personal Exchange Format): PFX formats are often used to import TLS certificates into Windows servers. It is password-protected and contains the private key, TLS certificate and CA certificates together.
- CSR (Certificate Signing Requests): When you want to generate a TLS certificate signed by a CA, you send them a CSR. It has the information of the certificate owner requesting the certification to a CA, as well as - a public key. You can generate a CSR using open-source tools like OpenSSL.
- CER/CRT files: This is where X.509 certificates are stored. They are used to verify and assess the security of a web server. They have information about the certificate owner and the public key. They are usually - encoded in base64.
- PEM (Privacy Enhanced Mail): This format is used a lot in Linux, and it's used to store encoded cryptographic data, usually for the purpose of authentication. It can have certificates, private keys, public keys, separate public certificates, or the whole pair. For example, you can expect to see RSA keys exported in .pem format or SSH keys.
- P7b (PKCS#7): This format is often used to store chain certificates. It never has a private key, only the public key or public certificate counterpart. It's mostly used for distributing certificates (e.g., intermediate) for PKI operations and management.
