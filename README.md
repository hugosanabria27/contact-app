# Contact-app

## Requerimientos
- PHP: 8.0.2 o superior.
- Composer 2 en adelante
- [XAMPP 8.2.4](https://www.apachefriends.org/es/download.html) (Recomendado)
- [Node.js](https://nodejs.org/en/download)

## Instalar todo lo necesario en Linux (Debian based)
### Instalación DE XAMPP
Descarga la version 8.2.4 de XAMPP

Abre una terminal (Ctrl + Alt + T) y accede a Descargas.
```bash
cd Descargas 
```

Dale permisos de ejecución al archivo que descargaste utilizando el siguiente comando
```bash
chmod +x xampp-linux-x64-8.2.4-0-installer.run
```
Ejecuta el archivo con el siguiente comando 
```bash
sudo ./xampp-linux-x64-8.2.4-0-installer.run
```
Se ejecutará el instalador gráfico, sigue las instrucciones y espera a que se instale por completo, NO ejecutar xampp al finalizar la instalacion.

Una vez instalado navega al siguiente directorio
```bash
cd /opt/lampp/bin
```
Y ejecuta los siguientes comandos:
```bash
./php --version
./mysql --version
```
Si obtienes el output con las versiones respectivas de PHP y MySQL, significa que todo se instaló correctamente.
Ahora navega de vuelto a tu directorio raíz utilizando y ejecuta el siguiente comando
```bash
cd
nano .bashrc
```
Copia lo siguiente al final del archivo: `export PATH="/opt/lampp/bin:$PATH"` , Ctrl + O, luego enter para confirmar el nombre y Ctrl + X para salir
Haz un logout de tu sesion y vuelve a ingresar
Abre una terminal y escribe de vuelta
```bash
php --version
mysql --version
```
Si es que te salen las versiones, significa que ya tienes acceso global a PHP y MySQL
Ahora ejecuta inicia el servidor apache utilizando el siguiente comando:
```bash
sudo /opt/lampp/lampp start
```

Si todo fue bien en un navegador accede a 127.0.0.1 o localhost y deberías de ver un dashboard

### Instalacion de Composer
Composer es una herramienta popular de administración de dependencias en PHP. Te permite gestionar las bibliotecas y paquetes que tu proyecto PHP necesita.

Asegúrese de posicionarse en su directorio de inicio y obtenga el instalador usando curl:
```bash
cd ~
curl -sS https://getcomposer.org/installer -o composer-setup.php
```
Verificar la integridad de la instalación
```bash
HASH=`curl -sS https://composer.github.io/installer.sig`
```
```bash
echo $HASH
```

Ahora, ejecute el siguiente código PHP, como se indica en la [página de descarga de Composer](https://getcomposer.org/download/), para verificar que la secuencia de comandos de instalación se pueda ejecutar de forma segura:

```
php -r "if (hash_file('SHA384', 'composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
```

Si todo salió bien, se vera lo siguiente:
```bash
Installer verified
```
Para instalar composer de manera global, utilice el siguiente comando que lo descargará e instalará en todo el sistema como un comando llamado composer, en /usr/local/bin:
```bash
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
```
En caso de que no encuentre el sudo php, la solucion seria crear un enlace simbolico, si no te sucede eso, omitir este paso. 
```bash
sudo ln -s /ruta/a/tu/carpeta/xampp/bin/php /usr/local/bin/php
```

Verá un resultado similar a este:
```
All settings correct for using Composer
Downloading...

Composer (version 1.10.5) successfully installed to: /usr/local/bin/composer
Use it: php /usr/local/bin/composer
```

Para comprobar su instalación, ejecute lo siguiente:

```bash
composer
```

El output deberia de ser algo asi:
```bash
   ______
  / ____/___  ____ ___  ____  ____  ________  _____
 / /   / __ \/ __ `__ \/ __ \/ __ \/ ___/ _ \/ ___/
/ /___/ /_/ / / / / / / /_/ / /_/ (__  )  __/ /
\____/\____/_/ /_/ /_/ .___/\____/____/\___/_/
                    /_/
Composer version 1.10.5 2020-04-10 11:44:22

Usage:
  command [options] [arguments]

Options:
  -h, --help                     Display this help message
  -q, --quiet                    Do not output any message
  -V, --version                  Display this application version
      --ansi                     Force ANSI output
      --no-ansi                  Disable ANSI output
  -n, --no-interaction           Do not ask any interactive question
      --profile                  Display timing and memory usage information
      --no-plugins               Whether to disable plugins.
  -d, --working-dir=WORKING-DIR  If specified, use the given directory as working directory.
      --no-cache                 Prevent use of the cache
  -v|vv|vvv, --verbose           Increase the verbosity of messages: 1 for n
```
Fuente: [Instalar Composer en Ubuntu ](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-composer-on-ubuntu-20-04-es)

## Poner en marcha el proyecto
```
git clone https://github.com/hugosanabria27/contact-app.git
cd contact-app
composer install
npm install
```
El ultimo comando asume que ya tienes el gestor de paquetes npm instalado.

## Configurar el archivo .env 

En la terminal, ya situado en el directorio del proyecto, abrelo con tu editor de texto de preferencia
ejemplo con vs code
```
cd contact-app
code .
```

1. Renombra el archivo `.env.example` a `.env`.
2. Abre el archivo `.env` y configura la conexión a la base de datos con tu conexión local a MySQL (Por defecto xampp no tiene definida una password):

```
DB_CONNECTION=mysql DB_HOST=127.0.0.1 
DB_PORT=3306
DB_DATABASE=tu_nombre_de_base_de_datos
DB_USERNAME=tu_usuario_de_mysql
DB_PASSWORD=tu_contraseña_de_mysql
```
Luego de tener el archivo .env ejecuta el siguiente comando:
```
php artisan key:generate
```

## Ejecutar migraciones y seeders
Para ejecutar las migraciones y seeders ejecuta el sgte comando

```
php artisan migrate --seed
```
## Servir el proyecto

Utiliza el siguiente comando para ejecutar el servidor de desarrollo y acceder al proyecto en tu navegador:

```
php artisan serve
```
## Logearte
Puedes logearte con el usuario predeterminado utilizando el siguiente comando
```bash
curl -X POST http://localhost:8000/login -d "email=email@example.com" -d "password=test1234"
```



