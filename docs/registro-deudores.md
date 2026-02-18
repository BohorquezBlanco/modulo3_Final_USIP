# Módulo: Registro y Gestión de Deudores

## 1. Descripción General

El módulo de Registro de Deudores permite administrar las obligaciones
financieras asociadas a clientes dentro del sistema.

Incluye el registro de nuevas deudas, control de saldo pendiente,
gestión de pagos parciales o totales y consulta del historial financiero.

---

## 2. Objetivos del Módulo

- Registrar deudas asociadas a clientes.
- Calcular automáticamente el saldo pendiente.
- Permitir pagos parciales o totales.
- Controlar el estado de la deuda.
- Mantener historial completo de transacciones.
- Generar trazabilidad y auditoría.

---

## 3. Modelo de Datos

### Entidad: Deuda

- id
- cliente_id
- monto_total
- saldo_pendiente
- tasa_interes (opcional)
- fecha_registro
- fecha_vencimiento
- estado (pendiente, pagado, vencido)

---

### Entidad: Pago

- id
- deuda_id
- monto_pagado
- fecha_pago
- metodo_pago
- usuario_registro

---

## 4. Reglas de Negocio

- El saldo pendiente no puede ser negativo.
- Una deuda cambia a estado "pagado" cuando saldo_pendiente = 0.
- Si fecha_vencimiento < fecha actual y saldo > 0 → estado = "vencido".
- No se puede registrar pago mayor al saldo pendiente.
- Todo pago debe quedar registrado en historial.

---

## 5. Endpoints REST

### POST /deudas

Registra una nueva deuda.

Request:

```json
{
  "cliente_id": 10,
  "monto_total": 2000.00,
  "fecha_vencimiento": "2026-03-30"
}
