# Microservices Platform

Plataforma de microservicios con [NestJS](https://nestjs.com/), comunicados vía [NATS](https://nats.io/) y orquestados con Docker Compose.

## Servicios

| Servicio           | Descripción                      | Base de datos |
| ------------------ | -------------------------------- | ------------- |
| **Client Gateway** | API REST pública (puerto `3000`) | —             |
| **Products MS**    | Gestión de productos             | SQLite        |
| **Orders MS**      | Gestión de órdenes               | PostgreSQL    |
| **Payments MS**    | Gestión de pagos                 | —             |

## Inicio rápido

```bash
# 1. Clonar con submódulos
git clone --recurse-submodules git@github.com:MicroNest-Sv/microservices-platform.git

# 2. Copiar .env en cada submódulo
cp client-gateway/.env.example client-gateway/.env
cp products-microservice/.env.example products-microservice/.env
cp orders-microservice/.env.example orders-microservice/.env
cp payments-microservice/.env.example payments-microservice/.env

# 3. Levantar todo
docker compose up --build
```

La API queda expuesta en `http://localhost:3000`.

## Estructura

```
├── client-gateway/          # Gateway HTTP → NATS
├── products-microservice/   # MS de productos (SQLite + Prisma)
├── orders-microservice/     # MS de órdenes (Postgres + Prisma)
├── payments-microservice/   # MS de pagos (Postgres + Prisma)
└── compose.yaml             # Orquestación de todos los servicios
```
