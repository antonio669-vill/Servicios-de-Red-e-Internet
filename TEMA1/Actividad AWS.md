# Instalar Apache
1. Como ya hemos hecho multiples veces en Proxmox sere rápido:
`````
sudo apt update
`````
`````
sudo apt upgrade
`````
`````
sudo apt-get install apache2
`````
<br>
<img src="../TEMA1/Imágenes/apa.png"/>
<br>
# Activar la autenticación con MySql
1. Instalamos PHP, MySQL y MariaDB.

`````
sudo apt-get install apache2 php7.0 libapruti11-dbd-mysql -y
`````
`````
sudo apt-get install mariadb-server mariadb-client -y
`````
2. Tras activar los sercicios de apache y mysql ("sudo systemctl enable apache2" y "sudo systemctl enable mysql") abriremos este último para crear en el una base de datos:

`````
sudo mysql -u root -p
`````
<br>
<img src="../TEMA1/Imágenes/ma.png"/>
<br>

`````
create database defaultsite_db;
`````
<br>
<img src="../TEMA1/Imágenes/row.png"/>
<br>
3. Dar permisos.

`````
GRANT SELECT, INSERT, UPDATE, DELETE ON defaultsite_db.* TO 'defaultsite_admin'@'localhost' IDENTIFIED BY 'usuario';
`````
![image](https://github.com/user-attachments/assets/6c0f800c-be12-477b-aa28-b37c2d675317)

`````
GRANT SELECT, INSERT, UPDATE, DELETE ON defaultsite_db.* TO 'defaultsite_admin'@'localhost.localdomain' IDENTIFIED BY 'password';
`````
![image](https://github.com/user-attachments/assets/41cb6e03-68aa-4986-9b23-9f6f6a9b6643)

`````
flush privileges;
`````
![image](https://github.com/user-attachments/assets/ff703b07-1848-4a73-b3e7-c9dfdf2ec71b)
4. Entramos en la base de datos y creamos una tabla:
`````
use defaultsite_db;
`````
![image](https://github.com/user-attachments/assets/5959f5bc-4957-437e-815d-d950665add98)
`````
create table mysql_auth ( username varchar(191) not null, passwd varchar(191), groups varchar(191), primary key (username) );
`````
![image](https://github.com/user-attachments/assets/e1bd2113-ca2e-4fa1-be82-ae193689c365)

5. Para autentificar el usuario convertimos la contraseña en hash y luego insertaremos los datos de la tabla
`````
htpasswd -bns siteuser siteuser
`````
![image](https://github.com/user-attachments/assets/b2f8394b-d964-4787-a31c-325fae671948)

6. Abriremos de nuevo nuestra base de datos con ("sudo mysql -u root -p" y "use defaultsite_db") y escribilos los datos de la tabla:

`````
INSERT INTO `mysql_auth` (`username`, `passwd`, `groups`) VALUES('siteuser', '{SHA}tk7HEH6Wo7SKT6+3FHCgiGnJ6dA=', 'sitegroup');
`````
![image](https://github.com/user-attachments/assets/efd57b9e-83d2-4ecb-87ba-87f03578d01a)

7. Salimos con "ctrl + z" y activamos todos los módulos con los comandos que se ven en la imagen:
![image](https://github.com/user-attachments/assets/da5d43b4-1510-4192-bf94-a457d13d5643)

8. Por último "sudo mkdir /var/www/html/protecteddir" y "sudo chown -R www-data:www-data /var/www/html/protecteddir" y terminamos de configurar apache abriendp ("sudo nano /etc/apache2/sites-available/000-default.conf"):
![image](https://github.com/user-attachments/assets/0e3508cf-a0f2-4f08-97eb-1b5b248554b8)

![image](https://github.com/user-attachments/assets/c7d43d0a-505b-4bb8-99e4-dde1bee1a0a3)


# Crear un certificado autofirmado y activar el módulo SSL
