COMPONENTE MODAL
==================


Nuestro modal está compuesto por un gran formulario, dando continuación a nuestro módulo de Perfil. En nuestra plantilla html, definimos todo lo que irá dentro de nuestro modal y sobre todo, se encontrarán los campos habilitados para poder realizar los cambios que el usuario encuentre pertinentes sobre su perfil.

::


      <mat-dialog-content class="dialog-content">
          <div class="container">
              <form [formGroup]="perfilForm" (ngSubmit)="onRegister()" class="formxD">
                <h1 style="color: Black; text-align: center; margin-top: 20px">
                  EDITANDO MI PERFIL
                </h1>

                <div class="card-body">
                <!-- <ng-div class="contImg" *ngIf="urlImage | async;else select"> src="{{urlimg}} | async" -->
                  <div class="contImg" *ngIf="filePath; else select">
                    <img class="profPic"
                    src="https://img2.freepng.es/20180330/zoq/kisspng-computer-icons-three-dimensional-space-check-mark-green-tick-5abe6e5977a841.0874474515224295294901.jpg"
                    alt="unabProfile"
                    style="width: 100px; height: 80px;">
                    <div class="container-input-file">
                      <label class="custom-file">
                        <input style="text-align: center;" type="file"
                        accept=".png, .jpg, .jepg"
                        (change)="onUploadFoto($event)">
                        <mat-icon class="loginIcon" style="cursor: pointer;">cloud_upload</mat-icon>
                        <span style="cursor: pointer;">&nbsp;CAMBIAR IMAGEN</span>
                      </label>
                    </div>

                  </div>
                  <ng-template  #select>
                    <div class="contImg">
                    <img class="profPic"
                    src="{{urlimg}} | async "
                    alt="unabProfile"
                    style="width: 100px; height: 100px;">
                    <div class="container-input-file">
                      <label class="custom-file">
                        <input style="text-align: center;" type="file"
                        accept=".png, .jpg, .jepg"
                        (change)="onUploadFoto($event)">
                        <mat-icon class="loginIcon" style="cursor: pointer;">cloud_upload</mat-icon>
                        <span style="cursor: pointer;">&nbsp;CAMBIAR IMAGEN</span>
                      </label>
                    </div>

                  </div>
                  </ng-template>
                    <input  #imageuser  style="text-align: center;" type="hidden" [value]="urlImage | async">

                    <div class="cont1">

                    <mat-form-field
                      appearance="outline"
                      style="text-align: center"
                      class="formItem">
                      <label class="label">Nombre</label>


                      <input
                        formControlName="nombre"
                        type="text"
                        matInput
                        placeholder="Nombre{p.ej. Juan, José, Maria}"
                        required
                      />
                    </mat-form-field>

                    <mat-form-field appearance="outline" class="formItem">
                      <label class="label">Apellido</label>

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

                    <mat-form-field appearance="outline" class="formItem">
                      <label class="label">Cédula de ciudadanía</label>

                      <input
                        formControlName="cc"
                        class="numberCc"
                        type="number"
                        matInput
                        placeholder="Cedula{p.ej. 1098457869}"
                        required
                        (change)="validarCC()"
                      />
                    </mat-form-field>


                    <mat-form-field
                      appearance="outline"
                      class="formItem"
                      style="text-align: center"
                    >
                    <label class="label">Correo Electrónico</label>
                      <input
                        formControlName="email"
                        type="email"
                        matInput
                        placeholder="email personxx@hotmail.com"
                        required
                        (change)="validarMail()"
                      />
                    </mat-form-field>
                  </p>

                  <p>

                    <mat-form-field appearance="outline" class="formItem">
                      <label class="label">Fecha de nacimiento</label>
                      <input
                        name="date"
                        matInput
                        [matDatepicker]="picker"
                        formControlName="fechaN"
                        required
                      />
                      <mat-datepicker-toggle
                        matSuffix
                        [for]="picker"
                      ></mat-datepicker-toggle>
                      <mat-datepicker #picker></mat-datepicker>
                    </mat-form-field>


                    <mat-form-field appearance="outline" class="formItem">
                      <label class="label">Dirección</label>
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

                    <mat-form-field appearance="outline" class="formItem">
                      <label class="label">Ciudad</label>

                      <input
                        formControlName="ciudad"
                        type="text"
                        matInput
                        placeholder="Ciudad {Bucaramanga, Bogotá, Lima}"
                        [matAutocomplete]="autoC"
                        required
                      />
                      <mat-autocomplete #autoC="matAutocomplete">
                        <mat-option *ngFor="let option of opcionesFiltradasCiudad | async" [value]="option.municipio">
                          {{option.municipio}}
                        </mat-option>
                    </mat-autocomplete>
                    </mat-form-field>


                    <mat-form-field appearance="outline" class="formItem">
                      <label class="label">Departamento</label>

                      <input
                        formControlName="dept"
                        type="text"
                        matInput
                        placeholder="Departamento {Santander, Cundinamarca}"
                        [matAutocomplete]="autoD"
                        required
                      />
                      <mat-autocomplete #autoD="matAutocomplete">
                        <mat-option *ngFor="let option of opcionesFiltradas | async" [value]="option.departamento">
                          {{option.departamento}}
                        </mat-option>
                      </mat-autocomplete>
                    </mat-form-field>
                  </p>

                  <p>

                    <mat-form-field appearance="outline" class="formItem">
                      <label class="label">País</label>
                      <input
                        formControlName="pais"
                        type="text"
                        matInput
                        placeholder="País {Indonesia, Colombia}"
                        required
                      />
                    </mat-form-field>


                    <mat-form-field appearance="outline" class="formItem">
                      <label class="label">Número Postal</label>

                      <input
                        formControlName="postal"
                        type="number"
                        matInput
                        placeholder="Postal{p.ej. 13425}"
                        required
                      />
                    </mat-form-field>
                  </p>

                  <mat-form-field
                  class="chips"
                  appearance="standard"
                  class="formItem"
                  style="text-align: center"
                >
                <label class="matLabProf">Profesión(es)</label>

                  <mat-chip-list #chipList aria-label="Profesion">
                    <mat-chip
                      *ngFor="let fruta of frutas"
                      [selectable]="selectable"
                      [removable]="removable"
                      (removed)="remove(fruta)"
                      >{{ fruta.name
                      }}<mat-icon matChipRemove *ngIf="removable">cancel</mat-icon>
                    </mat-chip>
                    <input
                      matInput
                      placeholder="profesiones{p.ej. Ingeniero, Dentista, Doctor}"
                      [matChipInputFor]="chipList"
                      [matChipInputSeparatorKeyCodes]="separatorKeysCodes"
                      [matChipInputAddOnBlur]="addOnBlur"
                      (matChipInputTokenEnd)="add($event)"
                      required
                    />
                  </mat-chip-list>
                </mat-form-field>


                  <div class="card-body">
                    <div
                      class="habilidades"
                      >
                      <br />
                      <label style="color: rgb(0, 0, 0)"
                        >Seleccione 3 de sus habilidades</label
                      >
                      <hr />
                      <mat-list
                        class="example-section"
                        *ngFor="let t of habilidades "
                        style="color: rgb(0, 0, 0)"
                      >
                        <mat-checkbox
                          color="primary"
                          class="example-margin"
                          (change)="onChange(t, $event)"
                          [disabled]="t.checkeable"
                          [checked]="t.checked"
                          >{{ t.nombre }}
                        </mat-checkbox>
                      </mat-list>
                      <br />
                    </div>
                  </div>

                  <p>


                    <mat-form-field appearance="outline" class="formItem">
                      <label style="color: rgb(185, 185, 185);">Descripción</label>

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
                      [disabled]="perfilForm.invalid"
                      (click)="onRegister()"
                    >
                      <mat-icon class="loginIcon">login</mat-icon><span> Guardar cambios</span>
                    </button>
                    <button
                    mat-button
                    class="botonCancel"
                    type="button"
                    (click)="onCancel()"
                  >
                    <mat-icon class="loginIcon">login</mat-icon><span> Descartar cambios</span>
                  </button>
                  </div>
                </div>
              </div>
              </form>
            </div>

      </mat-dialog-content>



