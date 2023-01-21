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
         
         
       
Una vez hecho el docker.compose.yml lo iniciamos. Después de haberlo iniciado nos conectamos a la base de datos del postgres poninendo las creedenciales, en este caso:

![image](https://user-images.githubusercontent.com/91607146/212317497-2dac7aa7-935c-4688-9298-77963f81ea56.png)
![image](https://user-images.githubusercontent.com/91607146/212642426-12ced54c-ce72-495b-8581-14683e8be531.png)

