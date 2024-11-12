# Proyecto de Base de Datos para Blockbuster LLC

Este proyecto simula una base de datos que típicamente se encontraría en un establecimiento de alquiler de películas y videojuegos como Blockbuster LLC. Los clientes están registrados y pueden alquilar películas con un tiempo máximo de alquiler, junto con un histórico de alquileres. La base de datos incluye información sobre las películas disponibles, los empleados y las tiendas.

## Actividades Realizadas

1. **Restauración de la base de datos**:
   - Restauramos la base de datos `alquilerdvd.tar` disponible en GitHub utilizando `psql` y `pg_restore`. Observamos que la base de datos está en un formato `tar`, no en un archivo SQL convencional.

2. **Identificación de elementos de la base de datos**:
   - **Tablas**: Listado completo de todas las tablas de la base de datos.
   - **Vistas**: Identificación de las vistas existentes.
   - **Secuencias**: Determinación de las secuencias empleadas para la generación automática de identificadores.

3. **Identificación de tablas principales y sus elementos clave**:
   - Identificamos las tablas más importantes de la base de datos, como `film`, `customer`, `rental`, `payment`, `staff`, `store`, y `category`. Describimos sus columnas principales y las relaciones que mantienen entre sí.

4. **Consultas realizadas**:
   - **Ventas totales por categoría de películas**: Consulta que obtiene las ventas totales por cada categoría, ordenadas descendentemente.
   - **Ventas totales por tienda**: Consulta que muestra las ventas por tienda, junto con la ciudad, el país (concatenados con coma como separador) y el nombre del encargado de cada tienda.
   - **Lista de películas**: Consulta que devuelve el identificador, título, descripción, categoría, precio, duración, clasificación, y el nombre completo de los actores de cada película.
   - **Información de los actores**: Consulta que muestra los nombres y apellidos de los actores, junto con las categorías y películas en las que participan, con los nombres de categorías y títulos concatenados con “:”.

5. **Creación de vistas**:
   - Se crearon vistas (`view_ventas_categoria`, `view_ventas_tienda`, `view_lista_peliculas`, `view_informacion_actores`) para cada una de las consultas anteriores con el prefijo `view_`.

6. **Análisis del modelo y restricciones `CHECK`**:
   - Se realizó un análisis del modelo de datos y se implementaron restricciones `CHECK` adicionales para asegurar la integridad de los datos en columnas clave, como duración de alquiler, tarifa de alquiler, costo de reemplazo, y fechas de devolución en las tablas `film`, `payment`, y `rental`.

7. **Explicación de la sentencia de disparador en la tabla `customer`**:
   - Analizamos la sentencia `last_updated` en la tabla `customer`, que actualiza automáticamente el campo `last_update` cada vez que se modifica un registro en esta tabla.

8. **Identificación de tablas con soluciones de disparador similares**:
   - Identificamos tablas adicionales que utilizan una solución similar para mantener un registro de la última actualización, como `actor`, `address`, `category`, `film`, `inventory`, `rental`, y `staff`.

9. **Creación de disparadores personalizados**:
   - **Disparador de inserción en `film`**: Creamos un disparador que guarda la fecha de inserción de un nuevo registro en la tabla `film`, registrando el `film_id` y la fecha de inserción en una tabla `film_registers`.
   - **Disparador de eliminación en `film`**: Creamos un disparador que guarda la fecha de eliminación de un registro en la tabla `film`, registrando el `film_id` y la fecha de eliminación en una tabla `film_delete_log`.

10. **Significado y relevancia de las secuencias**:
    - Explicamos el uso de secuencias en la base de datos, su propósito en la generación automática de identificadores únicos, y su importancia para la integridad de los datos en entornos de alta concurrencia.
