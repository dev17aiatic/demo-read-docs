MÓDULO PERFIL
==============


En el módulo de perfil se encuentra la plantilla, los métodos y demás componentes que permitirán al usuario entrar a una sección de nuestro home llamada Mi Perfil en el cual, encontraremos una foto del usuario loggeado & la información del usuario que se encuentra loggeado en ese instante, al fodo de este formulario, encontramos un botón de editar que desplegará un gran modal con los campos de nuestro formulario abiertos para poder ser modificados por el usuario, esto incluye la funcionalidad de poder actualizar la foto y demás datos que el usuario considere pertinentes de modificar.

El diseño del html para este componente está diseñada y construida bajo el siguiente bloque de código.



::

   <div class="container">
     <form [formGroup]="perfilForm" class="formxD">
       <h1 style="color: Black; text-align: center; margin-top: 20px">
         PERFIL DE USUARIO
        </h1>

      <div class="card-body">
        <div class="contImg">
          <img class="profPic"
        src="{{imgurl}} | async"
        alt="unabProfile">
      </div>
        <div class="cont1">
          <label class="label">Nombre:</label>
          <mat-form-field
          appearance="outline"
          style="text-align: center"
          class="formItem">
          <input
            formControlName="nombre"
            type="text"
            matInput
            placeholder="Nombre{p.ej. Juan, José, Maria}"
            required
          />
        </mat-form-field>


        <label class="label2">Apellidos:</label>
        <mat-form-field
        appearance="outline"
        class="formItem">


          <input
            formControlName="apellido"
            type="text"
            matInput
            placeholder="{p.ej. Rey, Reyes, Zapata}"
            required
            value="{{users?.apellidos}}"
          />
        </mat-form-field>


      <p>
        <label class="label">Número de cédula:</label>
        <mat-form-field appearance="outline" class="formItem">
          <input
            formControlName="cc"
            class="numberCc"
            type="number"
            matInput
            placeholder="Cedula{p.ej. 1098457869}"
            required

          />
        </mat-form-field>

        <label class="label2">Correo Electrónico:</label>
        <mat-form-field
          appearance="outline"
          class="formItem"
          style="text-align: center"
        >
          <input
            formControlName="email"
            type="email"
            matInput
            placeholder="email {p.ej.  personxx@hotmail.com}"
            required

          />
        </mat-form-field>
      </p>

      <p>
        <label class="label">Fecha de nacimiento:</label>
        <mat-form-field appearance="outline" class="formItem">
          <input
            matInput
            formControlName="fechaN"
            required
            placeholder= "Fecha {p.ej. 30 / 12 / 2020}"
          />
       <!-- <mat-datepicker-toggle
            matSuffix
            [for]="picker"
          ></mat-datepicker-toggle>
          <mat-datepicker #picker></mat-datepicker>-->
        </mat-form-field>

        <label class="label2">Dirección:</label>
        <mat-form-field appearance="outline" class="formItem">
          <input
            formControlName="direccion"
            type="text"
            matInput
            placeholder="Dirección{cra 3 # 12-68}"
            required
          />
        </mat-form-field>
      </p>
      <p>
        <label class="label">Ciudad:</label>
        <mat-form-field appearance="outline" class="formItem">
          <input
            formControlName="ciudad"
            type="text"
            matInput
            placeholder="Ciudad {Bucaramanga, Bogotá, Lima}"
            required
          />
        </mat-form-field>

        <label class="label2">Departamento:</label>
        <mat-form-field appearance="outline" class="formItem">
          <input
            formControlName="dept"
            type="text"
            matInput
            placeholder="Departamento {Santander, Cundinamarca}"
            required
          />
        </mat-form-field>
      </p>

      <p>
        <label class="label">País:</label>
        <mat-form-field appearance="outline" class="formItem">
          <input
            formControlName="pais"
            type="text"
            matInput
            placeholder="País {Indonesia, Colombia}"
            required
          />
        </mat-form-field>

        <label class="label2">Código Postal:</label>
        <mat-form-field appearance="outline" class="formItem">
          <input
            formControlName="postal"
            type="number"
            matInput
            placeholder="Postal{p.ej. 13425}"
            required
          />
        </mat-form-field>
      </p>
      <label
          >Profesiones:</label>

      <div class="card-body">
        <div
          class="profesiones"
          style="
            margin: auto;
            display: block;
            width: 200px;
            padding-left: 25px;
            padding-right: 20px;
          "
        >
          <br />
          <mat-list
            class="example-section"
            *ngFor="let p of profesiones"
            style="color: rgb(172, 172, 172)"
          >
          <mat-list-item
          color="primary"
          class="example-margin"        
          >{{ p }}
        </mat-list-item>

          </mat-list>
          <br />
        </div>
      </div>


      <label>
      Habilidades:
      </label>
      <div class="card-body">
        <div
          class="habilidades"
          style="
            margin: auto;
            display: block;
            width: 200px;
            padding-left: 25px;
            padding-right: 20px;
          ">
          <br />
          <mat-list
            class="example-section"
            *ngFor="let h of habilidades"
            style="color: rgb(172, 172, 172)"
          >
          <mat-list-item
          color="primary"
          class="example-margin"
          >{{ h }}
        </mat-list-item>

          <!--
          <mat-checkbox
          color="primary"
          class="example-margin"
          formControlName="checked"
          >{{ t }}
        </mat-checkbox>
        -->

          </mat-list>
          <br />
        </div>
      </div>

      <p>
        <legend>Descripción:</legend>
        <mat-form-field appearance="outline" class="formItem">
          <mat-label></mat-label>
          <textarea
            name="textDesc"
            id=""
            cols="10"
            rows="1"
            class="textDesc"
            formControlName="descript"
            matInput
            placeholder="Detalles importantes"
            maxlength="500"
            required
          >
          </textarea>
        </mat-form-field>
      </p>

      <div class="btnRegister" >
        <button
          mat-button
          class="botonRegis"
          type="submit"
          (click)="onRegister()"
        >
          <mat-icon class="loginIcon">login</mat-icon><span>    Editar </span>
         </button>
        </div>
       </div>
      </div>
     </form>
   </div>


