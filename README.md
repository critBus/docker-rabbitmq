# RabbitMQ Docker Deployment

Este repositorio contiene una configuración básica para desplegar un servicio de **RabbitMQ** utilizando **Docker**. Está diseñado para ser simple y fácil de usar, ideal para proyectos que requieren una cola de mensajes o un sistema de mensajería.

## Tabla de Contenidos

- [Requisitos previos](#requisitos-previos)
- [Configuración](#configuración)
- [Despliegue](#despliegue)
- [Acceso al Servicio](#acceso-al-servicio)
- [Variables de Entorno](#variables-de-entorno)
- [Contribuciones](#contribuciones)
- [Licencia](#licencia)

---

## Requisitos previos

Antes de comenzar, asegúrate de tener instalado lo siguiente en tu sistema:

1. **Docker**: [Guía de instalación de Docker](https://docs.docker.com/get-docker/)
2. **Docker Compose**: Viene incluido con Docker Desktop en Windows y Mac. Para Linux, sigue esta [guía](https://docs.docker.com/compose/install/).

---

## Configuración

Para personalizar la configuración de RabbitMQ, debes definir las siguientes variables de entorno en un archivo `.env`. Este archivo debe estar en la raíz del proyecto.

Crea un archivo `.env` con el siguiente contenido:

```env
# RabbitMQ Configuration
RABBITMQ_DEFAULT_USER=your_username
RABBITMQ_DEFAULT_PASS=your_password
RABBITMQ_DEFAULT_VHOST=your_vhost

# Ports
RABBITMQ_HOST_PORT=5672
RABBITMQ_MANAGEMENT_PORT=15672
```

### Descripción de las variables:

- `RABBITMQ_DEFAULT_USER`: Nombre de usuario predeterminado para acceder a RabbitMQ.
- `RABBITMQ_DEFAULT_PASS`: Contraseña del usuario predeterminado.
- `RABBITMQ_DEFAULT_VHOST`: Virtual host predeterminado para RabbitMQ.
- `RABBITMQ_HOST_PORT`: Puerto del host donde se expondrá RabbitMQ (AMQP).
- `RABBITMQ_MANAGEMENT_PORT`: Puerto del host donde se expondrá la interfaz de administración de RabbitMQ.

> **Nota:** Asegúrate de no comprometer este archivo `.env` en tu repositorio público. Agrega `.env` al archivo `.gitignore` para evitar que se suba accidentalmente.

---

## Despliegue

1. Clona este repositorio:
   ```bash
   git clone https://github.com/critBus/docker-rabbitmq.git
   cd rabbitmq-docker
   ```

2. Crea y configura el archivo `.env` como se describe en la sección anterior.

3. Inicia el contenedor de RabbitMQ con Docker Compose:
   ```bash
   docker-compose up -d
   ```

4. Verifica que el contenedor esté funcionando correctamente:
   ```bash
   docker ps
   ```

---

## Acceso al Servicio

Una vez que el contenedor esté en ejecución, puedes acceder a RabbitMQ de las siguientes maneras:

- **Interfaz de Administración**: Abre tu navegador y ve a `http://localhost:15672`. Usa las credenciales definidas en las variables de entorno (`RABBITMQ_DEFAULT_USER` y `RABBITMQ_DEFAULT_PASS`) para iniciar sesión.
  
- **Conexión AMQP**: Puedes conectarte a RabbitMQ utilizando el puerto `5672` (o el puerto que hayas configurado en `RABBITMQ_HOST_PORT`). Por ejemplo, si estás usando una biblioteca de cliente en Python, Node.js, etc., apunta a `amqp://localhost:5672`.

---

## Variables de Entorno

| Variable                  | Descripción                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| `RABBITMQ_DEFAULT_USER`   | Usuario predeterminado para acceder a RabbitMQ.                            |
| `RABBITMQ_DEFAULT_PASS`   | Contraseña del usuario predeterminado.                                     |
| `RABBITMQ_DEFAULT_VHOST`  | Virtual host predeterminado para RabbitMQ.                                 |
| `RABBITMQ_HOST_PORT`      | Puerto del host donde se expondrá RabbitMQ (AMQP).                         |
| `RABBITMQ_MANAGEMENT_PORT`| Puerto del host donde se expondrá la interfaz de administración de RabbitMQ.|

---

## Contribuciones

Si deseas contribuir a este proyecto, sigue estos pasos:

1. Haz un fork del repositorio.
2. Crea una nueva rama (`git checkout -b feature/nueva-funcionalidad`).
3. Realiza tus cambios y haz commit (`git commit -m "Añadir nueva funcionalidad"`).
4. Sube tus cambios (`git push origin feature/nueva-funcionalidad`).
5. Abre un Pull Request describiendo tus cambios.

---

## Licencia

Este proyecto está bajo la licencia [MIT](LICENSE). Consulta el archivo `LICENSE` para más detalles.

---

¡Esperamos que este proyecto te sea útil! Si tienes alguna pregunta o sugerencia, no dudes en abrir un issue en este repositorio.

---

Este `README.md` es claro, conciso y cubre todas las bases necesarias para que otros desarrolladores puedan entender y utilizar tu proyecto sin problemas.