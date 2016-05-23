# Precios Claros API

## GET SucursalesList:
* La api recibe 3 parametros { LATITUD, LONGITUD, LIMITE }

https://8kdx6rx8h4.execute-api.us-east-1.amazonaws.com/prod/sucursales?lat= {LATITUD} &lng= {LONGITUD} &limit= {LIMITE}

* Sucursales response:

``` Json
{
	status: 200,
	totalPagina: 50,
	total: 2327,
	sucursales: [
		{
			distanciaNumero: 0.1332,
			distanciaDescripcion: "0.13 kilómetros",
			banderaId: 3,
			lat: "-34.6000",
			lng: "-58.4312",
			id: "9-3-5231",
			provincia: "AR-C",
			direccion: "Guardia Vieja 4558",
			banderaDescripcion: "Jumbo",
			localidad: "CIUDAD AUTONOMA BUENOS AIRES",
			comercioId: 9
		}
	],
	maxLimitPermitido: 50
}
```

## GET ProductosList:
* La api recibe 3 parametros { ID_SUCURSAR, OFFSET, LIMITE }

https://8kdx6rx8h4.execute-api.us-east-1.amazonaws.com/prod/productos?&id_ sucursal= {ID_SUCURSAR} &offset= {OFFSET} &limit= {LIMITE}

``` Json
{
	status: 200,
	total: 2981,
	maxLimitPermitido: 100,
	maxCantSucursalesPermitido: 50,
	productos: [
		{
			presentacion: "1.5 lt",
			nombre: "Aceite CañUelas Girasol Alto Oleico y Oliva X 1.50 Lt",
			precio: 86.55,
			id: "7792180005359",
			marca: "CAÑUELAS"
		}
	],
	totalPagina: 10
}
```


## GET ProductosDetail:
* La api recibe 3 parametros { LIMITE, ID_PRODUCTO, LATITUD, LONGITUD }

https://8kdx6rx8h4.execute-api.us-east-1.amazonaws.com/prod/producto?limit= {LIMITE} &id_producto= {ID_PRODUCTO} &lat= {LATITUD} &lng= {LONGITUD}

``` Json
{
	status: 200,
	total: 314,
	producto: {
		presentacion: "1.5 lt",
		nombre: "Aceite CañUelas Girasol Alto Oleico y Oliva X 1.50 Lt",
		id: "7792180005359",
		marca: "CAÑUELAS"
	},
	maxLimitPermitido: 50,
	totalPagina: 30,
	sucursales: [
		{
			distanciaNumero: 0.1332,
			distanciaDescripcion: "0.13 kilómetros",
			banderaId: 3,
			lat: "-34.6000",
			lng: "-58.4312",
			actualizadoHoy: true,
			id: "5231",
			provincia: "AR-C",
			preciosProducto: {
			precioLista: 86.55,
				promo1: {
					descripcion: "",
					precio: ""
				},
				promo2: {
					descripcion: "",
					precio: ""
				}
			},
			direccion: "Guardia Vieja 4558",
			banderaDescripcion: "Jumbo",
			localidad: "CIUDAD AUTONOMA BUENOS AIRES",
			comercioId: 9
		},
	]
}
```

### GET SearchProduct:
* La api recibe 3 parametros { QUERY, LATITUD, LONGITUD, OFFSET, LIMITE }

/*
 * https://8kdx6rx8h4.execute-api.us-east-1.amazonaws.com/prod/productos?string=aceite&lat=-34.59880069999999&lng=-58.431125699999996&offset=0&limit=10
 */

https://8kdx6rx8h4.execute-api.us-east-1.amazonaws.com/prod/productos?string= {QUERY} &lat= {LATITUD} &lng= {LONGITUD} &offset= {OFFSET} &limit= {LIMITE}

* Search response:

``` Json
{
  "status": 200,
  "total": 63,
  "maxLimitPermitido": 100,
  "maxCantSucursalesPermitido": 50,
  "productos": [
    {
      "marca": "CAÑUELAS",
      "id": "7792180005359",
      "precioMax": 87.69,
      "precioMin": 86.55,
      "nombre": "Aceite CañUelas Girasol Alto Oleico y Oliva X 1.50 Lt",
      "presentacion": "1.5 lt"
    }
  ],
  "totalPagina": 10
}
```

### GET ProductImage:
* La URL de la imagen recibe el ID de la imagen que trae el response del search.

http://imagenes.preciosclaros.gob.ar/productos/ { IMAGE_ID } .jpg

* Si no hay imagen del producto es necesario insertar una imagen place_holder





### Apps que usan los servicios:
https://play.google.com/store/apps/details?id=ar.com.comprando.comprando

https://play.google.com/store/apps/details?id=com.pochigil.preciosclaros

