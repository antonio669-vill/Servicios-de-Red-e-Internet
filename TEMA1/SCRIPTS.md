### Crea un script que añada un puerto de escucha en el fichero de configuración de Apache. El puerto se recibirá como parámetro en la llamada y se comprobará que no esté ya presente en el fichero de configuración.

1. Para comenzar, accedemos al directorio donde se encuentra la configuración de Apache
`````
cd /etc/apache2
`````
2. Y una vez dentro, procedemos a crear y editar un script que llevará a cabo las acciones necesarias. Al abrir el editor de texto, desarrollaremos el contenido correspondiente.
`````
gedit NombreScript.sh
`````
`````
#!/bin/bash

if [ $# -eq 0 ]; then
  echo 'Error'                     
else
  grep "$1" ports.conf             
                                   

  if [ $? -ne 0 ]; then            
    cp ports.conf ports.bak        
    echo "listen $1" >> ports.conf
  else
    echo 'Puerto configurado'
  fi
fi
`````
3. Tras escribir el script, ejecutamos este comando:
`````
bash NombreScript.sh NumeroPuerto
phpinfo
`````
(por ejemplo, Actividad1.sh 300)

4. Durante la ejecución si el puerto no existe, se genera una copia de respaldo del archivo de configuración antes de añadir el puerto, en el archivo llamado ports.conf
<img src="../TEMA1/Imágenes/p.png"/>
<img src="../TEMA1/Imágenes/listen.png"/>
### Crea un script que añada un nombre de dominio y una ip al fichero hosts. Debemos comprobar que no existe dicho dominio en el fichero hosts

Primero, ingresamos en el directorio donde se encuentra el archivo de configuración correspondiente. Después, creamos y editamos un script que gestionará la inclusión del dominio y la IP. En el editor de texto, redactamos las instrucciones necesarias para que el script verifique si el dominio ya está configurado y, de no estarlo, realice una copia de seguridad y lo añada al archivo.
Una vez finalizado, ejecutamos el script, comprobando que, si el dominio es nuevo, se ha realizado un respaldo del archivo y que tanto el dominio como la IP fueron añadidos correctamente. Finalmente, validamos que la operación haya tenido éxito revisando el archivo modificado.

Creación de un script para generar una página web con título, cabecera y mensaje
Accedemos al directorio destinado a gestionar los archivos y dominios web. A continuación, procedemos a crear y editar un script que automatice la creación de una página HTML. En este script, se definen parámetros como el dominio, el título de la página, el encabezado y el mensaje que contendrá.
Tras finalizar el desarrollo del script, lo ejecutamos para comprobar que la página web se genera correctamente. Si el dominio y la ubicación especificados existen, la página será creada con el formato indicado. Para verificar el resultado, accedemos al navegador utilizando la dirección adecuada y confirmamos que la página funciona como se espera.
