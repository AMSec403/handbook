## Instalación
```bash
git clone https://github.com/adionditsak/blacklist-check-unix-linux-utility.git

cd blacklist-check-unix-linux-utility

chmod +x ./bl

mv ./bl /usr/local/bin
```

# Use with domains or IP addresses

```bash
 ./bl domain.tld

 ./bl 8.8.8.8 # IP
```

# Pipe with other UNIX utils, eg. grep. Only blacklisted:


```bash
 ./bl domain.tld | grep "blacklisted"
```
