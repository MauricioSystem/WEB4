# Gestor Multimedia

## Descripción General

Gestor Multimedia es una plataforma web desarrollada bajo una arquitectura de microservicios para la gestión de imágenes y videos.

La aplicación permite a los usuarios registrarse, autenticarse mediante JWT, organizar contenido multimedia en portafolios, interactuar con un asistente de inteligencia artificial y ejecutar procesos automatizados mediante N8N.

La solución está diseñada para ejecutarse completamente mediante Docker y Docker Compose en un entorno local.

---

# Objetivos del Proyecto

* Gestionar imágenes y videos.
* Implementar autenticación basada en JWT.
* Aplicar arquitectura de microservicios.
* Utilizar SQL Server con Entity Framework Core y migraciones.
* Integrar servicios de Inteligencia Artificial mediante API externas.
* Integrar automatizaciones mediante N8N.
* Implementar comunicación asíncrona mediante RabbitMQ.
* Utilizar Nginx como Reverse Proxy.
* Contenerizar toda la solución utilizando Docker.

---

# Tecnologías

## Backend

* .NET 10
* ASP.NET Core Web API
* Entity Framework Core
* JWT Authentication
* SQL Server

## Frontend

* React
* TypeScript
* Vite

## Infraestructura

* Docker
* Docker Compose
* Nginx

## Mensajería

* RabbitMQ (Opcional)

## Automatización

* N8N

## Inteligencia Artificial

* OpenAI API / Gemini API (Opcional)

---

# Arquitectura General

```text
                    Usuario
                       |
                    Nginx
                       |
            ---------------------
            |                   |
            |                   |
        Auth API        Multimedia API
            |                   |
            |                   |
            ---------------------
                       |
                  SQL Server

                       |
                  RabbitMQ
                       |
                      N8N
```

---

# Microservicios

## Auth API

Responsable de:

* Registro de usuarios.
* Inicio de sesión.
* Generación de JWT.
* Gestión de perfiles.
* Control de acceso.
* Roles y permisos.

---

## Multimedia API

Responsable de:

* Gestión de portafolios.
* Gestión de imágenes.
* Gestión de videos.
* Carga de archivos.
* Eliminación de archivos.
* Consulta de archivos.
* Integración con IA.
* Integración con N8N.
* Servir la aplicación React compilada.

---

# Frontend

La aplicación contará con un único frontend desarrollado en React.

El frontend será compilado y publicado dentro de:

```text
wwwroot
```

de Multimedia.API.

Módulos principales:

* Login
* Registro
* Dashboard
* Portafolios
* Gestión de Imágenes
* Gestión de Videos
* Chat IA
* Automatizaciones
* Perfil de Usuario

---

# Comunicación Entre Servicios

## Comunicación Síncrona

REST API mediante HTTP.

```text
Frontend
    |
Multimedia API
    |
Auth API
```

---

## Comunicación Asíncrona

RabbitMQ será utilizado para publicar eventos de negocio.

Ejemplo:

```text
Usuario sube un video

Multimedia API
       |
       | Publica Evento
       v
    RabbitMQ
       |
       v
      N8N
```

Eventos posibles:

* ArchivoSubido
* VideoProcesado
* ImagenEliminada
* PortafolioCreado

---

# Arquitectura de Cada Microservicio

Cada microservicio seguirá Arquitectura Onion.

Ejemplo:

```text
Auth.API

├── API
├── Application
├── Domain
└── Infrastructure
```

La misma estructura será utilizada para:

```text
Auth.API
Multimedia.API
```

---

# Base de Datos

Se utilizará SQL Server como motor principal.

Para simplificar el desarrollo académico se utilizará una única base de datos compartida:

```text
MultimediaDB
```

Las tablas serán administradas mediante migraciones de Entity Framework Core.

---

# Almacenamiento Multimedia

Los archivos serán almacenados mediante volúmenes Docker.

```text
/uploads/images

/uploads/videos
```

La metadata será almacenada en SQL Server.

---

# Estructura del Proyecto

```text
multimedia-platform/

├── services/
│   ├── Auth.API/
│   └── Multimedia.API/
│
├── nginx/
│
├── uploads/
│   ├── images/
│   └── videos/
│
├── docker-compose.yml
│
└── README.md
```

---

# Contenedores Docker

La solución estará compuesta por los siguientes contenedores:

* nginx
* auth-api
* multimedia-api
* sqlserver
* rabbitmq
* n8n

Total: 6 contenedores.

Si RabbitMQ no es requerido por la materia:

* nginx
* auth-api
* multimedia-api
* sqlserver
* n8n

Total: 5 contenedores.

---

# Dominios Locales

```text
multimedia.local

api.multimedia.local

n8n.multimedia.local
```

Archivo hosts:

```text
127.0.0.1 multimedia.local

127.0.0.1 api.multimedia.local

127.0.0.1 n8n.multimedia.local
```

---

# Reverse Proxy

Nginx será responsable de enrutar las solicitudes.

```text
/api/auth/*
        |
        └── Auth API

/api/multimedia/*
        |
        └── Multimedia API
```

---

# Ejecución del Proyecto

## Construcción

```bash
docker compose build
```

## Inicio

```bash
docker compose up -d
```

## Ver contenedores

```bash
docker ps
```

## Ver logs

```bash
docker compose logs -f
```

## Detener servicios

```bash
docker compose down
```

---

# Características Implementadas

* Arquitectura de Microservicios
* Arquitectura Onion
* ASP.NET Core .NET 10
* React + TypeScript
* SQL Server
* Entity Framework Core
* JWT Authentication
* Docker
* Docker Compose
* Nginx Reverse Proxy
* RabbitMQ
* N8N
* Integración con Inteligencia Artificial
* Gestión de Imágenes
* Gestión de Videos
* Gestión de Portafolios Multimedia
* Almacenamiento Persistente mediante Volúmenes Docker
* Comunicación Asíncrona Basada en Eventos

---

