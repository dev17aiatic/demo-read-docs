Manual de usuario
===================


Principales requisitos para la página web 
----------------------------------------

- Acceso a internet

- Navegador que soporte HTML5

- Habilitación y aceptación de uso de cookies para la página web


Características de la página web
---------------------------------

* La página se encuentra desarrollada en Angular10, lenguaje TypeScript

* Estilos usados con SCSS

* Hosting en web app de Firebase By Google

* Base de datos en la nube usando Firebase Cloud

* Uso del Storage ofrecido por Firebase-Storage

Modo de uso
------------

1. Barra de  navegación
''''''''''''''''''''''

.. image :: ../images/navbarweb.JPG
Barra de navegación para aplicación web


.. image :: ../images/navbarmovil.JPG
Barra de navegación para aplicación móvil

        En la barra de navegación se encuentra un diseño responsivo, de colores en gradiente de anaranjado a blanco. Para aplicación web se encuentra el logo del equipo en la esquina  superior izquierda la cual permite activar el menú de navegación y en el centro un menú con las pestañas de información a cerca de la página web. 
        Para aplicación móvil el logo se encuentra centrado y se añade un "botón menú" en la parte superior izquierda, que permite acceder al menú de navegación y un "botón menú" en la parte superior derecha que permite acceder al menú de información a cerca de la página web.

2. Menú de navegación lateral
''''''''''''''''''''

.. image :: ../images/menu.JPG
Menú de navegación lateral

        El menú de navegación permite de una manera practica ver y acceder a las funcionalidades de la página, en ella encontramos el logo del equipo que permite desplazarnos a la página principal, los ítems de  registro, iniciar sesión y video para el caso de no haber iniciado sesión, y cuando se ha iniciado sesión se muestran los ítems de registros, perfil, video y salir

#. Registros
#. Perfil
#. Video
#. Salir


3. Menú de información
''''''''''''''''''''''

.. image :: ../images/menuinfo.JPG
Menú de información para aplicación web

.. image :: ../images/menuinfomovil.JPG
Menú de información para aplicación móvil

        El menú de información permite con su ítem "Inicio" dirigirse a la página principal de la aplicación, con su segundo ítem "Equipo" acceder a una breve biografía a cerca de los desarrolladores y con su tercer ítem redirige a la página de contacto, que pondrá en contacto directo con los desarrolladores, de alguna queja, reclamo, sugerencia o felicitación que se desee enviar al correo ceo@aiatic.com.


4. Conocer la página principal
'''''''''''''''''''''''''''''''

.. image :: ../images/home.JPG
Página principal


        La página principal presenta el logo del equipo Marvel, centrado, debajo de este se encuentran las fotos, nombres y cargos de los desarrolladores, debajo se encuentra el logo de la universidad donde están realizando sus estudios, como realización de este proyecto para las prácticas 2020.



5. Equipo
'''''''''''''

.. image :: ../images/equipo.JPG
Página de equipo


        La página de equipo muestra en tarjetas las fotos de los desarrolladores, junto con una breve autobiografía y descripción de ellos



6. Contacto
'''''''''''

.. image :: ../images/contacto.JPG
Página de contacto

        La página de contacto permite contactar al equipo de desarrollo, cuenta con un diseño de un formulario en la primera mitad de la pantalla y una imagen de agradecimiento por contactarnos al lado derecho, la imagen no está disponible para la versión responsive, en el momento que se rellenen los campos con la información requerida se habilitará el botón "enviar", que permitirá el envió directo de la información al correo ceo@aiatic.com.
   

7. Realizar el registro
''''''''''''''''''''''''

.. image :: ../images/registro.JPG
Página de Registro

        Para iniciar el proceso de registro, podemos acceder desde el menú de navegación, dando clic al ítem Registro, se deben proporcionar los datos en los campos requeridos, se permite máximo un registro por cédula de ciudadanía y correo electrónico. Una vez se haya finalizado de rellenar todos los campos, se habilitará el botón de registrarse, al dar clic sobre  este, se notificara si el registro fue exitoso o si ha ocurrido algún error.


8. Iniciar sesión
'''''''''''''''''

.. image :: ../images/loginweb.JPG 
Página web de inicio de sesión

.. image :: ../images/loginmovil.JPG
Página móvil de inicio de sesión

        Una vez realizado un registro exitoso, se puede iniciar sesión en la aplicación, en el menú, dando clic al ítem iniciar sesión, donde es necesario proporcionar el correo y dar clic en el botón "INICIAR SESIÓN", posteriormente se enviara un link al correo electrónico suministrado que permitirá acceso a las otras funciones de la página.


9. Video
''''''''

.. image :: ../images/videoweb.JPG
Página web de  video

        En esta página se encuentra un video de YouTube, este video puede variar cada cierto tiempo y serán de música que le agrada a los desarrolladores


10. Registros
''''''''''''
.. image :: ../images/registros.JPG
Página web de registros


        Para acceder a esta página, es necesario haber iniciado sesión, se encuentra información a cerca de todos los usuarios registrados en la base de datos. 
        Los datos se muestran en una tabla, los títulos de cada columna describen el dato a mostrar y cada fila detalla la información asociada de cada usuario

11. Mi perfil
''''''''''''

.. image :: ../images/perfilweb.JPG
Página web de perfil


        Para acceder a esta página es necesario haber iniciado sesión, se encuentra la información del usuario actual, adicional a esto se encuentra una foto de perfil por defecto si es la primera vez que se inicia sesión. En la parte inferior se encuentra un botón de editar, el cual te permitirá editar todos los campos incluyendo la foto de perfil, como se muestra a continuación:

.. image :: ../images/editarweb.JPG
página web de editar perfil

        Al dar clic en "CAMBIAR IMAGEN" se abrirá un explorador de archivos, donde permite seleccionar la foto por la que se desea cambiar, (se permiten fotos de máximo 1MB), si el archivo es exitoso el recuadro de la foto tomara un "check" verde (la nueva foto la podras ver en el momento de guardar los cambios), también se permite actualizar otros datos a excepción del correo electrónico, una vez finalizado esto en la parte inferior se habilitará un botón de guardar cambios o estará el botón de descartar cambios (también se pueden descartar los cambios cierran el diálogo dando clic afuera o con la tecla salir) 

12. Salir
''''''''

        Este ítem del menú de navegación solo está disponible al haber iniciado sesión, al dar clic permite cerrar la sesión actual de la aplicación
