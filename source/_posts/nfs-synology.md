title: Montar directorio NFS en Synology DS214
date: 2016-08-22 18:18:03
tags:
- Synology
- NAS
- NFS
- Ubuntu
categories:
- Synology
---

##### Guia para configurar carpetas NFS en Synology en nuestro equipo Ubuntu

Como indican en la web de [Synology](https://www.synology.com/es-es/knowledgebase/DSM/tutorial/File_Sharing/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS) seguimos todos los pasos para crear nuestras carpetas compartidas en local mediante NFS.

Una vez configurado el NAS, para montar las carpetas necesitamos instalar el paquete `nfs-commons` :

```
sudo apt-get install nfs-common

```

Y añadimos en el archivo `/etc/fstab` como root:
```
sudo nano /etc/fstab
```
las carpetas a montar, como por ejemplo:

```
192.168.1.129:/volume1/video    /mnt/video      nfs     auto    0 0
```

En mi caso `192.168.1.129` es la IP del NAS y luego seguido de dos puntos `:` el directorio de la carpeta del NAS a montar `/volume1/video`.
La ruta `/mnt/video` es donde se va a montar en nuestro equipo.
