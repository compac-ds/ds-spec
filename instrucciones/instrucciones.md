# Instrucciones · Pantallas y prototipos CONTPAQi

Reglas comunes para construir pantallas, dashboards y prototipos de los aplicativos CONTPAQi con el Design System. Aplican a las cuatro líneas de producto. Lo específico de cada línea (colores, componentes, logos) vive en su DESIGN.md.

Versión de estas instrucciones: 1.0.1 · 2026-10-15

## 1. Fuente de verdad

- La única fuente de verdad visual es el DESIGN.md de la línea de producto. Nada de lo que generes puede usar colores, tipografías, radios, espaciados o íconos que no estén en ese archivo.
- Usa un solo DESIGN.md por pantalla. Nunca mezcles dos líneas.
- Si una regla de estas instrucciones contradice al DESIGN.md, prevalece el DESIGN.md.

## 2. Identificar línea y aplicativo

| Línea | Aplicativo por defecto | Otros aplicativos |
|---|---|---|
| Contable | Contabilidad | Bancos, Tesorería, Anticipa, Optimiza, XML en Línea, Conecta tu Banco |
| Administrativo | Comercial Pro | Comercial Start, Comercial Premium, Factura Electrónica, CFDI Facturación, Mi Factura, Timbra, Vende |
| Personas | Nóminas | Colabora, Evalúa, Kursa |
| Servicios | Respaldos | VDI |

- Si el usuario nombra un aplicativo, la línea se deduce de la tabla.
- Si no nombra aplicativo, usa el de la línea por defecto.
- Si no se puede deducir la línea, pregunta antes de construir.

## 3. Estructura obligatoria de toda pantalla

Lienzo de 1440 px de ancho:

```
App Header (96 px, ancho completo)
└─ Cuerpo: [Sidebar] [Contenido]
```

- **App Header:** copia literal de la implementación de referencia de la subsección App Header del DESIGN.md. Solo cambian el logo, los textos (versión, etapa, empresa, RFC, iniciales), los íconos de acción (0 a 5, según el aplicativo) y las secciones visibles. Al ocultar una sección se oculta su divisor.
- **Sidebar:** copia literal de la implementación de referencia de la subsección Sidebar. Inicia colapsado. Solo cambian los módulos del aplicativo, sus íconos Phosphor, el módulo activo y las opciones inferiores.
- **Contenido:** 16 px de separación respecto al sidebar, 32 px de margen derecho y 24 px de margen inferior. El primer elemento se alinea con el borde superior del sidebar.

"Copia literal" significa conservar el HTML, el CSS y el JS de referencia sin reescribirlos, reordenarlos ni simplificarlos. Si el entorno exige otro framework (por ejemplo React), porta la referencia sin cambiar medidas, colores, estructura ni comportamiento.

## 4. Logos

- Toma la URL del logo del manifiesto (`index.json`) o de la tabla de logos del DESIGN.md y úsala directamente en `<img src="...">` dentro del contenedor de 176×48 px.
- Si el logo del aplicativo figura como pendiente (`null` en el manifiesto), sustituye el `<img>` por `<div class="ah-logo ah-logo-pending" role="img" aria-label="Logo <Aplicativo> pendiente">Logo <Aplicativo></div>` (contenedor de 176×48 px con borde punteado, definido en el CSS de referencia) y avísalo.
- Nunca dibujes, recrees con texto ni sustituyas un logo por el de otro aplicativo.

## 5. Contenido

**Tokens y componentes**
- Usa los componentes de `components:` del DESIGN.md con sus valores exactos y sus estados (hover, focus, disabled, activo).
- Si necesitas un patrón que el archivo no define (por ejemplo, una gráfica), constrúyelo solo con tokens del archivo y dilo en tu respuesta.
- Espaciado solo en la escala del archivo: 4, 8, 12, 16, 24, 32, 40, 48, 56 y 64 px.
- Tipografía: solo Manrope y los niveles de `typography:`, con letter-spacing de -2%.

**Jerarquía**
- Una sola acción `button-primary` por vista. El resto va en `button-default`, `button-link` o `button-text`.
- El color `secondary` solo se usa en el tab segmentado y en superficies de acento, nunca en botones ni links.
- Orden de lo general a lo específico: tabs que definen el contenido, barra de herramientas que actúa sobre él, contenido.
- Separa los tabs del encabezado de una tabla con una barra de herramientas o al menos 16 px.

