# Sistema Satelital   
## 1.	Presentación del proyecto    
### 1.1	Visión global     
El proyecto consiste en la implementación del prototipo de un sistema satelital como el mostrado en la figura. El sistema satelital se compone de dos elementos fundamentales: el satélite y la estación de tierra.    
   
El satélite se encarga de captar datos del espacio, procesarlos y enviarlos periódicamente a la estación de tierra. También recibe órdenes de la estación de tierra que pueden modificar alguna de las tareas que realiza.    
   
La estación de tierra recibe los datos que le envía el satélite y se los muestra al usuario de la manera más clara posible a través de una interfaz gráfica amigable, desde la que el usuario también puede enviar órdenes al satélite.    

<img src="https://github.com/user-attachments/assets/e323d51f-95e6-4069-9fa2-d090085aab35" width="400" height="200">      

### 1.2	 El satélite    
El elemento principal del satélite es un microprocesador Arduino, que llamaremos controlador. El satélite también está equipado con sensores que permiten al controlador adquirir datos de humedad, temperatura y proximidad de objetos que pueden impactar contra el satélite. Además, dispone de sistemas mecánicos que le permiten cambiar la orientación de alguno de los sensores (por ejemplo, del sensor de proximidad).     
   
El controlador también es capaz de proporcionar datos sobre su posición exacta en la órbita que recorre. Y naturalmente, está equipado con los componentes necesarios para comunicarse con la estación de tierra.    
   
El controlador está programado en lenguaje C. El programa obtiene los datos de los diferentes sensores, realiza ciertos procesados de los datos, los envía a la estación de tierra y actúa sobre los elementos mecánicos, a petición del usuario.  
   
### 1.3	La estación de tierra    
Está compuesta por otro microprocesador Arduino y un portátil al que se conecta por USB. El microprocesador hace de intermediario entre el satélite y el portátil. Entrega al portátil los mensajes que recibe del satélite y envía al satélite los comandos que introduce el usuario a través del portátil. También procesa la información que llega del satélite, por ejemplo, para encender alarmas (leds de diferentes colores) en caso necesario. Lógicamente, también tiene incorporados los componentes necesarios para la comunicación con el satélite. El módulo Arduino está programado en C.   
   
La aplicación que se ejecuta en el portátil está programada en Python. Debe tener una interfaz de usuario cara y visualmente agradable. Debe permitir presentar al usuario los datos que se reciben (por ejemplo, una gráfica que muestre la evolución de la temperatura a lo largo del tiempo). También debe permitir al usuario enviar órdenes al satélite (por ejemplo, girar 90º el sensor que mide la proximidad de objetos).   
   
### 1.4	Comunicación 
La comunicación entre la estación de tierra y el satélite utiliza la tecnología LoRa (Long Range). Se trata de una tecnología de comunicación inalámbrica (como también lo son WiFi y Bluetooth), que es especialmente adecuada para comunicaciones a grandes distancias. No obstante, durante buena parte del desarrollo del proyecto, por cuestiones de comodidad y evitación de interferencias, la comunicación se realizará mediante cable.  
   
### 1.5	Demostración   
El siguiente vídeo es un ejemplo del resultado final en funcionamiento, elaborado por alumnos de cursos anteriores.    
   
