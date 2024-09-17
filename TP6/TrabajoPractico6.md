## **TRABAJO PRACTICO 6** 

#### Prerequisitos: Instalar Node, npm, AngularCLI y Dotnet8
![Descripción Imagen 1](imagenes/1.jpg)
![Descripción Imagen 1](imagenes/2.jpg)
![Descripción Imagen 1](imagenes/3.jpg)

#### 4.1 Creación de una BD SQL Server para nuestra App
#### A. Crear una BD Azure SQL Database 

![Descripción Imagen 1](imagenes/4.jpg)
![Descripción Imagen 1](imagenes/5.jpg)
![Descripción Imagen 1](imagenes/6.jpg)
![Descripción Imagen 1](imagenes/8.jpg)

#### 4.2 Obtener nuestra App
#### A. Clonar el repo https://github.com/ingsoft3ucc/Angular_WebAPINetCore8_CRUD_Sample.git
![Descripción Imagen 1](imagenes/9.jpg)
#### B. Seguir las instrucciones del README.md del repo clonado prestando atención a la modificación de la cadena de conexión en el appSettings.json para que apunte a la BD creada en 4.1
![Descripción Imagen 1](imagenes/10.jpg)
#### C. Navegar a http://localhost:7150/swagger/index.html y probar uno de los controladores para verificar el correcto funcionamiento de la API.
![Descripción Imagen 1](imagenes/11.jpg)
#### D. Navegar a http://localhost:4200 y verificar el correcto funcionamiento de nuestro front-end Angular 
![Descripción Imagen 1](imagenes/12.jpg)
#### E. Una vez verificado el correcto funcionamiento de la Aplicación procederemos a crear un proyecto de pruebas unitarias para nuestra API.

#### 4.3 Crear Pruebas Unitarias para nuestra API
#### A. En el directorio raiz de nuestro repo crear un nuevo proyecto de pruebas unitarias para nuestra API 
![Descripción Imagen 1](imagenes/13.jpg)
#### B. Instalar dependencias necesarias
##### cd EmployeeCrudApi.Tests 
##### dotnet add package Moq
##### dotnet add package xunit
##### dotnet add package Microsoft.EntityFrameworkCore.InMemory
#### C. Editar archivo UnitTest1.cs 
![Descripción Imagen 1](imagenes/14.jpg)
#### D. Renombrar archivo UnitTest1.cs por EmployeeControllerUnitTests.cs
![Descripción Imagen 1](imagenes/15.jpg)
#### E. Editar el archivo EmployeeCrudApi.Tests/EmployeeCrudApi.Tests.csproj para agregar una referencia a nuestro proyecto de EmployeeCrudApi reemplazando su contenido por
![Descripción Imagen 1](imagenes/16.jpg)
#### F. Ejecutar los siguientes comandos para ejecutar nuestras pruebas G. Verificar que se hayan ejecutado correctamente las pruebas
![Descripción Imagen 1](imagenes/17.jpg)
#### H. Verificar que no estamos usando una dependencia externa como la base de datos.
#### I. Modificar la cadena de conexión en el archivo appsettings.json para que use un usuario o password incorrecto y recompilar el proyecto EmployeeCrudApi
![Descripción Imagen 1](imagenes/18.jpg)
#### J. Verificar que nuestro proyecto ya no tiene acceso a la BD navegando a http://localhost:7150/swagger/index.html y probando uno de los controladores:
![Descripción Imagen 1](imagenes/19.jpg)
#### K. En la carpeta de nuestro proyecto EmployeeCrudApi.Tests volver a correr las pruebas 
![Descripción Imagen 1](imagenes/20.jpg)
#### L. Verificar que se hayan ejecutado correctamente las pruebas inclusive sin tener acceso a la BD, lo que confirma que es efectivamente un conjunto de pruebas unitarias que no requieren de una dependencia externa para funcionar.
#### M. Modificar la cadena de conexión en el archivo appsettings.json para que use el usuario y password correcto y recompilar el proyecto EmployeeCrudApi
![Descripción Imagen 1](imagenes/21.jpg)
#### N. Verificar que nuestro proyecto vuelve a tener acceso a la BD navegando a http://localhost:7150/swagger/index.html y probando uno de los controladores
![Descripción Imagen 1](imagenes/22.jpg)
#### 4.4 Creamos pruebas unitarias para nuestro front de Angular:
#### A. Nos posicionamos en nuestro proyecto de front, en el directorio EmployeeCrudAngular/src/app
#### B. Editamos el archivo app.component.spec.ts reemplazando su contenido por:
![Descripción Imagen 1](imagenes/23.jpg)
#### C. Creamos el archivo employee.service.spec.ts reemplazando su contenido por: 
![Descripción Imagen 1](imagenes/24.jpg)
#### D. Editamos el archivo employee.component.spec.ts ubicado en la carpeta employee reemplazando su contenido por:
![Descripción Imagen 1](imagenes/25.jpg)
#### E. Editamos el archivo addemployee.component.spec.ts ubicado en la carpeta addemployee reemplazando su contenido por:
![Descripción Imagen 1](imagenes/33.jpg)
#### F. En el directorio raiz de nuestro proyecto EmployeeCrudAngular ejecutamos el comando ng test
#### G. Vemos que se abre una ventana de Karma con Jasmine en la que nos indica que los tests se ejecutaron correctamente
![Descripción Imagen 1](imagenes/26.jpg)
#### H. Vemos que los tests se ejecutaron correctamente:
![Descripción Imagen 1](imagenes/27.jpg)
#### I. Verificamos que no esté corriendo nuestra API navegando a http://localhost:7150/swagger/index.html y recibiendo esta salida:
![Descripción Imagen 1](imagenes/28.jpg)
#### J. Los puntos G y H nos indican que se han ejecutado correctamente las pruebas inclusive sin tener acceso a la API, lo que confirma que es efectivamente un conjunto de pruebas unitarias que no requieres de una dependencia externa para funcionar.

