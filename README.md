# Odoo--Instalacion

Primero creamos una carpeta en el escritorio para hacer el proyecto y después abrimos la carpeta desde el pyCharm. Creamos el docker-compose.yml desde el pyCharm y lo configuramos:

      version: '3.1'                                Indica la versión de fichero utilizado (3.1)
      services:                                     Indica los servicios contenerizados que se van a ejecutar (postgres y odoo)
        db:                                         Se refiere a la base de datos    
         image: postgres:13                         Indica el nombre de la imagen asociada al servicio en este caso postgres (version 13)
         environment:                               Hace referencia a la opción que permite definir variables de entorno que pueden utilizarse en el interior de los contenedores de la plataforma
          - POSTGRES_DB=postgres                    Asignamos el nombre de la Base de Datos    
          - POSTGRES_PASSWORD=odoo                  Asignamos la contraseña de la Base de Datos     
          - POSTGRES_USER=odoo                      Asignamos el usuario de la Base de Datos     
         ports:                                     Permite mapear <puerto_host> a <puerto_contenedor>
          - "5432:5432"                             Mapeamos el puerto del ordenador (5432) al del contenedor (5432)
         volumes:                                   Permite mapear elementos del sistema de archivos del interior del contenedor con elementos del sistema de archivos en el exterior
          - ./datos:/var/lib/postgresql/data        Mapeamos los archivos del contenedor a la carpeta con esta dirección: ./datos:/var/lib/postgresql/data           
        odoo:                                       Se refiere al Odoo que utilizaremos               
         image: odoo:14.0                           Indica el nombre de la imagen asociada al servicio en este caso odoo (version 14.0)                            
         container_name: dam22_odoo                 Añadimos un nombre al contenedor (dam22_odoo)                                
         ports:                                     Permite mapear <puerto_host> a <puerto_contenedor>
          - "8069:8069"                             Mapeamos el puerto 8069 de la máquina al puerto 8069 del contenedor
         depends_on:                                Nos permite que el inicio de la ejecución de un servicio dependa de otras    
          - db                                      El inicio va a depender de la base de datos        
         
Respuesta: Aclarar que si el puerto 5432 o el 8069 del ordenador (local) está ocupado por otro servicio lo podremos 
solucionar siguiendo estes pasos:
    1º- Usaremos el comando **netstat** que sirve para generar visualizaciones que muestran el estado de la red 
        y estadísticas de protocolo donde podremos encontrar si algún servicio está ejecutándose enel puerto 5432 en 
        este caso.
    2º- En la situación de que haya un servicio ocupando ese puerto tendremos que pararlo y para ello usaremos el 
        comando **service stop** entre medias escribiremos el nombre del servicio en cuestión. Por ejemplo si hay un 
        postgres ejecutándose en ese puerto haremos un **service postgres stop**, si hiciese falta privilegios solo 
        necesitariamos escribir _sudo_ antes del comando **sudo service postgres stop**.
       
Una vez hecho el docker.compose.yml lo iniciamos. Después de haberlo iniciado nos conectamos a la base de datos del postgres poninendo las creedenciales, en este caso:

![image](https://user-images.githubusercontent.com/91607146/212317497-2dac7aa7-935c-4688-9298-77963f81ea56.png)
![image](https://user-images.githubusercontent.com/91607146/212642426-12ced54c-ce72-495b-8581-14683e8be531.png)


Después de tener la conexión hecha con la base datos procedemos a la instalación del oddo. Para ello pondremos localhost:8069 (dónde _8069_ es el puerto del odoo que pusimos en el docker-compose)

![image](https://user-images.githubusercontent.com/91607146/213925736-1d42e527-3590-471f-8239-d898c5940abc.png)

Una vez aquí solo tendremos que rellenar los campos que necesita el odoo y darle a "create database".
![image](https://user-images.githubusercontent.com/91607146/213925887-498644c8-a161-4404-891b-146490e26381.png)

Y ya tendríamos el **Odoo**!!
