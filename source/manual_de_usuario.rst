Manual de usuario
===================


Principales requisitos para la pagina web 
----------------------------------------

- Acceso a internet

- Navegador que soporte HTML5

- Habilitación y aceptación de uso de cookies para la pagina web


Caracteristicas de la pagina web
---------------------------------

* La pagina se encuentra desarrollada en Angular10, lenguaje TypeScript

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
Barra de navegación para aplicacion movil

        En la barra de navegación se encuentra un diseño responsivo, de colores en gradiente de anaranjado a blanco. Para aplicación web se encuentra el logo del equipo en la esquina  superior izquierda la cual permite activar el menu de navegación y en el centro un menú con las pestañas de información a cerca de la pagina web. 
        Para aplicación movil el logo se encuentra centrado y se añade un "botón menu" en la parte superior izquierda, que permite acceder al menu de navegación y un 'botón menu" en la parte superior derecha que permite acceder al menu de información a cerca de la pagina web.

2. Menu de navegación lateral
''''''''''''''''''''

.. image :: ../images/menu.JPG
Menu de navegación lateral

        El menu de navegacion permite de una manera practica ver y acceder a las funcionalidades de la pagina, en ella encontramos el logo del equipo que permite desplazarnos a la pagina principal, los items de  registro, iniciar sesión y video para el caso de no haber iniciado sesión, y cuando se ha iniciado sesión se muestran los items de registros, perfil, video y salir

#. Registros
#. Perfil
#. Video
#. Salir


3. Menu de información
''''''''''''''''''''''

.. image :: ../images/menuinfo.JPG
Menu de información para aplicación web

.. image :: ../images/menuinfomovil.JPG
Manu de información para aplicación movil

        El menú de información permite con su item "Inicio" dirigirse a la pagina primcipal de la aplicación, con su segundo itemd "Equipo" acceder a una breve biografia a cerca de los desarrolladores y con su tercer item redirige a la pagina de contacto, que pondra en contacto directo con los desarrolladores, de alguna queja, reclamo, sugerencia o felicitación que se desee enviar al correo ceo@aiatic.com.


4. Conocer la pagina principal
'''''''''''''''''''''''''''''''

.. image :: ../images/home.JPG
Pagina principal


        La pagina principal presenta el logo del equipo Marvel, centrado, debajo de este se encuentran las fotos, nombres y cargos de los desarrolladores, debajo se encuentra el logo de la universidad donde estan realizando sus estudios, como realización de este proyecto para las Practicas 2020.



5. Equipo
'''''''''''''

.. image :: ../images/equipo.JPG
Pagina de equipo


        La pagina de equipo muestra en tarjetas las fotos de los desarrolladores, junto con una breve autobiografia y descripción de ellos



6. Contacto
'''''''''''

.. image :: ../images/contacto.JPG
Pagina de contacto

        La pagina de contacto permite contactar al equipo de desarrollo, cuenta con un diseño de un formulario en la primera mitad de la pantalla y una imagen de agradecimeinto por contactarnos al lado derecho, la imagen no esta disponible para la versión responsive, en el momento que se rellenen los campos con la información requerida se habilitara el boton "enviar", que permitira el envio directo de la información al correo ceo@aiatic.com.
   

7. Realizar el registro
''''''''''''''''''''''''

.. image :: ../images/registro.JPG
Pagina de Registro

        Para iniciar el proceso de registro, podemos acceder desde el menu de navegación, dando click al iteme Registro, se deben proporcionar los datos en los campos requeridos, se permite maximo un registro por cedula de ciudadania y correo electronico, una vez se haya finalizado de rellenar todos los campos, se habilitara el boton de registrarse, al dar clic sobre  este, se notificara si el registro fue exitoso o si ha ocurrido algun error.


8. Iniciar sesión
'''''''''''''''''

.. image :: ../images/loginweb.JPG 
Pagina web de inicio de sesión

.. image :: ../images/loginmovil.JPG
Pagina movil de inicio de sesión

        Una vez realizado un registro exitoso, se puede iniciar sesión en la aplicación, en el menu, dando click al item iniciar sesión, donde es necesario proporcionar el correo y dar clic en el botón "INICIAR SESIÓN", posteriormente se enviara un link al correo electronico suministrado que permitira acceso a las otras funciones de la pagina.


9. Video
''''''''

.. image :: ../images/videoweb.JPG
Pagina web de  video

        En esta pagina encontraras un video de YouTube, este video puede variar cada cierto tiempo y serán de musica que le agrada a los desarrolladores


10. Registros
''''''''''''
.. image :: ../images/registros.JPG
Pagina web de registros


        Para acceder a esta pagina, es necesario haber iniciado sesión, se encuentra información a cerca de todos los usuarios registrados en la base de datos. 
        Los datos se muestran en una tabla, los titulos de cada columna describen el dato a mostrar y cada fila detalla la información asociada de cada usuario

11. Mi perfil
''''''''''''

.. image :: ../images/perfilweb.JPG
Pagina web de perfil


        Para acceder a esta pagina es necesario haber iniciado sesión, se encuentra la informacion del usuario actual, adicional a esto se encuentra una foto de perfil por defecto si es la primera vez que se inicia sesión. En la parte inferior se encuentra un boton de editar, el cual te permitira editar todos los campos incluyendo la foto de perfil, como se muestra a continuación:

.. image :: ../images/editarweb.JPG
Pagina web de editar perfil

        Al dar click en "CAMBIAR IMAGEN" se abrira un explorador de archivos, donde permite seleccionar la foto por la que se desea cambiar, (se permiten fotos de maximo 1MB), si el archivo es exitoso el recuadro de la foto tomara un "check" verde (la nueva foto la podras ver en el momento de guardar los cambios), tambien se permite actualizar otros datos a excepción del correo electronico, una vez finalizado esto en la parte inferior se habilitara un boton de guardar cambios o estara el boton de descartar cambios (tambien se pueden descartar los cambios cerran el dialogo dando click afuera o con la tecla salir) 

12. Salir
''''''''

        Este item del menu de navegación solo esta disponible al haber iniciado sesión, al dar click permite cerrar la sesión actual de la aplicación
