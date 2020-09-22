MODULO DE INICIO DE SESION
===========================

En el módulo de inicio se encuentran los archivos que le permiten al usuario loguearse con un correo existente y alojado en la Base de Datos de firebase.


El diseño del html para esta parte está diseñada de la siguiente manera:

.. code-block::

    <ng-container *ngIf="user | async; else login">
      Estas logueado con {{user.email}}
    </ng-container>
    <ng-template #login>
    <body>
    <div class="container">
        <form class="login" [formGroup]="loginForm">
        <input type="text" placeholder="Ingresa tu email"   formControlName="email">
        <button type="submit" (click)="onSignIn()" >Iniciar Sesión</button>
      </form>
    </div>
    </body>
    </ng-template>

Como primera instancia se crea un ngIf que nos avisará si el usuario se encuentra loggeado.

Dentro del body, se crea un contenedor con un formulario para poder loguearse, sin embargo este login está hecho para iniciarse a través del e-mail, por esta razón no se requiere de password, ya que una vez dado click al botón.

Los estilos de nuestro inicio de sesión está definido por la siguientes reglas encontradas en inicio.component.scss:

.. code-block::

	
    // Colors
    $greenSeaweed: rgb(255, 14, 14);
    $blueQueen: rgba(69, 105, 144, 1);
    $redFire: rgba(244, 91, 105, 1);

    // Fonts
    $fontAsap: 'Asap', sans-serif;

    body {
    //background-image: url(https://i.ytimg.com/vi/Q3IpUFB2SZY/maxresdefault.jpg);
    background-image: url(https://territorioinformativo.com/wp-content/uploads/2017/01/marvel-heroes-videojuego_Territorio-Informativo.jpg);
    background-size: 100vw 100vh;
    //background-position: center;
    //background-size: cover;
    //background-repeat: no-repeat;
      background-color: $redFire;
      font-family: $fontAsap;
      height: 100vh;
    }

    .container {
      overflow: hidden;
      background-color: white;
      padding: 40px 30px 30px 30px;
      border-radius: 10px;
      border-width: 10px;
      border-color: rgb(255, 115, 0);
      position: relative;
      text-align: center;
      left: 35%;
      color: black;
      top: 40%;
      width: 300px;
      background: rgba(255, 255, 255, 0.884);
    }

    .login{

      box-shadow: 5px 10px 10px rgb(255, 115, 0.2);


      &::before, &::after {
        content: '';
        position: absolute;
        width: 400px;
        height: 600px;
        border-top-left-radius: 40%;
        border-top-right-radius: 45%;
        border-bottom-left-radius: 35%;
        border-bottom-right-radius: 40%;
        z-index: -1;
      }

      &::before {
        left: 40%;
        bottom: -130%;
        background-color: rgba($blueQueen, 0.15);
      }

      &::after {
        left: 35%;
        bottom: -125%;
        background-color: rgba($greenSeaweed, 0.2);
      }

      > input {
        font-family: $fontAsap;
        display: block;
        border-radius: 5px;
        font-size: 16px;
        background: rgb(255, 255, 255);
        width: 90%;
        border: 0;
        padding: 10px 10px;
        margin: 15px -10px;
        color: rgb(0, 0, 0);
      }

      > button {
        font-family: $fontAsap;
        cursor: pointer;
        color: #fff;
        font-size: 16px;
        text-transform: uppercase;
        width: 50%;
        border: 0;
        padding: 10px 0;
        margin-top: 10px;
        margin-left: -5px;
        margin-bottom: 15px;
        border-radius: 5px;
        background-color: gray;


        &:hover {
          background-color: lighten(rgb(255, 102, 0), 10%);
          color: rgba($color: #000000, $alpha: 1.0);
        }
      }
    }


    a {
      text-decoration: none;
      color: rgba(white, 0.6);
      position: absolute;
      right: 10px;
      bottom: 10px;
      font-size: 12px;
    }
    @media screen and (max-width: 504px){

        .container{
          top: 35%;
          padding: 10px 9px 9px 9px;
          left: 0%;
          margin: auto;
          max-width: 100%;
          height: auto;

        }
        body{
          background-image: url(https://wallpapersite.com/images/wallpapers/avengers-infinity-war-2560x1440-4k-8k-13270.jpg);
          background-position: center;
          background-size: auto 100vh;

        }
    }
    @media screen and (max-width: 800px) and (min-width: 505px){

      .container{
        top: 35%;

        left: 30%;
        max-width: 50vw;
      }
      body{
        background-image: url(https://wallpapersite.com/images/wallpapers/avengers-infinity-war-2560x1440-4k-8k-13270.jpg);

      }
    }

Dentro de nuestro scss, definimos la posición dentrada en la cuál se encuentra nuestro contenedor del login junto con su botón, este botón también posee una opción de hover, que le agrega más estilo a nuestro aplicativo web.

También se definen las reglas para la responsividad, en esta reglas se encuentra la posición del container, su máxima anchura y también una background image.


.. code-block::

   import { NgModule } from '@angular/core';
   import { CommonModule } from '@angular/common';

   import { InicioRoutingModule } from './inicio-routing.module';
   import { InicioComponent } from './inicio.component';

   import { AuthService} from '../../services/auth/auth.service';

   import { FormsModule} from '@angular/forms';
   import {ReactiveFormsModule} from '@angular/forms';

   import {MatFormFieldModule} from '@angular/material/form-field';
   import { MatInputModule} from '@angular/material/input';



   @NgModule({
  declarations: [InicioComponent],
  imports: [
    CommonModule,
    InicioRoutingModule,
    FormsModule,
    ReactiveFormsModule,
    MatFormFieldModule,
    MatInputModule,
  ], 
   exports:[
    InicioComponent,
  ],
   providers:[ AuthService]
   })
   export class InicioModule { }


En nuestro inicio.module.ts importaremos & exportaremos todos los componentes, librerias y modelos para poder trabajar de manera eficiente en nuestro servicio de Inicio de sesion.



.. code-block::

   import { Component, OnInit } from '@angular/core';
   import { FormControl, FormGroup } from '@angular/forms';
   import { AuthService} from '../../services/auth/auth.service'; 
   import { Router } from '@angular/router';
   import { map, first } from 'rxjs/operators';
   import { Observable } from 'rxjs';


   @Component({
  selector: 'app-inicio',
  templateUrl: './inicio.component.html',
  styleUrls: ['./inicio.component.scss']
   })
   export class InicioComponent implements OnInit {

   loginForm = new FormGroup({
     email: new FormControl(''),
  });
   public user: Observable<any>;
   public enviado = false;
   constructor(private authSvc:AuthService,    private router: Router) { }

   async ngOnInit() {
    this.user = await this.authSvc.userData$;
    await this.authSvc.userData$.subscribe(res=>{
      if (res){
        this.router.navigate(['/home']);
      }
    });
    const url = this.router.url;
    this.authSvc.confirmSignIn(url);
  }
   onSignIn(){
    const {email} = this.loginForm.value;
    this.authSvc.login(email);
    this.enviado = true;
  }

La lógica detrás del inicio se encuentra detrás de Inicio.component.ts. En este archivo, nos encontraremos con una inicilización de un formulario de Login el cuál solo recibirá el E-mail. nuestro ngOnInit. de manera asincrona, hacemos una pequeña condicional de que si existe un usuario, se redirige hacia /Home, esto es gracias a la llamada de Router que se hace en el constructor, esto nos permite hacer navegación entre páginas.

OnSignIn(){} es el método importante, se activará una vez el usuario haga click en el botón "Iniciar Sesion", ya que utilizará nuestro servicio de AuthService, el cuál recorre en su método Login(), los usuarios que existen en la base de datos, si se encuentra alguna coincidencia, permite realizar el login enviando al correo ingresado por el usuario, un link con la habilidad de poder ingresar, es decir, nuestro módulo de inicio de Sesion, está hecho para enviar de manera segura, un correo con el link que le permitirá ingresar de manera segura y sin contraseña a nuestro portal.


