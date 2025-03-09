## DOCKER #3
Para descargar una imagen usamos este comando:
```
sudo docker pull ubuntu
```
![image](https://github.com/user-attachments/assets/eb963657-609e-4a96-8e4b-368d5916fb2a)

Ahora descargamos nginx con este comando:

```
sudo docker pull nginx
```
![image](https://github.com/user-attachments/assets/3bdbc194-7ae5-4055-b757-ce42ca037477)

Y hacemos un listado de las imagenes:
```
sudo docker images
```
![image](https://github.com/user-attachments/assets/a701ae32-32e1-4cc5-a267-3add35704e45)

Para ejecutar el contenedor hello-world con un seudónimo, usamos este comando:
```
sudo docker run --name myhello1 hello-world
```
![image](https://github.com/user-attachments/assets/ac94367b-340c-40a4-81a6-1b43f4991a43)

Y comprobamos:
```
sudo docker ps -a
```
![image](https://github.com/user-attachments/assets/186a04ff-d1a2-46e6-bbf1-a0fc38805172)


Ahora lo mismo pero cambiando los nombres:
```
sudo docker run --name myhello2 hello-world
```
```
sudo docker run --name myhello3 hello-world
```
![image](https://github.com/user-attachments/assets/c33797df-9282-45d8-a27b-28009c64a89f)
![image](https://github.com/user-attachments/assets/de41ac53-5447-4dff-82e2-cf95a562dc6e)

Mostraremos, acontinuación, todos los contenedores, usaremos este comando:
```
sudo docker ps
```
![image](https://github.com/user-attachments/assets/2198ac39-2336-4e4a-bc77-5c687f164199)

Ahora para parar los distintos contenedores usamos estos comandos con cada uno:
```
sudo docker stop myhello1
```
```
sudo docker stop myhello2
```
![image](https://github.com/user-attachments/assets/75195593-27b9-4ada-8c9d-cae3276fa04d)

![image](https://github.com/user-attachments/assets/d181d0b2-9089-414c-8625-cf0c35fbf230)

## Borra el contenedor “myhello1”

Y para borrar "myhello1" usamos:
```
docker rm myhello1
```
![image](https://github.com/user-attachments/assets/6e67483c-9131-4a5b-a6a1-8ef814041547)

Si queremos saber los contenedores que estan activados usamos este comando:
```
sudo docker ps
```
![image](https://github.com/user-attachments/assets/62313924-2bcf-4231-8f4c-e0c6468b694a)

Por último borraremos todos los contenedores, usando este comando:
```
docker stop $(docker ps -q)
```
```
sudo docker rm $(docker ps -a -q)
```
![image](https://github.com/user-attachments/assets/cf6e951c-6be2-4694-84fc-4518e6588162)
![image](https://github.com/user-attachments/assets/183349e0-c011-4eff-9e7f-0214b5a58b76)

Y aqui comprobamos que no queda ni uno:
```
sudo docker ps -a
```
![image](https://github.com/user-attachments/assets/b5ad8e24-0b08-4c28-af3e-3c033c779178)
