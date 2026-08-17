# Gestor de Cuadrantes

Aplicación multiplataforma para gestionar el personal de un equipo y
**generar automáticamente el cuadrante mensual de turnos**, con opción de
editarlo a mano, exportarlo a PDF y enviarlo por email a cada trabajador.

## Acceso

- **Registro**: cualquiera puede crear una cuenta (email + contraseña), pero
  queda pendiente de validación (`status = pending`) hasta que el
  **super_admin** la aprueba manualmente desde Supabase.
- **Login**: una vez aprobada la cuenta, se accede con normalidad.
- Solo se puede ver y modificar la información introducida por la propia
  cuenta (trabajadores, puestos y cuadrantes son privados por administrador).

## ¿Para qué sirve?

Sustituye el cuadre manual de turnos (típicamente hecho en Excel),
teniendo en cuenta la disponibilidad de cada trabajador, los requisitos de
cada puesto, las reglas básicas de descanso y reparto de horas, y los días
festivos del mes.

## Opciones de la app

1. **Inicio** — Panel de resumen (de momento vacío, sin contenido real).
2. **Trabajadores** — Alta, edición y baja del personal: disponibilidad
   por franja horaria, política de turnos largos, horas mensuales
   objetivo, horas extra y habilitaciones/requisitos de cada uno.
3. **Horarios** — Alta, edición y baja de los puestos de trabajo a
   cubrir: turno, horario y requisitos que debe cumplir quien lo ocupe.
4. **Ver/Modificar Cuadrantes** — Selección de mes y año, generación
   automática del cuadrante, edición manual celda a celda, guardado, y
   resumen de horas por trabajador.
5. **Exportar/Email** — Vista previa e impresión en PDF del cuadrante
   completo, y envío individual por email a cada trabajador.

También incluye una pantalla de acceso (login y registro de cuenta).

## Funcionamiento

- Al generar el cuadrante, el sistema recorre el mes día a día y asigna
  cada puesto al trabajador más adecuado, dando prioridad a quien cumple
  los requisitos, respeta sus descansos y franjas permitidas, y acumula
  menos horas trabajadas hasta el momento (para repartir la carga).
- Garantiza al menos un fin de semana libre al mes por trabajador y evita
  rachas de trabajo demasiado largas.
- Si nadie cumple todas las condiciones, relaja algunas reglas para no
  dejar un puesto sin cubrir.
- Al final ajusta el resultado para acercar a todos los trabajadores a sus
  horas contractuales objetivo y para evitar días de trabajo sueltos entre
  días libres.
- Marca automáticamente los fines de semana y los festivos del mes.

## Qué falta por implementar

- El panel de "Inicio" no muestra ningún resumen real todavía.
- No existe ningún control visible en la app para aprobar o validar
  cuentas nuevas antes de poder usarlas.
- Está previsto (pero no activado) un modo de funcionamiento sin conexión;
  actualmente la app siempre trabaja conectada.
- El envío de email depende de un servicio externo que no forma parte de
  este proyecto, así que sin configurarlo esa función no envía nada.
- No se puede elegir el país para el cálculo de festivos desde la
  interfaz.
- No hay envío masivo de emails, solo uno por uno.
- El PDF solo se genera de forma conjunta (todos los trabajadores juntos),
  no hay PDF individual por trabajador.
- No hay pruebas automatizadas que verifiquen la lógica de generación de
  cuadrantes.
- Si en un mes no hay suficiente personal para cubrir todos los puestos,
  la app no avisa claramente de qué turnos han quedado sin cubrir.
