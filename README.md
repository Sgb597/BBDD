<p align="center">
    <img src=https://github.com/Sgb597/BBDD/blob/master/imgs/SongGuesser.png>
</p>

# Proyecto Individual
## Tecnologías de Almacenamiento de datos no Relacionales
## Sebastián García Bustamante
  
### Índice

- Introducción 
- MongoDB
- Aplicación
- Diseño de la Base de Datos  	
- CRUD	– Create	(Inserts) 	
- CRUD – Read	(Queries) 	
- CRUD	– Update	(Updates) 	
- CRUD	– Delete	(Remove)
- MongoDB Atlas

## Introducción 
### NoSQL
NoSQL es un término que se utiliza para describir un conjunto de bases de datos que se diferencian de las relacionales (RDBMS) en los siguientes aspectos: 

- Esquema prescindible, desnormalización, escalan horizontalmente y en sus premisas no está garantizar ACID.

Las Bases de Datos surgen en los tiempos que  los servicios de redes sociales como Facebook, Twitter o Ebay aparecieron; estos necesitaban dar servicio a miles de usuarios concurrentes y responder millones de peticiones diarias y la tecnología relacional no podía satisfacer el nivel de escalabilidad ni el rendimiento adecuado Adicionalmetne, los avances en virtualización condujeron a uan arquitectura distribuida de computación en la nube (cloud computing), que a su vez requería nodos de almacenamiento distribuido y escalable horizontalmente (cloud storage).

En estas bases de datos se utiliza el término BASE en lugar de ACID, el cual significa:

- Basically Available, está operativo la mayoría del tiempo
- Soft state, los datos en las diferentes réplicas no tienen que ser mutuamente consistentes en todo momento.
- Eventually Consistent, se asegura la consistencia solo después de que pase cierto tiempo.

## MongoDB

### Historia
MongoDB: derivado de la palabra inglesa “humongous” (enorme). El desarrollo de la base de datos MongoDB inicia en el 2007 cuando la empresa 10gen Inc. desarrollaba un producto similar al Google App Engine (un servicio PaaS como plataforma de computación en la nube con el fin de proporcionar servicios para desarrollar y alojar aplicaciones web en datacenters administrados por Google). 10gen Inc. (ahora llamada MongoDB Inc.) lanzó la base de datos MongoDB como producto el 2009 bajo licencia de código abierto AGPL.

### Funcionamiento
MongoDB es una base de datos no relacional basada en documentos. Estos documentos tienen un formato llamado BSON que es muy similar al JSON. El BSON tiene funcoinalidades adicionales a las del formato JSON y estas incluyen:

- Tipos de datos adicionales.

- En teoría diseñado para ocupar menos espacio que un JSON.

- Diseñado para busquedas más eficientes.

En una base de datos Mongo se tienen los siguientes conjuntos:

1. Colección: un conjunto de documentos cuya comparación al modelo relacional sería una tabla de datos. Sin embargo, de forma predeterminada no tiene un esquema estricto para los datos y siempre tienen ID's únicos.

2. Documento: Conjunto de campos de campo-valor similar a las filas en las relacionales. Adicionalmente, estos documentos pueden contener documentos embebidos dentro de ellos para crear relaciones entre colecciones.

3. Campos: Similar a las columnas en el modelo relacional. Son campos que se rellenan con datos y sobre los que se crean índices.

## Aplicación
### SongGuesser

Esta base de datos Mongo  está pensada para un proyecto personal desarrollado con amigos egresados del grado en Ingeniería Informática que consiste en un juego utilizando Spotify. La aplicación web tiene como nombre provicional 'SongGuesser' y le presentaría a los usuarios registrados un juego cuyo objetivo es hacer más dinámicas las reuniones  entre amigos al hacer que el grupo de personas tengan que adivinar los nombres de las canciones que están sonando. 

Los usuarios escogerán una playlist o artista del cual pueden reproducir música para poner aprueba el conocimiento propio y el de su grupo de amigos. 

Esta aplicación empezó como un proyecto para familiarizarse con NodeJS para la programación de código backend. El conjunto de tecnologías o stack es denimonado 'MEAN' usando las siglas de las tencologías que se emplean:

- NodeJS: Uno de los puntos más importantes es que ejecuta el código JavaScript fuera del navegador. Es multiplataforma y Open Source.
- Express: Express es un framework web construido en Node.js y se utiliza para crear APIs y para crear aplicaciones web.
- Angular: Angular es un framework open source para el front-end desarrollado por Google.
- MongoDB: La base de datos NoSQL.

<p align="center">
    <img src=https://th.bing.com/th/id/R.8e37fdda5b3d836fa65522272eef9b34?rik=tkOEu4ekZGl4IA&riu=http%3a%2f%2feluminoustechnologies.com%2fblog%2fwp-content%2fuploads%2f2017%2f01%2f7-Features-of-MEAN-Stack_785.png&ehk=To3u9ZIzyKvNhDrmbrOJIrI%2bT40w7z66FIYb4dbxCDI%3d&risl=&pid=ImgRaw>
