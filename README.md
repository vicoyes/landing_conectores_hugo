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
   - Una vez completado, tu sitio estará disponible en: `https://vicoyes.github.io/landing_conectores_hugo/`

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

## 📝 Gestión de Contenido con Decap CMS

Este proyecto incluye **Decap CMS** (anteriormente Netlify CMS) para gestionar el contenido de forma visual.

### Acceder al CMS

Una vez desplegado, accede al panel de administración en:
```
https://vicoyes.github.io/landing_conectores_hugo/admin/
```

### Configuración

El CMS está configurado para usar GitHub OAuth a través de un proxy público. Para más detalles sobre la configuración, consulta el archivo **[SVELTIA_CMS_SETUP.md](SVELTIA_CMS_SETUP.md)** (aunque el nombre del archivo menciona Sveltia, la configuración es para Decap CMS).

### Opción 1: Configuración Rápida (Recomendada)

**¡No necesitas hacer nada!** La configuración ya está lista:

1. Despliega el sitio en GitHub Pages
2. Visita `/admin/` en tu sitio
3. Haz clic en "Login with GitHub"
4. Autoriza la aplicación
5. ¡Ya puedes editar contenido!

### Desarrollo Local

Para probar el CMS localmente:

1. Descomenta `local_backend: true` en `static/admin/config.yml`
2. Ejecuta `hugo server`
3. Accede a `http://localhost:1313/admin/`
4. El CMS funcionará sin autenticación (solo para desarrollo)

## 📝 Licencia

© 2025 Empieza de Cero. Todos los derechos reservados.

