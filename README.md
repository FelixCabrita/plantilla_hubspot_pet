# Plantilla HubSpot Pet - Nala Theme

Un tema completo de HubSpot CMS diseñado para páginas de mascotas, específicamente para "Vida Perruna con Nala". Este tema incluye módulos drag-and-drop completamente editables desde el CMS de HubSpot.

## Estructura del Proyecto

```
plantilla_hubspot_pet/
├── hsproject.json              # Configuración del proyecto HubSpot
├── nala_theme/                 # Directorio principal del tema
│   ├── theme.json              # Configuración del tema
│   ├── fields.json             # Variables globales del tema
│   ├── templates/
│   │   └── landing_page.dnd.json
│   ├── modules/
│   │   ├── hero_image.module/
│   │   ├── stat_card.module/
│   │   ├── content_card.module/
│   │   ├── day_card.module/
│   │   └── cta_button.module/
│   └── css/
│       └── main.css
```

## Características

- **Drag & Drop**: Plantilla completamente editable con módulos drag-and-drop
- **Módulos Reutilizables**: Tarjetas de estadísticas, contenido y programación repetibles
- **Variables Globales**: Control de colores, tipografías y efectos visuales desde Theme Settings
- **Responsive**: Diseño adaptativo para todos los dispositivos
- **Animaciones**: Efectos visuales suaves y modernos
- **SEO Friendly**: Estructura semántica y accesible

## Variables de Tema

El tema incluye las siguientes variables globales editables:

- **Primary Gradient**: Color principal del gradiente
- **Accent Gradient**: Color secundario del gradiente  
- **Base Font**: Fuente principal del sitio
- **Show Card Shadows**: Toggle para activar/desactivar sombras en tarjetas

## Módulos Incluidos

1. **Hero Image**: Sección principal con emoji, título, subtítulo y CTA
2. **Stat Cards**: Tarjetas de estadísticas repetibles
3. **Content Cards**: Tarjetas de contenido con emoji y texto
4. **Day Cards**: Tarjetas para mostrar días de programación
5. **CTA Button**: Sección de llamada a la acción final

## Instalación

1. Clona este repositorio
2. Asegúrate de tener la HubSpot CLI instalada
3. Ejecuta `hs upload nala_theme` para subir el tema a tu portal

## Uso

1. Ve a Design Manager en tu portal de HubSpot
2. Selecciona el tema "Nala Theme"
3. Crea una nueva página usando la plantilla "Nala Landing Page"
4. Edita el contenido usando los módulos drag-and-drop

## Personalización

- Modifica los colores y fuentes desde **Theme Settings**
- Agrega/elimina elementos repetibles desde cada módulo
- Personaliza los estilos editando `css/main.css`

## Soporte

Para dudas o soporte, consulta la documentación oficial de HubSpot CMS:
- [HubSpot CMS Developer Docs](https://developers.hubspot.com/docs/cms)
- [HubSpot CLI](https://developers.hubspot.com/docs/cms/developer-reference/local-development-cms-cli)