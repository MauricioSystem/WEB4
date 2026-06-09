# Multimedia Platform

## Proyecto Universitario

Sistema de gestión multimedia desarrollado con .NET 10 y React + TypeScript.

La plataforma permitirá almacenar, organizar y gestionar imágenes y videos mediante una arquitectura basada en Docker y servicios especializados.

---

# Objetivo

Desarrollar una plataforma web donde los usuarios puedan:

* Registrarse e iniciar sesión.
* Crear portafolios multimedia.
* Crear álbumes.
* Subir imágenes.
* Subir videos.
* Organizar contenido.
* Buscar contenido.
* Utilizar herramientas de Inteligencia Artificial.
* Optimizar archivos multimedia automáticamente.

---

# Arquitectura General

```text
                    INTERNET
                         |
                      NGINX
                         |
      ----------------------------------
      |               |                |
      |               |                |
 Auth Service   Multimedia API    IA Service
      |               |
      |               |
      |          RabbitMQ
      |               |
      |               |
      |        Media Processor
      |               |
      -----------------
              |
         SQL Server

              |
       Local Storage
```

---

# Tecnologías

## Backend

* .NET 10
* ASP.NET Core
* Entity Framework Core
* SQL Server

## Frontend

* React
* TypeScript
* Vite

## Infraestructura

* Docker
* Docker Compose
* NGINX
* RabbitMQ

## Multimedia

* FFmpeg
* ImageSharp

## Inteligencia Artificial

* OpenAI API
* Ollama (opcional)

---

# Contenedores

## NGINX

Responsabilidades:

* Reverse Proxy
* Entrada principal del sistema
* Redirección de solicitudes

Rutas:

```text
/auth/*
/api/*
/ai/*
```

---

## Auth Service

Responsabilidades:

* Registro
* Login
* JWT
* Roles
* Permisos

Tecnología:

```text
.NET 10
```

Endpoints:

```text
POST /auth/register
POST /auth/login
POST /auth/refresh
```

---

## Multimedia API

Es el núcleo del sistema.

Responsabilidades:

* Usuarios
* Portafolios
* Álbumes
* Imágenes
* Videos
* Comentarios
* Compartir contenido

Arquitectura:

```text
Onion Architecture

Domain
Application
Infrastructure
Presentation
```

---

## IA Service

Responsabilidades:

* Chat IA
* Etiquetado automático
* Descripción automática
* Búsqueda inteligente

Ejemplos:

```text
Mostrar fotos de playa

Mostrar videos de vacaciones

Buscar imágenes con perros
```

---

## Media Processor

Responsabilidades:

* Optimización de imágenes
* Compresión de videos
* Conversión de formatos
* Generación de miniaturas

Herramientas:

```text
FFmpeg
ImageSharp
```

---

## RabbitMQ

Responsabilidades:

* Comunicación asíncrona
* Procesamiento en segundo plano

Eventos:

```text
ImageUploaded
VideoUploaded
ImageOptimized
VideoOptimized
```

---

## SQL Server

Responsabilidades:

* Persistencia de datos

Almacena:

```text
Usuarios
Roles
Portafolios
Álbumes
Metadatos
Etiquetas IA
```

No almacena:

```text
Imágenes
Videos
```

---

# Almacenamiento Local

Las imágenes y videos serán almacenados en una carpeta compartida del host.

Estructura:

```text
Storage

├── images
├── videos
├── thumbnails
└── optimized
```

Ejemplo:

```text
Storage/images/foto1.webp

Storage/videos/video1.mp4

Storage/thumbnails/video1.jpg

Storage/optimized/foto1.webp
```

---

# Flujo de Imagen

```text
Usuario

↓

React

↓

Multimedia API

↓

Storage/images

↓

RabbitMQ

↓

Media Processor

↓

Storage/optimized

↓

SQL Server
```

---

# Flujo de Video

```text
Usuario

↓

React

↓

Multimedia API

↓

Storage/videos

↓

RabbitMQ

↓

Media Processor

↓

FFmpeg

↓

Storage/optimized

↓

Thumbnail

↓

SQL Server
```

---

# Base de Datos

Entidades principales:

## User

```text
Id
Name
Email
PasswordHash
Role
```

## Portfolio

```text
Id
Name
Description
UserId
```

## Album

```text
Id
Name
PortfolioId
```

## MediaFile

```text
Id
FileName
FilePath
FileType
FileSize
UploadDate
UserId
AlbumId
```

---

# Estructura del Repositorio

```text
multimedia-platform

backend
│
├── auth-service
├── multimedia-api
├── ai-service
└── media-processor

frontend
│
└── react-app

storage
│
├── images
├── videos
├── thumbnails
└── optimized

infra
│
├── nginx
│
└── docker-compose.yml
```

---

# Docker Compose

Contenedores:

```text
nginx
auth-service
multimedia-api
ai-service
media-processor
rabbitmq
sqlserver
```

Total:

```text
7 contenedores
```

---

# Roadmap

## Fase 1

* Registro
* Login
* JWT
* Portafolios

## Fase 2

* Álbumes
* Subida de imágenes

## Fase 3

* Subida de videos
* Optimización multimedia

## Fase 4

* Chat IA

## Fase 5

* Búsqueda inteligente

---

# Objetivo Académico

Demostrar el uso de:

* Arquitectura Onion
* Docker
* RabbitMQ
* SQL Server
* React + TypeScript
* .NET 10
* Procesamiento multimedia
* Integración con Inteligencia Artificial
* Comunicación entre servicios

sin necesidad de desplegar en la nube ni utilizar infraestructura distribuida compleja.
