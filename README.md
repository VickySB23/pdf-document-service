# pdf-document-service

API REST de documentos: recibe PDFs, delega la extracción del texto en `pdf-extraction-service` y persiste el resultado en MongoDB.

Expone el CRUD de documentos en `/api/documents` y el chequeo de estado en `/health`. Calcula el checksum SHA-256 de cada archivo, rechaza duplicados y escucha en el puerto `8000`.

## Tests

Requiere Python 3.11 o superior y [uv](https://docs.astral.sh/uv/).

```bash
uv sync
uv run pytest -q
```

Los tests no necesitan Docker ni MongoDB: usan dobles de prueba.

## Despliegue

Este servicio se despliega desde [VickySB23/pdf-extractext-microservicios](https://github.com/VickySB23/pdf-extractext-microservicios), que contiene el `docker-compose.yml` con Traefik, Consul y MongoDB, la documentación y las pruebas de carga.

## Origen

Este repositorio surge de separar la carpeta `services/document-service` de [VickySB23/pdf-extractext-microservicios](https://github.com/VickySB23/pdf-extractext-microservicios), conservando su historial, para que cada microservicio tenga su propio repositorio.
