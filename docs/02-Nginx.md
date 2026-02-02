# 🔗 Instalación y Configuración de NGINX

## ⬇️ Instalación

Para instalar en NGINX en Ubuntu Server simplemente corremos.

```bash
sudo apt update
sudo apt install nginx -y
```

## 🛠️ Configuración

NGINX incluye un sitio por defecto que debe deshabilitarse para evitar conflictos de puertos y rutas.

```bash
sudo rm /etc/nginx/sites-enabled/default
```

Ahora podemos crear el archivo de proyecto.

```bash
sudo nano /etc/nginx/sites-available/pixca.config
```

Está es la configuración que usaremos para nuestro servidor.


```bash
server {

    listen 8080 default_server;
    listen [::]:8080 default_server;

    listen 443 ssl;
    listen [::]:443 ssl;

    server_name _;

    ssl_certificate     /etc/nginx/ssl/certificate.crt;
    ssl_certificate_key /etc/nginx/ssl/private.key;

    root /var/www/html/pixca;

    location / {
        try_files $uri $uri/ =404;
    }

}
```

> Nota: La ubicación de los certificados y de la raíz dependeran de donde creas tus archivos.

Ahora crearemos un enlace simbólico a nuestro archivo de configuración `pixca.config`

```bash
sudo ln -s /etc/nginx/sites-available/pixca.config /etc/nginx/sites-enabled/
```

