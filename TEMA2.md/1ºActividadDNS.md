# Caching & Fordwarding

## **BIND9**
Empezamos actualizando los paquetes para posterriormente instaalar BIND9 con los siguientes comando:

```
sudo apt update
sudo apt upgrade
```
```
sudo apt install bind9 -y
```
![image](https://github.com/user-attachments/assets/9ec12298-3a78-41ca-9632-ee708fe018a4)

Para ejecutarlo usando comando:
```
sudo systemctl start bind9
sudo systemctl enable bind9
```
Y verificamos que el servicio está activo con:
```
systemctl status bind9
```
![image](https://github.com/user-attachments/assets/3645a5f0-d462-4bc0-9a4f-0e70dd37144c)


Ahora configuraremos bind9 abriendo el archivo y cambiando su contenido por el que se vé en la captura:
```
sudo nano /etc/bind/named.conf.options
```
![image](https://github.com/user-attachments/assets/5c3f480a-dd73-4339-ba08-6bf1de3dcf56)

Y reiniciamos bind9:
```
sudo systemctl restart bind9
```

(Si queremos verificar que funciona haremos un "nslookup google.com 127.0.0.1" a google)

![image](https://github.com/user-attachments/assets/cd6bcf99-6c41-47c8-a612-f01f77f4f29b)

## **Configurar como Servidor Forwarding**

Ahora debemos editar de nuevo el archivo con el comando:
```
sudo nano /etc/bind/named.conf.options
```
Y poner lo siguiente:

![image](https://github.com/user-attachments/assets/b234213b-2281-44b7-a541-52b645354117)

Reiniciamos.
```
sudo systemctl restart bind9
```

Y realizamos una consulta para comprobarlo:
```
nslookup facebook.com 127.0.0.1
```
Si devuelve una IP correctamente, el servidor está funcionando.
