# 🌐 Manual de configuración

![Ubuntu](https://img.shields.io/badge/Ubuntu-22.04-orange)
![NGINX](https://img.shields.io/badge/NGINX-active-green)
![ESP32](https://img.shields.io/badge/ESP32-integrated-blue)

Este repositorio sirve como manual para la configuración del servidor **Lenovo Thinksystem SR250 V2** que tiene como propósito adquirir datos climáticos a partir de microcontroladores ESP32.

## 📚 Contenido

1. [Instalación de Ubuntu Server](docs/01-Ubuntu.md)
2. [Instalación y Configuración de NGINX](docs/02-Nginx.md)
3. [Firewall](docs/03-Firewall.md)
4. [HTTPS](docs/04-HTTPS.md)
5. [Despliegue de la API](docs/05-API.md)
6. [Despligue de la aplicación web](docs/06-Web.md)

## Repositorios Utilizados

Este proyecto integra componentes desarrollados en repositorios externos.  
El presente manual se enfoca en la configuración del servidor y la integración de dichos componentes.

- 🌐[Aplicación web](https://github.com/ma-robles/pixca-ppm)
- 🔌 [API](https://github.com/ma-robles/pixca-ppm_api)
- 🤖 [Firmware ESP32](https://github.com/ma-robles/pm_pembu)
- 🧱 [Modelos 3D](https://github.com/ma-robles/abrigo_pm)