</p>


## Diseño de la Base de Datos
Para la base de datos se han creado 6 colecciones distintas para almacenar y mostrar la información necesaria. Los nombres de las seis colecciones son:

1. User: usuario que utiliza nuestra aplicación para juagr.
2. Artist: Persona que publica su música a Spotify.
3. Track: Una canción
4. Album: Conjunto de canciones publicada por el artista.
5. Playlist: Conjunto de canciones puestas en una lista de reproducción pro un usuario de Spotify. 
6. Match: Una partida en la cual participan los usuarios registrados.

Las colecciones y el modelo de los documentos y con sus campos se pueden ver fácilmente con el siguiente diagrama.

<p align="center">
    <img width="100" height="100" src=https://github.com/Sgb597/BBDD/blob/master/imgs/diagram.png>
</p>

Como se puede ver en el diagrama se han implementado el uso de índices en la base de datos. Los índices se han implementado debido a las consultas que se harían desde el front-end. Los tres campos por los cuales más se buscaría son: 

1. El nombre de una cancíon
2. El nombre de un artista
3. El nombre de una playlist

Los índices implementan una estructura de datos para poder agilizar y optimizar las busquedas y debido a que la aplicación estaría constantemente haciendo uso de la operación `find` con los campos previamente descritos.

## Creación de Base de Datos y Sentencias
Para la creación de la base de datos se ha utilizado el software proporcionado por MongoDB llamado Compass. Este software permite la conectarse a bases de datos locales y remotas para poder gestionarlas a través de una interfaz gráfica intuitiva. Adicionalmente, se proporciona una consola desde la cual se pueden realizar las consultas de una manera cómoda al poder ver los datos también con la interfaz. 

<p align="center">
    <img src=https://github.com/Sgb597/BBDD/blob/master/imgs/compass1.png>
</p>


Para iniciar la práctica se han utilizado los comandos básicos para configurar el entorno de trabajo:

`show dbs - Nos muestra las base de datos disponibles`

`use	<db	name> - Nos permite utilizar una base de datos en concreto.`

`db - Muestra que base de datos estamos usando.`

`help Muestra ayuda con los comandos`

`show collections nos muestra las colecciones acutalmente disponibles en la base de datos que estamos usando.`

## CRUD	– Create	(Inserts) 
Para la creación de las colecciones se ha utilizado herramientas que revisan y ayudan a crear documentos con los campos requeridos. Para esto se ha usado JSONLint (https://jsonlint.com/) para verificar que los JSON escritos son correctos y adicionalmente se ha utilizado JSONSchema (https://www.jsonschema.net/) para crear los schemas de mi base de datos. Se ha utilizado este sitio web ya que permite especificar un schema para la base de datos a base de JSON con el fin de 

## CRUD – Read	(Queries) 

`db.track.find({artistTitle:"Daft Punk"})`

`db.playlist.find({trackIds: ObjectId('60e32b7c577d48ec78c1b404')})`

`db.track.find({trackTitle: "11th Dimension"})`

## CRUD	– Update	(Updates) 

## CRUD	– Delete	(Remove)

## MongoDB Atlas
MongoDB Atlas es una base de datos en la nube totalmente administrada desarrollada por las mismas personas que construyen MongoDB. Atlas se encarga de toda la complejidad de implementar, administrar y sanar sus implementaciones en el proveedor de servicios en la nube de su elección (AWS, Azure y GCP). 

MongoDB Atlas tiene un free tier para poder realizar pruebas y familiarizarse con el entorno DBaaS (Database as a Service) que ellos proporcionan. Este servicio no solo facilita el despliegue en la nube de una base de datos, sino que proporciona al usuario con servicios de métricas y gráficos que permiten visualizar y entender mejor los datos almacenados y también el rendimiento del sistema. Por ejemplo, el servicio de Atlas permite monitorizar el rendimiento de nuestra base de datos con el uso de dashboards. 

<p align="center">
    <img src=https://github.com/Sgb597/BBDD/blob/master/imgs/atlas_metrics.png>
</p>

Adicionalmente nos permite visualizar cómo se comportan nuestros datos de una manera visual con el uso de gráficos que fácilmente se añaden a un dashboard inicial como en el siguiente ejemplo donde se muestra como en los usuarios suele verse una tendencia en la cual los usuarios que son Premium (pagan suscripción a Spotify) suelen ganar más juegos.

<p align="center">
    <img src=https://github.com/Sgb597/BBDD/blob/master/imgs/atlas_charts.png>
</p>

En el caso de este proyecto, se ha desplegado la base de datos en MongoDB Atlas usando el free tier que proporcionan para que los usuarios aprendan el entorno. Esto se ha facilitado debido a que Atlas es capaz de leer ficheros JSON para crear colecciones y documentos. Al utilizar el software MongoDB Compass para la creación y modificación de la base de datos SongGuesser has sido fácil el exportar todo el contenido como ficheros JSON para que Atlas lea y cree datos a base de los ficheros JSON siguiendo el schema que se tenía en los datos.