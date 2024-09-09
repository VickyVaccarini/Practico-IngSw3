## **TRABAJO PRACTICO 5** 

#### 1. Crear una cuenta en Azure
![Descripción Imagen 1](imagenes/1.jpg)

#### 2. Crear un recurso Web App en Azure Portal y navegar a la url provista
![Descripción Imagen 1](imagenes/2.jpg)
![Descripción Imagen 1](imagenes/3.jpg)
![Descripción Imagen 1](imagenes/4.jpg)
![Descripción Imagen 1](imagenes/5.jpg)
![Descripción Imagen 1](imagenes/6.jpg)
![Descripción Imagen 1](imagenes/8.jpg)

#### 3. Actualizar Pipeline de Build para que use tareas de DotNetCoreCLI@2 como en el pipeline clásico, luego crear un Pipeline de Release en Azure DevOps con CD habilitada
![Descripción Imagen 1](imagenes/9.jpg)
![Descripción Imagen 1](imagenes/10.jpg)
#### Creamos un pipeline de release
![Descripción Imagen 1](imagenes/11.jpg)
![Descripción Imagen 1](imagenes/12.jpg)
![Descripción Imagen 1](imagenes/13.jpg)
![Descripción Imagen 1](imagenes/14.jpg)
![Descripción Imagen 1](imagenes/15.jpg)
![Descripción Imagen 1](imagenes/16.jpg)
![Descripción Imagen 1](imagenes/17.jpg)
![Descripción Imagen 1](imagenes/18.jpg)
#### Le cambio el nombre
![Descripción Imagen 1](imagenes/19.jpg)

#### 4. Optimizar Pipeline de Build. 
#### El pipeline del build ya está optimizado (.yaml que nos pasó el profe)

#### 5. Verificar el deploy en la url de la WebApp /weatherforecast
![Descripción Imagen 1](imagenes/20.jpg)
![Descripción Imagen 1](imagenes/21.jpg)
![Descripción Imagen 1](imagenes/22.jpg)

#### 6. Realizar un cambio al código del controlador para que devuelva 7 pronósticos, realizar commit, evaluar ejecución de pipelines de build y release, navegar a la url de la webapp/weatherforecast y corroborar cambio
![Descripción Imagen 1](imagenes/23.jpg)
#### Luego del commit se ejecutan los pipelines y vemos que lo hacen de forma correcta
![Descripción Imagen 1](imagenes/24.jpg)
![Descripción Imagen 1](imagenes/25.jpg)
#### Vemos que están los 7 pronósticos
![Descripción Imagen 1](imagenes/26.jpg)

#### 7. Clonar la Web App de QA para que contar con una WebApp de PROD a partir de un Template Deployment en Azure Portal y navegar a la url provista para la WebApp de PROD.
![Descripción Imagen 1](imagenes/27.jpg)
![Descripción Imagen 1](imagenes/28.jpg)
![Descripción Imagen 1](imagenes/29.jpg)
![Descripción Imagen 1](imagenes/30.jpg)
![Descripción Imagen 1](imagenes/31.jpg)
![Descripción Imagen 1](imagenes/32.jpg)

#### 8. Agregar una etapa de Deploy a Prod en Azure Release Pipelines
![Descripción Imagen 1](imagenes/33.jpg)
![Descripción Imagen 1](imagenes/34.jpg)
![Descripción Imagen 1](imagenes/35.jpg)

#### 9. Realizar un cambio al código del controlador para que devuelva 10 pronósticos, realizar commit, evaluar ejecución de pipelines de build y release, navegar a la url de la webapp/weatherforecast y corroborar cambio, verificar que en la url de la webapp_prod/weatherforecast se muestra lo mismo. 
![Descripción Imagen 1](imagenes/36.jpg)
#### Vemos que en el QA aparecen los 10 pronósticos
![Descripción Imagen 1](imagenes/37.jpg)
#### Y también vemos que aparecen en el PROD
![Descripción Imagen 1](imagenes/38.jpg)

#### 10. Modificar pipeline de release para colocar una aprobación manual para el paso a Producción.
![Descripción Imagen 1](imagenes/39.jpg)

#### 11. Realizar un cambio al código del controlador para que devuelva 5 pronósticos, realizar commit, evaluar ejecución de pipelines de build y release, navegar a la url de la webapp/weatherforecast y corroborar cambio, verificar que en la url de la webapp_prod/weatherforecast aun se muestra la versión anterior.
![Descripción Imagen 1](imagenes/40.jpg)
#### Vemos que solo se actualizó en el QA
![Descripción Imagen 1](imagenes/41.jpg)

#### 12. Aprobar el pase ya sea desde el release o desde el mail recibido.
![Descripción Imagen 1](imagenes/42.jpg)
![Descripción Imagen 1](imagenes/43.jpg)
![Descripción Imagen 1](imagenes/44.jpg)
#### Se hizo el deploy a PROD
![Descripción Imagen 1](imagenes/45.jpg)
#### Notar que se puede dar la aprobación, pero posponer su aplicación hasta una determinada fecha

#### 13. Esperar a la finalización de la etapa de Pase a Prod y luego corroborar que en la url de la webapp_prod/weatherforecast se muestra la nueva versión coinicidente con la de QA.
![Descripción Imagen 1](imagenes/46.jpg)

#### 14. Realizar un pipeline (no release) que incluya el deploy a QA y a PROD con una aprobación manual. El pipeline debe estar construido en YAML sin utilizar el editor clásico de pipelines ni el editor clásico de pipelines de release.
![Descripción Imagen 1](imagenes/47.jpg)
![Descripción Imagen 1](imagenes/48.jpg)
![Descripción Imagen 1](imagenes/49.jpg)
![Descripción Imagen 1](imagenes/50.jpg)






