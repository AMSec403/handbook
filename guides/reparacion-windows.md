# 🛠️ Reparación de Windows con SFC y DISM

---

## 📌 System File Checker (SFC)

El comando **SFC** (System File Checker) analiza y repara archivos del sistema dañados o faltantes.

### Uso

```batch
sfc /scannow
```

### Detalles

- **/scannow** → Escanea todos los archivos protegidos del sistema y reemplaza los dañados.
- El proceso puede tardar varios minutos.
- Si encuentra errores que no puede reparar, se recomienda usar **DISM**.

---

## 📌 Deployment Imaging Service and Management Tool (DISM)

El comando **DISM** repara la imagen de Windows, que es la base que usa SFC para restaurar archivos.

### Comandos principales

1. **Verificar la imagen**

```batch
DISM /Online /Cleanup-Image /CheckHealth
```

2. **Escanear la imagen**

```batch
DISM /Online /Cleanup-Image /ScanHealth
```

3. **Reparar la imagen**

```batch
DISM /Online /Cleanup-Image /RestoreHealth
```

- Repara automáticamente la imagen usando Windows Update o una fuente local.

- En servidores sin Internet, se puede usar una fuente local:
  
  ```batch
  DISM /Online /Cleanup-Image /RestoreHealth /Source:D:\sources\install.wim /LimitAccess
  ```

---

## 🔄 Flujo recomendado

```text
   ┌───────────────┐
   │  SFC /scannow │
   └───────┬───────┘
           │
           │ ¿Reparó todo?
           │
   ┌───────▼────────┐
   │     Sí         │ → Fin
   └────────────────┘
           │
   ┌───────▼────────┐
   │     No         │
   └───────┬────────┘
           │
   ┌───────▼───────────────┐
   │ DISM /RestoreHealth   │
   └─────────┬─────────────┘
             │
   ┌─────────▼─────────────┐
   │ Ejecutar SFC de nuevo │
   └───────────────────────┘
```

---

## ⚠️ Notas importantes

- Ejecutar siempre en una **ventana de PowerShell o CMD con privilegios de administrador**.
- SFC repara archivos activos, DISM repara la imagen base.
- Es recomendable tener un respaldo antes de realizar reparaciones críticas.

---

## 📚 Recursos

- Microsoft Docs: SFC [(learn.microsoft.com in Bing)](https://www.bing.com/search?q=%22https%3A%2F%2Flearn.microsoft.com%2Fes-es%2Fwindows-server%2Fadministration%2Fwindows-commands%2Fsfc%22)
- Microsoft Docs: DISM [(learn.microsoft.com in Bing)](https://www.bing.com/search?q=%22https%3A%2F%2Flearn.microsoft.com%2Fes-es%2Fwindows-hardware%2Fmanufacture%2Fdesktop%2Fdism-reference%22)
