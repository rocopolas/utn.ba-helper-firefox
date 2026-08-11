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

> ⚠️ **El mantenedor del proyecto original sabotea activamente a este port.**

El **servidor comunitario** (`pablomatiasgomez.com.ar/utnba-helper`) no está caído: funciona, pero el
mantenedor le puso un candado **anti-fork deliberado** para que la extensión que él controla sea la
única que pueda usar los datos. Solo responde con datos reales si la request lleva
`Origin: chrome-extension://jdgdheoeghamkhfppapjchbojhehimpe` — el ID de su extensión oficial de
Chrome —. A cualquier otro cliente (este port de Firefox, curl, otros navegadores, incluso la propia
web del proyecto) le devuelve un `{}` falso como señuelo, fingiendo que no hay nada.

Es imposible que Firefox envíe ese header de `Origin` (es un header **prohibido** por el spec de
fetch, no se puede forzar), así que **este port queda bloqueado del servidor comunitario por decisión
del mantenedor, no por un defecto nuestro**:

- ✅ **Funcionan** (leen el DOM de Guaraní y calculan localmente): nombre de materias en la grilla
  de la Agenda/Horarios, Seguimiento de Plan (cálculo local de promedios/peso académico),
  recolección y envío de datos anonimizados (los POST al servidor están bloqueados igual que los GET).
- ❌ **No funcionan** (dependen del servidor comunitario): Buscar Docentes, Buscar Cursos, la
  predicción de profesores al inscribirse y las encuestas docentes agregadas. Muestran
  "No hay resultados disponibles del servidor comunitario en este momento.".

Esta actitud es contraproducente: los datos fueron aportados por la comunidad de estudiantes, no por
el mantenedor, y bloquear forks para acaparar el acceso a datos comunitarios va en contra del
espíritu del proyecto (código abierto, licencia MIT). Si en algún momento quiere reconsiderarlo,
bastaría con que agregue el origen de este port a una whitelist en el servidor.

## Instalación y privacidad

- Guía: [GUIA_DE_INSTALACION.md](GUIA_DE_INSTALACION.md)
- Política de privacidad: [PRIVACY_POLICY.md](PRIVACY_POLICY.md)

## Créditos

- Original: [pablomatiasgomez/utn.ba-helper](https://github.com/pablomatiasgomez/utn.ba-helper)
- Este port: [rocopolas/utn.ba-helper-firefox](https://github.com/rocopolas/utn.ba-helper-firefox)