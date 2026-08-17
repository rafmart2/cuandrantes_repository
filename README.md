# Generador de Cuadrantes — Guía de uso

App para gestion de trabajadores, puestos de trabajo
y se genere/edite/envíe el cuadrante mensual de turnos. Los datos se guardan
en la nube (Supabase), por lo que hace falta cuenta y conexión a internet.

## Acceso

- **Registro**: cualquiera puede crear una cuenta (email + contraseña), pero
  queda pendiente de validación (`status = pending`) hasta que el
  **super_admin** la aprueba manualmente desde Supabase.
- **Login**: una vez aprobada la cuenta, se accede con normalidad.
- Solo se puede ver y modificar la información introducida por la propia
  cuenta (trabajadores, puestos y cuadrantes son privados por administrador).

## Secciones de la app

### 1. Inicio
Panel de resumen (de momento solo un marcador de posición).

### 2. Trabajadores
Alta, edición y baja de trabajadores. Por cada uno se configura:
