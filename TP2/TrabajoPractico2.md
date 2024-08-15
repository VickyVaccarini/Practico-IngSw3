## **TRABAJO PRACTICO 2** 
### Docker
#### 1. Obtengo la imagen BusyBox
![Descripción Imagen 1](imagenes/1.png)
![Descripción Imagen 1](imagenes/2.png)
![Descripción Imagen 1](imagenes/3.png)
#### 2. Ejecutando contenedores
![Descripción Imagen 1](imagenes/4.png)
#### 3. Ejecutando en modo interactivo
![Descripción Imagen 1](imagenes/5.png)
![Descripción Imagen 1](imagenes/6.png)
#### Para salir uusamos exit
#### 4. Borrando contenedores terminados
![Descripción Imagen 1](imagenes/7.png)
![Descripción Imagen 1](imagenes/8.png)
#### 5. Construir una imagen
#### Describir las siguientes instrucciones:
##### •	FROM: traemos la imagen base
##### •	RUN: corre un comando dentro del contenedor
##### •	ADD: agrega archivos
##### •	COPY: copia archivos
##### •	EXPOSE: expone puertos
##### •	CMD: otra forma de decirle que haga algo
##### •	ENTRYPOINT: el más importante, nos dice con qué archivo ejecutable queda corriendo mi contenedor
![Descripción Imagen 1](imagenes/9.png)
![Descripción Imagen 1](imagenes/10.png)
![Descripción Imagen 1](imagenes/11.png)
#### A continuación, vemos qué hace cada línea del Dockerfile
![Descripción Imagen 1](imagenes/12.png)
![Descripción Imagen 1](imagenes/13.png)
![Descripción Imagen 1](imagenes/14.png)
#### Ver imágenes disponibles
![Descripción Imagen 1](imagenes/15.png)
#### a. Subir imagen a nuestra cuenta de dockerhub
#### b. Iniciar session en Docker Hub y ver si estas autenticado desde la terminal
![Descripción Imagen 1](imagenes/16.png)
#### c. Etiquetar la imagen a subir con tu nombre de usuario de Docker Hub y el nombre de la imagen. 
#### d. Subir la Imagen
#### e. Verificar la Subida
![Descripción Imagen 1](imagenes/17.png)
![Descripción Imagen 1](imagenes/18.png)
#### 6. Publicando puertos
![Descripción Imagen 1](imagenes/19.png)
![Descripción Imagen 1](imagenes/20.png)
![Descripción Imagen 1](imagenes/21.png)
#### Lo corro de nuevo pero publicando el puerto 74
![Descripción Imagen 1](imagenes/22.png)
![Descripción Imagen 1](imagenes/23.png)
#### De forma gráfica y en el puerto 73:
![Descripción Imagen 1](imagenes/24.png)
![Descripción Imagen 1](imagenes/25.png)
#### 7. Modificar Dockerfile para soportar bash
![Descripción Imagen 1](imagenes/26.png)
![Descripción Imagen 1](imagenes/27.png)
![Descripción Imagen 1](imagenes/28.png)
#### 8. Montando volúmenes
![Descripción Imagen 1](imagenes/29.png)
![Descripción Imagen 1](imagenes/30.png)
#### 9. Utilizando una base de datos
![Descripción Imagen 1](imagenes/31.png)
![Descripción Imagen 1](imagenes/32.png)
![Descripción Imagen 1](imagenes/33.png)
##### •	docker run: Crea y ejecuta un nuevo contenedor, configurando una instancia de PostgreSQL con almacenamiento persistente, y la expone para que sea accesible desde fuera del contenedor.
##### •	docker exec: Proporciona acceso interactivo a un contenedor en ejecución, permitiendo la administración directa de la base de datos u otras operaciones de mantenimiento dentro del entorno del contenedor.
#### 10. Hacer el punto anterior con Microsoft SQL Server
![Descripción Imagen 1](imagenes/34.png)
![Descripción Imagen 1](imagenes/35.png)
![Descripción Imagen 1](imagenes/36.png)
#### El comando sqlcmd no está disponible en el contenedor de SQL Server o la ruta es incorrecta. 
#### Por eso, accedemos al contenedor de SQL Server con una shell interactiva para investigar y una vez dentro del contenedor, busco el archivo sqlcmd
![Descripción Imagen 1](imagenes/37.png)
#### Acá veo que sqlcmd está en /opt/mssql-tools18/bin/sqlcmd (otra ruta).
![Descripción Imagen 1](imagenes/38.png)
#### Conectándome a DBeaver
![Descripción Imagen 1](imagenes/39.png)



