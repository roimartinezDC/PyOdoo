# PyOdoo

## Crear entorno de desarrollo Odoo

  * Lo primero es crear un proyecto en un IDE, en este caso PyCharm.
  * Lo siguiente es crear un fichero ``docker-compose.yml``
  * Para crear un contenedor odoo + postgresql, en el docker-compose:
      * Declarar un servicio de odoo, con un pull de la imagen oficial, 
        y mapeando el puerto en el que se va a levantar.
      * Declarar el servicio de la base de datos, con un pull de la imagen 
        oficial de postgres, y mapeando el puerto que va a utilizar. También 
        se puede configurar el enviroment, como es en nuestro caso.
  * Para la configuración de odoo y el desarrollo de módulos, se mapea mediante
    un volumen, el directorio de los archivos de la bd en el entorno virual, a 
    un directorio en nuestro equipo. Entorno de Desarrollo con Visual Code
  * Una vez terminado el _docker-compose_, para levantar el repositorio haríamos 
    un ``docker-compose.yml up``

### Acceso a la BD desde PyCharm

Para acceder a la base de datos desde el IDE PyCharm:

1. Dirigirse a la pestaña _Database_ situada en el panel lateral derecho.
2. Darle al ``+`` > _Data Source_ > _PostgreSQL_
3. Se nos abrirá una ventana para realizar la conexión, y la rellenamos con los
   credenciales de acceso a la bd.
4. Al darle a ``Aplicar`` se nos abrirá la conexión a la bd en la tabla de _*Databases*_


## Entorno de Desarrollo con Visual Code

 * Para levantar Odoo con el docker-compose, el proceso es exactamente igual al que 
   explico arriba.
  
 * Una vez esté levantado y corriendo el Odoo, iremos a la tabla de la extensión de Docker en Visual Code.
   Allí pincharemos con el click derecho sobre el contenedor del servicio de odoo, y le daremos a _"Attach Shell"_,
   esto nos abrirá una terminal dentro del entorno virutal del propio Odoo.
   
### Creación de un módulo
   
 * Una vez en el entorno del odoo, vamos a crear la estructura del módulo. Para esto nos desplazaremos al directorio _"extra-addons"_:
   ``cd /mnt/extra-addons``, y una vez allí ejecutaremos el siguiente comando ``odoo scaffold dam21``, "dam21" es el nombre que le vamos
   a dar al módulo.
   
 * Al hacer esto, si mediante la interfaz del Code nos desplazamos a la carpeta "Files"(es el directorio raiz de Odoo) dentro del odoo, 
   y vamos a _/mnt/extra-addons_, veremos que se ha creado una carpeta llamada "dam21", y dentro de esta hay una serie de documentos.
   
    * Dentro de estos documentos destacan los archivos ___\_\_init\_\_.py___ y ___\_\_manifest\_\_.py___, ___init.py___ simplemente
      importa los archivos de los directorios _models_ y _controller_ y los lanza al inicarse el módulo.
      
    * ___\_\_manifest\_\_.py___, incluye toda la información del módulo que va a aparecer en la tienda de aplicaciones de Odoo, cuando vayamos
      a instalar el módulo. Aquí podemos modificar cosas para personalizarlo a nuestro gusto.
      
  * Si hacemos cambios en algún archivo dentro del repositorio del módulo, tendremos que hacer que este se actualice para que se puedan ver 
    reflejados los cambios en Odoo. Esto se hace mediante el siguiente comando:
    
    `odoo -u dam21 -d odoo --db_host=db -r odoo -w odoo`
    
     - `-u`: update
     - `-d`: nombre de la base de datos
     - `--db_host`: IP de la base de datos
     - `-r`: usuario para la bd
     - `-w`: contraseña para la bd
   
