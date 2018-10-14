# Configuracion de Un servidor Con Node Js y Express 

```
'use strict'

// Llamar a las dependencias
const express    = require('express');
const bodyParser = require('body-parser');
const request    = require('request');
// uso de express
const app = express(); 

// modificar el puerto para el servidor
app.set('port' , '5000');
// obtener respuestas en formato JSON 
app.use(bodyParser.json());


//Primera ruta 
app.get('/' , function(req , response){
	response.send('Hola Mundo!');
})

//token 
app.get('/webhook' , function(req, response){
	if(req.query['hub.verify_token'] === 'pugpizza_token' ){

		response.send(req.query['hub.challenge'])
	} else {
		response.send("Pug pizaa no tiene permisos")
	}
})

// escuchar el puerto 
app.listen(app.get('port') , function(){

	console.log(`Nuestro servidor esta corriendo en el Puerto: ${app.get('port')} `)
})
```