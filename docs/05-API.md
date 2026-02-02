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