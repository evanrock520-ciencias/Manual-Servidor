# 🔥 Configuración de Firewall

## Abrir el firewall

Por lo general el firewall incluido en las distribuciones de **Ubuntu Server** está cerrado por defecto. Por lo tanto tendremos que abrirlo.

Verificamos si está instalado.

```bash
sudo ufw --version
```

Si no lo está:

```bash
sudo apt update
sudo apt install ufw
```

Y abrimos el firewall con:

```bash
sudo ufw enable
```

## 🔌 Puertos

Habilitaremos los puertos necesarios para poder usar Nginx. 

```bash
sudo ufw allow "Nginx Full"
sudo ufw allow OpenSSH
```

Además para nuestra aplicación web usaremos el puerto `8081`, por lo que deberemos abrirlo también.

```bash
sudo ufw allow 8081
```
