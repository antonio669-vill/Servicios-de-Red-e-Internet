## Paso 1: Configurar la Zona Directa
Editamos el archivo de configuración de BIND para añadir la zona directa.

```
sudo nano /etc/bind/named.conf.local
```
![image](https://github.com/user-attachments/assets/6123cf4c-232c-4bbf-8b28-9bddb8184cd9)

![image](https://github.com/user-attachments/assets/dff40a6f-1ba0-4612-84bf-057a5b8d6e80)

Creamos el archivo de zona:

```
sudo cp /etc/bind/db.local /etc/bind/db.marisma
```
```
sudo nano /etc/bind/db.marisma
```
Editamos su contenido:

![image](https://github.com/user-attachments/assets/d47051f9-16a7-449c-aef1-75cd6f3d1298)

## Paso 2: Configurar la Zona Inversa
Editamos el archivo de configuración de BIND:

```
sudo nano /etc/bind/named.conf.local
```

![image](https://github.com/user-attachments/assets/938d58ad-5b6a-4586-b7a2-fd5ea7e401e9)


Creamos el archivo de zona inversa:

```
sudo cp /etc/bind/db.127 /etc/bind/db.192
sudo nano /etc/bind/db.192
```
![image](https://github.com/user-attachments/assets/87885f3a-dc0d-46e1-9404-dc8314447e45)


## Paso 3: Reiniciar el Servidor DNS

```
sudo systemctl restart bind9
```

Verificamos la configuración:

```
sudo named-checkconf
```
![image](https://github.com/user-attachments/assets/45f95949-f61c-418b-aea3-59f4cefb8ca7)

```
sudo named-checkzone marisma.intranet /etc/bind/db.marisma
```
```
sudo named-checkzone 1.168.192.in-addr.arpa /etc/bind/db.192
```
![image](https://github.com/user-attachments/assets/1bd8fcda-9d1c-4385-8aa1-40134c8d47c1)
![image](https://github.com/user-attachments/assets/08aae687-b237-4434-b845-1c57c0d7c01a)
