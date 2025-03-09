## DOCKER #3

Deberemos empezar creando una red Docker.

Para que los contenedores se comuniquen creamos una la red `red_guestbook`, usaremos el comando:

```
sudo docker network create red_guestbook
```
![image](https://github.com/user-attachments/assets/1f5015b7-ae04-49d3-8efd-fc1d87d0b9f8)

Activamos el contenedor de Redis con:

```
sudo docker run -d --name redis --network red_guestbook -v /opt/redis:/data redis redis-server --appendonly yes
```


![image](https://github.com/user-attachments/assets/966e43f5-49ba-4455-ae24-9ee7a53d51c4)


### Guestbook
Para activar el contenedor que contiene Guestbook a traves del puerto 80 ponemos este comando:

```
sudo docker run -d -p 80:5000 --name guestbook --network red_guestbook iesgn/guestbook
```
![image](https://github.com/user-attachments/assets/5f2b5238-7765-4b63-ad72-4d6d44d6ae79)

A continuación ponemos "localhost" en el navegador y veremos que Guestbook funciona:

![image](https://github.com/user-attachments/assets/a37e0e4a-c6f6-4e11-a96f-99977b527f54)

### Temperaturas

Creamos la red con los cambios correspondientes:

```
sudo docker network create red_temperaturas
```

![image](https://github.com/user-attachments/assets/e9698dd4-58b3-4298-8ff5-72c140c7bc0e)


Ahora tendremos que desplegar Backend y Frontend con los comandos:

```
sudo docker run -d --name temperaturas-backend --network red_temperaturas iesgn/temperaturas_backend
```
```
sudo docker run -d -p 80:3000 --name temperaturas-frontend --network red_temperaturas iesgn/temperaturas_frontend
```
![image](https://github.com/user-attachments/assets/e9243c89-0c60-42e9-87ee-d2d230e74ff8)

![image](https://github.com/user-attachments/assets/bcb81e3d-357d-452b-bf68-e67eae94ad45)


Si todo esta correcto, cuando volvamos a poner "localhost" en el navegador aparecera lo siguiente

![image](https://github.com/user-attachments/assets/7954b76e-0d2f-47c1-a21a-85b6976ee648)

(Podremos ver la temperatura de cualquier lugar de España).

## Wordpress + MariaDB

Creamos la red con los cambios correspondientes:
```
sudo docker network create red_wp
```
![image](https://github.com/user-attachments/assets/14f1dcf9-3f64-4df4-be39-e4bd467dee9a)


Desplegamos el contenedor que contiene la base de datos MariaDB, para ello ponemos el siguiente comando:

![image](https://github.com/user-attachments/assets/75a39165-d91e-4d59-9428-2aa1f0e86150)


Y ahora el contenedor de WordPress con este otro comando:

![image](https://github.com/user-attachments/assets/367bddc3-8f1a-4635-827c-188e24073ce0)

Si todo esta correcto, cuando volvamos a poner "localhost" en el navegador aparecera lo siguiente

![image](https://github.com/user-attachments/assets/d17f1eee-279c-45ea-a2f7-c60605fdd6e1)
![image](https://github.com/user-attachments/assets/47bb8c81-c607-4835-925a-cf1871772952)
![image](https://github.com/user-attachments/assets/62ccc787-e68f-4bb6-b170-7b5e3d0440f9)
![image](https://github.com/user-attachments/assets/a7c39135-59f2-48af-bebe-f7ef071753ad)


## IMPORTANTE

Es muy recomendable poner el comando "sudo docker stop $(sudo docker ps -aq)" entre ejercicios:
```
sudo docker stop $(sudo docker ps -aq)
```


