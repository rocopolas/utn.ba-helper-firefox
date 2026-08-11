<div align="center">
  <img src="https://raw.githubusercontent.com/pablomatiasgomez/utn.ba-helper/master/public/icons/icon128.png" alt="logo">

  # UTN.BA Helper - Port para Firefox

  **Fork para Firefox/Gecko** del proyecto original [utn.ba-helper](https://github.com/pablomatiasgomez/utn.ba-helper) de [Pablo Matías Gomez](https://github.com/pablomatiasgomez). Extensión que facilita el uso del sitio de la **UTN - FRBA** (SIU Guaraní).
</div>

## Diferencias con el original

- **Firefox** — adaptado a Manifest V3 de Gecko (`background.scripts`, `browser_specific_settings.gecko`, APIs `browser.*`); versión mínima Firefox 109. Funciona también en Zen Browser.
- **Sin telemetría** — se eliminaron el SDK de Embrace y el logging/estadísticas (`logMessage`, `logUserStat`). No se envían datos de uso ni errores a servidores de análisis.
- Header `X-Client: FIREFOX@<versión>`.

## Funcionalidades y limitación del servidor comunitario

El código es idéntico al original, pero el **servidor comunitario** (`pablomatiasgomez.com.ar/utnba-helper`)
tiene un candado **anti-fork**: solo responde con datos reales a la extensión oficial de Chrome,
identificada por su `Origin: chrome-extension://jdgdheoeghamkhfppapjchbojhehimpe`. A cualquier otro
cliente (incluido este port de Firefox, curl, u otros navegadores) le devuelve `{}` como señuelo.

Firefox no puede enviar ese header de `Origin` (es un header prohibido por el spec de fetch), por lo
que **este port no puede acceder a los datos del servidor comunitario**:

- ✅ **Funcionan** (leen el DOM de Guaraní y calculan localmente): nombre de materias en la grilla
  de la Agenda/Horarios, Seguimiento de Plan (cálculo local de promedios/peso académico),
  recolección y envío de datos anonimizados (los POST al servidor están bloqueados igual que los GET).
- ❌ **No funcionan** (dependen del servidor comunitario): Buscar Docentes, Buscar Cursos, la
  predicción de profesores al inscribirse y las encuestas docentes agregadas. Muestran
  "No hay resultados disponibles del servidor comunitario en este momento.".

Esto no es un bug del port: la extensión original de Chrome funciona porque es la única que el
servidor acepta. Para habilitar estas secciones haría falta que el mantenedor del proyecto original
whitelistee el origen de este port en el servidor.

## Instalación y privacidad

- Guía: [GUIA_DE_INSTALACION.md](GUIA_DE_INSTALACION.md)
- Política de privacidad: [PRIVACY_POLICY.md](PRIVACY_POLICY.md)

## Créditos

- Original: [pablomatiasgomez/utn.ba-helper](https://github.com/pablomatiasgomez/utn.ba-helper)
- Este port: [rocopolas/utn.ba-helper-firefox](https://github.com/rocopolas/utn.ba-helper-firefox)