Se observa la agregación a nuestro formulario ya conocido en nuestro modulos de registro, sin embargo, cabe resaltar cómo se hace la agregación del contenedor que contendra la foto.

Los estilos de nuestro inicio de sesión está definido por la siguientes reglas encontradas en nuestro scss.



::

     .foto{
          position: absolute;
          margin-left: 50px;
          margin-top: 50px;
      }

      .cont1{
        display: inline-block;
      }

      .cont1 .label{
        position: absolute;
        display: inline-block;
        margin-top:-20px;


      }


      .cont1 .label2{
        position: absolute;
        display: inline-block;
        margin-top:-20px;
        }

      .example-section {
        display: flex;
        align-content: center;
        align-items: center;
      }

      .loginIcon {
        position: relative;
        left: auto;
      }

      .btnRegister{
        text-align: center;
      }
      .botonRegis{
        background-color:#ff8800da;
        border: 1px solid gray;
      }


      .botonRegis:hover{
        background-color: rgb(180, 180, 180);

      }

      .input[type="textDesc"] {
        margin-bottom: 30px;
        width: 100%;
        margin-bottom: 20px;
        box-sizing: border-box;
        padding: 7px;
        min-height: 100px;
        max-height: 200px;
        max-width: 200px;
        min-width: 100;
      }

      input[type=number]::-webkit-outer-spin-button,

      input[type=number]::-webkit-inner-spin-button {

          -webkit-appearance: none;

          margin: 0;

      }



      input[type=number] {

          -moz-appearance:textfield;

      }


      .formxD {
        width: 900px;
        margin: auto;
        padding: 30px;
        text-align: center;
        border: 3px solid gray;
        border-radius: 5px;
        background:white;
      }

      .container{
        text-align: center;
        float: none;
        border: 1px solid gray;
        background:white ;
        margin-bottom: 15px;
        margin-right: 15px;
        margin-left: 10px;
        border: 1.5px solid gray;
        border-radius: 10px;
      }
      .formItem{
        width: 300px;
        text-align: center;
      }
      .descrip{
        width: 31em;
      }
      .textDesc{
        height: 10em;
      }
      .formItem1 {


        background:white ;
        padding: 5px;
        border: 1.5px solid gray;
        border-radius: 10px;
      }
      .habilidades{

        background:white ;
        border: 1.5px solid gray;
        border-radius: 10px;
      }
      .card-body{
        margin-bottom: 3em;
      }
      .container {
        align-items: center;
        width: 100%;
        background:linear-gradient(#ff7b00,white) ;
      }

    .contImg{
      width: 297px;
      height: 297px;
      //margin-left:-100px;
      margin-bottom: 60px;
    }

      .profPic{
        width: 297px;
        height: 297px;
        border-radius: 60%;
        border: 1.5px solid gray;
      }

      @media screen and (max-width: 768px) {

        .formxD {
          position: relative;
          text-align: center;
          float: none;
          max-width: 70vw;
          height: auto;
        }

        .profPic{
          left: 0px;
          width: 150px;
          height: 150px;
          margin-top: 0;
          position: relative;
          text-align: center;
          float: none;
          //height: auto;

        }

        .formItem{
          max-width: 55vw;
          margin-top: 0;
        }

        .formItem1{
          width: 55vw;
          margin-top: 0;
          position: relative;
          text-align: center;
          float: none;
          height: auto;
        }
        .card-body{
          max-width: auto;
          left: -3%;
          text-align: center;
          position: relative;
          display: block;
          margin: auto;
          margin-bottom: 2em;
          }
          .contImg{
            display: block;
            width: 80vw;
            height: auto;
            margin: 0 0 0 0;
            margin-bottom: 50px;
            border: none;
            text-align: center;
          }
          .contImg .profPic{
            left: -17px;
          }

      .cont1 .label{
        position: relative;
        display: block;
        margin-top:-20px;
        width: auto;


      }
      .cont1 .label2{
        position: relative;
        display: block;
        margin-top:-20px;
        width: auto;

      }
      }



Dentro de nuestro scss definimos la posición de nuestros items, su color, sus magenes, la posición de la imagen, las reglas de responsividad & los colores de principales de la página, también se remueven las flechas que aparecían en algunos campos que servían para aumentar una cantidad numérica.



::

      import { Component, OnInit } from '@angular/core';
      import {MatDialog} from '@angular/material/dialog';
      import {ModalComponent} from '../../componentes/modal/modal.component';
      import { FormGroup, FormControl, Validators} from '@angular/forms';
      import { AuthService} from '../../services/auth/auth.service';
      import { Usuario} from '../../models/usuario.model';
      import { AngularFireStorage } from '@angular/fire/storage';
      import { DataBaseService } from 'src/app/services/data-base.service';
      import {DatePipe } from  '@angular/common';
      import { first } from 'rxjs/operators';



      export interface Habilidad{
        nombre:string;
        checked:boolean;
        checkeable:boolean;
      }

      @Component({
        selector: 'app-perfil',
        templateUrl: './perfil.component.html',
        styleUrls: ['./perfil.component.scss']
      })

      export class PerfilComponent implements OnInit {
        public users= new Usuario();
        perfilForm = new FormGroup({
          nombre: new FormControl({value:'', disabled:true}),
          apellido:new FormControl({value:'', disabled:true}),
          cc:new FormControl({value:'', disabled:true},[]),
          email:new FormControl({value:'', disabled:true}, [Validators.email]),
          fechaN:new FormControl({value:'', disabled:true}),
          direccion:new FormControl({value:'', disabled:true}),
          pais:new FormControl({value:'', disabled:true}),
          dept:new FormControl({value:'', disabled:true}, Validators.required),
          ciudad:new FormControl({value:'', disabled:true}, Validators.required),
          postal: new FormControl({value:'', disabled:true}),
          profes: new FormControl({value:'', disabled:true}),
          //skills: new FormControl(''),
          descript:new FormControl({value:'', disabled:true}),
          checked: new FormControl({value:'', disabled:true,}),
        });
        public user:any;

        public imgurl:string;

        public habilidades = [];
        public profesiones = [];

        constructor(public dialog: MatDialog, private storage: AngularFireStorage, private authSvs: AuthService, private db:DataBaseService) { }

        async ngOnInit() {
            this.user = await this.authSvs.afAuth.authState.pipe(first()).toPromise() ;
            const date = new DatePipe('en_US');
            (await this.db.busquedaEmail(this.user.email)).subscribe(res=>{
            this.users = res[0];
            const thedate= this.users.fecha.valueOf();
            //MARCA ERROR pero no quitarloooo!!!!!!!!!!!!!!!!!!!!!
            //console.log(this.users.fecha.seconds);
            //const fechaF = 12;
            const fechaF = date.transform( this.users.fecha['seconds']*1000 , 'dd/MM/yyyy');//NO QUITARLOOOOOOOOOOOOOO
            //NO QUITARLOOOOOOOOOOOOOOOOOOOO!!!!!!!!!
            //NO QUITARLOOOOOOOOOOOOOOOOOOOO!!!!!!!!!
            console.log(fechaF)
                this.perfilForm.get('nombre').setValue(this.users.nombres);
                this.perfilForm.get('apellido').setValue(this.users.apellidos);
                this.perfilForm.get('cc').setValue(this.users.cc);
                this.perfilForm.get('email').setValue(this.users.email);
                this.perfilForm.get('fechaN').setValue(fechaF);
                this.perfilForm.get('direccion').setValue(this.users.direccion);
                this.perfilForm.get('pais').setValue(this.users.pais);
                this.perfilForm.get('dept').setValue(this.users.departamento);
                this.perfilForm.get('ciudad').setValue(this.users.ciudad);
                this.perfilForm.get('postal').setValue(this.users.codigo_postal);
                this.profesiones = this.users.profesion;
                this.perfilForm.get('descript').setValue(this.users.descripcion);
                this.habilidades = this.users.habilidades;
                this.perfilForm.get('checked').updateValueAndValidity();
                this.imgurl = this.users.urlImagen;
              }
            );
        }
        onRegister(){
          this.dialog.open(ModalComponent);
        }

      }



En nuestra parte lógica, podemos observar cómo hacemos la creación de nuestro formulario con cada uno de sus respectivos items, para poder mostrar los datos del usuario loggeado y traido desde nuestro storage en su correspondiente espacio. también observamos que al monmento de dar click en nuestro botón de editar, se reutiliza nuestro método onRegister() para abrir nuestro componente modal que contendrá toda nuestra parte lógica y front end del resto de la funcionalidad de MiPerfil
