SERVICIO GUARD
================


El servicio Guard ha sido creado con la función de restringir el acceso a los módulos de nuestro portal, la condición para poder acceder a dichos modulos es que se encuentre loggeado, de no ser así, al intentar ingresar a estos modulos, se le pedirá al usuario que por favor se loguee.


::

       constructor(private authsvc: AuthService, private router: Router){}


        canActivate(){
          return this.authsvc.userData$.pipe(map(user=>{
            if (!user){
              alert('no has iniciado sesion para ingresar a ver los registros, por favor registrate o inicia sesion');
              this.router.navigate(['/login']);
              return false;
            }else{
              return true;
            }
          }));
        }



nuestro método CanActivate, buscará gracias a nuestro authservice, que nuestro usuario ingresado existe, sino existe, aparecerá su respectivo alert y será enviado a Login.