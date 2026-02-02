# Configurar HTTPS

## 🗝 Crear claves

Para crear los certificados de nuestro servidor usaremos **OpenSSL**.

Primero crearemos nuestra llave privada.

```bash
sudo mkdir /etc/nginx/ssl
sudo openssl genrsa -out /etc/nginx/ssl/private.key 2048
```

Después crearemos una solicitud de firma de certificado (**CSR**)

```bash
sudo openssl req -new -key /etc/nginx/ssl/private.key -out /etc/nginx/ssl/csr.csr
```

Y finalmente generaremos el certificado.

```bash
sudo openssl x509 -req -days 365 -in /etc/nginx/ssl/csr.csr -signkey /etc/nginx/ssl/private.key  -out etc/nginx/ssl/certificate.crt
```

Al ejecutar el comando de arriba se nos harán varias preguntas y es muy importante que el `Common name` corresponda con el nombre del **dominio web** o de la **dirección IP** de nuestro servidor.

Podemos verificar la clave generada con el siguiente comando.

```bash
sudo openssl x509 -in /etc/nginx/ssl/certificate.crt -text -noout
```