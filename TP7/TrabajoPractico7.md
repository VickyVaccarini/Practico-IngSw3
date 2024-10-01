## **TRABAJO PRACTICO 7** 

#### 4.1 Agregar Code Coverage a nuestras pruebas unitarias de backend y front-end e integrarlas junto con sus resultados en nuestro pipeline de build.
#### •	Desarrollo del punto 4.1:
#### o	4.1.1 En el directorio raiz de nuestro proyecto Angular instalar el siguiente paquete:
![Descripción Imagen 1](imagenes/1.jpg)
#### o	4.1.2 Editar nuestro archivo karma.conf.js para que incluya reporte de cobertura
![Descripción Imagen 1](imagenes/2.jpg)
#### o	4.1.3 En el dir raiz del proyecto EmployeeCrudApi.Tests ejecutar:
![Descripción Imagen 1](imagenes/3.jpg)
![Descripción Imagen 1](imagenes/4.jpg)
#### o	4.1.4 Agregar a nuestro pipeline ANTES del Build de Back la tarea de test con los argumentos especificados y la de publicación de resultados de cobertura.
![Descripción Imagen 1](imagenes/5.jpg)
#### o	4.1.5 Agregar a nuestro pipeline ANTES del Build de front la tarea de test y la de publicación de los resultados.
![Descripción Imagen 1](imagenes/6.jpg)
#### o	4.1.6 Ejecutar el pipeline y analizar el resultado de las pruebas unitarias y la cobertura de código.
![Descripción Imagen 1](imagenes/7.jpg)
![Descripción Imagen 1](imagenes/8.jpg)
![Descripción Imagen 1](imagenes/9.jpg)
![Descripción Imagen 1](imagenes/10.jpg)
 
#### •	Desarrollo del punto 4.2: Demostración de cómo integrar SonarCloud en un pipeline de CI/CD y cómo leer los reportes de análisis estático.
![Descripción Imagen 1](imagenes/11.jpg)
#### o	4.2.1 Integraremos SonarCloud para analizar el código fuente. Configurar SonarCloud en nuestro pipeline siguiendo instructivo 5.1
#### -	Antes de nuestra tarea de Build del Back:
![Descripción Imagen 1](imagenes/12.jpg)
#### -	Despues de nuestra tarea de Build del Back:
![Descripción Imagen 1](imagenes/13.jpg)
#### o	4.2.2 Vemos el resultado de nuestro pipeline, en extensions tenemos un link al análisis realizado por SonarCloud
![Descripción Imagen 1](imagenes/14.jpg)
#### o	4.2.3 Ir al link y analizar toda la información obtenida. Detallar en la entrega del TP los puntos más relevantes del informe, qué significan y para qué sirven.
![Descripción Imagen 1](imagenes/15.jpg)
#### El informe de SonarCloud actúa como un escáner del código, proporcionando una evaluación exhaustiva de la calidad del software y la deuda técnica. Identifica problemas como bugs, vulnerabilidades, code smells y duplicados, que afectan el rendimiento y la seguridad de la aplicación. Además, analiza la cobertura de pruebas, resaltando la importancia de tener un alto porcentaje de código cubierto por pruebas automatizadas de calidad. Agrupa los problemas en categorías de Mantenibilidad, Fiabilidad y Seguridad, permitiendo detectar y priorizar arreglos críticos para optimizar el código y facilitar su mantenimiento a largo plazo. En última instancia, SonarCloud no solo ayuda a identificar defectos, sino que también establece un marco para monitorear la calidad del código de forma continua, mejorando así la seguridad y la sostenibilidad del proyecto.

#### 4.3 Pruebas de Integración con Cypress:
#### o	4.3.1 En el directorio raiz de nuestro proyecto Angular instalar el siguiente paquete:
![Descripción Imagen 1](imagenes/16.jpg)
#### o	4.3.2 Abrir Cypress:
![Descripción Imagen 1](imagenes/17.jpg)
#### o	4.3.3 Inicializar Cypress en nuestro proyecto como se indica en el instructivo 5.2
![Descripción Imagen 1](imagenes/18.jpg)
![Descripción Imagen 1](imagenes/19.jpg)
#### o	4.3.4 Crear nuestra primera prueba navegando a nuestro front.
![Descripción Imagen 1](imagenes/20.jpg)
#### o	4.3.5 Correr nuestra primera prueba
![Descripción Imagen 1](imagenes/21.jpg)
#### Si está abierta la interfaz gráfica de Cypress, aparecerá el archivo primer_test.cy.js en la lista de pruebas. Clic en el archivo para ejecutar la prueba. 
![Descripción Imagen 1](imagenes/22.jpg)
#### También es posible ejecutar Cypress en modo "headless" (sin interfaz gráfica) utilizando el siguiente comando: npx cypress run
![Descripción Imagen 1](imagenes/23.jpg)
#### o	4.3.6 Modificar nuestra prueba para que falle.
#### -	Editamos el archivo primer_test.cy.js y hacemos que espere otra cosa en el título
![Descripción Imagen 1](imagenes/24.jpg)
#### -	Ejecutamos cypress en modo headless
![Descripción Imagen 1](imagenes/25.jpg)
#### Cypress captura automáticamente pantallas cuando una prueba falla. Las capturas de pantalla se guardan en la carpeta cypress/screenshots.
#### o	4.3.6 Grabar nuestras pruebas para que Cypress genere código automático y genere reportes: Cerramos Cypress
#### o	Editamos el archivo cypress.config.ts incluyendo la propiedad experimentalStudio en true y la configuración de reportería.
 ![Descripción Imagen 1](imagenes/26.jpg)
