# Gestor de Cuadrantes

Aplicación multiplataforma para gestionar el personal de un equipo y
**generar automáticamente el cuadrante mensual de turnos**, con opción de
editarlo a mano, exportarlo a PDF y enviarlo por email a cada trabajador.

## Acceso

- **Registro**: cualquiera puede crear una cuenta (email + contraseña), pero
  queda pendiente de validación hasta que el **super_admin** la aprueba manualmente desde Supabase.
- **Login**: una vez aprobada la cuenta, se accede con normalidad.
- Solo se puede ver y modificar la información introducida por la propia
  cuenta (trabajadores, puestos y cuadrantes son privados por administrador).

## ¿Para qué sirve?

Sustituye el cuadre manual de turnos (típicamente hecho en Excel),
teniendo en cuenta la disponibilidad de cada trabajador, los requisitos de
cada puesto, las reglas básicas de descanso y reparto de horas, y los días
festivos del mes.

## Opciones de la app

1. **Inicio — Panel de Control**

   Panel de resumen general del sistema. Muestra información del periodo seleccionado y permite cambiar de mes o actualizar los datos manualmente.

   Incluye:

   * **Trabajadores**: número total de trabajadores registrados.
   * **Puestos**: número total de puestos configurados.
   * **Vacaciones**: número de trabajadores con vacaciones durante el mes.
   * **Horas extra**: número de trabajadores que tienen activada la opción de realizar horas extra.
   * **Estado del cuadrante**: indica si existe un cuadrante generado para el periodo seleccionado.
   * **Turnos descubiertos**: número de puestos que han quedado sin cubrir.
   * **Trabajadores bajo mínimo**: número de trabajadores que no alcanzan su objetivo mensual de horas.
   * **Horas extra realizadas**: total de horas que superan el objetivo ordinario.
   * **Horas extra pendientes**: horas extra que todavía faltan para alcanzar las horas extra mínimas deseadas por los trabajadores que tienen activada esta opción.

   También muestra las **alertas del cuadrante**, incluyendo trabajadores por debajo de su objetivo, turnos descubiertos, horas extra pendientes y otros errores detectados.

   Las alertas se pueden abrir en una **pantalla completa independiente**, con desplazamiento para consultar todas las incidencias y un botón para volver al panel.

   Además, el panel consulta automáticamente el **cuadrante del mes siguiente**. Si ya existe, muestra sus próximas alertas para poder detectar problemas con antelación. Si todavía no existe, informa de que aún no se ha generado.

2. **Trabajadores** — Gestión integral del personal dividida en dos secciones independientes para mayor comodidad visual:

   * **Listado de Personal**: Pantalla completa dedicada exclusivamente a ver la plantilla activa y navegar por el módulo.
   * **Formulario de Alta/Edición**: Una ventana limpia a pantalla completa con scroll propio que permite introducir o modificar los datos de un trabajador (disponibilidad por franja horaria, turnos largos, horas objetivo, horas extra y habilitaciones) sin que la lista estorbe o apriete los campos. Incluye botones claros de confirmación y guardado.

3. **Horarios** — Alta, edición y baja de los puestos de trabajo a cubrir: turno, horario y requisitos que debe cumplir quien lo ocupe.

4. **Ver/Modificar Cuadrantes** — Selección de mes y año, generación automática del cuadrante, edición manual celda a celda, guardado y resumen de horas por trabajador.

   Incluye dos vistas independientes:

   * **Por trabajadores**: muestra el cuadrante organizado por trabajador.
   * **Por puestos**: muestra el cuadrante organizado por puesto.

   Ambas vistas permiten editar manualmente las asignaciones. Cada celda de la tabla interactiva muestra el horario real de entrada y salida (ej: `06:00-14:00`) en lugar de letras o abreviaturas, unificando el diseño con los documentos impresos.

   En la vista por trabajadores:

   * La columna **Puesto** no se muestra.
   * Las columnas se ajustan al contenido.
   * Se muestran líneas divisorias entre las celdas.
   * Los sábados y domingos se diferencian visualmente.
   * Los días de vacaciones aparecen diferenciados y con texto negro sobre fondo azul.
   * El usuario puede editar manualmente las asignaciones de cada día.

