# Punto Meeple - Entorno de Desarrollo

Este repositorio contiene la configuración Docker necesaria para levantar el entorno completo del proyecto Punto Meeple.

El proyecto está dividido en dos partes:

- Backend + BBDD → API desarrollada en NestJS conectada a una base de datos PostgreSQL
- Frontend → Aplicación web en React

## 📁 Estructura del proyecto
Este repositorio actúa como punto central del entorno:

```bash
punto-meeple/
├── backend/                # Repo independiente (NO incluido en este repo)
├── frontend/               # Repo independiente (NO incluido en este repo)
├── docker-compose.yml
├── docker-compose.full.yml
├── docker-compose.linux.yml
├── .env
├── .env.example
├── .gitignore
```

## 📋 Requisitos
- Docker
- Docker Compose
- Git

## 📥 Instalación del proyecto
### 1️⃣ Clonar repositorio principal
```bash
git clone https://github.com/sergiova97/punto-meeple-docker.git punto-meeple
cd punto-meeple
```

### 2️⃣ Clonar backend y frontend
⚠️ Este paso es obligatorio, ya que este repositorio NO incluye su código.

```bash
git clone https://github.com/sergiova97/punto-meeple-backend.git backend 
git clone https://github.com/sergiova97/punto-meeple-frontend.git frontend
```

### 3️⃣ Configurar variables de entorno
Crear archivo .env:
```bash
cp .env.example .env
```

Editar valores:
```bash
POSTGRES_USER=admin
POSTGRES_PASSWORD=DB_password
POSTGRES_DB=punto_meeple

JWT_SECRET=your_secret
```

## 🚀 Ejecución del entorno
### 🔹 Backend + Base de datos
```bash
docker compose up -d
```

### 🔹 Entorno completo (frontend incluido)
```bash
docker compose -f docker-compose.yml -f docker-compose.full.yml up -d
```

### Linux (problemas de permisos)
```bash
docker compose -f docker-compose.yml -f docker-compose.linux.yml up -d
```

## 🌐 Accesos
- Backend → http://localhost:3000
- Frontend → http://localhost:5173

## 🧪 Comandos útiles
### Acceder a los contenedores
```bash
docker compose exec backend bash
docker compose exec frontend bash
```