#### -	Corremos nuevamente Cypress con npx cypress open, una vez que se ejecute nuestra prueba tendremos la opción de "Add Commands to Test". Esto permitirá interactuar con la aplicación y generar automáticamente comandos de prueba basados en las interacciones con la página:
![Descripción Imagen 1](imagenes/27.jpg) 
#### -	Por ejemplo, si agregamos un nuevo empleado y luego verificamos que esté en la lista, Cypress nos generará un código como este:
![Descripción Imagen 1](imagenes/28.jpg)
![Descripción Imagen 1](imagenes/29.jpg)
#### o	Por supuesto que habrá que hacerle ajustes, como por ejemplo que se fije siempre en la última fila de la grilla y no en la posición 15 como lo grabó, es ahí cuando consultando la documentación de Cypress debemos ver cómo modificar el código, en nuestro caso de ejemplo sería así:
![Descripción Imagen 1](imagenes/30.jpg)
#### o	4.3.7 Hacemos prueba de editar un empleado
#### -	Creamos en cypress/e2e/ un archivo editEmployee_test.cy.js con el siguiente contenido, guardamos y aparecerá en Cypress:
![Descripción Imagen 1](imagenes/31.jpg) 
![Descripción Imagen 1](imagenes/32.jpg)
#### -	Hacemos "Add command to the test" y empezamos a interactuar con la página
#### o	Hacemos algunos ajustes al código generado:
![Descripción Imagen 1](imagenes/33.jpg)
#### 4.4 Desafíos:
#### •	Integrar en el pipeline SonarCloud para nuestro proyecto Angular, mostrar el resultado obtenido en SonarCloud
![Descripción Imagen 1](imagenes/34.jpg) 
![Descripción Imagen 1](imagenes/35.jpg)
![Descripción Imagen 1](imagenes/36.jpg) 
#### •	Implementar en Cypress pruebas de integración que incluya los casos desarrollados como pruebas unitarias del front en el TP06.
![Descripción Imagen 1](imagenes/37.jpg) 
![Descripción Imagen 1](imagenes/38.jpg)
![Descripción Imagen 1](imagenes/39.jpg) 
![Descripción Imagen 1](imagenes/40.jpg)
![Descripción Imagen 1](imagenes/41.jpg) 
![Descripción Imagen 1](imagenes/42.jpg)
![Descripción Imagen 1](imagenes/43.jpg) 
![Descripción Imagen 1](imagenes/44.jpg)
![Descripción Imagen 1](imagenes/45.jpg) 
![Descripción Imagen 1](imagenes/46.jpg)
![Descripción Imagen 1](imagenes/47.jpg) 
![Descripción Imagen 1](imagenes/48.jpg)

#### •	Incorporar al pipeline de Deploy la ejecución de las pruebas de integración y la visualización de sus resultados.
#### •	Resultado esperado:
#### o	Un Pipeline en YAML que incluya a) Build de QA y Front con ejecución y resultado de pruebas de code coverage, pruebas unitarias y análisis de Sonar Cloud y b) Deploy a WebApp(s) de QA y Front que incluya ejecución y resultado de pruebas de integración
![Descripción Imagen 1](imagenes/49.jpg)
#### o	Dos Stages: Una para Build, Test Unitarios, Code Coverage y SonarCloud y otra para el Deploy a QA con Tests de Integración
![Descripción Imagen 1](imagenes/50.jpg)
#### o	En la pestaña Test, poder visualizar los Test Unitarios de Front y Back y los Test de Integracion:
![Descripción Imagen 1](imagenes/51.jpg)
#### o	En la pestaña Code Coverage, visualizar la cobertura de las pruebas unitarias de Back y de Front:
![Descripción Imagen 1](imagenes/52.jpg)
#### o	En la pestaña Extensions, ver el análisis de SonarCloud en verde
![Descripción Imagen 1](imagenes/53.jpg) 
![Descripción Imagen 1](imagenes/54.jpg)
![Descripción Imagen 1](imagenes/55.jpg)
#### 4.4.4 Un documento de una carilla explicando qué información pudieron sacar del análisis de Sonar Cloud y de las pruebas de cobertura.
#### Calidad del Código: El análisis de SonarCloud reveló varias métricas clave sobre la calidad del código:
#### •	Vulnerabilidades: Se identificaron vulnerabilidades que requieren atención para mitigar riesgos de seguridad en la aplicación. 
#### •	Deuda Técnica: El análisis mostró que la deuda técnica está presente, lo cual afecta la mantenibilidad y escalabilidad del proyecto. 
#### Metrologías de Cobertura. Los resultados de las pruebas de cobertura indican lo siguiente:
#### •	Cobertura Total: La cobertura total del código es del 54.55%, lo que significa que, de un total de 209 líneas de código, se han ejecutado 114 líneas durante las pruebas.
#### •	Cobertura por Módulo: Se presentan los resultados de cobertura de algunos módulos críticos:
![Descripción Imagen 1](imagenes/56.jpg)
##### o	Los controladores tienen una cobertura del 100%, lo cual es excelente y muestra que todas las rutas de este módulo están siendo probadas adecuadamente.
##### o	Sin embargo, el archivo Program.cs presenta una cobertura del 0%, lo que indica que no se están ejecutando pruebas en este módulo. Es crucial agregar pruebas para este archivo para mejorar la cobertura total.
##### o	El componente addemployee.component.ts tiene una baja cobertura del 16.07%, lo que sugiere que muchas de sus funcionalidades no están siendo probadas. Se recomienda crear más pruebas para cubrir los casos de uso de este componente.