[![](https://markdown-videos-api.jorgenkh.no/url?url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DnBh4BNyI6vw)](https://www.youtube.com/watch?v=nBh4BNyI6vw)
   
### 1.6	Versiones
Deben implementarse cuatro versiones del sistema satelital, de complejidad creciente. Las características esenciales de cada versión se describen a continuación, aunque los requerimientos precisos se describen en próximos apartados de esta guía y las fechas de entrega se especificarán en el plan de la asignatura.  
   
<ins>Versión 1</ins>  
   
El satélite capta periódicamente los datos que ofrece el sensor de temperatura y humedad y los envía a tierra con la frecuencia establecida. El subsistema de tierra los recibe y los muestra en consola.   
   
El satélite también procesa mínimamente los datos captados (por ejemplo, calculando medias que también envía a tierra).
Además de mostrarlos en consola, la estación de tierra procesa los datos recibidos (por ejemplo, muestra una alarma en el caso de una secuencia alarmante de datos de temperatura).    
   
<ins>Versión 2</ins>    
   
El satélite dispone de un sensor de ultrasonidos que le permite captar datos de proximidad de objetos que pueden dañar al satélite y también los envía a tierra, junto con los datos indicados en la descripción de la versión 1.   
   
La estación de tierra muestra ahora los datos en forma de gráficas lo más claras e informativas posibles, incluyendo las alarmas establecidas en la versión 1. La estación de tierra también dispone de los elementos que le permiten al usuario enviar órdenes al satélite que modifiquen la tarea que realiza (por ejemplo, detener el envío de algunos de los datos o modificar las frecuencias de envío).  
   
Adicionalmente, el sensor de ultrasonidos puede estar montado sobre una plataforma que puede girar movida por un servo-motor. Desde la estación de tierra el usuario debe poder modificar la orientación del sensor de ultrasonidos enviando órdenes que hagan que el controlador actúe sobre el servo-motor.   
   
<ins>Versión 3</ins>    
   
El satélite dispone de un mecanismo que le permite obtener la posición exacta en la que se encuentra dentro de la órbita que recorre. El controlador enviará a tierra esa información periódicamente, junto a los datos ya descritos en las versiones anteriores.   
   
El controlador guarda en ficheros algunos datos de manera que puedan ser recuperados cuando los solicite la estación de tierra.  
    
La estación de tierra muestra al usuario la posición del satélite en cada momento, usando los mapas más adecuados. Además, también guarda en ficheros los datos recibidos y los recupera a petición del usuario. Todo ello debe poder gestionarse de forma cómoda desde la interfaz gráfica de la estación de tierra.   
   
<ins>Versión 4</ins>     
   
La última versión debe incluir todas las funcionalidades adicionales que elija el equipo, en función de su motivación y tiempo disponible. Naturalmente, se esperan funcionalidades espectaculares y sorprendentes.   
   
En las fechas indicadas en la planificación de la asignatura, cada grupo debe entregar el código correspondiente a la versión que se entrega junto con un vídeo de no más de 3 minutos que muestre que el código satisface los requisitos de la versión que se está entregando.   
   
### 1.7	Calificación    

La calificación del proyecto tiene un peso del 40% en la nota final de la asignatura. Esa calificación se obtiene de la siguiente forma:  

•	Calidad del producto final: 30%   
•	Resultados individuales de los exámenes de conocimiento del proyecto: 5%   
•	Resultados grupales de los exámenes de conocimiento del proyecto: 5%   
   
La calidad del producto final se valorará utilizando los criterios que se indican en la tabla siguiente.    
   
| Criterio  | Descripción | Peso |
| ------------- | -------------  | ------------- |
| Correcto |El prototipo realiza correctamente todas las funciones especificadas en los requisitos (la lista completa de esas funcionalidades se proporcionará durante el curso)  |40% 
| Robusto |El sistema resiste sin bloquearse los fallos que puedan producirse (por ejemplo, errores del usuario al interactuar con el sistema o fallos en los sensores del satélite) |7.5% |
| Amigable |El usuario no tiene dudas al interactuar con el sistema a través de la interfaz gráfica, que es, además, visualmente agradable.  |7.5% |
| Organizado y documentado	 |El código del controlador y de la estación de tierra está bien organizado en funciones. Además, se han añadido comentarios adecuados que deben permitir a otras personas, con poco esfuerzo, entender el código y hacer modificaciones si son necesarias	  |10% |
| Eficiente |El código usa siempre los algoritmos más adecuados para realizar las operaciones  |5% |
| Sorprendente |Las funcionalidades adicionales son interesantes, complejas y sorprendentes.	  |20% |
| Bien presentado	 |El vídeo que acompaña a la versión final presenta claramente el funcionamiento del sistema y resulta espectacular  |10% |
| TOTAL |  |100% |


Durante el curso se realizarán dos exámenes de conocimientos del proyecto, coincidiendo con la entrega de dos de las versiones antes descritas. Estos exámenes son individuales y se realizan en clase. Consisten en la realización, en el tiempo indicado, de una sencilla modificación del código del sistema desarrollado por el grupo. Un ejemplo de enunciado de un examen de conocimiento de proyecto puede ser este:   
 
_Añade a la interfaz gráfica de la estación de tierra un botón que haga que los datos de humedad se envíen cada segundo.
Cada examen se calificará con un 10 si durante el tiempo previsto se pone en evidencia que se ha resuelto bien el reto. La calificación será 0 en caso contrario._   
   
La media de las dos notas individuales obtenidas por cada alumno tendrá un peso del 5% en la nota del proyecto de ese alumno. La media de TODAS las notas de los miembros del grupo tendrá un peso de 5% en la nota del proyecto de cada miembro.   


