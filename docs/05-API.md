# 🔁 Configuración de la API

Nuestro servidor recopila datos de sensores conectados a microcontroladores ESP32. Para poder hacer esto, necesitamos configurar la API
que lo permite.

## ⬇️ Instalación

Usaremos el siguiente repositorio. [Repositorio de la API](https://github.com/ma-robles/pixca-ppm_api)

Si no tenemos **git** instalado:

```bash
sudo apt install git
```

Podemos clonar el repositorio en una computadora externa y cargarlo mediante USB o clonarlo directamente en el servidor.

```bash
git clone https://github.com/ma-robles/pixca-ppm_api.git
```

## Instalación del servicio en systemd

Para poder correr la API necesitamos tener instalado **NodeJS**

```bash
sudo apt install nodejs npm
```

Necesitamos crear el siguiente directorio en el **home/** de nuestro usuario. 
> Nota: Se recomienda crear un usuario que no pertenezca a **sudo** para hacerlo

```bash
mkdir -p ~/.config/systemd/user
cd ~/.config/systemd/user
```

Creamos un archivo `pixca.service`

```bash
sudo nano pixca.service
```

Y colocamos la siguiente configuración para el daemon.

```bash
  [Unit]
  Description= Servicio pixca_ppm
  After=network.target
  
  [Service]
  Type=simple
  WorkingDirectory=/home/*user*/pixca-ppm_api/
  ExecStart=/usr/bin/node /home/*user*/pixca-ppm_api/pixca-ppm_api.js
  Restart=on-failure
  
  [Install]
  WantedBy=default.target
```

## 🎯 Configurar Rutas

Antes de poder usar nuestra API en conjunto con nuestra página web deberemos realizar algunas modificaciones a los repositorios.

Edita el archivo:

```bash
nano ~/pixca-ppm_api/pixca-ppm_api.js
```

Y asegúrate de que las constantes coincidan con nuestra configuración local:

- Host e IP: Cambia el dominio por la IP local del servidor.

- Path de datos: Ajusta la ruta a la carpeta data/ local. 

- Certificados: Apunta a la ruta absoluta donde guardamos los certificados de OpenSSL (/etc/nginx/ssl/).

```javascript
// Antes
const host = 'ruoa.unam.mx';
const path_data = "pm-pembu/data/";

// Ahora
const host = 'IP' // Aquí va tu IP;
const path_data = "data/";

// Configuración de certificados SSL
var options = {
    key: fs.readFileSync('/etc/nginx/ssl/private.key'),
    cert: fs.readFileSync('/etc/nginx/ssl/certificate.crt')
};
```

> Nota: Puedes ver tu ip con `ip a`.

Para que podamos comprobar que la API funciona deberemos crear:

```bash
mkdir -p ~/data/pixca_ppm012
```

Después de haber creado el archivo deberemos correrlo con el siguiente comando.

```bash
systemctl --user daemon-reload
systemctl --user enable pixca.service
systemctl --user start pixca.service
```

> Nota: `user` debe ser remplazdo por el usuario con el que creaste el archivo. 

Podemos verificar el estado con el siguiente comando.

```bash
    systemctl --user status pixca.service
```

[Anterior](04-HTTPS.md) | [Siguiente](06-Web.md)
