## DOCKER #5

### Crear Imagen a partir de un Contenedor

Para comenzar, ejecutamos un contenedor interactivo basado en una imagen base.

```
 docker run -it --name mi_contenedor debian bash
```

![image](https://github.com/user-attachments/assets/6481b081-d77e-49b6-9fda-ee3d785b5f9b)

Dentro del contenedor podemos instalar paquetes, modificar archivos, o realizar cualquier otra personalización.

```
apt update && apt install -y apache2
```
```
echo "<h1>Mi Servidor Web</h1>" > /var/www/html/index.html
```

![image](https://github.com/user-attachments/assets/914b2e22-71d6-47d1-8090-3f083948bea3)
![image](https://github.com/user-attachments/assets/70f9e08b-4d8b-46d6-befa-e95841c76311)

Ahora con "docker commit" para capturar los cambios realizados en una nueva imagen.

```
docker commit mi_contenedor usuario/miapache:v1
```

![image](https://github.com/user-attachments/assets/96e0a8c1-5fd1-4e23-ad2b-bceb4d102597)

### 4. Crear un Contenedor desde la Nueva Imagen
Para ejecutar nuestra imagen personalizada, es necesario indicar el proceso principal que debe ejecutarse al iniciarse el contenedor.

```
 docker run -d -p 8080:80 \
             --name servidor_web \
             usuario/miapache:v1 \
             bash -c "apache2ctl -D FOREGROUND"
```

![image](https://github.com/user-attachments/assets/f24a6d16-574b-4bc3-9b07-f850875fadd5)

Ahora comprobamos poniendo en el navegador "localhost:8080":

![image](https://github.com/user-attachments/assets/b3dbe905-a723-4aa0-ae35-f0bfd36f7ece)

### Crear una imagen en página estática

Hay 3 formas de hacerlo:

#### 1º Forma:

Descaramos

![image](https://github.com/user-attachments/assets/316f37d2-04d4-4c85-b782-448234ef3b7b)

Descargamos [esto](https://downgit.github.io/#/home?url=https://github.com/josedom24/curso_docker_ies/tree/main/ejemplos/modulo5/ejemplo1/version2) y descomprimimos

![image](https://github.com/user-attachments/assets/1335d92a-1317-4252-8f82-b01be5886652)

Construimos la imagen:

```
docker build -t usuario/ejemplo1:v1
```

![image](https://github.com/user-attachments/assets/4cf06bed-3116-41d1-98e3-377b9bd25457)


Ejecutamos el contenedor:

```
docker run -d -p 80:80 --name ejemplo1 usuario/ejemplo1:v1
```
![image](https://github.com/user-attachments/assets/ce96b5a5-d324-4e5c-8d3d-bd3091246253)

Comprobamos poniendo "loclhost:80" navegador:

![image](https://github.com/user-attachments/assets/4c44b767-d1be-4edb-83b7-2395a9914262)

#### 2º Forma:
Hacemos lo mismo pero con [estos archivos](https://downgit.github.io/#/home?url=https://github.com/josedom24/curso_docker_ies/tree/main/ejemplos/modulo5/ejemplo1/version2)
![image](https://github.com/user-attachments/assets/5b021811-d0bf-4297-97d2-061e457ff19d)

```
sudo unzip Descargas/version2.zip
```

Lo ejecutamos:

```
sudo docker build -t josedom24/ejemplo1:v2 .
```

![image](https://github.com/user-attachments/assets/372626a8-4942-4bb9-b278-013be5f6a23d)


Ahora debemos poner "sudo docker run -d -p 80:80 --name ejemplo1 josedom24/ejemplo1:v2" y comprobamos:

![image](https://github.com/user-attachments/assets/81682845-777b-479c-a55a-30bcc0686b66)

#### 3º Forma:

Descargamos [esto](https://downgit.github.io/#/home?url=https://github.com/josedom24/curso_docker_ies/tree/main/ejemplos/modulo5/ejemplo1/version3), y descomprimimos:

```
sudo unzip Descargas/version3.zip
```

![image](https://github.com/user-attachments/assets/566cd354-bee3-46bc-8f86-77417cb3befd)

Lo ejecutamos:

```
sudo docker build -t josedom24/ejemplo1:v3 .
```
Y comprobamos

```
sudo docker run -d -p 80:80 --name ejemplo1 josedom24/ejemplo1:v3
```

![image](https://github.com/user-attachments/assets/4105a11e-5d90-4b29-82b0-a664bd9508ea)


## Crear Imágenes Docker con aplicación PHP

Para ahorrar tiempo dire que debemos hacer todo lo anterior de nuevo pero con otros archivos por lo que pondre los enlaces, los comandos en orden y la comprobación.

#### 1º Forma:

Descargamos [estos archivos](https://downgit.github.io/#/home?url=https://github.com/josedom24/curso_docker_ies/tree/main/ejemplos/modulo5/ejemplo2/version2) y descomprimimos con:

```
sudo unzip Descargas/version1.zip
```
Ejecutamos:

```
$ docker build -t josedom24/ejemplo2:v1 .
```
```
$ docker run -d -p 80:80 --name ejemplo2 josedom24/ejemplo2:v1
```

Comprobamos poniendo "localhost:80":

![image](https://github.com/user-attachments/assets/f21ec533-40ee-4dd0-8ed6-488b54fcb80f)


#### 2º Forma:

Descargamos [estos archivos](https://downgit.github.io/#/home?url=https://github.com/josedom24/curso_docker_ies/tree/main/ejemplos/modulo5/ejemplo2/version2) y descomprimimos con:

```
sudo unzip Descargas/version2.zip
```
Ejecutamos:

```
$ docker build -t josedom24/ejemplo2:v2 .
```
```
$ docker run -d -p 80:80 --name ejemplo2 josedom24/ejemplo2:v2
```

Comprobamos poniendo "localhost:80":

![image](https://github.com/user-attachments/assets/affa9ca9-cebd-4a80-aa96-a8d35aa6616a)

#### 3º Forma:

Descargamos [estos archivos](https://downgit.github.io/#/home?url=https://github.com/josedom24/curso_docker_ies/tree/main/ejemplos/modulo5/ejemplo2/version2) y descomprimimos con:

```
sudo unzip Descargas/version3.zip
```
Ejecutamos:

```
$ docker build -t josedom24/ejemplo3:v3 .
```
```
$ docker run -d -p 80:80 --name ejemplo3 josedom24/ejemplo3:v3
```

Comprobamos poniendo "localhost:80":

![image](https://github.com/user-attachments/assets/b3f2f932-2c90-4e72-9b7b-c11051a24025)
