
# React-App-API
Proyecto Final

El propósito de Programación Web era que al finalizar el curso se tuviera una pagina Web Full Stack alojada en la nube.
# Contrucción de la pagina
- [x] FrontEnd en Angular (cambio a React)
- [x] BackEnd con NodeJs, MongoDB
- [x] FullStack con Redis
- [x] Docker
- [x] Docker in Azure y MongoDB en AWS

## FrontEnd
Al comienzo de este proyecto se realizo el `CRUD` en Angular, posteriormente se realizó el cambio a React debido a que este es un lenguaje que mantiene su tendencia de popularidad a diferencial de Angular.
Se empleo `React-Bootstrap` para manejar el diseño de la página.

Se siguio la guia para crear una App en React del Git de Facebook [Facebook/create-react-app](https://github.com/facebook/create-react-app). Los comandos que se ejecutaron fueron los siguientes:

```
npx create-react-app cloth-site
cd cloth-site
npm start
```
Para ver la app se debe de ingresar a [http://localhost:3000/](http://localhost:3000/). 

Cuando el proyecto este listo y terminado para mandarlo a producción se ejecuta el comando `npm run build`


## BackEnd
Para este se empleo NodeJs, se realizo una conexión con una base de datos MongoDB alojada en AWS, el resultado final fue una
[API con conexión a Mongo](https://github.com/DeboraArzu/Laboratorio6).

Los comandos que se ejecutaron para construir el BackEnd fueron:
```
npm init
npm install --save express body-parser mongoose
```
Se creo un `app.js` donde se configura la conexion al servidor y el puerto en donde se hara la conexión. 
### Modelo del BackEnd
El BackEnd se creo en base a un MVC; por lo que se tiene un Product.model.js donde se define la estructura del schema de la base de datos de MongoDB
```
const mongoose = require('mongoose');
const Schema = mongoose.Schema;

let ClothSchema = new Schema({
    name: { type: String, required: true, max: 100 },
    size: { type: String, required: true, max: 100 },
    color: { type: String, required: true, max: 100 },
    cost: { type: Number, required: true },
    status: { type: Number, required: true, default:0},
    codigobarra: {type: Number, require: true}
});

// Export the model
module.exports = mongoose.model('Cloth', ClothSchema);
```
Luego se creo un Product.route.js donde se definieron las rutas del APi y un Product.controller.js donde se definieron las acciones para cada verbo.

## FullStack
Como siguiente punto en la implementación se llevo a cabo la [unión del BackEnd con el FrontEnd](https://github.com/DeboraArzu/BackEnd-FrontEnd).
Para realizar la comunicación entre ambos se utilizo la función [Fetch](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Utilizando_Fetch) que ya viene integrada y es reconocida por varios navegadores y se definio un `Proxy` en el archivo `package.json` del FrontEnd.
```
"proxy": "http://localhost:4000"
```
De esta manera al momento de realizar el `Fetch` la app sabia a donde redirigirse.

## Docker
Para independizar cada uno de los servicios de BackEnd y FrontEnd cada uno se coloco en [Docker](https://github.com/DeboraArzu/DockerLab). En esta fase se aprendió como realizar un Dockerfile y un Docker-Compose, el objetivo final de esto sería Dockerizar la aplicación en la nube.

Se instalo Docker en una VM con SO Ubuntu 18.04LTS, se siguio la guia de  instalación de la [página oficial de Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

Los comandos que se ejecutaron fueron:
```
docker build -t <tag de la images>:<verion> .
docker run -d -p <puerto interno>:<puerto externo> <tag de la images>:<verion>
docker-compose up 
```

## Servicios en la nube
Como ya antes mencionado, el punto final del proyecto fue colocar el BackEnd y el FrontEnd en la [nube](https://github.com/DeboraArzu/Laboratorio-9) y que estos se pudieran comunicar entre ellos y de esta manera poder apreciar el flujo completo del CRUD. 
La página esta en Azure mientras que la base de datos MongoDB se encuentra en AWS.

Se creo una base de datos de MongoDb en Mlab y esta esta alojada en AWS.
En azure se creo una VM con una imgen de Docker en Ubuntu. Luego de creada se realizo un `git clone` del repo que contenia el codigo final del proyecto y se realizó el `docker-compose up` para crear los contenedores.

**Notas importantes: fue necesario cambiar el Proxy del package.json del FrontEnd a la dirección pública de la VM y para ejecutar el docker compose up es necesario estar dentro del directorio que contiene el archivo dockercompose.yaml**

**FrontEnd**
http://13.68.132.145:3000/home/
**BackEnd**
http://13.68.132.145:4000/home/products
