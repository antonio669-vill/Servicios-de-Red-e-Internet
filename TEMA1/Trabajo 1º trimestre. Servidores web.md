## Instalación del servidor web Apache
### Instalación de Apache en Ubuntu

1. Abrimos una terminal en Linux

<br>
<img src="../TEMA1/Imágenes/cmd.png"/>
<br>

2. Actualizamos los paquetes instalados
`````
sudo apt update
`````
3. Instalamos las nuevas versiones
````
sudo apt upgrade
````
4. Instalamos el paquete de Apache
`````
sudo apt install apache2
`````
5. Ajustamos el Firewall para Apache con los siguientes dos comandos:
`````
sudo ufw app list
`````
`````
sudo ufw allow "Apache"
`````
6. Comprobar en nuestro navegador la siguiente dirección
````
https://localhost
````
Si hemos seguido los pasos habremos instalado correctamente Apache2 para Ubuntu

<br>
<img src="../TEMA1/Imágenes/APACHE2.png"/>
<br>