Podemos observar, cómo agregamos nuestra sección donde el usuario puede cambiar la foto de su perfil, a través de una que posea localmente y también observamos cada campo de nuestro formulario con sus respectivo botones, haciendo una agregación de un Botón de descartar cambios.

Los estilos y reglas de diseño se definen dentro del scss, también se establecen las reglas de la responsividad del modal para que sea agradable e intuitivo a la hora de usarlo desde un mobile.


::

      .cont1{
        display: inline-block;


      }

      .habilidades{
        margin: auto;
      display: block;
      width: 200px;
      padding-left: 25px;
      padding-right: 20px;
      }

      .cont1 .label{
        position: relative;
        display: block;
        color: rgb(185, 185, 185);
      }


      .foto{
          position: absolute;
          margin-left: 50px;
          margin-top: 50px;
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
      .botonCancel{
        background-color:#e60000da;
        border: 1px solid gray;
      }

      .botonRegis:hover .botonCancel:hover{
        background-color: rgb(180, 180, 180);

      }
      input[type="file"]{
      display: none;
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
      width: 300px;
      height: auto;
      margin-left:-100px;
      margin-bottom: 30px;
      }

      .profPic{
        width: 300px;
        height: auto;
        border-radius: 60%;
        border: 1.5px solid gray;
      }

      @media screen and (max-width: 880px) {
        .formxD {
          position: relative;
          text-align: center;
          float: none;
          max-width: 40vw;
          height: auto;
        }

        .profPic{
          width: auto;
          margin-top: 0;
          position: relative;
          text-align: center;
          float: none;
          height: auto;

        }

        .formItem{
          max-width: 40vw;
          margin-top: 0;
        }

        .formItem1{
          width: 40vw;
          margin-top: 0;
          position: relative;
          text-align: center;
          float: none;
          height: auto;
        }
        .card-body{
          width: 40vw;
          text-align: center;
          position: relative;
          display: block;
          margin: auto;
          margin-bottom: 2em;
      }
      .habilidades
      {
          width: 100px;
          text-align: center;
          position: relative;
          display: block;
          margin: auto;
          margin-bottom: 2em;
      }
      }



Pasamos a la parte lógica de nuestro modal, el cual es la siguiente. 


::
        export interface Habilidad{
        nombre:string;
        checked:boolean;
        checkeable:boolean;
      }
      export interface Fruta{
        name:string;
      }
      @Component({
        selector: 'app-modal',
        templateUrl: './modal.component.html',
        styleUrls: ['./modal.component.scss']
      })



      export class ModalComponent implements OnInit {


        constructor(
          public dialog:MatDialogRef<ModalComponent>,
          //@Inject(MAT_DIALOG_DATA) public message: string, 
          private storage: AngularFireStorage, 
          private authSvs: AuthService, 
          private db:DataBaseService,
          private datosSvc: APIRestMunicipiosService
          ) { }
          @ViewChild('imageuser') inputImageUser: ElementRef;

          public users= new Usuario();

          perfilForm = new FormGroup({
          nombre: new FormControl({value:'',}),
          apellido:new FormControl({value:this.users?.apellidos, }),
          cc:new FormControl({value:'',},[]),
          email:new FormControl({value:'',disabled:true}, [Validators.email]),
          fechaN:new FormControl({value:'', }),
          direccion:new FormControl({value:'', }),
          pais:new FormControl({value:'', }),
          dept:new FormControl({value:'',}, Validators.required),
          ciudad:new FormControl({value:'', }, Validators.required),
          postal: new FormControl({value:'',}),
          //skills: new FormControl(''),
          descript:new FormControl({value:'',}),
          imgperfil: new FormControl({value:'',}),
        });
        public user:any;
        public usuarios:Usuario[];


        urlImage: Observable<string>;
        porcentaje: Observable<number>;
        public urlimg:string='';


        //arreglo de habilidades (el checkeable es el desahilitador de los checkbox)
        public habilidades:Array<Habilidad> = [
          {nombre: 'Proactividad', checked: false, checkeable: false},
          {nombre: 'Disciplina', checked: false, checkeable: false},
          {nombre: 'Diligente', checked: false, checkeable: false},
          {nombre: 'Estratégico', checked: false, checkeable: false},
          {nombre: 'Calmado', checked: false, checkeable: false},
          {nombre: 'Orientación', checked: false, checkeable: false},
          {nombre: 'Investigador', checked: false, checkeable: false},
          {nombre: 'Pensamiento'+'\n\n'+'Logaritmico', checked: false, checkeable: false},
          {nombre: 'Crítico', checked: false, checkeable: false},
          {nombre: 'Objetivo', checked: false, checkeable: false},
        ];
        seleccionados: number = 0;

          //CHIPS
          visible = true;
          selectable = true;
          removable = true;
          addOnBlur = true;
          readonly separatorKeysCodes: number[] = [ENTER, COMMA];
          frutas: Fruta[]=[];

            add(event: MatChipInputEvent):void{    //agregamos fruta o habilidad
              const input=event.input;
              const value=event.value;

            if((value || '').trim()){
              //if(this.frutas.length<3){
              //this.frutas.push({name:value.trim()});
              this.frutas.push({name:value.trim()});
            //}
            }
              //reset
            if (input) {
              input.value = '';
            }
          }



            remove(fruta: Fruta): void{ // remoooove
              const index= this.frutas.indexOf(fruta);
              if(index>=0){
                this.frutas.splice(index, 1);
              }

            }
        //fin de los CHIPS


        //array de municipios
        public datos : Municipio[] =[];
        //array de departamentos sin repetir
        public dptos : Municipio[] =[];
        //array de ciudades segun el departamento elegido
        public ciudades : Municipio[] = [];
        public opcionesFiltradas: Observable<Municipio[]>;
        public opcionesFiltradasCiudad: Observable<Municipio[]>; 
        selectDept(departamento:String){
          this.datos.forEach(muni=>{
            if (muni.departamento.toLowerCase() == departamento.toLowerCase()){
              this.ciudades.push(muni);
            }
          });
        }
        filtroDept(value:string):Municipio[]{
          this.selectDept(value);
          const valorFiltro = value.toLowerCase();
          return this.dptos.filter(option=>
            option.departamento.toLowerCase().includes(valorFiltro)
          );
        }
        filtroCiudad(value:string):Municipio[]{
          const valorFiltro = value.toLowerCase();
          if (this.ciudades.length==0){
            return this.datos.filter(option=>
              option.municipio.toLowerCase().includes(valorFiltro)
            );
          }
          return this.ciudades.filter(option=>
            option.municipio.toLowerCase().includes(valorFiltro)
          );
        }
      
        async ngOnInit() {
            //lenar el arreglo con los municipios
          await this.datosSvc.getAll().subscribe(res =>{        
            this.datos = res;
            res.forEach(resultado=>{
              var t = 0;
              this.dptos.forEach(obj=>{
                if(obj.departamento==resultado.departamento){
                  t++;
                }
              });
              if (t == 0){
                this.dptos.push(resultado);
              }
            });
            //console.log(this.dptos);
          }
        );
        //obtener lista de usuarios
        (await this.db.obtenerUsuarios()).subscribe(res=>{
          this.usuarios = res;
          //esto comentado es para poner el validator con la bd local (se esta usando metodo en el cambio)
          //console.log(this.users);
          //this.registerForm.get('cc').setValidators(validatorCC(this.users));
          //this.registerForm.get('email').setValidators(validatorMail(this.users));
        });

        //filtro departamentos y ciudades
        this.opcionesFiltradas = this.perfilForm.get('dept').valueChanges.pipe( 
          startWith(''),
          map(value=> 
            this.filtroDept(value)
            ),);
        this.opcionesFiltradasCiudad = this.perfilForm.get('ciudad').valueChanges.pipe( 
          startWith(''),
          map(value=>
            this.filtroCiudad(value))
        );

            this.user = await this.authSvs.afAuth.authState.pipe(first()).toPromise() ;
            const date = new DatePipe('en_US');
            (await this.db.busquedaEmail(this.user.email)).subscribe(res=>{
              this.users = res[0];
              const thedate= this.users.fecha.valueOf();
              //MARCA ERROR pero no quitarloooo!!!!!!!!!!!!!!!!!!!!!
              //console.log(this.users.fecha.seconds);
              //const fechaF = 12;
              //this.fechaF = date.transform( this.users.fecha['seconds'] *1000 ,'dd/MM/yyyy');//NO QUITARLOOOOOOOOOOOOOO
              const fechaF = date.transform( this.users.fecha['seconds'] *1000 ,'yyyy,MM,dd');//NO QUITARLOOOOOOOOOOOOOO
              //NO QUITARLOOOOOOOOOOOOOOOOOOOO!!!!!!!!!
              //NO QUITARLOOOOOOOOOOOOOOOOOOOO!!!!!!!!!
              //console.log(fechaF);
                this.perfilForm.get('nombre').setValue(this.users.nombres);
                this.perfilForm.get('apellido').setValue(this.users.apellidos);
                this.perfilForm.get('cc').setValue(this.users.cc);
                this.perfilForm.get('email').setValue(this.users.email);           
                this.perfilForm.get('fechaN').setValue(new Date(fechaF));
                this.perfilForm.get('direccion').setValue(this.users.direccion);
                this.perfilForm.get('pais').setValue(this.users.pais);
                this.perfilForm.get('dept').setValue(this.users.departamento);
                this.perfilForm.get('ciudad').setValue(this.users.ciudad);
                this.perfilForm.get('postal').setValue(this.users.codigo_postal);
                this.perfilForm.get('descript').setValue(this.users.descripcion);
                this.urlimg = this.users.urlImagen;
                this.habilidades.forEach(h1=>{
                  if (this.users.habilidades.includes(h1.nombre)){
                    this.onChange(h1);
                  }
                });
                this.users.profesion.forEach(elemnt=>{
                  this.frutas.push({name:elemnt});
                });
        
              }
            );
        }

        onChange(t:Habilidad, e?){
        //console.log('form ->', this.perfilForm);
        var bool= true;
      //metodo para registrar la habilidad en el momento que esta sea checkeada
          if(e){      
            bool = e.checked;
          }
          if (bool){
            this.seleccionados++;      
            if (this.seleccionados==3){
            this.habilidades.forEach(element => {
              if (element.nombre == t.nombre){
                element.checked = true;
              }
              if (element.checked == false){
                element.checkeable = true
              }
            });
            
          }else{
            this.habilidades.forEach(element => {
              if (element.nombre == t.nombre){
                element.checked = true;
              }
            });
          }
          }else{
            if (this.seleccionados==3){
              this.seleccionados--;
            this.habilidades.forEach(element => {
              if (element.nombre == t.nombre){
                element.checked = false;
              }
              if (element.checked == false){
                element.checkeable = false
              }
            });
            //console.log(this.habilidades);
          }else{
            this.seleccionados--;
            this.habilidades.forEach(element => {
              if (element.nombre == t.nombre){
                element.checked = false;
              }
            });
          }
          }
          //console.log(this.habilidades);

        }

        async onRegister(){
              //obtenemos datos del formGroup
          const {nombre, apellido, cc, email, fechaN, direccion, pais, dept, ciudad, postal, descript, imgperfil} = this.perfilForm.value;
              //tomar los datos de los arrays
              const habs:string [] = [];
              const profesiones: string[] = [];
              this.frutas.forEach(element=>{
                profesiones.push(element.name);
              });
              this.habilidades.forEach(element=>{
                if (element.checked){
                  habs.push(element.nombre);
                }
              });
          
              //creamos el usuario
              const user = new Usuario();
              user.nombres = nombre;
              user.apellidos = apellido;
              user.cc = cc;
              user.email = this.users.email;
              user.fecha = fechaN;
              user.direccion = direccion;
              user.pais = pais;
              user.ciudad = ciudad;
              user.codigo_postal = postal;
              user.profesion = profesiones;
              user.habilidades = habs;
              user.descripcion = descript;
              user.departamento = dept;
          if (this.file && this.filePath){   
          try{     
            const ref = this.storage.ref(this.filePath);
            const task = this.storage.upload(this.filePath, this.file);
            this.porcentaje = task.percentageChanges();
            task.then(f=>{
              f.ref.getDownloadURL().then(async l=>{
                    //tomar los datos de los arrays
            //creamos el usuario
          user.urlImagen = l;
          await this.db.crearUsuario(user).then(rta=>{
            debounceTime(500);
          //console.log('registro', rta);
          if (rta){
            timeout(500);        
            //alert('Usuario registrado satisfactoriamente');
          window.location.reload();
          }
        });
      });
      });
      //task.snapshotChanges().pipe(finalize(() =>
      //this.urlImage = ref.getDownloadURL())).subscribe(); 
          } catch (error) {
            console.log(error);
          }
          }else{
          user.urlImagen = this.users.urlImagen;
          await this.db.crearUsuario(user).then(rta=>{
            debounceTime(500);
          //console.log('registro', rta);
          if (rta){
            timeout(500);
            //alert('Usuario registrado satisfactoriamente');
            window.location.reload();
          }
        });
      }
        }
        file:any;
        filePath:any;  
        onUploadFoto(e){
          if (e.target.files && e.target.files[0]) {
          //console.log(e.target.files[0]);
          console.log(e.target.files[0].size);
          //if (e.target.files[0].size>99999){
            if(e.target.files[0].size>1042000){
            alert('Archivo no permitido, maximo 1MB');
          }else { 
              const id = this.users.email;
              this.file = e.target.files[0];
              this.filePath = 'perfil/'+id+'.png';
        }
        }
        }
          //Validacion de la cc por metodo con la bd quemada localmente
        validarCC(){
          const correo = this.perfilForm.get('cc');
          //this.registerForm.controls['email'];
          if(this.usuarios){ 
          this.usuarios.forEach(usuario=>{
            if (usuario.cc==correo.value){
              if (correo.value != this.users.cc){
                alert('cedula ya registrada');
                correo.setValue('');
              }

            }else {
              //console.log("No such cc!");
              }
          });
        }
        }
        //Validacion de email por metodo con la bd quemada localmente
        validarMail(){
          const correo = this.perfilForm.get('email');
          //this.registerForm.controls['email'];
          if(this.usuarios){ 
          this.usuarios.forEach(usuario=>{
            if (usuario.email==correo.value){
              if (correo.value != this.users.email){
                alert('email ya registrada');
                correo.setValue('');
              }
            }else {
              //console.log("No such email!");
              }
          });
        }
        }
        onCancel(){
          //window.location.reload();
          this.dialog.close();
        }

      }



Fácilmente se empieza con la incialización y creación de nuestro formulario con cada uno de los items que se posee, se crea un array de habilidades que nos permitirá elegir máximo 3. y unos chips que servirán para poder meter dentro de pequeñas etiquetas las profesiones en las cuales el usuario se puede desempeñar, trabajamos también en esta sección con la API de municipios para el autocompletado de este mismo. y por ultimo tenemos nuestros métodos más importantes que son OnRegister que guardará todos los cambios que realicemos a nuestro perfil y onCancel que cerrará el modal sin guardar cambios. existen otros métodos como ValidarCC el cual recorre con un foreach los usuarios con cédula para compararla con la ingresada para ver si existe o no dicho número dentro de nuestra base de datos y un pequeño validar mail con la misma función de recorrido.