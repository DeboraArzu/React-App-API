
# React-App-API
Proyecto Final

A lo largo de este curso se trabajo una `Full stack app`.

## FrontEnd
Al comienzo de este proyecto se realizo el `CRUD` en Angular, posteriormente se realizó el cambio a React debido a que este es un lenguaje que mantiene su tendencia de popularidad a diferencial de Angular.
Se empleo `React-Bootstrap` para manejar el diseño de la página.

## BackEnd
Para este se empleo NodeJs, se realizo una conexión con una base de datos MongoDB alojada en AWS, el resultado final fue una
[API con conexión a Mongo](https://github.com/DeboraArzu/Laboratorio6)

## FullStack
Como siguiente punto en la implementación se llevo a cabo la [unión del BackEnd con el FrontEnd](https://github.com/DeboraArzu/BackEnd-FrontEnd).

## Docker
Para independizar cada uno de los servicios de BackEnd y FrontEnd cada uno se coloco en [Docker](https://github.com/DeboraArzu/DockerLab). En esta fase se aprendió como realizar un Dockerfile y un Docker-Compose, el objetivo final de esto sería Dockerizar la aplicación en la nube.

## Servicios en la nube
Como ya antes mencionado, el punto final del proyecto fue colocar el BackEnd y el FrontEnd en la [nube](https://github.com/DeboraArzu/Laboratorio-9) y que estos se pudieran comunicar entre ellos y de esta manera poder apreciar el flujo completo del CRUD. 
La página esta en Azure mientras que la base de datos MongoDB se encuentra en AWS.

**FrontEnd**
http://13.68.132.145:3000/home/
**BackEnd**
http://13.68.132.145:4000/home/products
