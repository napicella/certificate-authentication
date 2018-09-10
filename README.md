## Generate keys for CA
```bash
ssh-keygen -t rsa -b 4096 -f ca_user_key
```
which generates `ca_user_key` and `ca_user_key.pub` 

## Copy CA public key to server
```bash
scp bla bla ...
```

## Generate user keys
```bash
ssh-keygen -t rsa -b 4096 -f ssh_user_key
```
which generates `ssh_user_key` and `ssh_user_key.pub` 


## CA signs user public key with its private key
```bash
ssh-keygen -s ca_user_key -I ec2 ssh_user_key

```
which generates `ssh_user_key-cert.pub`
