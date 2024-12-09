## Instalación del servidor web Apache
### Instalación de Apache en Ubuntu

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
6. Por último escribiremos en nuestro navegador: "https://localhost" y veremos lo siguiente:

<br>
<img src="../TEMA1/Imágenes/APACHE2.png"/>
<br>
