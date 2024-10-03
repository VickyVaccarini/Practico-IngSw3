## Trabajo Práctico 8
#### 4- Desarrollo:
#### Prerequisitos:
 - Azure CLI instalado 

#### 4.1 Modificar nuestro pipeline para construir imágenes Docker de back y front y subirlas a ACR
- Desarrollo del punto 4.1: 
	- ##### 4.1.1 Crear archivos DockerFile para nuestros proyectos de Back y Front
   	  - En la raiz de nuestro repo crear una carpeta docker con dos subcarpetas api y front, dentro de cada una de ellas colocar los dockerfiles correspondientes para la creación de imágenes docker en función de la salida de nuestra etapa de Build y Test
![Descripción Imagen 1](imagenes/1.jpg)
![Descripción Imagen 1](imagenes/2.jpg)
![Descripción Imagen 1](imagenes/3.jpg)

   	- ##### 4.1.2 Crear un recurso ACR en Azure Portal siguiendo el instructivo 5.1
![Descripción Imagen 1](imagenes/4.jpg)
  	- ##### 4.1.3 Modificar nuestro pipeline en la etapa de Build y Test
   	  - Luego de la tarea de publicación de los artefactos de Back agregar la tarea de publicación de nuestro dockerfile de back para que esté disponible en etapas posteriores:
![Descripción Imagen 1](imagenes/5.jpg)
   	  - Luego de la tarea de publicación de los artefactos de Front agregar la tarea de publicación de nuestro dockerfile de front para que esté disponible en etapas posteriores:
![Descripción Imagen 1](imagenes/6.jpg)
  	- ##### 4.1.4 En caso de no contar en nuestro proyecto con una ServiceConnection a Azure Portal para el manejo de recursos, agregar una service connection a Azure Resource Manager como se indica en instructivo 5.2 
![Descripción Imagen 1](imagenes/7.jpg)
  	- ##### 4.1.5 Agregar a nuestro pipeline variables 
