# Configuración de Decap CMS con GitHub

Esta guía te ayudará a configurar Decap CMS (anteriormente Netlify CMS) para que funcione con GitHub Pages usando autenticación OAuth.

## 📋 Requisitos Previos

1. Un repositorio en GitHub
2. El sitio desplegado en GitHub Pages
3. Acceso de administrador al repositorio

## 🔧 Configuración Paso a Paso

### Opción 1: Usar Proxy OAuth (Recomendado - Más Fácil)

Esta es la opción más simple y no requiere configuración adicional de OAuth Apps.

1. **Verificar configuración actual**:
   - El archivo `static/admin/config.yml` ya está configurado con:
     ```yaml
     backend:
       name: github
       repo: vicoyes/landing_conectores_hugo
       branch: master
       base_url: https://decapcms-oauth.netlify.app
     ```
   - Este es un proxy OAuth público y gratuito que facilita la autenticación.

2. **Acceder al CMS**:
   - Ve a: `https://vicoyes.github.io/landing_conectores_hugo/admin/`
   - Haz clic en "Login with GitHub"
   - Autoriza la aplicación
   - ¡Listo! Ya puedes editar contenido

**¡Eso es todo!** No necesitas configurar nada más. El proxy OAuth maneja la autenticación automáticamente.

### Opción 2: Configurar tu Propia OAuth App (Opcional)

Si prefieres usar tu propia OAuth App de GitHub (más control):

#### Paso 1: Crear GitHub OAuth App

1. Ve a tu perfil de GitHub → **Settings** → **Developer settings** → **OAuth Apps**
2. Haz clic en **"New OAuth App"**
3. Completa el formulario:
   - **Application name**: `Decap CMS - Landing Conectores`
   - **Homepage URL**: `https://vicoyes.github.io/landing_conectores_hugo`
   - **Authorization callback URL**: `https://vicoyes.github.io/landing_conectores_hugo/admin/`
4. Haz clic en **"Register application"**
5. **Copia el Client ID** (lo necesitarás después)
6. Haz clic en **"Generate a new client secret"** y **copia el Client Secret**

#### Paso 2: Actualizar config.yml

Actualiza `static/admin/config.yml`:

```yaml
backend:
  name: github
  repo: vicoyes/landing_conectores_hugo
  branch: master
  base_url: https://vicoyes.github.io/landing_conectores_hugo
  auth_type: implicit
  app_id: TU_CLIENT_ID_AQUI  # El Client ID que copiaste
```

## 🔐 Permisos Necesarios

El usuario que se autentique necesita tener **permisos de escritura** en el repositorio. Para repositorios privados o si quieres limitar quién puede editar:

1. Ve a **Settings** → **Collaborators** en tu repositorio
2. Añade colaboradores con permisos de **Write** o **Admin**

## 🚀 Verificación

1. Despliega tu sitio en GitHub Pages
2. Visita `https://vicoyes.github.io/landing_conectores_hugo/admin/`
3. Deberías ver la pantalla de login de Decap CMS
4. Haz clic en "Login with GitHub"
5. Autoriza la aplicación
6. Deberías ver el editor de contenido

## ⚠️ Notas Importantes

- **Rama del repositorio**: Asegúrate de que `branch: master` en `config.yml` coincida con tu rama principal
- **URL del repositorio**: El formato debe ser `usuario/repositorio` (sin `https://github.com/`)
- **Archivos editables**: Solo los archivos definidos en `collections` de `config.yml` serán editables
- **Cambios**: Los cambios se guardan directamente en el repositorio como commits

## 📝 Sobre Decap CMS

Decap CMS (anteriormente Netlify CMS) es un CMS headless de código abierto:

- ✅ Interfaz intuitiva y fácil de usar
- ✅ Soporte completo para GitHub OAuth
- ✅ Buen rendimiento
- ✅ Formato de configuración simple y flexible

## 🐛 Solución de Problemas

### Error: "Failed to load entry"
- Verifica que la ruta del archivo en `config.yml` sea correcta
- Asegúrate de que el archivo existe en el repositorio

### Error: "Authentication failed"
- Verifica que la URL de callback en GitHub OAuth App sea correcta (si usas Opción 2)
- Asegúrate de que el `base_url` en `config.yml` coincida con tu URL de GitHub Pages

### No puedo ver el botón de login
- Verifica que el archivo `static/admin/index.html` esté presente
- Asegúrate de que el sitio esté desplegado correctamente
- Verifica la consola del navegador para errores

## 📚 Recursos Adicionales

- [Documentación oficial de Decap CMS](https://decapcms.org/)
- [Guía de GitHub OAuth Apps](https://docs.github.com/en/apps/oauth-apps/building-oauth-apps/creating-an-oauth-app)

