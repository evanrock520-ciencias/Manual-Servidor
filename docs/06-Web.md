# 🛜 Desplegando la aplicación web

## ⬇️ Instalación

Usaremos el siguiente repositorio para cargar la página web. [Aplicación Web](https://github.com/ma-robles/pixca-ppm)

Deberemos clonarlo en la siguiente ruta:

```bash
cd /var/www/html
sudo git clone https://github.com/ma-robles/pixca-ppm
```

```bash
sudo systemctl restart nginx
```

## 🎯 Configurar Rutas

Tenemos que modificar la URL que usa el `script.js`

Edita el archivo:

```bash
sudo nano /var/www/html/pixca-ppm/script.js
```

Cambiamos esta linea:

```javascript
// Antes
const url = 'https://10.20.12.50:8042/pm_api&sid='+ sid + '&date='+ date;

// Después
const url = 'https://IP:8041/pm_api&sid='+ sid + '&date='+ date; // Aquí va tu API

```

Y finalmente también modificamos la IP que usa el `plot.js`

Edita el archivo:

```bash
sudo nano /var/www/html/pixca-ppm/lib/plot.js
```

Cambiamos esta linea:

```javascript
// Antes
const ip = 'https://10.20.12.50:8042'

// Después
const ip = 'https://IP:8041' // Aquí va tu nueva IP

```

## 🚀 Iniciar Servicio

Verificamos que nuestro archivo de **NGINX** tenga una correcta sintáxis.

```bash
sudo nginx -t
```

> Nota: Si falla regresa a [NGINX](02-Nginx.md)

Y reiniciamos el servicio.

## ➜🚪 Ingresar

Deberas colocar por la IP de tu servidor en un navegador web. Como nos autocertificamos saltará una alerta. Deberas avanzar de todos modos. 

Veras algo como lo siguiente

![Pantalla de Inicio](images/inicio.png)

Podras comprobar que la API funciona seleccionando la `pixca_ppm012`
Si carga la selección de año entonces lo está haciendo correctamente. ✅

![Buscando](images/buscando.png)

[Anterior](05-API.md) | [Siguiente](../README.md)
