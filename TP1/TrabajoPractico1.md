## **TRABAJO PRACTICO 1** 
### Creación de Repos 1
#### 1. Crear Repo en GitHub.
![Descripción Imagen 1](imagenes/1.png)
#### 2. Clonarlo localmente.
![Descripción Imagen 1](imagenes/2.png)
![Descripción Imagen 1](imagenes/3.png)
#### 3. Editar archivo Readme.md, agregar algunas líneas con texto a dicho archivo.
![Descripción Imagen 1](imagenes/4.png)
#### Verifico el cambio con un git status
![Descripción Imagen 1](imagenes/5.png)
#### 4.	Editar (crearlo si no existe) el archivo .gitignore. Agregar *.bak
![Descripción Imagen 1](imagenes/6.png)
#### 5. Crear un commit y proveer un mensaje descriptivo.
![Descripción Imagen 1](imagenes/7.png)
#### 6. Hacer un push al repositorio remoto
![Descripción Imagen 1](imagenes/8.png)
![Descripción Imagen 1](imagenes/9.png)

### Creación de clave SSH
#### 1. Ir al directorio ssh y generar una clave usando el mail de la cuenta de GitHub
![Descripción Imagen 1](imagenes/10.png)
![Descripción Imagen 1](imagenes/11.png)
#### 2.	Abrir el archivo id_rsa.pub con el editor y copiar todo el contenido
#### 3. En la cuenta de GitHub ir a Settings SSH y crear una nueva clave con el contenido copiado.
![Descripción Imagen 1](imagenes/12.png)
#### 4. Verficar conexión
![Descripción Imagen 1](imagenes/13.png)

### Creación de Repos 2
#### 1.	Crear un repositorio local en un nuevo directorio.
#### 2.	Crear archivo .gitignore.
![Descripción Imagen 1](imagenes/14.png)
#### 3.	Agregar archivo Readme.md, agregar algunas líneas con texto a dicho archivo.
![Descripción Imagen 1](imagenes/15.png)
#### 4.	Crear un commit y proveer un mensaje descriptivo.
![Descripción Imagen 1](imagenes/16.png)
#### 5.	Crear repo en github.
![Descripción Imagen 1](imagenes/17.png)
#### 6.	Asociar local con remoto.
![Descripción Imagen 1](imagenes/18.png)
![Descripción Imagen 1](imagenes/19.png)

### Ramas
#### 1.	Crear una nueva rama
#### 2.	Cambiarse a esa rama
![Descripción Imagen 1](imagenes/20.png)
#### 3.	Hacer un cambio en el archivo Readme.md y hacer commit
![Descripción Imagen 1](imagenes/21.png)
![Descripción Imagen 1](imagenes/22.png)
#### 4. Revisar la diferencia entre ramas
![Descripción Imagen 1](imagenes/23.png)

### Merge
#### 1. Hacer un merge FF (fast-forward)
![Descripción Imagen 1](imagenes/24.png)
#### 2. Borrar la rama creada
![Descripción Imagen 1](imagenes/25.png)
#### 3. Ver el log de commits
![Descripción Imagen 1](imagenes/26.png)
#### 4. Repetir el ejercicio 6 para poder hacer un merge con No-FF 
![Descripción Imagen 1](imagenes/27.png)
![Descripción Imagen 1](imagenes/28.png)
![Descripción Imagen 1](imagenes/29.png)
![Descripción Imagen 1](imagenes/30.png)
##### Luego realicé un git merge --no-ff newFeature
![Descripción Imagen 1](imagenes/31.png)

### Resolución de conflictos
#### 1.	Crear una nueva rama conflictBranch
![Descripción Imagen 1](imagenes/32.png)
#### 2. Realizar una modificación en la linea 1 del Readme.md desde main y commitear
![Descripción Imagen 1](imagenes/33.png)
![Descripción Imagen 1](imagenes/34.png)
##### Acá realicé el cambio de la línea desde el main
#### 3. En la conflictBranch modificar la misma línea del Readme.md y commitear
![Descripción Imagen 1](imagenes/35.png)
![Descripción Imagen 1](imagenes/36.png)
![Descripción Imagen 1](imagenes/37.png)
#### 4.	Ver las diferencias con git difftool main conflictBranch
![Descripción Imagen 1](imagenes/38.png)
#### 5.	Cambiarse a la rama main e intentar mergear con la rama conflictBranch
#### 6.	Resolver el conflicto con git mergetool
![Descripción Imagen 1](imagenes/39.png)
![Descripción Imagen 1](imagenes/40.png)
#### 7.	Agregar .orig al .gitignore
#### 8.	Hacer commit y push
##### Realice echo "*.orig" >> .gitignore 
![Descripción Imagen 1](imagenes/41.png)
![Descripción Imagen 1](imagenes/42.png)

### Pull Request
#### 1. Explicar que es un pull request.
##### Un Pull Request es una solicitud que alguien que ha hecho una copia (fork) de un repositorio de código hace al dueño del repositorio original, pidiendo que los cambios que ha hecho en su copia sean añadidos al proyecto original.
##### EJEMPLO: user2 ha hecho cambios en su copia del repositorio y ahora le está pidiendo a user1 (el dueño del repositorio original) que incorpore esos cambios en el proyecto principal.
#### 2.	Crear un branch local y agregar cambios a dicho branch.
![Descripción Imagen 1](imagenes/43.png)
![Descripción Imagen 1](imagenes/44.png)
#### 3.	Subir el cambio a dicho branch y crear un pull request.
#### 4.	Completar el proceso de revisión en github y mergear el PR al branch master.
![Descripción Imagen 1](imagenes/45.png)
![Descripción Imagen 1](imagenes/46.png)
![Descripción Imagen 1](imagenes/47.png)
![Descripción Imagen 1](imagenes/48.png)

