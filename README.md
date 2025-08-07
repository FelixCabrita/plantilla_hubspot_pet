# 🐕 Vida Perruna con Nala - Tema HubSpot

Un tema moderno y adorable para HubSpot CMS diseñado para cuentas de mascotas en redes sociales. Perfecto para crear landing pages tiernas y profesionales.

## ✨ Características

- **Diseño responsive** - Se adapta perfectamente a móviles, tablets y desktop
- **Drag & Drop** - Los marketers pueden reordenar secciones fácilmente
- **Completamente editable** - Todos los textos e imágenes son editables desde el CMS
- **Colores personalizables** - Variables CSS para cambiar colores desde el editor
- **Animaciones suaves** - Efectos visuales modernos y profesionales
- **SEO optimizado** - Estructura semántica y meta tags incluidos

## 🎨 Paleta de Colores

- **Primario**: Rosa suave (#ffeef8)
- **Botones**: Rosa vibrante (#ff69b4)
- **Gradientes**: Rosa a azul pastel
- **Texto**: Grises profesionales

## 📁 Estructura del Proyecto

```
mi_landing_theme/
├── theme.json                    # Configuración del tema
├── fields.json                   # Variables globales (colores)
├── templates/
│   ├── landing.html             # Plantilla principal
│   └── landing.dnd.json         # Configuración Drag & Drop
├── modules/                     # Módulos reutilizables
│   ├── cta_button/             # Botón de call-to-action
│   ├── stats_cards/            # Tarjetas de estadísticas
│   ├── gallery/                # Galería de fotos
│   ├── content_cards/          # Tarjetas de contenido
│   ├── schedule/               # Horario de publicaciones
│   ├── cta_section/            # Sección CTA final
│   └── footer/                 # Pie de página
├── css/
│   └── main.css                # Estilos principales
└── images/
    └── template-preview.png    # Preview del tema
```

## 🚀 Instalación

### Prerrequisitos

1. **Cuenta HubSpot** con acceso al CMS Hub
2. **HubSpot CLI** instalado globalmente:
   ```bash
   npm install -g @hubspot/cli
   ```
3. **Configuración de cuenta**:
   ```bash
   hs init
   ```

### Pasos de Instalación

1. **Crea la carpeta del proyecto**:
   ```bash
   mkdir mi_landing_theme
   cd mi_landing_theme
   ```

2. **Crea la estructura de archivos** según la estructura mostrada arriba

3. **Copia todos los archivos** del repositorio en sus respectivas carpetas

4. **Sube el tema a HubSpot**:
   ```bash
   hs upload mi_landing_theme
   ```

5. **Activa el modo watch** para desarrollo (opcional):
   ```bash
   hs watch mi_landing_theme
   ```

## 📋 Módulos Incluidos

### 🎯 CTA Button
- Texto del botón editable
- URL personalizable
- Estilo consistente con el tema

### 📊 Stats Cards
- 4 tarjetas para mostrar datos de la mascota
- Completamente personalizables
- Diseño responsive

### 🖼️ Gallery
- Galería de fotos drag & drop
- Hasta 12 imágenes
- Placeholders automáticos
- Texto descriptivo editable

### 📝 Content Cards
- Tarjetas de contenido con emojis
- Texto personalizable
- Diseño de grid responsive

### 📅 Schedule
- Horario de publicaciones
- Días editables
- Diseño de calendario visual

### 📢 CTA Section
- Sección de llamada a la acción final
- Texto editable con Rich Text
- Botón integrado

### 🦶 Footer
- Enlaces sociales personalizables
- Copyright editable
- Iconos de redes sociales

## 🎛️ Personalización

### Colores Globales

Los colores se pueden cambiar desde el editor de HubSpot en la sección de **Configuración del Tema**:

- `primary_bg`: Color de fondo principal
- `btn_color`: Color de botones
- `btn_hover_color`: Color de botones al hacer hover

### Variables CSS

```css
:root {
    --primary-bg: {{ theme.primary_bg.color }};
    --btn-color: {{ theme.btn_color.color }};
    --btn-hover-color: {{ theme.btn_hover_color.color }};
}
```

## 📱 Uso en el Editor

1. **Crear nueva página** en HubSpot
2. **Seleccionar** el template "Landing Page Nala"
3. **Usar el editor Drag & Drop** para personalizar secciones
4. **Editar contenido** directamente en cada módulo
5. **Personalizar colores** en la configuración del tema
6. **Publicar** la página

## 🔧 Desarrollo

### Comandos útiles

```bash
# Subir cambios
hs upload mi_landing_theme

# Modo desarrollo (sync automático)
hs watch mi_landing_theme

# Ver logs
hs logs

# Validar tema
hs lint mi_landing_theme
```

### Estructura de un Módulo

Cada módulo debe tener:
- `module.html` - Template del módulo
- `fields.json` - Campos editables
- `meta.json` - Metadatos del módulo

## 🎨 Capturas de Pantalla

### Vista Desktop
- Hero section con gradiente rosa
- Tarjetas de estadísticas interactivas
- Galería de fotos responsiva
- Sección de horarios visual

### Vista Mobile
- Diseño completamente responsive
- Navegación optimizada para móvil
- Botones de tamaño apropiado

## 🐛 Solución de Problemas

### Error: "Template missing standard_header_includes"
**Solución**: Asegúrate de que `{{ standard_header_includes }}` esté en el `<head>`

### Error: "Template missing standard_footer_includes"
**Solución**: Agrega `{{ standard_footer_includes }}` antes de `</body>`

### Error: "Cannot deserialize fields.json"
**Solución**: Los `fields.json` deben ser arrays `[]`, no objetos `{}`

### CSS no se carga
**Solución**: Verifica que el path en `require_css()` sea correcto

## 📞 Soporte

Para problemas relacionados con:
- **HubSpot CMS**: [Documentación oficial](https://developers.hubspot.com/docs/cms)
- **HubSpot CLI**: [Guía CLI](https://developers.hubspot.com/docs/cms/developer-reference/local-development-cms-cli)

## 📄 Licencia

Este tema está diseñado para uso personal y comercial. Siéntete libre de modificarlo según tus necesidades.

## 🤝 Contribuir

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -am 'Agrega nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Crea un Pull Request

## 📝 Changelog

### v1.0.0 (2025-01-01)
- ✨ Lanzamiento inicial
- 🎨 Diseño completo responsive
- 📱 7 módulos personalizables
- 🎛️ Variables de color globales
- 🐕 Tema optimizado para mascotas

---

**¡Hecho con ❤️ para los amantes de las mascotas!**