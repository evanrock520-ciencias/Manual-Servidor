# 🐧 Instalar Ubuntu Server

## 🖼️ Instalar imagen

Puedes obtener la imagen (**.iso**) de Ubuntu Server en la siguiente página. [Ubuntu Server](https://ubuntu.com/download/server)

## ⚡Bootear USB

Para bootear el USB podemos usar el siguiente comando. 

```bash
sudo dd if=imagen.iso of=/dev/sdX bs=4M status=progress
```

> Nota: imagen.iso es la ubicación de la imagen y `/dev/sdX` es la ubicación de tu USB. Puedes consultarla con el comando `lsblk`

Tambíen podrias usar una aplicación como [Balena Etcher](https://etcher.balena.io/) para flashear la USB.

## Inicializar servidor

Para poder instalar Ubuntu Server colocamos la USB en algún puerto USB del servidor. Esperamos a que cargue el BIOS y apretamos `F12` y seleccionamos nuestro dispositivo USB.

## 💾 Configurar Instalación

Al iniciar la instalación verás una pantalla como está.

![Selección de Idioma](images/p1.png)

Cuando llegues al paso de configuración de red es importante ya tener cableada la conexión **Ethernet**. 
Además si la dirección IP de los puertos de red está cerrada es importante cargarla.

![Network](images/p2.png)

Configuramos nuestras credenciales.

![Credenciales](images/p3.png)

Habilitamos SSH.

![SSH](images/p4.png)

Y finalizamos la instalación.

![Final](images/p5.png)

[Anterior](../README.md) | [Siguiente](02-Nginx.md)