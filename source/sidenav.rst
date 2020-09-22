SIDENAV COMPONENTE:
====================

El componente de nuestro sidenav está compuesto mayormente por una plantilla creada por los developers desde cero, en la cuál definen una sidenav para mostrar los módulos existentes dependiendo si el usuario está loggeado o desloggeado, así como también contiene los íconos que se muestren en el momento en que entremos en modo responsivo, el cual creará dos iconos de hamburguesa, uno a cada lado, el segundo botón, desplegará un menú que permitirá navegar por secciones extras como Inicio, Equipo y Contacto, este menú también es visible en la mitad de nuestra barra principal en modo web.

::



      <!--Este es el contenedor de todo el sidebar-->
      <mat-sidenav-container class="container"  (backdropClick)='close()'>

        <!-- este sidenav es el menú lateral que se desplegará haciendo click en la hamburguesa como un evento-->

          <mat-sidenav class="sidenav" #sidenav mode="over">
            <div class="sideItems menuHeader2">
              <!--<button mat-icon-button class="btnMenu" aria-label="icon-button menu icon" (click)="sidenav.toggle()">-->
                <button mat-icon-button class="" aria-label="icon-button menu icon" [routerLink]="['/home']">
                <img src="../../../assets/LOGO.png" alt="LOGO" class="logo" style="width: 80px;height: 40px;" >
              </button>
              <div class="user" *ngIf="user$ | async as user; else nouser"></div>
              <ng-template #nouser>
              <a class="nav-link active" [routerLink]="['/registro']"><mat-icon class="matIcon">person_add</mat-icon>Registrarse</a>
              <br>
              <a class="nav-link active" [routerLink]="['/login']"><mat-icon class="matIcon">login</mat-icon>Iniciar Sesión</a>
              <br>
              </ng-template>
              <a *ngIf="user$ | async as user" class="nav-link active" [routerLink]="['/records']"><mat-icon class="matIcon"> list</mat-icon>Registros</a>
              <br>
              <a class="nav-link active" [routerLink]="['/video']"><mat-icon class="matIcon">ondemand_video</mat-icon>Video</a>
              <br>
              <a *ngIf="user$ | async as user" class="nav-link active" [routerLink]="['/miperfil']"><mat-icon class="matIcon">account_circle</mat-icon>Mi perfil </a>
              <br>
              <a *ngIf="user$ | async as user" class="nav-link active" (click)=salir() [routerLink]="['/login']"><mat-icon class="matIcon">android</mat-icon>Salir</a>

            </div>
          </mat-sidenav>

          <mat-sidenav #menuIcon class="sidenav" position="end">

            <div class="menuHeader2" style=" width: 100%; height: fit-content;"  >
              <a class="menuIt" class="nav-link active" [routerLink]="['/home']"><mat-icon class="matIcon">home</mat-icon> <span class="label">Inicio</span> </a>
              <br>
              <a class="menuIt" class="nav-link active" [routerLink]="['/equipo']"><mat-icon class="matIcon">group</mat-icon><span class="label">Equipo</span></a>
              <br>
              <a class="menuIt" class="nav-link active" [routerLink]="['/contactanos']"><mat-icon class="matIcon">contact_mail</mat-icon><span class="label">Contacto</span></a>
            </div>

          </mat-sidenav>

          <mat-sidenav-content class="total">

              <!--este es el toolbar, con los iconos y textos-->
              <mat-toolbar id="navbar" class="navbar">

                <mat-icon mat-icon-button class="btnMenu" (click)="sidenav.toggle()">menu</mat-icon>
                <mat-icon mat-icon-button class="btnMenu2" (click)="menuIcon.toggle()">menu</mat-icon>
                <div class="cont" style="width: max-content;">
                <button mat-icon-button class="" aria-label="icon-button menu icon" (click)="sidenav.toggle()">
                  <img src="../../../assets/LOGO.png" alt="LOGO" style="width: 80px;height: 40px;" class="logo2">
                </button>
                </div>

                <div class="menuHeader" style=" width: 100%; height: fit-content;"  >
                  <a class="menuIt" class="nav-link active" [routerLink]="['/home']"><span class="label">Inicio</span> </a>
                  <a class="menuIt" class="nav-link active" [routerLink]="['/equipo']"><span class="label">Equipo</span></a>
                  <a class="menuIt" class="nav-link active" [routerLink]="['/contactanos']"><span class="label">Contacto</span></a>
                </div>

                </mat-toolbar>

                <mat-sidenav-content class="content">

             <router-outlet>   </router-outlet>
   
          </mat-sidenav-content>
          <mat-sidenav-content style="height: 20px; overflow: hidden;">   
            <app-footer></app-footer>
          </mat-sidenav-content>

          </mat-sidenav-content>

        </mat-sidenav-container>



