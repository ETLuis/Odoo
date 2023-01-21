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
 