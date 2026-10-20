---
name: contpaqi-screens
version: "1.0.1"
description: Genera pantallas, dashboards y prototipos de los aplicativos CONTPAQi apegados al Design System, cargando en vivo el DESIGN.md y las instrucciones publicadas en https://compac-ds.github.io/ds-spec/. Úsalo siempre que el usuario pida una pantalla, vista, dashboard, mockup, prototipo o rediseño de cualquier aplicativo CONTPAQi (Contabilidad, Bancos, Comercial, Factura Electrónica, Nóminas, Colabora, Evalúa, Kursa, Respaldos, VDI, etc.), aunque no mencione el Design System, y también cuando comparta una captura de una pantalla actual para modernizarla.
inclusion: auto
---

# Pantallas CONTPAQi · DS Spec

Construyes pantallas de aplicativos CONTPAQi con el Design System. Las reglas, los tokens y los logos no están en este skill: se publican en un sitio y se actualizan ahí. Antes de construir cualquier cosa, cárgalos.

Manifiesto: https://compac-ds.github.io/ds-spec/index.json

## Paso 1. Cargar el manifiesto

Descarga el manifiesto agregando `?t=<fecha y hora actual>` al final de la URL, para evitar versiones en caché. De ahí obtienes:

- `version`: versión vigente del DS Spec.
- `instructions`: URL de las instrucciones comunes.
- `lines.<línea>.design`: URL del DESIGN.md de cada línea.
- `lines.<línea>.sentinel`: marca con la que termina ese DESIGN.md.
- `lines.<línea>.defaultApp` y `lines.<línea>.apps`: aplicativos y la URL de su logo (`null` si está pendiente).

## Paso 2. Identificar línea y aplicativo

Con la petición del usuario y la lista `apps` del manifiesto, identifica la línea y el aplicativo. Si no indica aplicativo, usa `defaultApp`. Si no puedes deducir la línea, pregunta.

## Paso 3. Cargar las instrucciones y el DESIGN.md completos

1. Descarga el archivo de `instructions` y el `design` de la línea, también con `?t=<fecha y hora>`.
2. Necesitas el **texto completo y literal**, no un resumen. Si tu herramienta de navegación resume o recorta páginas, descarga los archivos con ejecución de código (por ejemplo, `requests.get(url).text` en Python) y trabaja con el texto obtenido.
3. **Verifica que los archivos estén completos:**
   - El DESIGN.md debe terminar exactamente con el `sentinel` de su línea.
   - Las instrucciones deben terminar con `<!-- FIN instrucciones`.
   - Los bloques de código de App Header y Sidebar deben estar completos.

## Paso 4. Si no pudiste cargarlos, detente

Si no puedes descargar algún archivo, o no encuentras su marca de fin, **no construyas la pantalla de memoria ni con supuestos**. Dile al usuario qué archivo falló y pídele que lo adjunte en la conversación, o que pegue su contenido. Continúa solo cuando lo tengas completo.

## Paso 5. Declarar lo que cargaste

Empieza tu respuesta con una línea como esta:

> DS Spec v`<version>` · Línea `<línea>` · Aplicativo `<aplicativo>` · Logo: `<cargado | pendiente>`

## Paso 6. Construir

Sigue las instrucciones descargadas y el DESIGN.md de la línea al pie de la letra. Si algo de este skill contradice a esos archivos, prevalecen ellos, porque son la versión vigente.
