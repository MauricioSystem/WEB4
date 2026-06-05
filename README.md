# 📁 MediaVault

Sistema de gestión de archivos multimedia desarrollado con **ASP.NET Core**, **React + TypeScript** y **SQL Server**, siguiendo los principios de **Arquitectura Hexagonal**.

---

# Descripción

MediaVault es una plataforma que permite a los usuarios almacenar, organizar y administrar imágenes y videos mediante portafolios personalizados.

Cada usuario dispone de un espacio de almacenamiento limitado y puede gestionar sus archivos multimedia, consultar metadatos, modificarlos y descargar versiones actualizadas.

---

# Objetivos

* Centralizar la gestión de imágenes y videos.
* Organizar contenido mediante portafolios.
* Administrar metadatos multimedia.
* Controlar el uso de almacenamiento por usuario.
* Aplicar Arquitectura Hexagonal para mantener un sistema escalable y mantenible.

---

# Tecnologías

## Backend

* ASP.NET Core 9
* C#
* Entity Framework Core
* SQL Server
* JWT Authentication
* AutoMapper
* FluentValidation

## Frontend

* React
* TypeScript
* Vite
* React Router
* Axios
* Material UI

## Base de Datos

* SQL Server
* EF Core Migrations

---

# Arquitectura

El proyecto sigue una Arquitectura Hexagonal (Ports and Adapters).

```text
┌──────────────────────────┐
│       React Client       │
└────────────┬─────────────┘
             │ HTTP
             ▼

┌──────────────────────────┐
│         Web API          │
└────────────┬─────────────┘
             │
             ▼

┌──────────────────────────┐
│      Application         │
│      Use Cases           │
└────────────┬─────────────┘
             │
             ▼

┌──────────────────────────┐
│         Domain           │
│ Business Rules & Models  │
└────────────┬─────────────┘
             │
             ▼

┌──────────────────────────┐
│      Infrastructure      │
│ SQL Server / Storage     │
└──────────────────────────┘
```

---

# Funcionalidades

## Autenticación

* Registro de usuarios
* Inicio de sesión
* JWT Authentication
* Gestión de perfil

---

## Gestión de Portafolios

* Crear portafolio
* Editar portafolio
* Eliminar portafolio
* Listar portafolios

Ejemplos:

* Viajes
* Trabajo
* Universidad
* Redes Sociales

---

## Gestión de Archivos

### Imágenes

Formatos soportados:

* JPG
* JPEG
* PNG
* WEBP

### Videos

Formatos soportados:

* MP4
* AVI
* MOV

Operaciones:

* Subir archivo
* Visualizar archivo
* Descargar archivo
* Eliminar archivo

---

## Metadatos

El sistema permite visualizar y editar metadatos.

### Imágenes

* Nombre
* Autor
* Descripción
* Etiquetas
* Fecha de creación
* Resolución

### Videos

* Nombre
* Autor
* Descripción
* Etiquetas
* Duración
* Resolución

---

## Control de Almacenamiento

Cada usuario posee una cuota máxima configurable.

Ejemplo:

```text
Espacio Total: 10 GB
Espacio Utilizado: 4.2 GB
Disponible: 5.8 GB
```

Al intentar superar el límite:

```text
Error:
Espacio de almacenamiento insuficiente.
```

---

# Estructura de Carpetas

```text
src

├── Domain
│   ├── Entities
│   ├── ValueObjects
│   ├── Interfaces
│   └── Rules
│
├── Application
│   ├── DTOs
│   ├── Services
│   ├── Commands
│   ├── Queries
│   └── UseCases
│
├── Infrastructure
│   ├── Persistence
│   ├── Repositories
│   ├── Storage
│   └── Security
│
├── WebAPI
│   ├── Controllers
│   ├── Middleware
│   └── Configuration
│
└── Frontend
    ├── components
    ├── pages
    ├── hooks
    ├── services
    └── routes
```

---

# Modelo de Datos

## Usuarios

```text
Id
Nombre
Email
PasswordHash
EspacioMaximoMB
EspacioUsadoMB
FechaRegistro
Estado
```

## Portafolios

```text
Id
UsuarioId
Nombre
Descripcion
FechaCreacion
FechaActualizacion
```

## Archivos

```text
Id
PortafolioId
NombreOriginal
NombreFisico
RutaArchivo
TipoArchivo
Extension
TamanoBytes
FechaSubida
Ancho
Alto
Duracion
Estado
```

## Metadatos

```text
Id
ArchivoId
Clave
Valor
```

## Etiquetas

```text
Id
Nombre
```

## ArchivoEtiquetas

```text
ArchivoId
EtiquetaId
```

---

# Casos de Uso

### Usuario

* Registrarse
* Iniciar sesión
* Consultar almacenamiento

### Portafolio

* Crear
* Editar
* Eliminar
* Visualizar

### Archivo

* Subir
* Visualizar
* Descargar
* Eliminar

### Metadatos

* Consultar
* Editar

---

# API REST

## Auth

```http
POST /api/auth/register
POST /api/auth/login
```

## Portafolios

```http
GET    /api/portafolios
POST   /api/portafolios
PUT    /api/portafolios/{id}
DELETE /api/portafolios/{id}
```

## Archivos

```http
GET    /api/archivos
POST   /api/archivos/upload
GET    /api/archivos/{id}
DELETE /api/archivos/{id}
```

## Metadatos

```http
GET /api/archivos/{id}/metadata
PUT /api/archivos/{id}/metadata
```

## Descargas

```http
GET /api/archivos/{id}/download
```

## Almacenamiento

```http
GET /api/usuarios/storage
```

---

# Requisitos No Funcionales

* Arquitectura Hexagonal
* JWT Authentication
* Validación de datos
* Escalabilidad
* Seguridad de archivos
* Auditoría de operaciones
* Migraciones automáticas
* Separación Frontend y Backend

---

# Futuras Mejoras

* Compartir archivos mediante enlaces.
* Compartir portafolios.
* Miniaturas automáticas.
* Papelera de reciclaje.
* Versionado de archivos.
* Búsqueda avanzada.
* Dashboard estadístico.
* Roles de Administrador y Usuario.
* Integración con Azure Blob Storage.
* Integración con AWS S3.

---

# Autor

Proyecto académico desarrollado para demostrar la implementación de una plataforma de gestión multimedia utilizando Arquitectura Hexagonal con ASP.NET Core, React y SQL Server.
