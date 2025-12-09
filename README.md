# Landing Page - Programa de Conectores

Landing page para el Programa de Conectores de Empieza de Cero, construida con Hugo.

## 🚀 Despliegue en GitHub Pages

Este proyecto está configurado para desplegarse automáticamente en GitHub Pages usando GitHub Actions.

### Requisitos previos

1. Tener un repositorio en GitHub
2. Habilitar GitHub Pages en la configuración del repositorio:
   - Ve a **Settings** → **Pages**
   - En **Source**, selecciona **GitHub Actions**

### Configuración

1. **Rama principal**: El workflow está configurado para la rama `master`. Si tu repositorio usa `main`, actualiza el archivo `.github/workflows/hugo.yml`:

```yaml
push:
  branches: ["main"]  # Cambia "master" por "main" si es necesario
```

2. **Primer despliegue**:
   - Haz push de tu código a la rama principal
   - El workflow se ejecutará automáticamente
   - Ve a **Actions** en GitHub para ver el progreso
   - Una vez completado, tu sitio estará disponible en: `https://[tu-usuario].github.io/[nombre-repositorio]/`

### Desarrollo local

```bash
# Instalar Hugo (si no lo tienes)
# macOS: brew install hugo
# Linux: Consulta https://gohugo.io/installation/

# Ejecutar servidor local
hugo server

# El sitio estará disponible en http://localhost:1313
```

### Estructura del proyecto

```
.
├── content/          # Contenido en Markdown
├── layouts/          # Plantillas HTML
├── static/           # Archivos estáticos (CSS, JS, imágenes)
├── public/           # Sitio generado (no commitear)
└── hugo.toml         # Configuración de Hugo
```

### Notas importantes

- El directorio `public/` se genera automáticamente y está en `.gitignore`
- Los archivos en `static/` se copian directamente al sitio final
- El `baseURL` en `hugo.toml` se ajusta automáticamente durante el despliegue

## 📝 Licencia

© 2025 Empieza de Cero. Todos los derechos reservados.

