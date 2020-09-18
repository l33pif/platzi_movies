# platzi movies database

movies database with 

queries to do:

SELECT ciudades.ciudad_id,
	   ciudades.ciudad,
	   COUNT(*) AS rentas_por_ciudad
FROM ciudades
	INNER JOIN direcciones ON ciudades.ciudad_id = direcciones.ciudad_id
	INNER JOIN tiendas ON tiendas.direccion_id = direcciones.direccion_id
	INNER JOIN inventarios ON inventarios.tienda_id = tiendas.tienda_id
	INNER JOIN rentas ON inventarios.inventario_id = rentas.inventario_id
GROUP BY ciudades.ciudad_id;
		
    
   -------------
   
   SELECT peliculas.pelicula_id,
		tipos_cambio.tipo_cambio_id,
		tipos_cambio.cambio_usd * peliculas.precio_renta AS precio_mxn
FROM peliculas,
	tipos_cambio
WHERE tipos_cambio.codigo = 'MXN';


--------------------
SELECT date_part('year', rentas.fecha_renta) AS anio,
	date_part('month', rentas.fecha_renta) AS mes,
	COUNT(*) AS num_rentas
FROM rentas
GROUP BY anio, mes
ORDER BY anio, mes;

------------------------
