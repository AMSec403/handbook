Identificar el PID asociado a termservice
```cmd
tasklist /svc /fi "services eq termservice"
```

Finalizar el PID
```cmd
taskkill /f /pid 1040
```
