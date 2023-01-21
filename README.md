# Odoo--Instalacion

Primero creamos una carpeta en el escritorio para hacer el proyecto y después abrimos la carpeta desde el pyCharm. Creamos el docker-compose.yml desde el pyCharm y lo configuramos:

      version: '3.1'
      services:
        db:
         image: postgres:13
         environment:
          - POSTGRES_DB=postgres
          - POSTGRES_PASSWORD=odoo
          - POSTGRES_USER=odoo
         ports:
          - "5432:5432"
         volumes:
          - ./datos:/var/lib/postgresql/data
        odoo:
         image: odoo:14.0
         container_name: dam22_odoo
         ports:
          - "8069:8069"
        depends_on:
          - db
         
         
       
Una vez hecho el docker.compose.yml lo iniciamos. Después de haberlo iniciado nos conectamos a la base de datos del postgres poninendo las creedenciales, en este caso:

![image](https://user-images.githubusercontent.com/91607146/212317497-2dac7aa7-935c-4688-9298-77963f81ea56.png)
![image](https://user-images.githubusercontent.com/91607146/212642426-12ced54c-ce72-495b-8581-14683e8be531.png)

