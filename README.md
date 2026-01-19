# Servidor Apache con Docker para Entorno Educativo

Este repositorio proporciona una configuración de un servidor web Apache sobre una imagen de Ubuntu, gestionado a través de Docker. Es una herramienta ideal para estudiantes y educadores que necesiten un entorno de servidor web local para aprender, realizar pruebas y desarrollar aplicaciones web.

El servidor viene con PHP preinstalado, lo que permite trabajar con contenido dinámico.

## Características

- **Base del sistema:** Ubuntu 22.04
- **Servidor web:** Apache 2
- **Soporte de scripting:** PHP
- **Orquestación:** Docker Compose
- **Configuración personalizable:** La configuración de Apache y el contenido web se gestionan en carpetas locales, facilitando su modificación.

## Prerequisitos

Para poder utilizar este proyecto, es necesario tener instalados en su sistema:

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Estructura del Directorio

- `docker-compose.yml`: Archivo principal que define y orquesta el servicio del contenedor Docker.
- `Dockerfile`: Contiene las instrucciones para construir la imagen de Docker, instalando Apache y PHP sobre Ubuntu.
- `conf/`: Contiene la configuración completa del servidor Apache. Cualquier cambio en estos archivos se reflejará en el servidor.
- `www/`: Es la carpeta raíz del servidor web (`DocumentRoot`). Todos los archivos y carpetas que coloques aquí serán servidos por Apache.

## Instrucciones de Uso

### 1. Iniciar el Servidor

Para construir la imagen y levantar el contenedor, sitúese en la raíz del proyecto y ejecute el siguiente comando:

```bash
docker-compose up -d
```

El parámetro `-d` (detached) hace que el contenedor se ejecute en segundo plano.

### 2. Acceder al Servidor Web

Una vez que el contenedor esté en funcionamiento, puede acceder al contenido web a través de su navegador en la siguiente dirección:

[http://localhost:8080](http://localhost:8080)

Verá el contenido que se encuentre en la carpeta `www/`.

### 3. Ver los Logs del Servidor

Si necesita revisar los registros de acceso o de errores de Apache, puede usar el siguiente comando:

```bash
docker-compose logs -f
```

El parámetro `-f` (follow) muestra los logs en tiempo real.

### 4. Detener el Servidor

Para detener el contenedor y liberar los recursos, ejecute:

```bash
docker-compose down
```

Este comando detiene y elimina el contenedor, pero no borrará sus archivos de configuración (`conf/`) ni el contenido web (`www/`).

## Personalización

- **Contenido web:** Simplemente añada, modifique o elimine archivos en la carpeta `www/`. Los cambios se verán reflejados inmediatamente.
- **Configuración de Apache:** Puede modificar los archivos de configuración en la carpeta `conf/`. Para que la mayoría de los cambios surtan efecto, es necesario reiniciar el servicio:

  ```bash
  docker-compose restart
  ```
