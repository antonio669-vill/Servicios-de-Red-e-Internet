# DOCKER #4

## Guestbook

Para esta actividad tenemos que crear un archivo llamado "docker-compose.yaml" mientras estamos posicionados en "Descargas":

![image](https://github.com/user-attachments/assets/a4ed2e3c-a5d9-4e89-907b-f49f3897b367)

Tendremos que escribir lo que vemos en esta imagen:

![image](https://github.com/user-attachments/assets/3805a30a-0ec9-4f3a-b13a-599433ebd57f)

Ahora para ejecutar la aplicación ponemos el siguiente comado:

```
sudo docker compose up -d
```

![image](https://github.com/user-attachments/assets/50a5430c-13a7-4219-8e53-4261a0568065)


Y si ponemos en el navegador "http://localhost:8080" veremos que lo hemos hecho correctamente:

![image](https://github.com/user-attachments/assets/78df2df3-a12b-47d1-a39d-432d0ed6f371)

Para saber que puerto debemos poner podemos usar el siguiente comando y buscarlo:

```
sudo docker compose ps
```

![image](https://github.com/user-attachments/assets/c4f6ca59-08df-4d46-88b7-c5409e3bfb94)

## Temperaturas

Volvemos a abrir "docker-compose.yaml" y lo modificamos poniendo lo siguiente:

![image](https://github.com/user-attachments/assets/a9158130-f040-4844-81f4-8a0a8d9c9b55)

Ahora para ejecutar la aplicación ponemos de nuevo el comando "sudo docker compose up -d" y si ponemos en el navegador "http://localhost:8081" veremos que lo hemos hecho correctamente:

![image](https://github.com/user-attachments/assets/6b0604e3-8ae4-4e8a-b60e-f10fa96fad20)

## Wordpress + MariaDB

Volvemos a abrir "docker-compose.yaml" y lo modificamos poniendo lo siguiente (No he puesto camptura ya que no salia todo el código en una captura):

```
version: '3.1'
services:
  wordpress:
    container_name: servidor_wp
    image: wordpress
    restart: always
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: user_wp
      WORDPRESS_DB_PASSWORD: asdasd
      WORDPRESS_DB_NAME: bd_wp
    ports:
      - 80:80
    volumes:
      - wordpress_data:/var/www/html/wp-content
  db:
    container_name: servidor_mysql
    image: mariadb
    restart: always
    environment:
      MYSQL_DATABASE: bd_wp
      MYSQL_USER: user_wp
      MYSQL_PASSWORD: asdasd
      MYSQL_ROOT_PASSWORD: asdasd
    volumes:
      - mariadb_data:/var/lib/mysql
volumes:
    wordpress_data:
    mariadb_data:
```
Ahora para ejecutar la aplicación ponemos de nuevo el comando "sudo docker compose up -d" y si ponemos en el navegador "http://localhost:8081" veremos que lo hemos hecho correctamente:

![image](https://github.com/user-attachments/assets/5b9ed224-d654-47b7-926b-612e6972a319)

Y si ponemos en el navegador "http://localhost:80" veremos que lo hemos hecho correctamente:

![image](https://github.com/user-attachments/assets/2c0f167c-5024-45b0-8bd9-76fa66677467)
![image](https://github.com/user-attachments/assets/ef08103e-095f-473b-8309-fb8cfc5b56df)
![image](https://github.com/user-attachments/assets/bde1e8ef-0bd3-4648-b467-efa550d25de0)
![image](https://github.com/user-attachments/assets/02dfce0b-a68a-4c1b-907c-7b2214d111fe)

#### Usando Bind Mounts
También tenemos la opción de usar Bind Mounts si en lugar del código anterior usamos este:
```
version: '3.1'
services:
  wordpress:
    container_name: servidor_wp
    image: wordpress
    restart: always
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: user_wp
      WORDPRESS_DB_PASSWORD: asdasd
      WORDPRESS_DB_NAME: bd_wp
    ports:
      - "80:80"
    volumes:
      - ./wordpress:/var/www/html/wp-content
  db:
    container_name: servidor_mysql
    image: mariadb
    restart: always
    environment:
      MYSQL_DATABASE: bd_wp
      MYSQL_USER: user_wp
      MYSQL_PASSWORD: asdasd
      MYSQL_ROOT_PASSWORD: asdasd
    volumes:
      - ./mysql:/var/lib/mysql
```
Esto lo usaremos en el caso de que queramos gestionar datos desde el sistema de archivos del host.

### IMPORTANTE

Es recomendable que cada vez que queramos hacer alguna de estas actividades o ejemplos deberemos escribir estos dos comandos para parar y eliminar los contenedores:
```
sudo docker compose down
```
```
sudo docker compose stop
```

![image](https://github.com/user-attachments/assets/b8f015d7-caec-4442-a302-318dcaa1d237)
![image](https://github.com/user-attachments/assets/c8a552a5-724f-4ab1-a044-862385fe042c)