#### 4.5 Agregamos generación de reporte XML de nuestras pruebas de front.
#### Para cuando integremos nuestras pruebas en un pipeline de Build, vamos a necesitar el resultado devuelto por nuestras pruebas para reportarlas junto a las pruebas de back que se reportan automáticamente.
#### A.	Instalamos dependencia karma-junit-reporter
![Descripción Imagen 1](imagenes/29.jpg)
#### B.	En el directorio raíz de nuestro proyecto (al mismo nivel que el archivo angular.json) creamos un archivo karma.conf.js con el siguiente contenido
![Descripción Imagen 1](imagenes/30.jpg)
#### C.	Ejecutamos nuestros test de la siguiente manera:
![Descripción Imagen 1](imagenes/31.jpg)
#### D.	Verificamos que se creó un archivo test-result.xml en el directorio test-results que está al mismo nivel que el directorio src
![Descripción Imagen 1](imagenes/32.jpg)

#### 4.6 Modificamos el código de nuestra API y creamos nuevas pruebas unitarias:
#### A. Realizar al menos 5 de las siguientes modificaciones sugeridas al código de la API:
#### •	La longitud máxima del nombre y apellido del empleado debe ser de 100 caracteres.
#### •	Validar que el nombre tenga un número mínimo de caracteres, por ejemplo, al menos dos caracteres para evitar entradas inválidas como "A".
#### •	Verificar que el nombre no contenga números, ya que no es común en los nombres de empleados.
#### •	Verificar que no haya palabras vacías o que el nombre no esté compuesto solo de espacios.
#### •	Asegurar que cada parte del nombre (separada por espacios) tenga al menos un carácter o más, por ejemplo, para evitar "A B".
#### En todos los casos donde no se cumplan las condiciones, la API debe devolver un error de HTTP 400 Bad Request y un Json indicando el error, por ejemplo: { "status": 400, "error": "Bad Request", "message": "El nombre del empleado ya existe." }
![Descripción Imagen 1](imagenes/34.jpg)
![Descripción Imagen 1](imagenes/35.jpg)
![Descripción Imagen 1](imagenes/36.jpg)

#### B. Crear las pruebas unitarias necesarias para validar las modificaciones realizadas en el código
![Descripción Imagen 1](imagenes/37.jpg)
![Descripción Imagen 1](imagenes/38.jpg)
![Descripción Imagen 1](imagenes/39.jpg)4
#### Vemos que se ejecutan correctamente
![Descripción Imagen 1](imagenes/40.jpg)

#### 4.7 Modificamos el código de nuestro Front y creamos nuevas pruebas unitarias:
![Descripción Imagen 1](imagenes/41.jpg)
#### A. Realizar en el código del front las mismas modificaciones hechas a la API. 
![Descripción Imagen 1](imagenes/42.jpg)
![Descripción Imagen 1](imagenes/43.jpg)
#### B. Las validaciones deben ser realizadas en el front sin llegar a la API, y deben ser mostradas en un toast como por ejemplo https://stackblitz.com/edit/angular12-toastr?file=src%2Fapp%2Fapp.component.ts o https://stackblitz.com/edit/angular-error-toast?file=src%2Fapp%2Fcore%2Frxjsops.ts
![Descripción Imagen 1](imagenes/44.jpg)
#### C. Crear las pruebas unitarias necesarias en el front para validar las modificaciones realizadas en el código del front.
![Descripción Imagen 1](imagenes/45.jpg)
![Descripción Imagen 1](imagenes/46.jpg)
![Descripción Imagen 1](imagenes/47.jpg)
![Descripción Imagen 1](imagenes/48.jpg)




