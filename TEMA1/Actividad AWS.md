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
# Crear un certificado autofirmado y activar el módulo SSL
