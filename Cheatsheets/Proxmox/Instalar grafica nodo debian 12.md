
```bash
apt update && apt upgrade -y
apt install -y xfce4 xfce4-goodies
```

```bash
apt install -y xrdp
```

```bash
adduser telecom
```

```bash
usermod -aG sudo telecom
```

```bash
echo "xfce4-session" > /home/telecom/.xsession
chown telecom:telecom /home/telecom/.xsession
systemctl restart xrdp
```

```bash
```
