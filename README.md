# Sitio Web de Calíape

Sitio web oficial de Calíape - Tu compañera inteligente para el aprendizaje.

## 🚀 Guía de Instalación Paso a Paso

### Requisitos del Sistema

Este proyecto requiere:
- Ruby (versión 2.7 o superior, recomendado 3.4+)
- RubyGems (gestor de paquetes de Ruby)
- Bundler (gestor de dependencias)
- GCC y Make (para compilar extensiones nativas)

### Paso 1: Instalar Ruby

#### En macOS

**Opción A: Usando Homebrew y rbenv (Recomendado)**

```bash
# Instalar Homebrew si no lo tienes
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Instalar rbenv y ruby-build
brew install rbenv ruby-build

# Inicializar rbenv en tu shell
echo 'eval "$(rbenv init - zsh)"' >> ~/.zshrc
source ~/.zshrc

# Instalar Ruby 3.4.5 (o la versión más reciente)
rbenv install 3.4.5
rbenv global 3.4.5

# Verificar la instalación
ruby -v
```

**Opción B: Usando RVM**

```bash
# Instalar RVM
\curl -sSL https://get.rvm.io | bash -s stable

# Cargar RVM
source ~/.rvm/scripts/rvm

# Instalar Ruby
rvm install 3.4.5
rvm use 3.4.5 --default

# Verificar
ruby -v
```

#### En Windows

