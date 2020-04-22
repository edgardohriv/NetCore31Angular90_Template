**1.-** Creamos el proyecto : 

	dotnet new angular --output NetCore31Angular90
	
**2.-** Construimos el proyecto desde el directorio raiz :

	dotnet build
	
**3.-** Entramos a la carpeta ClientApp para construir el proyecto Angular :

	ng build 	
	
**4.-** Corremos el proyecto desde el directorio raiz :

	dotnet run
	
**5.-** Inicializamos el proyecto con Git :

	git init

**6.-** Agregamos todos los archivos al repositorio menos los excluidos en gitignore:

	git add .
	
**7.-** Hacemos el comit de los cambios :

	git commit -m "Initial angular 8.2 template working well"
	
**8.-** Entramos al directorio de la aplicacion angular y actualizamos a la version mas reciente de 8.X : 

	cd ClientApp
	
	ng update @angular/core@8 @angular/cli@8
	
	git commit -m "Update to latest version of Angular 8"
	
**9.-** Dentro de ese mismo directorio ejecutamos un upgrade a la version 9 de angular

	ng update @angular/core@9.0.0 @angular/cli@9.0.0
  
	git commit -m "Upgrade to Angular 9.0.0"
	
**10.-** Nuevamente construimos el proyecto angular para asegurarnos que compilo perfectamente:

	ng build 
	
  36747 |   Window_run: function _run(code, file) {
		  136748 |     if (file) code += '\n//@ sourceURL=' + file;
		> 136749 |     with(this) eval(code);
				 |     ^
		  136750 |   },
		  136751 |   EventHandlerBuilder_build: function build() {
		  136752 |     try {
		See "C:\Users\jason\AppData\Local\Temp\ng-MEnshj\angular-errors.log" for further details.

	Si no te aparece este error pasa al paso numero 13 de lo contrario continua con el siguiente paso :
	
**11.-** Para resolver este error simplemente tenemos que remover o comentar la siguiente linea en el archivo :  **ClientApp/src/main.ts** :
	
    export { renderModule, renderModuleFactory } from '@angular/platform-server';
	
**12.-** Volvemos a tratar de construir el proyecto angular y registramos el issue en la historia del proyecto con git commit: 

	ng build

	git commit  -m "Resolved issue with upgrading template to  angular 9.0.0"
	
**13.-** Volvemos a lanzar el proyecto desde el directorio raiz del mismo 

	dotnet run

**14.-** Puede aparecerte un error como el siguiente que se muestra, si no te aparece este error puedes pasar al paso 15

	#An unhandled exception occurred while processing the request.
	###TimeoutException: The Angular CLI process did not start listening for requests within the timeout period of 0 seconds. Check the log output for error information.
	
  para resolver este error debes abrir el archivo ClientApp/package.json y localizar esta linea :
 
	"start": "ng serve",
  
	debes cambiar el contenido agregabdo una sentencia "echo" como sigue :
  
	"start": "echo Starting... && ng serve",
  
	Asegurate de registrar estos cambios en git :
  
	git commit -m "Resolved issue #2 with template"


**15.-** Hacemos el commit de los cambios ( si no lo hiciste en algun paso anterior )

	git commit -m "Initial angular upgraded to 9.0.0 template working well"
	
**16.-** Registramos el repositorio repoto en GitHub :

	git remote add origin https://github.com/edgardohriv/NetCore31Angular90_Template.git
	
**17.-** Por último subimos todos los archvos fuente al repositorio remoto :

	git push -u origin master
	
**Listo, objetivo Alcanzado :) !!!**
	
He tomado de referencia la siguiente pagina : [Upgrade the Angular .NET Core SPA Template to Angular 9](https://jasontaylor.dev/asp-net-core-angular-9-upgrade/)
