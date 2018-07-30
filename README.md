# calculator Service
Coding Challenge: Calculator Service of Ditech

Autor: Johan Alexis Ruiz Echavarria

---------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------
COMO ESTÁ CONSTRUIDA LA APLICACIÓN

	- Tecnologias utilizadas:
		- .NET Framework 4.6
		- ASP.NET
		- Entity Framework 6.2 
		- Unity: utilizado para la inyección de dependencias

	-Prerrequisitos:
		- Dispobibilidad de servidor de base de datos Microsoft SQL Server 

	- Estructura de la solución:
	La solución consiste principalmente en un sistema cliente - servidor donde el cliente está representado por una
	aplicación de consola que sirve de componente de interacción con el usuario y un servidor consistente en un Web API
	el cual el encargado de ofrecer las capacidades de negocio de la aplicación, para este caso las operaciones
	aritmeticas.

	-Arquitectura
	Con el objetivo de mostrar las capacidades de desarrollo de una aplicación altamente estructturada y con 
	caracteristicas de un sistema de información robusto y dirigido por drivers de arquiectura, como el bajo 
	acoplamiento y alta cohesion por ejemplo, se determinó adoptar DDD (diseño dirigido por el dominio).

	Es por esta razón que la solución cuenta con componentes diferenciados en las siguientes capas:

		- Capa de Presentación: componentes de front - end, en este caso representado por la aplicacion de consola.

		- Capa de aplicación:   componentes livianos que se encargan de disponer las capacidades de negocio ofrecidas
					por el componente de negocio. En este caso el componente consiste en un web API que
					expone diferentes endpoint que ejecutan cada una de las operaciones matematicas.

		- Capa de negocio:	Componentes que representan el CORE del negocio, esta contienen las entidades 
					y toda la logica negocio de la aplicación.
					En esta solución, este componente es una dll que contiene toda la logica de las 
					operaciones matematicas de la calculadora.
					Para la correcta implementacion de inyección de dependecnias, en este componente 
					tambien se incluyen las interfaces de los repositorios y servicios
					de negocio.

		- Capa de infraestructra: 	Esta capa incluye principalmente los componentes de acceso a repositorios de base 
						de datos y aquellos transversales a toda la solución como utilitarios de seguridad
						y logs tecnicos.
						En nuestro caso, contamos con dos componentes en esta capa, uno llamado Repository
						que es el encargado del acceso a la base de datos y el llamado CROSS que se
						encarga de realizar el registro en un log para registro de excepciones.

---------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------
INSTRUCCIONES DE INSTALACIÓN

1. Despliegue de WEB API

	1.1 Abrir la solución en Visual Studio 2017

	1.2 En el directorio C:\inetpub\wwwroot crear una carpeta con el nombre "Calculator"

	1.3 En la solución hacer clic derecho sobre el proyecto CalculatorService.WebApi, seleccionar las opciones "Publicar" ->
		Carpeta y mediante el botón "Examinar" seleccione la carpeta creada en el numeral anterior.

	1.4 Dirigirse a la carpeta creada anteriormente y abrir el archivo Web.Config, modificar el string de conexión 
		asignando los siguientes valores:
		- data source= nombre de servidor de base de datos
		- User ID= usuario de base de datos
		- Password= clave del usuario de base de datos
	    Guardar los cambios realizados.

	1.5 Abrir IIS y crear una nueva aplicación haciendo clic derecho en "Default Web Site", diligenciar los siguintes campos:
		- Alias: Calculator
		- Ruta de acceso fisica: el path de la carpeta de despliegue creada en el paso 1.2
	    
	     	Ya Creado el sitio verificar su correcto funcionamiento haciendo clic en este y luego en la opción "Examinar*:80", al hacer
		esto se abrirá una nueva ventana de browser, copie la url de esta ventana ya que será utilizada posteriormente.

2. Despliegue de aplicación de consola

	2.1 En la solución hacer clic derecho sobre el proyecto CalculatorService.Client y seleccione la opcion "Compilar".

	2.2 Ahora haga nuevamente clic derecho sobre el protecto y seleccione "Abrir carpeta en el explorador de archivos", ahora 
		dirijase a la capeta bin\Debug 

	2.3 Abrir el archivo App.Config para editar, en la clave key="URL" asigne como valor la URL obtenida en el paso 1.5. Guarde los cambios.

		La carpeta actual contiene los archivos necesarios para ejecutar la consola, si desea puede copiarlos y llevarlos a otro
		directorio para ejecutar desde allí la aplicación.

---------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------
EJECUCIÓN DE LA APLICACIÓN

Lurgo de ejecutar las operaciones de instalación simplemente ejecute la aplicación llamada CalculatorService.Client
