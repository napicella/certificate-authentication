# Auth wflow

## Generate keys for CA
```bash
ssh-keygen -t rsa -b 4096 -f ca_user_key
```
which generates `ca_user_key` and `ca_user_key.pub` 

## Copy CA public key to server
```bash
scp bla bla ...
```

## Trust CA
For user certificates which have one or more principles listed, and where the setting is to have global effect, edit the `/etc/ssh/sshd_config` file as follows:
```bash
TrustedUserCAKeys /etc/ssh/ca_user_key.pub
```
Restart sshd
```bash
service sshd restart
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

# Resources
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/sec-creating_ssh_certificates_for_authenticating_users
