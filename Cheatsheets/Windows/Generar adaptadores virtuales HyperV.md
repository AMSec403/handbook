Solución a fallo de Windows al generar los adaptadores virtuales por interfaz grafica, aparentemente el adaptador se genera de forma correcta pero no logra dar salida.
```bash
New-VMSwitch -Name "vSwitchVLAN2" -NetAdapterName "Ethernet" -AllowManagementOS $true
```