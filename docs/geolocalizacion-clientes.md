# Módulo: Geolocalización de Clientes

## Descripción General

Este módulo permite registrar y consultar la ubicación geográfica de los clientes
mediante coordenadas de latitud y longitud.

Se integra con servicios de mapas como Google Maps u OpenStreetMap
para visualización y validación de direcciones.

---

## Objetivos

- Registrar ubicación exacta del cliente
- Visualizar cliente en mapa
- Permitir actualización de ubicación
- Mantener historial de cambios

---

## Modelo de Datos

ClienteUbicacion

- id
- cliente_id
- latitud
- longitud
- direccion
- fecha_registro

---

## Endpoints REST

### POST /clientes/{id}/ubicacion

Registra la ubicación del cliente.

Request:

```json
{
  "latitud": -17.7833,
  "longitud": -63.1821,
  "direccion": "Av. Principal 123"
}