1. Descarga e instala [RubyInstaller](https://rubyinstaller.org/)
2. Durante la instalación, asegúrate de marcar "Add Ruby executables to your PATH"
3. Al finalizar, ejecuta `ridk install` para instalar MSYS2
4. Verifica con `ruby -v` en el Command Prompt

#### En Linux (Ubuntu/Debian)

```bash
# Actualizar el sistema
sudo apt update
sudo apt install -y build-essential

# Instalar rbenv
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/HEAD/bin/rbenv-installer | bash

# Configurar el shell
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc

# Instalar Ruby
rbenv install 3.4.5
rbenv global 3.4.5

# Verificar
ruby -v
```

### Paso 2: Instalar Bundler

Bundler es el gestor de dependencias para Ruby:

```bash
gem install bundler

# Verificar la instalación
bundle -v
```

### Paso 3: Clonar el Repositorio

```bash
# Clonar el repositorio
git clone https://github.com/fcolavecchia/caliape-website.git

# Entrar al directorio
cd caliape-website
```

### Paso 4: Instalar Dependencias del Proyecto

```bash
# Instalar todas las gemas necesarias (Jekyll, plugins, etc.)
bundle install
```

Este comando instalará:
- Jekyll 4.3.3
- Plugins de Jekyll (feed, seo-tag)
- Dependencias adicionales (csv, logger, base64)
- Todas las demás dependencias listadas en el Gemfile

### Paso 5: Ejecutar el Sitio Localmente

```bash
# Iniciar el servidor de desarrollo
bundle exec jekyll serve
```

Deberías ver una salida similar a:

```
Configuration file: /path/to/caliape-website/_config.yml
            Source: /path/to/caliape-website
       Destination: /path/to/caliape-website/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
       Jekyll Feed: Generating feed for posts
                    done in 0.5 seconds.
 Auto-regeneration: enabled for '/path/to/caliape-website'
    Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
```

### Paso 6: Ver el Sitio

Abre tu navegador en: **http://localhost:4000**

El sitio se recargará automáticamente cuando hagas cambios en los archivos.

---

## 🔧 Solución de Problemas Comunes

### Error: "cannot load such file -- csv"

Si usas Ruby 3.4+, asegúrate de que tu Gemfile incluya:

```ruby
gem "csv"
gem "logger"
gem "base64"
```

Luego ejecuta `bundle install` nuevamente.

### Error: "Permission denied"

Si obtienes errores de permisos al instalar gemas:

```bash
# NO uses sudo con rbenv/rvm
# En su lugar, asegúrate de que rbenv esté configurado correctamente
rbenv rehash
```

### Error: "GCC not found" o "Make not found"

**En macOS:**
```bash
xcode-select --install
```

**En Ubuntu/Debian:**
```bash
sudo apt install build-essential
```

### El sitio no se actualiza automáticamente

Usa el flag `--livereload`:

```bash
bundle exec jekyll serve --livereload
```

### Puerto 4000 ya en uso

Especifica otro puerto:

```bash
bundle exec jekyll serve --port 4001
```

---

## 🚀 Inicio Rápido (Para Colaboradores que ya tienen Ruby instalado)

Si ya tienes Ruby y Bundler instalados:

```bash
# 1. Clonar el repositorio
git clone https://github.com/fcolavecchia/caliape-website.git
cd caliape-website

# 2. Instalar dependencias
bundle install

# 3. Ejecutar el servidor
bundle exec jekyll serve

# 4. Abrir http://localhost:4000 en tu navegador
```

## 📁 Estructura del Proyecto

```
caliape-website/
├── _config.yml          # Configuración de Jekyll
├── _layouts/            # Plantillas HTML
│   ├── default.html     # Layout principal
│   ├── post.html        # Layout para posts del blog
│   └── privacy.html     # Layout para política de privacidad
├── _posts/              # Artículos del blog
│   └── 2025-12-01-bienvenidos-blog-caliape.md
├── _privacidad/         # Contenido de política de privacidad
│   └── 2025-12-01-privacidad.md
├── assets/
│   ├── css/
│   │   └── style.css    # Estilos principales
│   └── images/          # Imágenes del sitio
├── index.html           # Página de inicio (landing)
├── blog.html            # Página del blog
├── acerca.html          # Página "Acerca de"
└── Gemfile              # Dependencias de Ruby
```

## 📝 Páginas Principales

- **Inicio** (`index.html`): Landing page con hero section y características
- **Blog** (`blog.html`): Listado de artículos del blog
- **Acerca de** (`acerca.html`): Información sobre Calíape
- **Privacidad** (`_privacidad/`): Política de privacidad (contenido en Markdown)

## ✍️ Crear Nuevos Posts

Para crear un nuevo artículo en el blog:

1. Crea un nuevo archivo en `_posts/` con el formato: `YYYY-MM-DD-titulo-del-post.md`

2. Agrega el front matter al inicio del archivo:

```markdown
---
layout: post
title: "Título del Post"
date: 2025-12-01 10:00:00 -0300
author: Tu Nombre
tags: [etiqueta1, etiqueta2]
---

Contenido del post aquí...
```

## 📄 Actualizar Política de Privacidad

La política de privacidad usa un sistema similar a los posts del blog, con contenido separado en Markdown:

1. Para actualizar la política de privacidad, edita el archivo en `_privacidad/2025-12-01-privacidad.md`

2. Para crear una nueva versión con fecha actualizada:

```markdown
---
layout: privacy
title: Política de Privacidad
description: Política de privacidad de Calíape
date: 2025-12-15
permalink: /privacidad.html
---

Tu contenido en Markdown aquí...
```

**Nota:** Solo el archivo más reciente (por fecha) se mostrará en `/privacidad.html` gracias al permalink.

## 🎨 Personalización

### Colores

Los colores principales se definen en `assets/css/style.css`:

```css
:root {
    --primary-color: #4a90e2;
    --secondary-color: #2c3e50;
    --accent-color: #e74c3c;
}
```

### Configuración del Sitio

Edita `_config.yml` para cambiar:
- Título del sitio
- Descripción
- URL base
- Idioma
- Y más...

## 🌐 Despliegue

### GitHub Pages

1. Haz push de tus cambios a GitHub:

```bash
git add .
git commit -m "Mensaje del commit"
git push origin main
```

2. Ve a la configuración del repositorio en GitHub
3. En "Pages", selecciona la rama `main` como fuente
4. El sitio estará disponible en `https://www.caliape.com`

### Otros Servicios

Este sitio también puede desplegarse en:
- Netlify
- Vercel
- GitLab Pages
- Y otros servicios compatibles con Jekyll

## 🛠️ Comandos Útiles

```bash
# Servir el sitio localmente
bundle exec jekyll serve

# Servir con reloading automático
bundle exec jekyll serve --livereload

# Generar el sitio (sin servidor)
bundle exec jekyll build

# Limpiar archivos generados
bundle exec jekyll clean
```

## 📦 Plugins Instalados

- `jekyll-feed`: Genera un feed RSS para el blog
- `jekyll-seo-tag`: Mejora el SEO del sitio

## 🤝 Contribuir

Si deseas contribuir al sitio web de Calíape:

1. Haz fork del repositorio
2. Crea una rama para tu feature (`git checkout -b feature/nueva-caracteristica`)
3. Commit tus cambios (`git commit -am 'Agregar nueva característica'`)
4. Push a la rama (`git push origin feature/nueva-caracteristica`)
5. Abre un Pull Request

## 📄 Licencia

© 2025 Calíape. Todos los derechos reservados.

## 📞 Contacto

Para preguntas o sugerencias sobre el sitio web, visita nuestra [página de contacto](https://www.caliape.com/acerca.html).
