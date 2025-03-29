# Hoppscotch AIO Selfhost

## Descripción
Proyecto de despliegue de Hoppscotch en modo todo-en-uno (AIO) usando Docker y Docker Compose.

## Características
- Contenedor AIO (hoppscotch/hoppscotch) con frontend, backend, y admin
- Base de datos PostgreSQL integrada
- Autenticación OAuth (Github, Email, Google, Microsoft)
- Envio de emails (SMTP)

## Requisitos
- Node.js V18+
- npm v9+ (se ejecuta dentro del contenedor)
- Docker v20+ y Docker Compose v2+
- Credenciales de la base de datos Postgres
- SMTP para envío de correos
- Credenciales OAuth (GITHUB, GOOGLE, EMAIL, MICROSOFT)

## Estructura del proyecto
<pre>
├── docker-compose.yml
├── .env
├── templates/       # Templates .hbs para emails
│   ├── user-invitation.hbs
│   ├── team-invitation.hbs
</pre>

## Instalacion
1. Crear archivo .env a partir de .env.example
2. Editar .env con tus credenciales de OAuth, Base de datos y SMTP (Importante)
3. Configurar las demas variables (opcional)
4. Levantar el contenedor en modo interactivo para correr migraciones: 
```bash
   docker compose run --entrypoint sh hoppscotch-aio
```
5. Dentro del contenedor
```bash
 pnpx prisma migrate deploy
```
6. Salir y levantar en modo daemon:
```bash
 docker compose up -d
```

## Servicios disponibles
| Servicio  | URL                            |
|-----------|---------------------------------|
| Frontend  | http://localhost:3000          |
| Admin     | http://localhost:3100          |
| Backend   | http://localhost:3170/graphql  |
| Base de datos | `localhost:5432` (Postgres) |