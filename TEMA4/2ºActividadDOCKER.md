## Docker #2
Empezaremos usando el comando y un nombre, esto nos permitira ejecutar el contenedor:
```
sudo docker run hello-world
```
![image](https://github.com/user-attachments/assets/b726265e-b036-4448-98b0-8007edc216b4)

Y para mostrarlos (los contenedores) usamos este comando:
```
sudo docker ps -a
```
![image](https://github.com/user-attachments/assets/e4efb238-f40c-4bd9-9e1f-afb30ed53a30)

Y para ver las imagenes usamos el comando:
```
sudo docker images
```
![image](https://github.com/user-attachments/assets/68ba8b4b-4912-467b-a34f-c68fa60dc49e)

A continuación ,para añadir una app, tenemos que añadir al repositorio del mismo.
```
git clone https://github.com/docker/getting-started-app.git
```
![image](https://github.com/user-attachments/assets/a37cdf71-431c-47ea-a39d-e7ac38775805)

Y posteriormente creamos el archivo "dockerfile" con esta configuración:

![image](https://github.com/user-attachments/assets/6c830c0c-0fc7-46c4-a9c0-dded7d4f69aa)


Construimos la app con:
```
sudo docker build -t getting-started .
```
![image](https://github.com/user-attachments/assets/c9897150-1dc4-4c81-ad82-7a888fc319bc)

Y lo ejecutamos
```
sudo docker run -d -p 127.0.0.1:3000:3000 getting-started
```
![image](https://github.com/user-attachments/assets/b803a96f-63c5-47ab-ae23-f33eb5782d18)

Ahora escribimos la dirección en el navegador para ver la app:

![image](https://github.com/user-attachments/assets/91f21dea-a5b6-4295-b366-11f20e48ae1e)


## IMPORTANTE

Debemos crear una sesión en docker.hub y acordarnos del usuario y la contraseña que pongamos:
![image](https://github.com/user-attachments/assets/642b4340-193d-44f0-8278-39aa40e9bdd0)
![image](https://github.com/user-attachments/assets/1fbb5f54-8652-4ea7-95d3-f5eb165e3032)
![image](https://github.com/user-attachments/assets/4e06284b-1041-4266-9175-6d09e7b1e6a4)


Ahora nos logeamos posicionándonos en "getting-started-app" con nuestro nombre gracias al comando:
```
sudo docker login -u <usuario>
```

![image](https://github.com/user-attachments/assets/aad1a56f-f9d6-4a08-aa32-25cd2be028c6)

Asociamos nuestra cuenta con:

```
sudo docker tag 74cc54e27dc4 tu-usuario/74cc54e27dc4:latest
sudo docker push tu-usuario/74cc54e27dc4:latest
```
![image](https://github.com/user-attachments/assets/5a23e879-a1ea-46a7-a7a1-781d8cca51ad)

Si lo hemos hecho bién, nos vamos a MyProfile y comprovamos que hemos creado la imagen:
![image](https://github.com/user-attachments/assets/a499a223-3fda-4c54-8dc3-e68d1b01a726)
![image](https://github.com/user-attachments/assets/3153a361-e512-4f80-882d-ef3497f00059)