Los estilos, colores, posiciones y demás reglas de diseño, se definen en nuestro scss.


::

      .container {
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        position: relative;
        height: 100vh;
        overflow-y: hidden;
      }
      .menuHeader a{
        position: relative;
        float: none;
        text-decoration: none;
        padding: 11px;
        color: black;
        justify-items: stretch;
      }
      .menuHeader2 a
      {

        padding: 14px;
        text-decoration: none;
        font-size: 25px;
        color: black;
        display: block;
        transition: 0.3s;
        text-align: justify;

      }

      .menuHeader{
        text-align: center;
      }

      .sideItems{
        text-align: center;
        position: relative;
        display: block;
      }
      .contentAll{
        height: 100%;

      }

      .sideItems .logo{
        width: 100%;
        height: auto;
        right: 25px;
        position: relative;
      }

      .logo2{
        position: relative;
      }
      .content{
        position: relative;
        margin: 0 0 0 0;
        height: 90%;
        //overflow: hidden;

      }
      .navbar{
        height: 100%;
        position: relative;
      }

      .navbar .btnMenu2{
        position: absolute;
        top: 9;
        right: 0;
        margin-right: 15px;
        float: none;
        text-align: left;
      }



      .matIcon{
        margin-right:5px ;
        max-width: auto;
        max-height: auto;
        float: none;
      }

      .containerLogs{
        width: 400px;
        height: 200px;
        overflow: auto;
        border: 1px solid #555;
      }

      .sidenav a{
        padding: 14px;
        text-decoration: none;
        font-size: 25px;
        color: black;
        display: block;
        transition: 0.3s;
        margin-top: 15px;
      }

      .sidenav a:hover{
        color: white;
      }

      .sidebar a:hover:not(.active){
        background-color: #f7a0cb6b;
        width: 100%;
        color:white;
      }




      .sidenav{
        background:linear-gradient(#FF9100,#EED7B0) ;
        margin: 0;
        padding: 5px;
        width: 220px;
        position: absolute;
        height: 100%;

      }



      .navbar{
        width: 100%;
        height: 100%;
        background:linear-gradient(#FF9100,#EED7B0)
      }

      #navbar{
        max-width: 100%;
        height: 70px;

      }



      .sectCont{
        text-align: center;
        }



      @media only screen and (min-width:769px){
        .btnMenu2 {
          display: none;
          }
          .btnMenu {
            display: none;
            }
        .menuHeader{
          display: inline-block;
        }
      }
      @media only screen and (max-width:768px){

        .mat-icon{
          display:inline-block;
        }
        .menuHeader{
          display:none;
        }


      }

      @media only screen and (max-width :768px)
      {

        .sectCont{
          width: 55vw;
          display: block;
          margin: auto;
          margin-bottom: 2em;
        }
        .container{
          position: relative;
          float: none;
          width: auto;
          height: auto;
        }
        #navbar{
          max-width: 100%;
          height: 50px;

        }
        .cont{
          display: block;
          margin: 10px auto;
          border: none;
          text-align: center;
        }
        .cont .logo2{
          right: 25px
        }


      .menuIt{
        text-align: center;
        float: none;
        position: relative;
        bottom: 5em;
      }
      }



Una vez definidas nuestras reglas, vamos al componente o la parte lógica de nuestro sidenav.


::

      export class SidenavMatComponent implements OnInit {
        public user$: Observable<any> = this.authSvc.afAuth.user;
        public user : any;

        @ViewChild('sidenav') sidenav: MatSidenav;


        events: string[]=[];
        opened: boolean;




        constructor(private authSvc: AuthService) { }

        ngOnInit(): void {

        }
        salir(){
          this.authSvc.logout();
        }
        close(){
          this.sidenav.close();
        }

      }



Observamos que tenemos un observable de un usuario que se encuentre dentrod de nuestro sistema de información y poseemos dos métodos, el de Salir() el cuál está ligado al Boton de Salir que se encontrará en nuestro sidenav y aparecerá si el usuario se loggea exitosamente. El método close() funciona para colapsar nuestro sidebar.


