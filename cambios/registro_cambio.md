# Registro de cambios

## INC-001 — Error en el total de la venta

- **Origen:** Incidencia detectada en el módulo de ventas.
- **Descripción:** El sistema devuelve el precio unitario como total, aunque se compren varias unidades.
- **Justificación:** El importe debe incluir todas las unidades compradas para evitar un cobro incorrecto.
- **Requisito afectado:** RF-001.
- **Archivo involucrado:** `src/ventas.py`.
- **Riesgo:** Cobrar un importe menor al que corresponde.
- **Criterio de aceptación:** Con un precio de S/ 50 y 3 unidades, el total debe ser S/ 150.
- **Prioridad:** Alta.
- **Decisión:** Aprobada mediante evaluación académica simulada.
- **Responsable:** Edwing Alejandro Mattos Hurtado.

- **Estado:** Implementada y verificada. La prueba con S/ 50 × 3 unidades dio S/ 150. La corrección quedó registrada en el commit `9954941` e integrada en `main`.


## CR-002 — Descuento por subtotal

- **Origen:** Solicitud del área comercial.
- **Descripción:** Aplicar un descuento del 10 % cuando el subtotal sea igual o superior a S/ 200.
- **Justificación:** Incorporar la promoción solicitada por el área comercial al cálculo de la venta.
- **Requisito afectado:** RF-002 (nuevo).
- **Archivos involucrados:** `src/ventas.py` y `docs/requisitos.md`.
- **Riesgo:** Aplicar mal el descuento en el límite de S/ 200.
- **Criterio de aceptación:** Con S/ 150 de subtotal, el total debe ser S/ 150. Con S/ 200, debe ser S/ 180. Con S/ 300, debe ser S/ 270.
- **Prioridad:** Media.
- **Decisión:** Aprobada mediante evaluación académica simulada.
- **Responsable:** Edwing Alejandro Mattos Hurtado.

- **Estado:** Implementada y verificada. Las pruebas con subtotales de S/ 150, S/ 200 y S/ 300 dieron totales de S/ 150, S/ 180.0 y S/ 270.0, respectivamente. El cambio quedó registrado en el commit `a6a8224` e integrado en `main`.


## Matriz de impacto

| Criterio | INC-001 | CR-002 |
| --- | --- | --- |
| Requisito | RF-001. Se corrige el cálculo del total según el precio y la cantidad. | RF-002 (nuevo). Se agrega la regla del 10 % de descuento desde S/ 200. |
| Archivos afectados | `src/ventas.py`, donde se calcula el total. | `src/ventas.py` para implementar el descuento y `docs/requisitos.md` para documentar RF-002. |
| Riesgo | Cobrar solo el precio unitario cuando el cliente compra varias unidades. | Omitir el descuento justo en S/ 200 o aplicarlo por debajo de ese monto. |
| Prueba prevista | S/ 50 × 3 unidades debe dar S/ 150. | S/ 150 debe quedar en S/ 150, S/ 200 debe bajar a S/ 180 y S/ 300 debe bajar a S/ 270. |
| Decisión simulada | Aprobada para corregir un error que afecta el cobro. | Aprobada para implementar la promoción solicitada por el área comercial. |


## Tabla de trazabilidad

| ID de cambio | Rama | Commit de implementación | Prueba aprobada | Versión de entrega |
| --- | --- | --- | --- | --- |
| INC-001 | `fix/INC-001-total` | `9954941` | S/ 50 × 3 unidades = S/ 150. | `v1.1.0` |
| CR-002 | `feature/CR-002-descuento` | `a6a8224` | Subtotal → total: S/ 150 → S/ 150, S/ 200 → S/ 180 y S/ 300 → S/ 270. | `v1.1.0` |