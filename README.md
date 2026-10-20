# Conpac DS Spec

Especificación del Design System para generar pantallas y prototipos con herramientas de IA.

## Contenido

| Ruta | Contenido |
|---|---|
| `index.json` | Manifiesto: versión vigente, líneas, aplicativos, URLs de DESIGN.md y logos |
| `instrucciones/instrucciones.md` | Reglas comunes a las cuatro líneas |
| `<línea>/DESIGN.md` | Tokens, componentes y referencias de App Header y Sidebar de la línea |
| `<línea>/assets/logos/<aplicativo>.svg` | Logos horizontales de los aplicativos |

Líneas: `contable`, `administrativo`, `personas`, `servicios`.

## Cómo publicar una actualización

1. Edita el archivo que cambia.
2. Sube el número de versión en los cuatro lugares donde aparece:
   - `index.json`: campos `version` y `updated`, y el `sentinel` de cada línea modificada.
   - `<línea>/DESIGN.md`: la versión al final de `description` y la marca de fin de la última línea.
   - `instrucciones/instrucciones.md`: la línea "Versión de estas instrucciones" y la marca de fin, si cambiaron.
3. La marca de fin de cada DESIGN.md debe coincidir exactamente con su `sentinel` en `index.json`. Si no coinciden, las herramientas rechazan el archivo.
4. Haz commit en `main`. GitHub Pages publica en 1 o 2 minutos.

Versionado: cambios de contenido sin impacto visual suben el último número (1.0.1); componentes nuevos o cambios de tokens suben el del medio (1.1.0); cambios de estructura suben el primero (2.0.0).

## Cómo agregar un logo

1. Exporta el logo horizontal como SVG con el nombre del aplicativo en minúsculas, sin acentos y con guion bajo (por ejemplo `factura_electronica.svg`).
2. Súbelo a `<línea>/assets/logos/`.
3. En `index.json`, cambia el `logo` de ese aplicativo de `null` a su URL.
4. En el DESIGN.md de la línea, sustituye "Pendiente" en la tabla de logos por la misma URL.
5. Sube la versión según el procedimiento anterior.
