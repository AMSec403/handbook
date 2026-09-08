
```bash
podman compose down
```


```bash
sudo apt-get remove --purge -y podman podman-compose buildah skopeo
```


```bash
sudo apt-get autoremove -y
```


```bash
# Detenemos lo que haya quedado colgado en el espacio de tu usuario
podman compose down

# Desinstalamos Podman y todas sus dependencias de red
sudo apt-get remove --purge -y podman podman-compose buildah skopeo
sudo apt-get autoremove -y

```