MODELO USUARIO:
===============

En este modelo se declaran cada uno de los atributos requeridos de un usuario.

.. code-block::
   
   export class Usuario { //creamos el usuario con los atributos requeridos
    nombres?:string;
    apellidos?: string;
    cc?: number;
    email?: string;
    fecha?: Date;
    direccion?: string;
    departamento?:string;
    ciudad?: string;
    pais?: string;
    codigo_postal?: number;
    profesion?: string[];
    habilidades?: string[];
    descripcion?: string;
    urlImagen?:string;
    }

Este modelo es necesario para su uso en varios Modulos como Mi Perfil, Registro y Registros, donde son creados, listados y editados.