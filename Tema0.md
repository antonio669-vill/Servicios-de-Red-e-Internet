```diff
+ Actividad de presentación de la asignatura `#f03c15`
```
# Actividad de presentación de la asignatura `#f03c15`
# Visualiza los siguientes videos y responde a las cuestiones planteadas a continuación

## Actividad 0.1 - HTTP Introduction
## https://www.youtube.com/watch?v=eesqK59rhGA
## https://www.youtube.com/watch?v=DuSURHrZG6I

### ¿Quién, dónde y cuándo se crea el primer servidor web?

El primer servidor del mundo se creó en Ginebra,Suiza, entre 1989 y 1991 por Tim Berners-Lee con ayuda de Robert Cailliau, fue conocido como NeXTcube. 

### ¿Qué es pila de protocolos usados por http?

Son TCP e IP.

### ¿Componentes de una URL?

Una URL está compuesta de un protocolo, seguido del dominio de la página que buscamos, el puerto donde buscamos, la ruta del recurso y por último la versión.

### ¿Pasos en la recuperación de una página web mediante HTTP?

El cliente pide una función como podría ser “Get” junto con los elementos vistos en la pregunta anterior al servidor a través de internet, este en cuestión de segundos le devuelve al usuario la respuesta para poder acceder a la página que ha pedido.

### Diferencia entre páginas dinámicas y estáticas

Las páginas estáticas se mantienen iguales par todos los usuarios, sin embargo las páginas dinámicas varían en determinados aspectos en función de quién sea el usuario que en la página, la ubicación dentro de la propia página o los cambios a tiempo real que hacen sus creadores, un ejemplo de estas últimas son las redes sociales.

### ¿Cómo usar telnet para acceder a un servidor web?
### (solución en actividad 0.3)

Abrimos el cmd de Windows y escribimos telnet (el servidor) (y el puerto).

### Request. Métodos principales

Get
Head
Post
Delete
Put
Connect
Patch
Options
Trace

### Response. Códigos

100 - Respuesta de que se ha recibido la petición
200 - Not error
300 - redirección
400 - error del cliente
500 - error del servidor

### Content type. Tipos principales
text/html
## Actividad 0.2 - UDP and TCP: Comparison of Transport Protocols
## https://www.youtube.com/watch?v=Vdc8TCESIg8

### Diferencias entre udp y tcp? (min 2:46 y 4:15)

### ¿Qué aplicaciones usan tcp?  http, smtp, pop, imap, ssh?
Telnet
### ¿Qué aplicaciones usan udp?
TFTP
DNS
RPC
NCS
SNMP
### ¿Qué capa almacena el puerto?
La capa de transporte.
### ¿Qué capa almacena la dirección IP?
La capa de red (también conocida como capa de internet).
### ¿Qué es three-way handshake?
Proceso que se utiliza en una red TCP/IP para establecer una conexión entre el servidor y el cliente. Es un proceso de tres pasos que requiere que tanto el cliente como el servidor intercambién paquetes sync de sincronización y reconocimiento antes de que comience el proceso real de comunicación de datos.


Este proceso ayuda a iniciar, negociar y separar conexiones de socket TCP al mismo tiempo.








Actividad 0.3 - Práctica telnet/http
https://www.youtube.com/watch?v=xpBpGC08f4Q&t=189s
http://www.profesordeinformatica.com/servicios/http/telnet
Lee el artículo y prueba los ejemplos sugeridos en él.

Nota: Si usamos Windows 10, tenemos que activar “telnet”
http://www.lawebdelprogramador.com/foros/Windows-10/1510815-Como-activar-Telnet-en-Windows-10.html


Actividad 0.4 - Usando cUrl
https://curl.se/docs/manual.html

Busca información sobre el comando curl y muestra al menos cinco ejemplos de uso



Actividad 0.5 - Práctica servidor web
Visita los siguientes enlaces:
Simple web server (ejemplo 1)
https://docs.python.org/3/library/http.server.html
python -m http.server 8000
http server (ejemplo 2)
https://github.com/python/cpython/blob/main/Lib/http/server.py
dummy web server (ejemplo 3)
https://gist.github.com/kabinpokhrel/6fd1275603e9d5f1e284be717cbd1bff


Instala Python.
Ejecuta los ejemplos mostrados con anterioridad.
Publica en GitHub los ejemplos llevados a cabo. Los ejemplos se acompañaran con capturas de pantalla en las que se muestre su funcionamiento.


Actividad 0.5. Repositorio Github

Crea una cuenta en Github, si no la tienes ya. Crea un repositorio en Github con el nombre del módulo. El repositorio incluirá una carpeta para cada tema: “Tema0”, “Tema1”,... “TemaN” en el que incluirás las actividades que se te indiquen expresamente.
El repositorio incluirá un archivo “README” en el que se enlazaran la solución a los ejercicios incluidos en las carpetas anteriores.

La página README del repositorio debe tener un aspecto parecido al mostrado a continuaciçon:

Nombre del módulo
Este repositorio incluye actividades llevadas a cabo en el módulo nombredelmódulo


Tema 0 - Nombre tema 0
Ejercicio 1
Breve descripción 0.1
Ejercicio 2
Breve descripción 0.2
…
…


Tema 1 - Nombre tema 1
Ejercicio 1
Breve descripción 0.1
Ejercicio 2
Breve descripción 0.2
…
…








Nota: Si no has utilizado antes Github, es recomendable que cree un repositorio nuevo llamado “prueba” que incluya una página “README.md”. Utiliza markdown para que incluya varias cabeceras, texto, una lista, un gráfico y una tabla. Previamente se recomienda leer:
https://github.com/Github-Classroom-Cybros/Learn-Github
https://guides.github.com/features/mastering-markdown/

