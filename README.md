# Contact-app

## Instalar todo lo necesario
Se puede encontrar una guia para instalar Composer en Ubuntu [Cómo instalar y usar Composer en Ubuntu 20.04](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-composer-on-ubuntu-20-04-es)

Ademas si no se va a utilizar docker, recomendable usar xampp [Descargar XAMPP aquí](https://www.apachefriends.org/es/download.html)



## Instalación

1. Ejecutar `composer install` para instalar las dependencias.
2. Ejecutar `npm install` seguido de `npm run dev` para compilar las plantillas de blade (Vistas HTML).


## Generar la clave de aplicación

Laravel utiliza una clave de aplicación para encriptar datos de forma segura. Debes generar una clave única para tu proyecto que será utilizada para este propósito.

Ejecuta el siguiente comando en tu terminal:

```php artisan key:generate```


## Configurar la base de datos

Si tu proyecto utiliza una base de datos, debes configurar la conexión en el archivo .env. Sigue los pasos a continuación:

1. Renombra el archivo `.env.example` a `.env`.
2. Abre el archivo `.env` y configura la conexión a la base de datos con tu conexión local a MySQL:

```DB_CONNECTION=mysql DB_HOST=127.0.0.1 
DB_PORT=3306
DB_DATABASE=tu_nombre_de_base_de_datos
DB_USERNAME=tu_usuario_de_mysql
DB_PASSWORD=tu_contraseña_de_mysql
```


## Ejecutar migraciones

Las migraciones de Laravel te permiten interactuar con la base de datos de forma estructurada y controlada. Ejecuta las migraciones para crear las tablas necesarias en la base de datos:

```php artisan migrate```


## Servir el proyecto

Utiliza el siguiente comando para ejecutar el servidor de desarrollo y acceder al proyecto en tu navegador:

```php artisan serve```


## Comandos de cURL

Estos son ejemplos de comandos cURL que puedes utilizar para probar la autenticación del proyecto:

- Iniciar sesión con una cuenta de ejemplo:
Registrarse en http://localhost:8000/register o http://127.0.0.1:8000/register

```curl -L -b /dev/null -d "email=email@example.com" -d "password=example" http://127.0.0.1:8000/login```

