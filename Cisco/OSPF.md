# OSPF

## Setting authentication between OSPF routed routers

>[!NOTE]
>Using the md5 auth, but it is not secure

```cisco
R1(config-if)# ip ospf message-digest-key 1 md5 cisco12345
R1(config-if)# ip ospf authentication message-digest
```

>[!NOTE]
>Using the sha256 auth, it is very secure

### Step 1.

```cisco
R1(config)# key chain SHA256
R1(config-keychain)# key 1
R1(config-keychain-key)# key-string ospfSHA256
R1(config-keychain-key)# cryptographic-algorithm hmac-sha-256
R1(config-keychain-key)# exit
R1(config-keychain)# exit
```

### Step 2.

```cisco
R1(config)# interface s0/0/0
R1(config-if)# ip ospf authentication key-chain SHA256
```