**Datos**
- Montos alineados a la derecha, con dígitos tabulares.
- Nombres de personas y empresas en formato título, no en mayúsculas.
- Estatus con badges semánticos: `success` para completado o pagado, `warning` para pendiente o por timbrar, `error` para vencido o fallido, `info` para parcial o informativo, `light` para neutral o abierto.
- Colorea la variación de un indicador según su efecto para el negocio, no según si sube o baja. Por ejemplo: que crezca "por cobrar" es negativo.
- Usa datos simulados verosímiles del dominio (RFC, folios, pólizas, CFDI) y aclara que son simulados.

**Íconos**
- Solo Phosphor Icons. Íconos de acción del header en peso Light; carets en peso Thin; módulos del sidebar en Light en reposo y Fill en activo o hover.
- Botones de solo ícono siempre con `aria-label`.

## 6. Modernizar una pantalla existente a partir de una captura

1. Conserva la información, las acciones y el flujo de la pantalla original. No elimines funciones sin decirlo.
2. Mapea cada elemento al componente equivalente del DESIGN.md: header y sidebar a sus referencias, tablas a `table-*`, botones a su tipo según jerarquía.
3. Reduce botones de colores distintos a una acción primaria más acciones default.
4. Unifica controles duplicados o sin etiqueta.
5. Entrega una tabla breve "pantalla actual → versión alineada al DS" y la lista de lo que no pudiste mapear o de los significados que desconoces.

## 7. Interacciones mínimas

- Toggle del sidebar entre colapsado y expandido, con la transición del DESIGN.md.
- Tabs y filtros que cambian de estado al hacer clic.
- Hover y focus visibles en todos los elementos interactivos; focus con contorno de 2 px en `focus-ring`.
- Otras interacciones solo si la pantalla las necesita (búsqueda que filtra, selección de filas, cierre de avisos, guardar con confirmación).

## 8. Formato de entrega según la herramienta

| Herramienta | Entrega |
|---|---|
| Claude | Artifact o archivo HTML autocontenido |
| ChatGPT | Canvas con un solo archivo HTML autocontenido |
| Genspark | Página o archivo HTML autocontenido |
| Figma Make | Componentes React; App Header y Sidebar como componentes propios portados de la referencia |
| Otra | Un solo archivo HTML autocontenido |

HTML autocontenido: CSS en `<style>`, JS mínimo en `<script>`, Manrope desde Google Fonts e íconos Phosphor como SVG inline o desde `@phosphor-icons/web`.

## 9. Errores conocidos que debes evitar

- **Íconos del sidebar:** las versiones Light y Fill de cada ícono comparten la misma celda (`.sb-icon > * { grid-area: 1 / 1; }`). Si se apilan, el ícono se desplaza al activarse.
- **Selectores del header:** el padding del selector de empresa (4 px 16 px) y el margen derecho del de usuario (8 px) deben prevalecer sobre la regla general de botones del header (`.app-header .ah-company-selector`, `.app-header .ah-user-selector`).
- **Tooltip del sidebar colapsado:** la lista de módulos no debe recortarlo; en colapsado su overflow es visible.
- **Cards de métrica en fila:** con el sidebar expandido quedan unos 1140 px útiles; calcula anchos para que 4 cards quepan y usa títulos cortos que no se partan en dos líneas.
- **Paneles y tablas:** paneles laterales y tablas ocupan el alto disponible; encabezado de tabla fijo al desplazar; paginación al fondo.
- **Botones de bloque:** ícono y texto centrados, nunca alineados a un lado.
- **Contraste:** si un token del DS no alcanza WCAG AA (por ejemplo, texto blanco sobre el naranja de Servicios o badges warning), úsalo tal cual y menciónalo. No lo corrijas por tu cuenta.

## 10. Revisión antes de entregar

- [ ] Todos los valores existen en el DESIGN.md.
- [ ] Header y sidebar son las referencias literales, con solo los cambios permitidos.
- [ ] Sidebar colapsado al cargar, con el módulo correcto activo.
- [ ] Una sola acción primaria.
- [ ] Logo real por URL o contenedor etiquetado; nunca un logo inventado.
- [ ] Sin elementos cortados, encimados ni textos partidos en controles.
- [ ] Botones de solo ícono con `aria-label`; focus visible.
- [ ] Respuesta con la versión cargada, los supuestos tomados, lo que no se pudo mapear y los warnings de contraste que aplican.

<!-- FIN instrucciones · v1.0.1 -->
