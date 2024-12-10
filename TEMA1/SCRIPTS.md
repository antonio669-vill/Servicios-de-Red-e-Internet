### Creación de un script para añadir un puerto de escucha en la configuración de Apache
Para comenzar, accedemos al directorio donde se encuentra la configuración de Apache
cd /etc/apache2
Y una vez dentro, procedemos a crear y editar un script que llevará a cabo las acciones necesarias. Al abrir el editor de texto, desarrollamos el contenido correspondiente.
Tras escribir el script, ejecutamos el comando necesario, asegurándonos de estar posicionados correctamente en el sistema. Durante la ejecución, verificamos que, si el puerto no existe, primero se genera una copia de respaldo del archivo de configuración antes de añadir el puerto. Por último, revisamos el archivo para confirmar que la nueva configuración se haya aplicado exitosamente.

Elaboración de un script para añadir un dominio y una IP al archivo hosts
Primero, ingresamos en el directorio donde se encuentra el archivo de configuración correspondiente. Después, creamos y editamos un script que gestionará la inclusión del dominio y la IP. En el editor de texto, redactamos las instrucciones necesarias para que el script verifique si el dominio ya está configurado y, de no estarlo, realice una copia de seguridad y lo añada al archivo.
Una vez finalizado, ejecutamos el script, comprobando que, si el dominio es nuevo, se ha realizado un respaldo del archivo y que tanto el dominio como la IP fueron añadidos correctamente. Finalmente, validamos que la operación haya tenido éxito revisando el archivo modificado.

Creación de un script para generar una página web con título, cabecera y mensaje
Accedemos al directorio destinado a gestionar los archivos y dominios web. A continuación, procedemos a crear y editar un script que automatice la creación de una página HTML. En este script, se definen parámetros como el dominio, el título de la página, el encabezado y el mensaje que contendrá.
Tras finalizar el desarrollo del script, lo ejecutamos para comprobar que la página web se genera correctamente. Si el dominio y la ubicación especificados existen, la página será creada con el formato indicado. Para verificar el resultado, accedemos al navegador utilizando la dirección adecuada y confirmamos que la página funciona como se espera.
