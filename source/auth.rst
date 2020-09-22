SERVICIO AUTH
=============


El servicio de auth está diseñado para realizar todas las confirmaciones y verificaciones de usuario. el Método Iniciando(email:string) que nos debe recibir un string de tipo email, nos monta las reglas en donde funcionará, en este caso en la URL de marvel-project. con un try catch, se crea toda la secuencia lógica de que una vez nuestro usuario de click en iniciar sesion, este correo ingresado sera verificado dentro de nuestra base de datos y una vez confirmado, se envía un e-mail al usuario para poder entrar a nuestro portal a través de este link seguro que se encontrará en su correo. una vez este se envíe aparece un alert indicando los pasos a seguir.


::

      export class AuthService {
        public userData$ : Observable<firebase.User>;
        public user:any;
        public usuario$:Usuario;

        constructor(public afAuth:AngularFireAuth, private db:DataBaseService, private router:Router) { 
          this.userData$ = afAuth.authState;
          this.user = this.afAuth.authState.pipe(first()).toPromise();
        }
        async inciando(email:string){
            const actionCodeSettings = {
              //url: 'http://localhost:4200/login',
              url: 'https://marvel-project-95aea.web.app/login',
              handleCodeInApp: true,
        
            };
            try {
              await this.afAuth.sendSignInLinkToEmail(email, actionCodeSettings);  
              window.localStorage.setItem('emailForSignIn', email);
              alert('Por favor inicia sesion ingresando al link que hemos enviado a tu correo electronico');
              window.location.reload();
              //alert(this.userData$);
              return true;
            } catch (error) {
              console.log(error);
            }
            
        }
        async login(email:string){
          var bandera = false;
          (await this.db.obtenerUsuarios()).subscribe(res=>{
            res.forEach(usuario =>{
              if (usuario.email == email){
                this.usuario$ = usuario;
                this.inciando(email); 
                bandera = true;   
              }
            });
            console.log(bandera);
            if (!bandera){
              alert('email no registrado');
            }
          }); 

        }
        async confirmSignIn(url){
          var bandera = false;
          this.userData$.pipe(map(user=>{
            if (user){
              bandera = true;
            }
          }));
          if  (!bandera){ 
          try {
            if (this.afAuth.isSignInWithEmailLink(url)){
              console.log('YES');
              let email = window.localStorage.getItem('emailForSignIn');
              if (!email){    
                //email = window.prompt('Por favor ingresa un email para iniciar sesion');
                //alert('Por favor ingrese con un email ya registrado');
              }
              const result = await this.afAuth.signInWithEmailLink(email, url);
              window.localStorage.removeItem('emailForSignIn');
              this.router.navigate(['/home']);
            }
          } catch (error) {
            
          }
        }
        }
        async logout(){
          try {
            await this.afAuth.signOut();
          } catch (error) {
            console.log(error);
          }
        }
      }



Con nuestro método, Login(), obtener al usuario desde la base de datos, para así confirmar que el e-mail ingresado, se compare con los demás e-mails que se han registrado hasta encontrar una coincidencia, sino lo hace aparece un alert indicando que este email no se encuentra registrado