5. **Exportar/Email** — Panel de distribución adaptado para dispositivos móviles que organiza las acciones de arriba a abajo de forma ordenada:

   * **Previsualizar PDF General**: Abre el visor nativo del dispositivo con el cuadrante completo de toda la plantilla, bloqueado estrictamente en formato horizontal.
   * **Enviar a Todos**: Permite el despacho masivo del cuadrante por correo electrónico.
   * **Opciones por Trabajador**: Cada empleado de la lista cuenta con un botón para descargar directamente en la memoria local su hoja de trabajo individual en cuadrícula horizontal oficial de seguridad, y otro botón para enviarle únicamente su cuadrante por email.

También incluye una pantalla de acceso (login y registro de cuenta).

## Funcionamiento del Sistema y Documentos

- Al generar el cuadrante, el sistema recorre el mes día a día y asigna cada puesto al trabajador más adecuado, dando prioridad a quien cumple los requisitos, respeta sus descansos y franjas permitidas, y acumula menos horas trabajadas hasta el momento (para repartir la carga).
- Garantiza al menos un fin de semana libre al mes por trabajador y evita rachas de trabajo demasiado largas.
- Si nadie cumple todas las condiciones, relaja algunas reglas para no dejar un puesto sin cubrir.
- Al final ajusta el resultado para acercar a todos los trabajadores a sus horas contractuales objetivo y para evitar días de trabajo sueltos entre días libres.
- Los trabajadores que no hayan alcanzado su objetivo pueden recibir asignaciones adicionales compatibles con las restricciones.
- Los trabajadores con la opción de horas extra desactivada no reciben horas adicionales una vez alcanzado su objetivo ordinario.
- Las horas extra se asignan prioritariamente a trabajadores que tienen activada esta opción y pueden utilizarse hasta alcanzar las horas extra mínimas deseadas configuradas.
- Se realizan pasadas adicionales de reparación para intentar completar las horas objetivo y cubrir puestos descubiertos antes de finalizar la generación.
- El sistema permite dejar un caso excepcional para revisión y modificación manual por parte del responsable cuando las restricciones impiden alcanzar exactamente el objetivo mensual.
- Marca automáticamente los fines de semana y los festivos del mes.
- Las vacaciones se contabilizan a razón de **5,22 horas por día** y se consideran horas normales/diurnas incluso cuando coinciden con un día festivo.
- El panel de inicio reconstruye las alertas de los cuadrantes guardados para que sigan visibles aunque el cuadrante no se haya generado durante la sesión actual.
- **Formato Profesional de PDFs**: Los documentos se generan fijos en formato apaisado. La columna con el nombre de los contratos y servicios se autoajusta de forma inteligente al tamaño del texto largo para que los nombres de los puestos quepan siempre en una sola línea sin cortarse.
- **Descargas Limpias y Correctas**: Al guardar los archivos en el almacenamiento del teléfono o el ordenador, el sistema propone automáticamente un nombre descriptivo ordenado por el servicio, el mes y el año (ej: `Cuadrante_RENFE_LOTE_6_8_2026.pdf`) garantizando que se descargue siempre como un documento PDF listo para abrir con un toque.
- **Sincronización de Datos**: El motor interno corrige automáticamente cualquier desfase de horas al leer la base de datos, asegurando que los turnos y los horarios de entrada y salida coincidan milimétricamente en el día exacto del mes tanto en las tablas de la aplicación como en las hojas impresas.

## Sistema de actualización

Se ha preparado un sistema de actualización automática de la aplicación basado en la versión definida en `pubspec.yaml`.

- La aplicación obtiene su versión instalada automáticamente.
- `UpdateService` consulta `version.json` en el repositorio público.
- Se comparan la versión y el número de build instalados con la versión publicada.
- Si existe una versión nueva, la aplicación puede mostrar un aviso al usuario.
- Se ha preparado el instalador para **Android** y **Windows**.
- En Android se utiliza `FileProvider` para compartir de forma segura el APK descargado con el instalador.
- La integración Android utiliza un `MethodChannel` nativo (`app.updater/install`) para iniciar la instalación del APK.
- El sistema de publicación utiliza automáticamente el nombre y la versión de `pubspec.yaml`.

## Publicación multiplataforma

El proyecto utiliza GitHub Actions para automatizar la publicación de las versiones.

La versión se obtiene directamente de:

```yaml
version: 0.0.2+2