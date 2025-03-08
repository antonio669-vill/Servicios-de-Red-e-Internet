## Instalación de Docker

Primero actualizamos ubuntu
```
 sudo apt update
 sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
![image](https://github.com/user-attachments/assets/8ef138d2-6b48-4cb1-8429-7dceabe32e4f)

Ahora tendremos que agregar una clave para luego poder descargar el repositorio con docker:
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
![image](https://github.com/user-attachments/assets/8aecc736-64fb-4352-804a-b91d0ce94212)

E instalamos el repositorio con docker:
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
```
![image](https://github.com/user-attachments/assets/b8ef745f-5c51-4dc1-b637-a5600041ab96)

(Recomendable hacer un update y un upgrade de los paquetes)
```
sudo apt update
sudo apt upgrade -y
```
Instalamos las politicas de Docker y Docker con:
```
apt-cache policy docker-ce
```
```
sudo apt install docker-ce
```
![image](https://github.com/user-attachments/assets/773dd15d-e5be-4098-ac48-948847f6c994)

![image](https://github.com/user-attachments/assets/3b04b40b-2dae-40b9-8934-3a7ebea69d31)

Por último podremos utilizar docker con:

![image](https://github.com/user-attachments/assets/4a043ab1-e90c-4526-ad32-fb106715cca4)
