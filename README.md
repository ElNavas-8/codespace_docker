# Levantar un entorno de MySQL con Docker

Este documento describe los pasos necesarios para levantar un contenedor de MySQL utilizando Docker.

## Requisitos

- Tener Docker instalado en tu máquina.
- Conexión a internet para descargar la imagen de MySQL.

## Paso 1: Crear un archivo `.env` (opcional pero recomendado)

Puedes definir las variables de entorno en un archivo `.env` para facilitar la configuración:

```env
MYSQL_ROOT_PASSWORD=rootpass
MYSQL_DATABASE=midatabase
MYSQL_USER=usuario
MYSQL_PASSWORD=usuariopass
```
## Paso 2: Crear el archivo docker-compose.yml
```env
version: '3.8'

services:
  mysql:
    image: mysql:8.0
    container_name: mysql_container
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: ${MYSQL_ROOT_PASSWORD}
      MYSQL_DATABASE: ${MYSQL_DATABASE}
      MYSQL_USER: ${MYSQL_USER}
      MYSQL_PASSWORD: ${MYSQL_PASSWORD}
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql

volumes:
  mysql_data:
```
## Paso 3: Levantar el contenedor
```env
docker-compose up -d
```
## Paso 4: Verificar que el contenedor esté corriendo
```env
docker ps
```
## Paso 5: Conectarse a MySQL
```env
Puedes conectarte desde tu host utilizando un cliente MySQL como mysql o aplicaciones gráficas como DBeaver o MySQL Workbench:

Host: localhost

Puerto: 3306

Usuario: definido en .env

Contraseña: definida en .env

Notas adicionales
Para detener el contenedor: docker-compose down

Para reiniciarlo: docker-compose restart

Para ver logs: docker-compose logs -f
```