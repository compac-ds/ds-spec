# Changelog · 2026-10-21

## 🆕 Agregado

### Skill `contpaqi-screens` (Commit 0a5d9b7)

**Qué:**
- Nuevo skill para generar pantallas, dashboards y prototipos de aplicativos CONTPAQi
- Carga dinámica del Design System Spec desde GitHub
- Automatización de descarga: manifiesto, instrucciones y DESIGN.md
- Validación de integridad mediante sentinelas
- Disponible en Claude, Genspark y Kiro

**Beneficios:**
- Los diseños usan la versión vigente del DS sin reinstalar
- Automatiza acceso a logos, tokens y componentes
- Evita errores por archivos incompletos o cacheados
- Consistencia en todas las plataformas

---

## 🔄 Actualizado / Cambios

### Instrucciones Figma nativa (Commit 4271767)

**Qué cambió:**

| Aspecto | Antes | Ahora |
|---------|-------|-------|
| Construcción en Figma | No documentada | Construcción nativa: componentes, variables, estilos del DS |
| Valores en Figma | Ambiguo | Explícito: "sin HTML ni valores literales" |
| Componentes faltantes | No especificado | "Repórtalo; no lo dibujes con valores literales" |
| Logos pendientes | HTML específico (`<div class="ah-logo-pending">`) | Agnóstico: "borde punteado y etiqueta" |

**Por qué:**
- MCP Figma permite envío directo de código a Figma
- Componentes + variables = pantallas editables y mantenibles
- Evita captura literal que crea pantallas estáticas
- Simplifica instrucciones (agnósticas a tecnología)

**Líneas alteradas:** 5 insertadas, 2 deletadas en `instrucciones/instrucciones.md`

---

## 🗑️ Deprecado

### Archivo `instrucciones.md` en raíz (Commit 22b2fea)

**Qué:** Eliminada copia de instrucciones en la raíz del repo

**Por qué:**
- Evita duplicación y confusión
- La fuente única es `instrucciones/instrucciones.md`
- Reduce mantenimiento

---

## 📊 Resumen

| Métrica | Valor |
|---------|-------|
| Archivos agregados | 1 (SKILL.md) |
| Archivos eliminados | 1 (instrucciones.md raíz) |
| Archivos modificados | 2 (instrucciones/instrucciones.md, index.json) |
| Cambios de contenido | 2 (Figma nativo + simplificación logos) |
| Versión | 1.0.2 (contenido actualizado) |
| Impacto | Medio — Solidifica integración Figma y automatiza cadena de diseños |
