# InventarioApi
Trabajo para entrevista

Instalar Dependencias
pip install django djangorestframework mysqlclient


********************************************************************
Crea un entorno virtual en el terminal de visual studio code:

python -m venv venv

Darle permisos de administrador:

Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned


Activa el entorno virtual:

venv\Scripts\activate
********************************************************************
Crear una base de datos en MySQL Workbench:

CREATE DATABASE inventario_simple;

Para ver los datos de la base de datos:

USE inventario_simple;

Ahora buscamos la tabla donde se aloja los datos que ingresamos:

SELECT * FROM productos_producto;

********************************************************************
Configurar MySQL en Django:

Abre el archivo settings.py que esta en inventario de tu proyecto y ajusta la configuración de la base de datos con las credenciales de tu servidor MySQL:


DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'inventario_simple',
        'USER': 'root',  # Cambia 'root' si usas otro usuario
        'PASSWORD': '111296Da',  # Reemplaza por tu contraseña de MySQL
        'HOST': 'localhost',
        'PORT': '3306',
    }
}


********************************************************************

Migraciones de base de datos (esto se hace en la terminal del visual studio code)
Aplica las migraciones para crear las tablas en MySQL:

python manage.py migrate

********************************************************************

Ejecutar el servidor de desarrollo
Para iniciar el servidor de desarrollo de Django, ejecuta en el terminal:


python manage.py runserver
********************************************************************

COMO ES EL USO DE LA API:


Accede a la API en tu navegador o herramienta como Postman en la siguiente URL:

http://127.0.0.1:8000/api/productos/

********************************************************************

*PARA CREAR UN PRODUCTO:
 En el HTML FROM podemos poner los datos y luego darle post
	
 	EJEMPLO
    "nombre": "Producto 1",
    "precio": 2,
    "stock": 10

********************************************************************

*PARA ACTUALIZAR EL PRODUCTO:

Para actualizar un producto, puedes hacer una solicitud PUT a la URL http://localhost:8000/api/productos/<id>/, donde <id> es el ID del producto que quieres actualizar.

IMPORTANTE: UBICARTE EN LA BASE DE DATOS DEL WORKBENCH EL NUMERO DEL DATO QUE QUIERES MODIFICAR Y REEMPLAZARLO EN EL URL.

Luego de modificar los datos que queremos, como otro producto, precio o stock, mandamos la solicitud.

Si la solicitud es exitosa, deberías obtener una respuesta como esta:

{
  "mensaje": "Producto actualizado correctamente",
  "producto": {
    "id": 1,
    "nombre": "Nuevo nombre",
    "precio": 5,
    "stock": 20
  }
}

********************************************************************

*PARA ELIMINAR EL PRODUCTO:

Para eliminar un producto, puedes hacer una solicitud DELETE a la URL http://localhost:8000/api/productos/<id>/.


Si la solicitud es exitosa, deberías obtener una respuesta como esta:

{
  "mensaje": "Producto eliminado correctamente"
}


********************************************************************
Requisitos:
Visual Studio Code
MySQL: Se necesita MySQL para almacenar los datos del inventario.
Django 3.x: El framework web que soporta la API.
Django REST Framework: Para crear la API RESTful.
