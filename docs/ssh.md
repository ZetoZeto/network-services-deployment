# SSH server (OpenSSH, key based)

SSH access is restricted to IT staff by key.

## Install

```bash
apt update
apt install openssh-server
```

![Install](../img/ssh/install.png)

Make sure SSH listens on port 22 and enable the service:

```bash
systemctl enable --now ssh
```

## Key authentication

Generate an RSA key (2048 bits):

```bash
ssh-keygen -t rsa -b 2048
```

![Key generation](../img/ssh/keygen.png)
![Key present](../img/ssh/key.png)

Copy the public key to the target so you can connect without a password each time:

```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub user@target
```

`ssh-copy-id` adds the key to `authorized_keys` on the target, and `-i` points to the generated key.

![Copy id](../img/ssh/copy_id.png)
![Connection test](../img/ssh/test_ok.png)

## Troubleshooting

If the key file is not generated, make sure the key is saved in the `~/.ssh` directory.
