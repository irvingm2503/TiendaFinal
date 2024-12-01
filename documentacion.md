# Tienda Online - Documentación

## Introducción
Este documento proporciona una explicación detallada de cada parte de la tienda online, incluyendo sus funcionalidades y cómo están implementadas.

## Estructura del Proyecto
La estructura del proyecto es la siguiente:


## Archivos HTML

### `index.html`
La página principal de la tienda muestra los productos disponibles de manera dinámica utilizando JavaScript para obtener los datos desde el servidor. Incluye un botón para ver el carrito de compras y otro para vender productos, redirigiendo a las respectivas páginas. La bienvenida personalizada se muestra utilizando datos almacenados en `localStorage`.

### `login.html`
Esta página contiene un formulario de inicio de sesión donde los usuarios pueden ingresar su correo electrónico y contraseña. Utiliza JavaScript para enviar una solicitud al servidor y validar las credenciales. Si el inicio de sesión es exitoso, se redirige al usuario a la página principal, y los datos del usuario se almacenan en `localStorage`.

### `register.html`
En esta página, los nuevos usuarios pueden registrarse proporcionando sus nombres, apellidos, correo electrónico y contraseña. Al enviar el formulario, los datos se envían al servidor para crear una nueva cuenta de usuario en la base de datos. Si el registro es exitoso, el usuario es redirigido a la página de inicio de sesión.

### `carrito.html`
La página del carrito de compras muestra los productos que el usuario ha añadido. Los datos del carrito se obtienen desde `localStorage` y se muestran dinámicamente en la página. También permite a los usuarios proceder con la compra de los artículos en el carrito, actualizando la disponibilidad en la base de datos.

### `myproducts.html`
Esta página muestra los productos que el usuario ha añadido a la tienda. Utilizando JavaScript, obtiene los productos desde el servidor y los muestra de manera dinámica. Los usuarios pueden editar o eliminar sus productos directamente desde esta página, enviando solicitudes de actualización o eliminación al servidor.

### `edit.html`
El formulario de edición de productos permite a los usuarios modificar los detalles de un producto existente. Al cargar la página, se obtienen los datos del producto seleccionado desde el servidor y se rellenan en el formulario. Los cambios se envían al servidor para actualizar la base de datos.

### `shell.html`
Esta página contiene un formulario para agregar nuevos productos a la tienda. Los usuarios deben proporcionar información como el nombre del producto, precio, unidades disponibles, características, descripción y fecha de publicación. Los datos se envían al servidor para crear un nuevo producto en la base de datos.

### `footer.html`
Incluye elementos comunes del pie de página, como el botón de "Salir". Este botón permite a los usuarios cerrar sesión, eliminando los datos de `localStorage` y redirigiéndolos a la página de inicio de sesión.

## Archivos CSS

### `style.css`
Este archivo define los estilos visuales de la tienda, asegurando una experiencia de usuario coherente y atractiva. Incluye estilos para el cuerpo de la página, contenedores principales, formularios, botones y listas de productos. Utiliza variables CSS para mantener consistencia en los colores y facilitar el mantenimiento.

## Archivos JavaScript

### `login.js`
Maneja la lógica de inicio de sesión, incluyendo la validación de campos y la interacción con el servidor. Verifica las credenciales del usuario y, si son correctas, almacena los datos del usuario en `localStorage` y redirige a la página principal. También maneja errores de autenticación, mostrando mensajes apropiados.

### `db.js`
Configura la conexión con la base de datos Supabase utilizando variables de entorno para almacenar las claves de la API. Exporta el cliente Supabase para que pueda ser utilizado en otros archivos del servidor para realizar operaciones en la base de datos.

### `server.js`
Archivo principal del servidor que maneja las rutas API y la interacción con la base de datos. Incluye rutas para la autenticación de usuarios, la gestión de productos (creación, actualización, obtención y eliminación), y la verificación de credenciales. Utiliza Express y Supabase para manejar solicitudes HTTP y operaciones de base de datos, respectivamente.

# Estructura de la Base de Datos `ventas`

## Tabla `usuario`
La tabla `usuario` almacena información sobre los usuarios que interactúan con la tienda. Aquí está su estructura:

```sql
CREATE TABLE usuario (
    id SERIAL PRIMARY KEY,
    nombres VARCHAR(255) NOT NULL,
    apellidos VARCHAR(255) NOT NULL,
    correo VARCHAR(255) NOT NULL UNIQUE,
    contrasena VARCHAR(255) NOT NULL,
    id_favoritos INTEGER,
    id_carrito INTEGER,
    vendedor BOOLEAN,
    numero_telefono VARCHAR(20)
);
```
# Estructura de la Base de Datos `ventas`

## Tabla `producto`
La tabla `producto` almacena información sobre los productos disponibles en la tienda. Aquí está su estructura:

```sql
CREATE TABLE producto (
    id SERIAL PRIMARY KEY,
    vendedor INTEGER REFERENCES usuario(id),
    nombre VARCHAR(255) NOT NULL,
    precio NUMERIC(10, 2) NOT NULL,
    unidades_disponibles INTEGER NOT NULL,
    caracteristicas_js TEXT,
    descripcion TEXT,
    fechapublicacion DATE NOT NULL,
    favoritos INTEGER DEFAULT 0
);
```
#   Inicializar en terminal
deberas ejecutar el codigo estando en la carpeta donde tienes los documentos

```
node server.js
```

## ENTRAR A PAGINA
Debiso a problemas con .netlify no se pudo ejecutar correctamente, pero una vez corrido este cmando en la carpeta donde tienes el documento podras visualizar la pagina en 
```
http://localhost:3000/login.html
```
