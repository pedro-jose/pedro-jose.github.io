---
layout: post
title:  Practica HTTPS
date:   2021-02-18 14:21:54 -0600
categories: jekyll update
---
# HTTPS con Let’s Encrypt y Certbot

En esta práctica vamos a habilitar el protocolo HTTPS en un sitio web WordPress que se estará ejecutando en una instancia EC2 de Amazon Web Services (AWS).

##  Tareas a realizar
## 1. Paso1
Registrar un nombre de dominio en Freenom y configurar dns para que el dominio haga referencia a la ip de la instancia. Tendremos que añadir dos registros DNS de tipo A con la dirección IP pública de su instancia EC2 de AWS. Un registro estará en blanco para que pueda resolver el nombre de dominio sin las www y el otro registro estará con las www.

![DNS](https://github.com/pedro-jose/pedro-jose.github.io/blob/master/images/dns.png)

## 2. Paso 2
 Haremos uso del script de la practica de Wordpress-CLI, añadiendo las siguientes lienas:
 ```
# Instalación de cerbot
1. Realizamos la instalación y actualización de snapd.
snap install core
snap refresh core

2. Eliminamos si existiese alguna instalación previa de certbot con apt.
apt-get remove certbot

3. Instalamos el cliente de Certbot con snapd.
snap install --classic certbot

4. Creamos una alias para el comando certbot.
ln -s /snap/bin/certbot /usr/bin/certbot

5. Obtenemos el certificado y configuramos el servidor web Apache.
sudo certbot --apache -m demo@demo.es --agree-tos -d practica-https.tk
 ```

Ahora solo nos faltaria cambiar una última cosa y es:
> - wp core install --url=http://practica-https.tk --title="Practica HTTPS" --admin_user=admin --admin_password=admin --admin_email=test@test.com --allow-root

Sustituir la url con la ip por el nombre de dominio.

Ya con esto podremos acceder a través del nombre y de forma segura.
![Prueba de funcionamiento](https://github.com/pedro-jose/pedro-jose.github.io/blob/master/images/practica.png)

