# LFTP

## Iniciar conexión

```bash
lftp -u usuario ftp://servidor.com
```

## Deshabilitar SSL (en caso de ser necesario)

```bash
set ssl:verify-certificate no
set ftp:ssl-allow no
```

## Generar copia espejo conservando los permisos

```bash
mirror --allow-chown --no-umask --verbose=2 --parallel=5 .
```

## Generar archivo comprimido

```bash
tar -czf archivo.tar.gz *
```

## Eliminar todo el contenido del directorio

```bash
glob rm -r *
rm -r wp-content/
```

## Eliminar los ocultos

```bash
glob rm -rf .[!.]*
```

## Elimina directorios

```bash
glob rmdir *
```
