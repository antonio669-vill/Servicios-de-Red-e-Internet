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
1. Abrimos una terminal en Linux de nuevo
2. Ahora instalaremos MySQL de la siguiente forma:
`````
sudo apt install mysql-server
`````