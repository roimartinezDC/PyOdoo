# PyOdoo

## Crear entorno de desarrollo Odoo

  * Lo primero es crear un proyecto en un IDE, en este caso PyCharm.
  * Lo siguiente es crear un fichero ``docker-compose.yml``
  * Para crear un contenedor odoo + postgresql:
      * Declarar un servicio de odoo, con un pull de la imagen oficial, 
        y mapeando el puerto en el que se va a levantar.
      * Declarar el servicio de la base de datos, con un pull de la imagen 
        oficial de postgres, y mapeando el puerto que va a utilizar. También 
        se puede configurar el enviroment, como es en nuestro caso.
  * Para la configuración de odoo y el desarrollo de módulos, se mapea mediante
    un volumen, el directorio de los archivos de la bd en el entorno virual, a 
    un directorio en nuestro equipo.

### Acceso a la BD desde PyCharm

Para acceder a la base de datos desde el IDE PyCharm:

1. Dirigirse a la pestaña _Database_ situada en el panel lateral derecho.
2. Darle al ``+`` > _Data Source_ > _PostgreSQL_
3. Se nos abrirá una ventana para realizar la conexión, y la rellenamos con los
   credenciales de acceso a la bd.
4. Al darle a ``Aplicar`` se nos abrirá la conexión a la bd en la tabla de _*Databases*_

