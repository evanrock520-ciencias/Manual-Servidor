# 🐧 Instalar Ubuntu Server

## 🖼️ Instalar imagen

Puedes obtener la imagen (**.iso**) de Ubuntu Server en la siguiente página. [Ubuntu Server](https://ubuntu.com/download/server)

## Bootear USB

Para bootear el USB podemos usar el siguiente comando. 

```bash
sudo dd if=imagen.iso of=/dev/sdX bs=4M status=progress
```

> Nota: imagen.iso es la ubicación de la imagen y `/dev/sdX` es la ubicación de tu USB. Puedes consultarla con el comando `lsblk`