# Instalación
```bash
git clone https://github.com/Und3rf10w/kali-anonsurf.git
cd kali-anonsurf
sudo ./installer.sh
sudo apt install secure-delete tor gufw

sudo dpkg --ignore-depends=i2p -i kali-anonsurf.deb
```

Uso

```bash
sudo anonsurf start
sudo anonsurf stop
sudo anonsurf status
sudo anonsurf change

curl https://check.torproject.org
```