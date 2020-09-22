COMPONENTE RECORDS
==================

Nuestro componente de records está construido para recorrer todos los objetos que se encuentren dentro de nuestra base de datos para después listarlos en una gran tabla reponsiva.

.. code-block::

 


      <div class="container">
      <table class="table">
        <tr>
          <th>Nombre</th>
          <th>Apellidos</th>
          <th>Cedula de Ciudadania</th>
          <th>Email</th>
          <th>Fecha Nacimiento</th>
          <th>Direccion</th>
          <th>Departamento</th>
          <th>Ciudad</th>
          <th>País</th>
          <th>Postal</th>
          <th>Profesion</th>
          <th>Habilidades</th>
          <th>Descripcion</th>
        </tr>
        <tr *ngFor="let user of usuarios">
          <td>{{ user.nombres }}</td>
          <td>{{ user.apellidos }}</td>
          <td>{{ user.cc }}</td>
          <td>{{ user.email }}</td>
          <td>{{ user.fecha.seconds * 1000 | date: "dd/MM/yyyy" }}</td>
          <!--Acá tira un error permanente
            , sin embargo .seconds*1000 es necesaria para transformar el time stamp en tipo date -->
          <td>{{ user.direccion }}</td>
          <td>{{ user.departamento }}</td>
          <td>{{ user.ciudad }}</td>
          <td>{{ user.pais }}</td>
          <td>{{ user.codigo_postal }}</td>
          <td>{{ user.profesion }}</td>
          <td>{{ user.habilidades }}</td>
          <td>{{ user.descripcion }}</td>
        </tr>
      </table>
      </div>

Los estilos de nuestro componente esta definidos por las siguientes reglas de scss.

.. code-block::

      table, th, td {
        border: 1px solid gray;
        border-collapse: collapse;
        padding: 6px 6px 6px 6px 28px ;
      }
      th, td {
        padding: 15px;
      }
      td{
        letter-spacing: 1px;
      }
      th {
        text-align: center;
        letter-spacing: 2px;
      }

      .container{
        overflow-x: auto;
      }

      .table{
        text-align: center;
        background: linear-gradient(#f8bd6f,#EED7B0);
        border-radius: 10px;
        width: 100%;
        border-collapse: collapse;
        border: 3px solid gray;

        font-size:16px solid;

      }


      @media only screen and (max-width: 760px),
      (min-device-width: 768px) and (max-device-width: 1024px){

        table, thead, tbody, th, td, tr {
          position: relative;
          max-width: auto;
          max-height: auto;
        }


      }


Una vez definida todas nuestras reglas de responsividad y estilo. vamos a nuestra parte lógica en donde traemos y listamos a todos los usuarios.

.. code-block::

      export class RecordsComponent implements OnInit {

        usuarios: Usuario[] =[];

        constructor(public dataAPi: DataBaseService){}


        async ngOnInit() {
          (await this.dataAPi.obtenerUsuarios()).subscribe(
            user=>{
            console.log('user' , this.usuarios=user);
          });
          
        }

Podemos observar la creación de un objeto de tipo Usuario definido como un array de datos, en nuestro ngOnInit, hacer la llamada de nuestros datos gracias al servicio de la base de datos, del cuál sale nuestro método obtener usuarios.

