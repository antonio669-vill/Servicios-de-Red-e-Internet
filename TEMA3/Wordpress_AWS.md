# Instalación y Configuración de WordPress en AWS con Ubuntu
## VPC
Tendremos que desde AWS acceder a VPC y configurar una de estas:

![image](https://github.com/user-attachments/assets/5c13121c-5e90-475b-91b3-f271db8f0b78)

En mi caso usare una creada anteriormente con la IP `10.2.0.0/16` y con los siguientes detalles:

![image](https://github.com/user-attachments/assets/e6213023-5289-426b-be43-3ea69796ee5f)

## EC2
Entramos en EC2 desde AWS y lanzamos una instancia a la que he llamado "Wordpress" y el Sistema Operativo es Ubuntu en su versión más reciente:

<br>
<img src="../TEMA3/Imágenes/1.PNG"/>
<br>

Tendremos que poner esta configuración, usaremos la clave `vockey` y **LO MÁS IMPORTANTE** elegir la VPC que usaremos para esta práctica ('SREIpractica1' en mi caso). Por último agregar una regla para permitir HTTP desde cualquier origen.

<br>
<img src="../TEMA3/Imágenes/2.PNG"/>
<br>

Terminamos de configurarla:

<br>
<img src="../TEMA3/Imágenes/3.PNG"/>
<br>

Y ya sea con Putty o con la opción de "Conectar" de AWS (esta última es la opción que yo he elegido) entramos:

<br>
<img src="../TEMA3/Imágenes/4.PNG"/>
<br>

## Apache y PHP
Actualizamos el sistema como lo hariamos en cualquier maquina ubuntu.
```
sudo apt update
```
```
sudo apt upgrade -y
```
<br>
<img src="../TEMA3/Imágenes/5.PNG"/>
<br>
<br>
<img src="../TEMA3/Imágenes/6.PNG"/>
<br>

E instalarmos Apache con el siguiente comando:
```
sudo apt install apache2 -y
```
<br>
<img src="../TEMA3/Imágenes/7.PNG"/>
<br>

La forma de iniciar Apache y usarlo es con los comandos:
```
sudo systemctl start apache2
sudo systemctl enable apache2
```

<br>
<img src="../TEMA3/Imágenes/8.PNG"/>
<br>

Y cuando pongamos la IP de nuestra instancia en el navegador veremos que se instalo correctamente:

<br>
<img src="../TEMA3/Imágenes/9.PNG"/>
<br>

Ahora, para instalar PHP:
```
sudo add-apt-repository ppa:ondrej/php
```
```
sudo apt install php7.4 libapache2-mod-php7.4 php7.4-cli php7.4-mysql -y
```
<br>
<img src="../TEMA3/Imágenes/10.PNG"/>
<br>
<br>
<img src="../TEMA3/Imágenes/11.PNG"/>
<br>
<br>
<img src="../TEMA3/Imágenes/12.PNG"/>
<br>

Reiniciar Apache:
```
sudo systemctl restart apache2
```
<br>
<img src="../TEMA3/Imágenes/14.PNG"/>
<br>

## RDS

Nos dirigimos a RDS para crear la base de datos:

![image](https://github.com/user-attachments/assets/2d04284d-2dc9-4491-b9ce-daa21a6d2f15)

Tendremos que poner esta configuración:

<br>
<img src="../TEMA3/Imágenes/15.PNG"/>
<br>

<br>
<img src="../TEMA3/Imágenes/16.PNG"/>
<br>

Importante añadir la VPC en la base de datos:

<br>
<img src="../TEMA3/Imágenes/18.PNG"/>
<br>

Creamos un nuevo grupo de seguridad le ponemos el nombre 

<br>
<img src="../TEMA3/Imágenes/19.PNG"/>
<br>

Tendremos que poner una contraseña a la base de datos la cual **NO** podemos olvidar:

<br>
<img src="../TEMA3/Imágenes/20.PNG"/>
<br>

Una vez se cree la RDS nos vamos a "Acciones" y "Configurar la conexión EC2":

![image](https://github.com/user-attachments/assets/caefc3ef-2bfa-477c-844f-82412b4d36f7)

Y ponemos nuestra instancia:

<br>
<img src="../TEMA3/Imágenes/21.PNG"/>
<br>


## EFS
Buscamos EFS en AWS y seleccionamos "Crear sistema de archivos", debemos asignar un nombre y elegir la VPC creada y muy importante, configurar una regla en la VPC para permitir conexiones NFS. 

![image](https://github.com/user-attachments/assets/f9f9e391-5299-4351-8b51-aa4fa51b5fbc)

<br>
<img src="../TEMA3/Imágenes/23.PNG"/>
<br>

Elegimos nuestra instancia:

<br>
<img src="../TEMA3/Imágenes/24.PNG"/>
<br>

Deberemos editar las reglas de entrada y la configuramos tal que así:

<br>
<img src="../TEMA3/Imágenes/25.PNG"/>
<br>

<br>
<img src="../TEMA3/Imágenes/26.PNG"/>
<br>

Y en EFS ponemos nuestra VPC.

<br>
<img src="../TEMA3/Imágenes/27.PNG"/>
<br>

Ahora le damos a "Asociar"

<br>
<img src="../TEMA3/Imágenes/28.PNG"/>
<br>

Lo configuramos como lo vemos en la foto de abajo y copiamos el comando que se marca en la misma imagen:

<br>
<img src="../TEMA3/Imágenes/29.PNG"/>
<br>

Instalamos NFS con 'sudo apt install nfs-common -y'. Por último montamos el sistema de archivos EFS:

```
sudo mkdir -p efs
```
```
sudo mount -t nfs4 -o nfsvers=4.1,rsize=1048576,wsize=1048576,hard,timeo=600,retrans=2,noresvport <IP_EFS>:/ efs
```
<br>
<img src="../TEMA3/Imágenes/30.PNG"/>
<br>

<br>
<img src="../TEMA3/Imágenes/31.PNG"/>
<br>


## Instalación de WordPress
Descargarmos WordPress y descomprimirlo con:
```
sudo wget http://wordpress.org/latest.tar.gz
```
```
sudo tar -xf latest.tar.gz
```
<br>
<img src="../TEMA3/Imágenes/32.PNG"/>
<br>

<br>
<img src="../TEMA3/Imágenes/33.PNG"/>
<br>

Ahora instalamos el cliente de MySQL:

```
sudo apt install mysql-client -y
```
<br>
<img src="../TEMA3/Imágenes/34.PNG"/>
<br>

Abrimos MySQL:

<br>
<img src="../TEMA3/Imágenes/35.PNG"/>
<br>

Y creamos las base de datos:
```
mysql -h <endpoint_RDS> -u admin -p
CREATE DATABASE wordpress;
CREATE USER 'wordpress_user'@'%' IDENTIFIED BY 'password123';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpress_user'@'%';
FLUSH PRIVILEGES;
```

<br>
<img src="../TEMA3/Imágenes/36.PNG"/>
<br>

Podemos comprobar que esta activo con:
```
sudo systemctl status apache2
```
<br>
<img src="../TEMA3/Imágenes/37.PNG"/>
<br>

Y ya podemos acceder a Wordpress desde el navegador.

![Wordpress](https://github.com/user-attachments/assets/9b40bc88-4de0-4d63-b748-736cb10b227e)

![image](https://github.com/user-attachments/assets/b9aec791-871d-4ad1-9079-d05875540055)

![image](https://github.com/user-attachments/assets/d968ca33-6b3c-43b1-b664-22b1a5346dc9)



