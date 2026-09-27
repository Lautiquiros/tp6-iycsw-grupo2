# AgendaYA TP6 — M03 Tipos de Evento y M04 Booking Público

Prototipo HTML/CSS/JS vanilla con lógica compartida en `src/logica-negocio.js`, 30 pruebas unitarias de Node (`node:test`) y 8 casos E2E de Cypress. Sin backend real: datos en `localStorage`, sin envío de correos ni autenticación. Requiere Node.js y npm instalados.

## Instalación y ejecución

```bash
npm install
npm run test
npm run start
```

Abrí `http://localhost:3000` para probar el frontend; dejá el servidor abierto. En **otra terminal**:

```bash
npm run test:e2e
# o npm run cypress:open
```

Para reproducir las fechas de los casos E2E: `http://localhost:3000/?demoDate=2026-07-06`. Esta fecha de demostración solo fija el calendario en pruebas; sin ella se usa la fecha local. Los datos se conservan en localStorage: para reiniciar desde el navegador, borrá el almacenamiento del sitio. Cypress reinicia el almacenamiento antes de cada test.

## Alcance

- M03: crear y editar tipo de evento; además, eliminación lógica con bloqueo ante reservas futuras (simuladas).
- M04: elegir evento, fecha disponible y franja horaria; cargar datos y confirmar reserva, bloqueando el horario ocupado.
- El calendario simula dos días disponibles y uno sin disponibilidad, siempre dentro del mes de la fecha base; si se prueba al final del mes puede haber menos días visibles. El horario 10:30 está reservado por defecto en las fechas disponibles.
- El frontend simula un administrador ya autenticado y no integra servicios M01, M02, M05 ni M06: notificaciones, reservas futuras y disponibilidad se modelan localmente. No usar con información sensible real.

## Estructura

- `frontend/`: vista web, lógica de interfaz y estilos.
- `src/logica-negocio.js`: validación, eliminación, fechas y slots, confirmación.
- `tests/logica-negocio.test.js`: 30 pruebas unitarias, 5 propuestas por integrante.
- `cypress/e2e/m03-m04.cy.js`: 8 pruebas E2E con Arrange / Act / Assert.
- `INFORME_TP6.md`: informe editable; completar evidencias, autorías, commits y enlace antes de entregar.

## Versionado y evidencia

```bash
git init
git add frontend src server.js package.json .gitignore README.md
git commit -m "feat: frontend minimo M03 y M04"
git add tests
git commit -m "test: 30 pruebas unitarias de logica de negocio"
git add cypress cypress.config.js INFORME_TP6.md
git commit -m "test: flujos E2E Cypress e informe TP6"
```

Las líneas son una guía **para realizar commits reales** (nunca se deben inventar hashes, autorías o ejecuciones). Crear repo remoto y subir la rama siguiendo el proveedor elegido. Guardar capturas o video reales de Cypress y la salida de `npm run test` en la entrega. Cypress puede requerir descarga de binarios mediante `npm install`.
