## Trabajo Práctico 8
#### 4- Desarrollo:
#### Prerequisitos:
 - Azure CLI instalado 

#### 4.1 Modificar nuestro pipeline para construir imágenes Docker de back y front y subirlas a ACR
- Desarrollo del punto 4.1: 
##### 4.1.1 Crear archivos DockerFile para nuestros proyectos de Back y Front
##### - En la raiz de nuestro repo crear una carpeta docker con dos subcarpetas api y front, dentro de cada una de ellas colocar los dockerfiles correspondientes para la creación de imágenes docker en función de la salida de nuestra etapa de Build y Test
![Descripción Imagen 1](imagenes/1.jpg)
![Descripción Imagen 1](imagenes/2.jpg)
![Descripción Imagen 1](imagenes/3.jpg)

##### 4.1.2 Crear un recurso ACR en Azure Portal siguiendo el instructivo 5.1
![Descripción Imagen 1](imagenes/4.jpg)
##### 4.1.3 Modificar nuestro pipeline en la etapa de Build y Test
##### - Luego de la tarea de publicación de los artefactos de Back agregar la tarea de publicación de nuestro dockerfile de back para que esté disponible en etapas posteriores:
![Descripción Imagen 1](imagenes/5.jpg)
##### - Luego de la tarea de publicación de los artefactos de Front agregar la tarea de publicación de nuestro dockerfile de front para que esté disponible en etapas posteriores:
![Descripción Imagen 1](imagenes/6.jpg)
##### 4.1.4 En caso de no contar en nuestro proyecto con una ServiceConnection a Azure Portal para el manejo de recursos, agregar una service connection a Azure Resource Manager como se indica en instructivo 5.2 
![Descripción Imagen 1](imagenes/7.jpg)
##### 4.1.5 Agregar a nuestro pipeline variables 
![Descripción Imagen 1](imagenes/8.jpg)
##### 4.1.6 Agregar a nuestro pipeline una nueva etapa que dependa de nuestra etapa de Build y Test
##### - Agregar tareas para generar imagen Docker de Back
![Descripción Imagen 1](imagenes/9.jpg)
![Descripción Imagen 1](imagenes/10.jpg)
##### 4.1.7 - Ejecutar el pipeline y en Azure Portal acceder a la opción Repositorios de nuestro recurso Azure Container Registry. Verificar que exista una imagen con el nombre especificado en la variable backImageName asignada en nuestro pipeline
![Descripción Imagen 1](imagenes/11.jpg)
![Descripción Imagen 1](imagenes/12.jpg)
##### 4.1.8 - Agregar tareas para generar imagen Docker de Front (DESAFIO)
#####  	  - A la etapa creada en 4.1.6 Agregar tareas para generar imagen Docker de Front
![Descripción Imagen 1](imagenes/13.jpg)
![Descripción Imagen 1](imagenes/14.jpg)
![Descripción Imagen 1](imagenes/15.jpg)
![Descripción Imagen 1](imagenes/16.jpg)
##### 4.1.9 - Agregar a nuestro pipeline una nueva etapa que dependa de nuestra etapa de Construcción de Imagenes Docker y subida a ACR
##### - Agregar variables a nuestro pipeline:
![Descripción Imagen 1](imagenes/17.jpg)
##### - Agregar variable secreta cnn-string-qa desde la GUI de ADO que apunte a nuestra BD de SQL Server de QA como se indica en el instructivo 5.3
![Descripción Imagen 1](imagenes/18.jpg)
##### - Agregar tareas para crear un recurso Azure Container Instances que levante un contenedor con nuestra imagen de back
![Descripción Imagen 1](imagenes/19.jpg)
![Descripción Imagen 1](imagenes/20.jpg)
##### Edito el Program.cs para que utilice la variable
![Descripción Imagen 1](imagenes/21.jpg)
##### Se otorgan permisos desde Azure CLI
![Descripción Imagen 1](imagenes/22.jpg)
![Descripción Imagen 1](imagenes/23.jpg)
##### 4.1.10 - Ejecutar el pipeline y en Azure Portal acceder al recurso de Azure Container Instances creado. Copiar la url del contenedor y navegarlo desde browser. Verificar que traiga datos.
![Descripción Imagen 1](imagenes/24.jpg)
![Descripción Imagen 1](imagenes/25.jpg)
![Descripción Imagen 1](imagenes/26.jpg)
  	     
#### 4.4 Desafíos:
##### - 4.4.1 Agregar tareas para generar imagen Docker de Front. (Punto 4.1.8)
![Descripción Imagen 1](imagenes/27.jpg)
![Descripción Imagen 1](imagenes/28.jpg)
![Descripción Imagen 1](imagenes/29.jpg)
![Descripción Imagen 1](imagenes/30.jpg)
##### - 4.4.2 Agregar tareas para generar en Azure Container Instances un contenedor de imagen Docker de Front. (Punto 4.1.11)
![Descripción Imagen 1](imagenes/31.jpg)
![Descripción Imagen 1](imagenes/32.jpg)
![Descripción Imagen 1](imagenes/33.jpg)
![Descripción Imagen 1](imagenes/34.jpg)
![Descripción Imagen 1](imagenes/35.jpg)
![Descripción Imagen 1](imagenes/36.jpg)
![Descripción Imagen 1](imagenes/37.jpg)
![Descripción Imagen 1](imagenes/38.jpg)
![Descripción Imagen 1](imagenes/39.jpg)
![Descripción Imagen 1](imagenes/40.jpg)
##### - 4.4.3 Agregar tareas para correr pruebas de integración en el entorno de QA de Back y Front creado en ACI. 
![Descripción Imagen 1](imagenes/41.jpg)
![Descripción Imagen 1](imagenes/42.jpg)
![Descripción Imagen 1](imagenes/43.jpg)
![Descripción Imagen 1](imagenes/44.jpg)
![Descripción Imagen 1](imagenes/45.jpg)
![Descripción Imagen 1](imagenes/46.jpg)
##### - 4.4.4 Agregar etapa que dependa de la etapa de Deploy en ACI QA y genere contenedores en ACI para entorno de PROD.
![Descripción Imagen 1](imagenes/47.jpg)
![Descripción Imagen 1](imagenes/48.jpg)
![Descripción Imagen 1](imagenes/49.jpg)
![Descripción Imagen 1](imagenes/50.jpg)
![Descripción Imagen 1](imagenes/51.jpg)
![Descripción Imagen 1](imagenes/52.jpg)
![Descripción Imagen 1](imagenes/53.jpg)
