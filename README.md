# 🎾 Control de Torneos de Raqueta

Aplicacion web estatica para gestionar competiciones de deportes de raqueta: padel, tenis, pickleball, squash, badminton u otros formatos por parejas/equipos.

Permite organizar equipos, fase de grupos, resultados al mejor de tres sets, clasificaciones automaticas y cuadros eliminatorios tipo bracket. Es una base funcional sin backend: se ejecuta en navegador y guarda los datos localmente.

## ✨ Funcionalidades

- Alta de equipos con jugadores y notas internas.
- Creacion de competiciones por categoria y numero de grupos.
- Asignacion de equipos a cada competicion.
- Generacion automatica de grupos y partidos todos contra todos.
- Registro de resultados al mejor de tres sets.
- Clasificacion calculada por puntos, sets y juegos.
- Generacion de eliminatoria desde la clasificacion de grupos.
- Cruces iniciales mejor clasificado vs peor clasificado de otro grupo.
- Ajuste manual de cruces de primera ronda mediante drag and drop.
- Cuadro visual tipo bracket con avance automatico de ganadores.
- Vista publica de solo lectura.
- Interfaz bilingue ES/EN con preferencia guardada.
- Exportacion e importacion de datos en JSON.
- Datos de ejemplo para probar rapidamente.
- Impresion del cuadro preparada para guardar como PDF desde el navegador.
- Exportacion PDF multipagina para cuadros grandes, dividiendo el bracket por rondas.

## 🚀 Puesta en marcha

Con Node.js instalado:

```bash
npm start
```

Despues abre:

```text
http://127.0.0.1:5173
```

Tambien puedes abrir `index.html` directamente en el navegador, aunque se recomienda usar el servidor local para una experiencia mas parecida a produccion.

## 🧪 Tests y validacion

La suite usa el runner nativo de Node, sin dependencias externas.

```bash
npm test
npm run check
```

Los tests cubren:

- Marcador al mejor de tres sets.
- Calculo de clasificacion por puntos, sets y juegos.
- Generacion de cruces mejor vs peor de otro grupo.
- Drag and drop de cruces y limpieza de resultados dependientes.
- Traducciones basicas y textos dinamicos generados.
- Division de rondas para impresion multipagina.

## 🌍 Internacionalizacion

La interfaz incluye selector ES/EN en la cabecera. La preferencia se guarda en `localStorage`.

La implementacion combina:

- Copia principal de cabecera y navegacion por claves estables.
- Diccionario bidireccional ES/EN para el contenido renderizado.
- Traduccion de placeholders, `aria-label`, estados, toasts y textos generados.

## 💾 Persistencia de datos

Actualmente los datos se guardan en el navegador:

- Clave principal: `padelTournamentControl.v1`.
- Idioma seleccionado: `padelTournamentControl.lang`.

Se conservan estos nombres de claves por compatibilidad con datos ya guardados antes del cambio de marca hacia deportes de raqueta.

Para mover datos entre equipos o hacer copias de seguridad, usa las opciones de exportar/importar JSON desde la seccion `Datos`.

## 🧱 Estructura del proyecto

```text
.
├── assets/
│   └── court-mark.svg
├── tests/
│   └── app.test.js
├── app.js
├── dev-server.js
├── index.html
├── package.json
├── README.md
└── styles.css
```

## 🗺️ Roadmap recomendado

- Backend con base de datos real para multiusuario.
- Autenticacion y roles de administrador.
- URLs publicas por competicion.
- Auditoria de cambios de resultados.
- Programacion de horarios, pistas/canchas y sedes.
- Exportacion PDF binaria sin dialogo del navegador, si mas adelante se introduce bundler o libreria dedicada.
- Configuracion por deporte: puntuacion, super tie-break, sets cortos o reglas especificas.

## 📌 Nota tecnica

El proyecto no introduce dependencias externas. La logica principal vive en `app.js`, la interfaz en `index.html` y `styles.css`, y el servidor local en `dev-server.js`.
