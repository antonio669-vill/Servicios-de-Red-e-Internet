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
### Configuración para Wordpress

1. Creamos un archivo para configuración con "sudo nano /etc/apache2/sites-available/wordpress.conf" y escribimos:

````
<VirtualHost *:80>
    DocumentRoot /var/www/html
    ServerName wordpress.local
    ServerAdmin admin@localhost
</VirtualHost>
````

2. Habilitaremos la página de Wordpress escribiendo

````
sudo a2ensite wordpress
````

3. Deshabilitamos la página por defecto de Apache con "sudo a2dissite 000-default" y añadimos el dominio al fichero hosts:

````
sudo nano /etc/hosts
````
4. Por último recargaremos Apache con "sudo service Apache2 reload"

### La base de datos
1. Accedemos a MySQL como administradrores con:

````
sudo mysql -u root
````

2. Creamos nuestra base datos poniendo "CREATE DATABASE" y el nombre que le querramos poner
````
CREATE DATABASE Wordpress;
````
3. Ahora tendremos que crear un usuario admininistrador y le asignamos los privilegios a dicho usuario

````
CREATE USER 'admin'@'localhost'  IDENTIFIED  BY 'admin';
````
````
GRANT ALL PRIVILEGES -> ON wordpress.* -> TO 'admin'@'localhost';
````

( Es importante actualizar los privilegios de nuestra base de datos con: "FLUSH PRIVILEGES;")

4. Cerramos la sesión de MySQL con "quit"


<br>

<img src="../TEMA1/Imágenes/con.png" alt="index" width="570"/>

<br>