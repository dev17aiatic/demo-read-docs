MÓDULO DE HOME:
===============

Este módulo se crea con el fin de que sea la primera página del aplicativo web, y también es el módulo al cual se redirecciona cuando la url no coincide con alguna extensión.


Estructura :
^^^^^^^^^^^^

.. image :: ../images/inicioDoc01.png
Esta es la estructura de archivos que se encuentra dentro del módulo de home. Los archivos como Home.Component.ts, home.routing.module y demás archivos que hacen parte de la estructura, no se muestran ya que no se modifican y se mantienen tan cuál se crean desde el Angular CLI




.. image :: ../images/inicioDoc02.png

En el home.module.ts, se exportan todas las librerias necesarias para construir lo requerido en el diseño.


.. image :: ../images/inicioDoc03.png
Este el home.component.html creamos un contenedor el cuál tendrá las dos tarjetas en las cuales se presentarán a los dos developers,
conteniendo el logo de la UNAB y su respectivo logo.

.. code-block::

   .sectCont{
    text-align: center;
    height: 100hv;
    }
   .stuCont{
     display: inline-flex;
     justify-content: center;
     align-items: center;
   //height: 100hv;
     }
   .container{
     margin: auto;
     margin-bottom: 0;}
   .logo{
    margin-bottom: 25px;
    margin-top: 35px;}

  .carda{
    text-align: center;
    width: 350px;
    height: 330px;
    //margin-left: 300px;
    color: black;
    background: inherit;
    border: 1px solid;
    padding: 10px;
    box-shadow: 5px 10px 8px 10px #888888;  }

  .cardb{
    width: 350px;
    height: 330px;
    //margin-left: 755px;
    text-align: center;
    color: black;
    background: inherit;
    border: 1px solid;
    padding: 10px;
    box-shadow: 5px 10px 8px 10px #888888;  }
  .imgResp{
    margin-top: 5px; width:200px;height:180px;  }




  @media screen and (max-width: 880px)
  {
    .sectCont{
      width: 55vw;
      display: block;
      margin: auto;
      margin-bottom: 2em;
    }
    .imgResp{
      width: 100;
      height: 100;
    }

    .stuCont{
      max-width: 55vw;
      margin-bottom: 2em;
      height: auto;
      margin: auto;
      display: block;
    }

    .container{
      position: relative;
      float: none;
      width: auto;
      height: auto;
    }
    .carda{width: 55vw;
      height: auto;
      display: block;
      margin: auto;
      margin-bottom: 3em;}
    .cardb{width: 55vw;
      display: block;
      margin: auto;
      height: auto;
      margin-bottom: 3em;}
  }
  .logo{
    max-height: auto;
    max-width: auto;
  }

Este es el Home.component.scss en el cual centramos nuestro contenido, le damos los shadows a cada uno de los cards creados, fijamos su tamaño, el borde y las reglas de la responsividad, en donde arreglamos cada uno de las cartas para que se acomoden una debajo de la otra con el mismo estilo y tamaño


 







