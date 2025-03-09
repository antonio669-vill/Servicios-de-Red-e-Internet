# Subdominios

Configuramos el DNS primario modificando el archivo "named.conf.local", estando posicionados en "/etc/bind":
```
sudo nano /etc/bind/named.conf.local
```
Ponemos lo siguiente:

![image](https://github.com/user-attachments/assets/ceb1564c-3de2-4cc7-8346-93adfcee431b)

Ahora creamos el archivo "zona" usando:
```
sudo mkdir -p /etc/bind/zones
```
![image](https://github.com/user-attachments/assets/a4bfec28-734d-4b98-b7c2-9b251726029b)

Y ahora en:
```
sudo nano /etc/bind/zones/db.iesmarisma.intranet
```

Ponemos:

![image](https://github.com/user-attachments/assets/616903ff-98af-4029-9edd-284055f795a7)


Ahora tenemos que editar"named.conf.local":
```
sudo nano /etc/bind/named.conf.local
```

Y añadimos:

![image](https://github.com/user-attachments/assets/b4297a2e-bfe2-44ad-bd78-31cf553d7700)


Creamos el archivo de zona y agregamos lo siguiente:
```
sudo nano /etc/bind/zones/db.informatica.iesmarisma.intranet
```

![image](https://github.com/user-attachments/assets/5480a5a5-3f4c-4ccd-b29c-7d35af3939d7)

Ahora, si queremos delegar la gestion del subdominio arimos "db.iesmarisma.intranet":
:
```
sudo nano /etc/bind/zones/db.iesmarisma.intranet
```
Y ponemos esto:

![image](https://github.com/user-attachments/assets/50e85e18-d916-4ef7-9233-d54157258d98)

También podemos automatizarlo todo con un bash:
```
sudo nano /usr/local/bin/create_subdomain.sh
```

![image](https://github.com/user-attachments/assets/cbcc2acd-4137-4b7f-a114-57c6124b6333)

Le damos permisos:
```
sudo chmod +x /usr/local/bin/create_subdomain.sh
```
![image](https://github.com/user-attachments/assets/69d98305-082c-4567-983d-51fb0c598572)

Y comprobamos:

```
sudo /usr/local/bin/create_subdomain.sh iesmarisma.intranet informatica 192.168.2.1
```

![image](https://github.com/user-attachments/assets/b10bccf4-15d4-4fc3-b0fe-6f8235636136)

Ahora, si queremos hacer lo mismo con Python hacemos:

```
sudo nano /usr/local/bin/create_subdomain.py
```
Y ponemos:
```
import subprocess

def create_subdomain(domain, subdomain, ip):
    """Crea un archivo de zona para un subdominio y reinicia el servidor DNS."""
    zone_file = f"/etc/bind/zones/db.{subdomain}.{domain}"
    config = f"""
$TTL 604800
@   IN  SOA  ns1.{subdomain}.{domain}. admin.{subdomain}.{domain}. (
        2
        604800
        86400
        2419200
        604800 )
;
@       IN  NS  ns1.{subdomain}.{domain}.
ns1     IN  A   {ip}
www     IN  A   {ip}
ftp     IN  A   {ip}
smtp    IN  A   {ip}
"""
    
    try:
        # Escribir la configuración en el archivo de zona
        with open(zone_file, "w") as file:
            file.write(config)
        print(f"Archivo de zona creado en {zone_file}")

        # Reiniciar el servicio BIND9 para aplicar los cambios
        subprocess.run(["systemctl", "restart", "bind9"], check=True)
        print("Servidor DNS reiniciado correctamente.")
    except Exception as e:
        print(f"Error al crear el subdominio: {e}")

# Uso del script
domain = "iesmarisma.intranet"
subdomain = "informatica"
ip = "192.168.2.1"
create_subdomain(domain, subdomain, ip)
```
Le damos los permisos

```
sudo chmod +x /usr/local/bin/create_subdomain.py
```

![image](https://github.com/user-attachments/assets/0fa80947-fd6e-4428-b056-8103c008798e)

Lo comprobamos:

```
sudo python3 /usr/local/bin/create_subdomain.py
```

![image](https://github.com/user-attachments/assets/e2caf5eb-8847-48ed-bffd-f2e4adc211d1)


### 5. Verificar la configuración
Verificamos que el subdominio se ha creado:

```
dig @localhost informatica.iesmarisma.intranet
```

![image](https://github.com/user-attachments/assets/509abbeb-8b8e-4ba3-ba00-bd333f432a6e)
