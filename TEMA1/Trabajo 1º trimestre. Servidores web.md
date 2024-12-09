## Instalación de Apache y MySQL
### Instalación de Apache

1. Abrimos una terminal en Linux

<br>
<img src="../TEMA1/Imágenes/CMD.png"/>
<br>

2. Actualizamos los paquetes instalados e instalamos las nuevas versiones
`````
sudo apt update
`````

````
sudo apt upgrade
````
3. Ahora instalaremos Apache de forma adecuada haciendo lo siguiente:
`````
sudo apt install apache2
`````

`````
sudo ufw app list
`````
`````
sudo ufw allow "Apache"
`````
4. Por último escribiremos en nuestro navegador: "https://localhost" y veremos lo siguiente:

<br>
<img src="../TEMA1/Imágenes/APACHE2.png"/>
<br>

### Instalación de MySQL
1. Abrimos una terminal en Linux de nuevo e instalaremos MySQL de la siguiente forma:
`````
sudo apt install mysql-server
`````
### Instalaremos Wordpress
1. Instalamos, primero, "unzip" con:

````
sudo unzip latest.zip
````

2. Luego descargaremos el archivo de instalación de Wordpress con el comando de abajo Y extraemos los archivos con el "unzip" instalado anteriormente.

````
wget https://es.wordpress.org/latest.zip
````

3. Ahora deberemos poner los contenidos de Wordpress a nuestra carpeta del dominio

````
sudo mv wordpress/* /var/www/html/
````

4. Por último modificaremos le concederemos permisos a la carpeta:

````
sudo chown -R www-data:www-data /var/www/html/*
````
