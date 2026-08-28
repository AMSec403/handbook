# Instalación 

```bash
sudo apt install kde-spectacle
```

# Spectacle predeterminado set-spectacle.sh

```bash
#!/bin/bash

# Print → Spectacle pantalla completa
gsettings set org.mate.Marco.global-keybindings run-command-screenshot 'Print'
gsettings set org.mate.Marco.keybinding-commands command-screenshot 'spectacle'

# Alt+Print → Spectacle ventana activa
gsettings set org.mate.Marco.global-keybindings run-command-window-screenshot '<Alt>Print'
gsettings set org.mate.Marco.keybinding-commands command-window-screenshot 'spectacle -w'

# Shift+Print → Spectacle región (usando command-2)
gsettings set org.mate.Marco.global-keybindings run-command-2 '<Shift>Print'
gsettings set org.mate.Marco.keybinding-commands command-2 'spectacle -r'

echo "✅ Configuración aplicada: Print, Alt+Print y Shift+Print ahora usan Spectacle."
```