# Prueba de login — Escabiando Pociones

Repo separado, sin ninguna conexión con el sitio real. Sirve para
probar el login con mail y contraseña usando Supabase antes de decidir
si lo llevamos al panel de verdad.

## 1. Crear el proyecto en Supabase

1. Entrá a supabase.com → creá una cuenta gratis → "New project".
2. Ponele un nombre (ej. "escabiando-pociones-auth"), una contraseña
   para la base (guardala, no la vas a necesitar para esto pero por
   las dudas) y elegí una región cercana (South America si está
   disponible).
3. Esperá 1-2 minutos a que el proyecto termine de crearse.
4. Andá a **Settings → API**. Ahí vas a ver dos datos que necesitás:
   - **Project URL** (algo como `https://abcdefgh.supabase.co`)
   - **anon public** key (una clave larga) — esta clave está pensada
     para usarse en el navegador, no es secreta, tranquilo.

## 2. Completar el archivo

Abrí `index.html` y reemplazá estas dos líneas cerca del final con tus
datos reales:

```js
const SUPABASE_URL = "https://TU-PROYECTO.supabase.co";
const SUPABASE_ANON_KEY = "TU-CLAVE-ANON-PUBLIC";
```

## 3. Crear el primer usuario de prueba

Supabase no deja que cualquiera se registre solo (a menos que lo
actives) — para este piloto, los usuarios se crean a mano, uno por
persona:

1. En el panel de Supabase: **Authentication → Users → Add user**.
2. Cargá un mail y una contraseña. Ese es el usuario con el que vas a
   probar el login.
3. Repetí por cada persona que quieras invitar a probar.

## 4. Publicar el repo de prueba

1. Creá un repo nuevo en GitHub, por ejemplo
   `escabiando-pociones-sandbox` (puede ser público o privado, no
   importa para esta prueba).
2. Subí estos archivos (incluida la carpeta oculta `.github/`).
3. Settings → Pages → Branch `main`, carpeta `/ (root)` → Save.
4. En 1-2 minutos vas a tener la URL de prueba, algo como
   `https://fgzan.github.io/escabiando-pociones-sandbox/`.

## 5. Activar el robotcito que mantiene despierto el proyecto

El plan gratis de Supabase pausa el proyecto si pasa más o menos una
semana sin uso. Este Action le manda un pedido liviano dos veces por
semana para evitarlo — no hace falta que nadie entre a la web para eso.

1. En el repo de prueba: **Settings → Secrets and variables →
   Actions → New repository secret**.
2. Creá un secreto llamado `SUPABASE_URL` con el valor de tu Project
   URL (el mismo del paso 1).
3. Creá otro llamado `SUPABASE_ANON_KEY` con el valor de la clave
   anon public.
4. Listo — el Action ya está en `.github/workflows/keep-alive.yml`,
   corre solo los lunes y jueves. Si querés probarlo ya mismo sin
   esperar, andá a la pestaña **Actions** → "Mantener despierto
   Supabase" → "Run workflow".

## Qué probar

Entrá a la URL de prueba, logueate con el mail y contraseña que
creaste en el paso 3, y confirmá que funciona. Esto es solo el login
en sí — todavía no tiene el formulario de carga de notas conectado,
eso es el paso siguiente una vez que el login te convenza.
