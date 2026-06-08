# Plan de Ejecucion de Pruebas Automatizadas con Postman

**Proyecto:** API Productos Mongo Node Express  
**Actividad:** Pruebas Automatizadas con API de Postman  
**Aprendiz:** Juan Sebastian Cajiao Cardona  
**Ficha:** 3064975  
**Instructor:** Cesar Marino Cuellar Chacon  
**Fecha:** 08/06/2026  

---

## Descripcion General

Este proyecto contiene la evidencia de pruebas automatizadas con **Postman** para una API REST de productos desarrollada con **Node.js**, **Express** y **MongoDB**.

La actividad valida el funcionamiento de las rutas CRUD de productos, verificando codigos de estado, estructura de respuesta, variables dinamicas, consulta por identificador, actualizacion, eliminacion y tiempo de respuesta.

La coleccion de Postman utiliza las siguientes variables:

| Variable | Descripcion |
|---|---|
| `base_url` | URL base de la API: `http://127.0.0.1:3000/api/productos` |
| `ID_PRODUCTO` | Guarda el identificador del producto creado para consultar, actualizar y eliminar |
| `CANTIDAD_PRODUCTOS` | Guarda la cantidad de productos obtenidos en la respuesta GET |
| `CODIGO_PRODUCTO` | Genera un codigo dinamico para evitar errores por codigos repetidos |

---

## Archivos Principales

| Archivo | Descripcion |
|---|---|
| `server.js` | Inicia el servidor en el puerto 3000 |
| `app.js` | Configura Express, JSON y rutas de productos |
| `routes/producto.js` | Define las rutas CRUD de productos |
| `controllers/producto.js` | Contiene la logica de crear, obtener, actualizar y eliminar productos |
| `models/producto.js` | Define el esquema de producto en MongoDB |
| `Juan_Sebastian_Cajiao_Cardona.postman_collection.json` | Coleccion Postman exportada con scripts de prueba |
| `Ejecucion_Casos_Prueba_Juan_Sebastian_Cajiao_Cardona.docx` | Documento formal de ejecucion de casos de prueba |
| `newman_100_iterations_report.json` | Reporte tecnico de ejecucion con Newman |

---

## Requisitos Previos

Antes de ejecutar las pruebas se debe tener instalado:

- Node.js
- npm
- MongoDB local activo
- Postman

La base de datos configurada es:

```text
mongodb://localhost:27017/Tienda-ADSO
```

---

## Instalacion De Dependencias

Desde la carpeta del proyecto, ejecutar:

```bash
npm install
```

---

## Ejecucion Del Backend

Para iniciar la API de productos, ejecutar:

```bash
npm start
```

Tambien se puede iniciar directamente con:

```bash
node server.js
```

Al ejecutar correctamente debe mostrarse un mensaje similar a:

```text
Servidor corriendo en puerto 3000
```

La API queda disponible en:

```text
http://127.0.0.1:3000/api/productos
```

Importante: la terminal donde se ejecuta el backend debe permanecer abierta mientras se hacen las pruebas en Postman.

---

## Ejecucion En Postman

### 1. Importar la coleccion

En Postman:

1. Hacer clic en **Import**.
2. Seleccionar el archivo:

```text
Juan_Sebastian_Cajiao_Cardona.postman_collection.json
```

3. Verificar que la variable `base_url` tenga este valor:

```text
http://127.0.0.1:3000/api/productos
```

### 2. Ejecutar la coleccion

La coleccion debe ejecutarse completa en este orden:

1. Crear producto
2. Obtener productos
3. Obtener producto por ID
4. Actualizar producto
5. Eliminar producto

### 3. Ejecutar con Runner

Para cumplir la actividad, ejecutar la coleccion con la siguiente configuracion:

| Configuracion | Valor |
|---|---|
| Iterations | `100` |
| Delay | `500 ms` |

Al finalizar, tomar captura del resultado general donde se evidencie que las pruebas pasaron correctamente.

---

## Casos De Prueba

| # | Nombre del caso | Metodo | Ruta | Validaciones principales | Estado esperado | Resultado |
|---|---|---|---|---|---|---|
| 1 | Crear producto | POST | `/api/productos` | Codigo 201, precio tipo number, `_id`, codigo dinamico, tiempo menor a 5000 ms | `201 Created` | PASSED |
| 2 | Obtener productos | GET | `/api/productos` | Codigo 200, respuesta tipo array, campo `codigo`, actualizacion de `CANTIDAD_PRODUCTOS` | `200 OK` | PASSED |
| 3 | Obtener producto por ID | GET | `/api/productos/:id` | Codigo 200, `_id` correcto, campo `codigo` | `200 OK` | PASSED |
| 4 | Actualizar producto | PUT | `/api/productos/:id` | Codigo 200, atributo `producto`, tipo object, nombre actualizado | `200 OK` | PASSED |
| 5 | Eliminar producto | DELETE | `/api/productos/:id` | Codigo 200, atributo `mensaje`, texto `Producto eliminado` | `200 OK` | PASSED |

---

## Scripts De Prueba En Postman

Los scripts de la coleccion validan:

- Codigos de estado esperados.
- Estructura de respuesta JSON.
- Tipos de datos.
- Tiempo de respuesta menor a 500 milisegundos.
- Uso de variables dinamicas.
- Guardado automatico de `ID_PRODUCTO`.
- Actualizacion de `CANTIDAD_PRODUCTOS`.
- Mensaje de eliminacion: `Producto eliminado`.

---

## Evidencia De Ejecucion

La coleccion fue validada con Newman y se obtuvo el siguiente resultado:

| Metrica | Resultado |
|---|---|
| Iteraciones | `100` |
| Peticiones ejecutadas | `500` |
| Aserciones ejecutadas | `1700` |
| Fallos | `0` |

---

## Entregables

Para la actividad de Postman se entregan los siguientes archivos:

| Archivo | Uso |
|---|---|
| `Juan_Sebastian_Cajiao_Cardona.postman_collection.json` | Coleccion exportada desde Postman con todos los scripts |
| `Ejecucion_Casos_Prueba_Juan_Sebastian_Cajiao_Cardona.docx` | Plantilla de ejecucion de casos de prueba diligenciada |
| `newman_100_iterations_report.json` | Soporte opcional de ejecucion automatizada |
| `EJECUCION_PLAN_PRUEBAS.md` | Guia de ejecucion y resumen de la actividad |

---

## Referencias

- Documentacion oficial de Postman: https://learning.postman.com/docs/tests-and-scripts/tests-and-scripts/
- Ejemplos de scripts en Postman: https://learning.postman.com/docs/tests-and-scripts/write-scripts/test-examples/
- Newman: https://www.npmjs.com/package/newman

---

*Actividad: Pruebas Automatizadas con API de Postman | SENA CTPI Cauca | Junio 2026*
