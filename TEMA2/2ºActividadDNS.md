## Paso 1: Configurar la Zona Directa
Abrimos el archivo de configuración de BIND con este comando:

```
sudo nano /etc/bind/named.conf.local
```
![image](https://github.com/user-attachments/assets/6123cf4c-232c-4bbf-8b28-9bddb8184cd9)

Y ponemos lo siguiente:

![image](https://github.com/user-attachments/assets/dff40a6f-1ba0-4612-84bf-057a5b8d6e80)

Nos posicionamos:
```
sudo cp /etc/bind/db.local /etc/bind/db.marisma
```
Ahora creamos el archivo de zona con el comando:
```
sudo nano /etc/bind/db.marisma
```
Por último, añadimos:

![image](https://github.com/user-attachments/assets/d47051f9-16a7-449c-aef1-75cd6f3d1298)

Ahora tendremos que configurar la zona inversa, para ello abrimos el comando:

```
sudo nano /etc/bind/named.conf.local
```
Ponemos lo siguiente:

![image](https://github.com/user-attachments/assets/938d58ad-5b6a-4586-b7a2-fd5ea7e401e9)

Y creamos el archivo de zona inversa con estos comandos:

```
sudo cp /etc/bind/db.127 /etc/bind/db.192
```
```
sudo nano /etc/bind/db.192
```

Y lo modificamos añadiendo lo siguiente:

![image](https://github.com/user-attachments/assets/87885f3a-dc0d-46e1-9404-dc8314447e45)

Reiniciamos:

```
sudo systemctl restart bind9
```

Verificamos con:

```
sudo named-checkconf
```
```
sudo named-checkzone marisma.intranet /etc/bind/db.marisma
```
```
sudo named-checkzone 1.168.192.in-addr.arpa /etc/bind/db.192
```
![image](https://github.com/user-attachments/assets/45f95949-f61c-418b-aea3-59f4cefb8ca7)
![image](https://github.com/user-attachments/assets/1bd8fcda-9d1c-4385-8aa1-40134c8d47c1)
![image](https://github.com/user-attachments/assets/08aae687-b237-4434-b845-1c57c0d7c01a)

Ahora nos vamos a una máquina cliente y editamos el archivo de resolución DNS poniendo:

```
sudo nano /etc/resolv.conf
```

Y añadiendo "nameserver 192.168.1.1" y cuando guardemos y cerremos el archivo escribimos lo siguiente:
```
DNS=192.168.1.1
Domains=marisma.intranet
```
![image](https://github.com/user-attachments/assets/ec56ceae-4117-458e-b9c6-5f3c2a6f9a3a)

Reiniciamos:

```
sudo systemctl restart systemd-resolved
```

![image](https://github.com/user-attachments/assets/51c0cb65-28ce-4dfd-84ee-cc8e79157609)


Desafortunadamente no he conseguido hacer que se resuelva el dominio pese a que he seguido los pasos, espero y no sea un inconveniente muy grave parala nota.

```
dig @192.168.1.1 marisma.intranet
```

![image](https://github.com/user-attachments/assets/198103c6-2427-4a10-9bb3-dbc12af862f5)
