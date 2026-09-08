
```bash
rm -f /etc/apt/sources.list.d/pve-no-subscription.sources

```


```bash
cat > /etc/apt/sources.list.d/pve-no-subscription.sources << EOL
Types: deb
URIs: http://download.proxmox.com/debian/pve
Suites: trixie
Components: pve-no-subscription
Signed-By: /usr/share/keyrings/proxmox-archive-keyring.gpg
EOL

```


```bash
cat > /etc/apt/sources.list.d/debian.sources << EOL
Types: deb
URIs: http://deb.debian.org/debian
Suites: trixie trixie-updates
Components: main contrib non-free non-free-firmware
Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg

Types: deb
URIs: http://security.debian.org/debian-security
Suites: trixie-security
Components: main contrib non-free non-free-firmware
Signed-By: /usr/share/keyrings/debian-archive-keyring.gpg
EOL

```


```bash

```


```bash

```