![Descripción Imagen 1](imagenes/8.jpg)
  	- ##### 4.1.6 Agregar a nuestro pipeline una nueva etapa que dependa de nuestra etapa de Build y Test
  	  - Agregar tareas para generar imagen Docker de Back
   	  
   	     ```yaml
		# #----------------------------------------------------------
		# ### STAGE BUILD DOCKER IMAGES Y PUSH A AZURE CONTAINER REGISTRY
		# #----------------------------------------------------------
		
		- stage: DockerBuildAndPush
		  displayName: 'Construir y Subir Imágenes Docker a ACR'
		  dependsOn: BuildAndTestBackAndFront #NOMBRE DE NUESTRA ETAPA DE BUILD Y TEST
		  jobs:
		    - job: docker_build_and_push
		      displayName: 'Construir y Subir Imágenes Docker a ACR'
		      pool:
		        vmImage: 'ubuntu-latest'
		
		      steps:
		        - checkout: self
		
		        #----------------------------------------------------------
		        # BUILD DOCKER BACK IMAGE Y PUSH A AZURE CONTAINER REGISTRY
		        #----------------------------------------------------------
		
		        - task: DownloadPipelineArtifact@2
		          displayName: 'Descargar Artefactos de Back'
		          inputs:
		            buildType: 'current'
		            artifactName: 'drop-back'
		            targetPath: '$(Pipeline.Workspace)/drop-back'
		        
		        - task: DownloadPipelineArtifact@2
		          displayName: 'Descargar Dockerfile de Back'
		          inputs:
		            buildType: 'current'
		            artifactName: 'dockerfile-back'
		            targetPath: '$(Pipeline.Workspace)/dockerfile-back'
		
		        - task: AzureCLI@2
		          displayName: 'Iniciar Sesión en Azure Container Registry (ACR)'
		          inputs:
		            azureSubscription: '$(ConnectedServiceName)'
		            scriptType: bash
		            scriptLocation: inlineScript
		            inlineScript: |
		              az acr login --name $(acrLoginServer)
		    
		        - task: Docker@2
		          displayName: 'Construir Imagen Docker para Back'
		          inputs:
		            command: build
		            repository: $(acrLoginServer)/$(backImageName)
		            dockerfile: $(Pipeline.Workspace)/dockerfile-back/dockerfile
		            buildContext: $(Pipeline.Workspace)/drop-back
		            tags: 'latest'
		
		        - task: Docker@2
		          displayName: 'Subir Imagen Docker de Back a ACR'
		          inputs:
		            command: push
		            repository: $(acrLoginServer)/$(backImageName)
		            tags: 'latest'
	  ```yaml
  	
  	- ##### 4.1.7 - Ejecutar el pipeline y en Azure Portal acceder a la opción Repositorios de nuestro recurso Azure Container Registry. Verificar que exista una imagen con el nombre especificado en la variable backImageName asignada en nuestro pipeline
  	  ![image](https://github.com/user-attachments/assets/57f0f0d2-2a23-4a8a-a1a0-6f5d4ea48756)

	- ##### 4.1.8 - Agregar tareas para generar imagen Docker de Front (DESAFIO)
  	  - A la etapa creada en 4.1.6 Agregar tareas para generar imagen Docker de Front
  	- ##### 4.1.9 - Agregar a nuestro pipeline una nueva etapa que dependa de nuestra etapa de Construcción de Imagenes Docker y subida a ACR
	  - Agregar variables a nuestro pipeline:
  	  ```yaml
  	  ResourceGroupName: 'NOMBRE_GRUPO_RECURSOS' #Por ejemplo 'TPS_INGSOFT3_UCC'
	  backContainerInstanceNameQA: 'NOMBRE_CONTAINER_BACK_QA' #Por ejemplo 'as-crud-api-qa'
	  backImageTag: 'latest' 
	  container-cpu-api-qa: 1 #CPUS de nuestro container de QA
	  container-memory-api-qa: 1.5 #RAM de nuestro container de QA
  	  ```
  	  - Agregar variable secreta cnn-string-qa desde la GUI de ADO que apunte a nuestra BD de SQL Server de QA como se indica en el instructivo 5.3
  	    
  	  - Agregar tareas para crear un recurso Azure Container Instances que levante un contenedor con nuestra imagen de back
  	  ```yaml
  	  #----------------------------------------------------------
		### STAGE DEPLOY TO ACI QA
		#----------------------------------------------------------
		
		- stage: DeployToACIQA
		  displayName: 'Desplegar en Azure Container Instances (ACI) QA'
		  dependsOn: DockerBuildAndPush
		  jobs:
		    - job: deploy_to_aci_qa
		      displayName: 'Desplegar en Azure Container Instances (ACI) QA'
		      pool:
		        vmImage: 'ubuntu-latest'
		
		      steps:
		        #------------------------------------------------------
		        # DEPLOY DOCKER BACK IMAGE A AZURE CONTAINER INSTANCES QA
		        #------------------------------------------------------
		
		        - task: AzureCLI@2
		          displayName: 'Desplegar Imagen Docker de Back en ACI QA'
		          inputs:
		            azureSubscription: '$(ConnectedServiceName)'
		            scriptType: bash
		            scriptLocation: inlineScript
		            inlineScript: |
		              echo "Resource Group: $(ResourceGroupName)"
		              echo "Container Instance Name: $(backContainerInstanceNameQA)"
		              echo "ACR Login Server: $(acrLoginServer)"
		              echo "Image Name: $(backImageName)"
		              echo "Image Tag: $(backImageTag)"
		              echo "Connection String: $(cnn-string-qa)"
		          
		              az container delete --resource-group $(ResourceGroupName) --name $(backContainerInstanceNameQA) --yes
		
		              az container create --resource-group $(ResourceGroupName) \
		                --name $(backContainerInstanceNameQA) \
		                --image $(acrLoginServer)/$(backImageName):$(backImageTag) \
		                --registry-login-server $(acrLoginServer) \
		                --registry-username $(acrName) \
		                --registry-password $(az acr credential show --name $(acrName) --query "passwords[0].value" -o tsv) \
		                --dns-name-label $(backContainerInstanceNameQA) \
		                --ports 80 \
		                --environment-variables ConnectionStrings__DefaultConnection="$(cnn-string-qa)" \
		                --restart-policy Always \
		                --cpu $(container-cpu-api-qa) \
		                --memory $(container-memory-api-qa)
  	  ```
  	  - ##### 4.1.10 - Ejecutar el pipeline y en Azure Portal acceder al recurso de Azure Container Instances creado. Copiar la url del contenedor y navegarlo desde browser. Verificar que traiga datos.
  	  - ##### 4.1.11 - Agregar tareas para generar un recurso Azure Container Instances que levante un contenedor con nuestra imagen de front (DESAFIO)
  	  	- A la etapa creada en 4.1.9 Agregar tareas para generar contenedor en ACI con nuestra imagen de Front
  	        - Tener en cuenta que el contenedor debe recibir como variable de entorno API_URL el valor de una variable container-url-api-qa definida en nuestro pipeline.
  	        - Para que el punto anterior funcione el código fuente del front debe ser modificado para que la url de la API pueda ser cambiada luego de haber sido construída la imagen. Se deja un ejemplo de las modificaciones a realizar en el repo https://github.com/ingsoft3ucc/CrudAngularConEnvironment.git
  	  - ##### 4.1.12 - Agregar tareas para correr pruebas de integración en el entorno de QA de Back y Front creado en ACI.
  	     
#### 4.4 Desafíos:
- 4.4.1 Agregar tareas para generar imagen Docker de Front. (Punto 4.1.8)
- 4.4.2 Agregar tareas para generar en Azure Container Instances un contenedor de imagen Docker de Front. (Punto 4.1.11)
- 4.4.3 Agregar tareas para correr pruebas de integración en el entorno de QA de Back y Front creado en ACI. (Punto 4.1.12)
- 4.4.4 Agregar etapa que dependa de la etapa de Deploy en ACI QA y genere contenedores en ACI para entorno de PROD.
