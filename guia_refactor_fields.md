# Guía para refactorizar `fields.json` y otros archivos de un theme en HubSpot

> **Objetivo:** Mantener los ajustes globales (`theme/fields.json`) enfocados en **estilos** y migrar todo el **contenido** a módulos o plantillas, evitando errores de validación.

---

## 1. Principios clave

- **Estilo en **``**:** colores, tipografías, espaciados, bordes, toggles, etc.
- **Contenido en módulos/plantillas:** texto, imágenes, listas, testimonios, tarjetas, etc.
- Mantener la separación facilita la edición para marketing y elimina advertencias en HubSpot.

---

## 2. Tipos de campo **permitidos** en `theme/fields.json`

| Tipo                                                                               | Uso recomendado                                    |
| ---------------------------------------------------------------------------------- | -------------------------------------------------- |
| `color`                                                                            | Paleta corporativa, colores de botones, fondos     |
| `font`                                                                             | Familias y tamaños base                            |
| `boolean`                                                                          | Activar/desactivar características visuales        |
| `choice`                                                                           | Selección de variantes de layout, estilos de borde |
| `number`                                                                           | Valores simples (ancho máx, radio de bordes)       |
| `border`, `spacing`, `alignment`, `gradient`, `icon`, `shadow`, `background_image` | Controles visuales avanzados                       |

> **Nota:** Estos campos afectan a todo el sitio y no deben contener información específica de una página.

---

## 3. Tipos **NO** permitidos en `theme/fields.json`

- `text`, `richtext`
- `image`, `file`
- `repeater`, `group` que contenga contenido textual o multimedia
- Cualquier campo destinado a mostrar **contenido** en lugar de **estilo**

---

## 4. Patrón de migración de contenido a módulos

1. **Detectar** el campo o grupo inválido.
2. **Crear** un módulo (p. ej. `/modules/content_cards.module`).
3. En el `fields.json` del módulo, definir los campos necesarios («repeater», `text`, `image`, etc.).
4. **Insertar** el módulo en la plantilla correspondiente:
   ```hubl
   {% module "content_cards" path="@custom/content_cards", label="Tarjetas de contenido" %}
   ```
5. **Eliminar** el campo del `theme/fields.json`.

---

## 5. Proceso de refactor paso a paso

1. **Auditoría rápida**
   ```bash
   grep -R "\"type\": \"text\"" theme/fields.json
   ```
2. **Clasifica** cada entrada:
   - ¿Afecta al diseño global? → Mantener y/o convertir a tipo permitido.
   - ¿Es contenido específico? → Migrar a módulo.
3. **Implementa** los cambios:
   - Crear módulo y mover campos.
   - Sustituir referencias en plantillas.
   - Limpiar `theme/fields.json`.
4. **Validación**
   - Ejecuta `hs lint` o revisa errores en Design Manager.
   - Sube con `hs upload` o `hs watch` y comprueba que no haya advertencias.
   - Prueba la edición en el CMS (Theme settings y módulos).

---
  
## 8. Recursos de referencia

- Documentación oficial: [https://developers.hubspot.com/docs/cms/building-blocks/themes#fields-json](https://developers.hubspot.com/docs/cms/building-blocks/themes#fields-json)
- Boilerplate recomendado: [https://github.com/HubSpot/cms-theme-boilerplate](https://github.com/HubSpot/cms-theme-boilerplate)

---

**¡Listo!** Con esta guía podrás corregir cualquier `fields.json` y mantener tu theme limpio, escalable y libre de errores.

