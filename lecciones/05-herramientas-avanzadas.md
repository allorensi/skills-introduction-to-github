# Lección 5: Herramientas Avanzadas y Buenas Prácticas

## 🎯 Objetivos de Aprendizaje
Al finalizar esta lección, podrás:
- Usar GitHub Pages para crear sitios web
- Configurar GitHub Actions básicos
- Implementar buenas prácticas de desarrollo
- Usar herramientas avanzadas de GitHub

## 🌐 GitHub Pages: Tu Sitio Web Gratis

### ¿Qué es GitHub Pages?
GitHub Pages te permite **alojar sitios web estáticos** directamente desde tus repositorios de GitHub, ¡gratis!

### Configurar GitHub Pages

#### Método 1: Desde la rama main
1. **Ve a tu repositorio** en GitHub
2. **Haz clic en "Settings"**
3. **Busca "Pages"** en el menú lateral
4. **Selecciona "Deploy from a branch"**
5. **Elige "main"** como rama
6. **Haz clic en "Save"**

#### Método 2: Carpeta docs/
```bash
# Crear carpeta para el sitio
mkdir docs
cd docs

# Crear archivo index.html
cat > index.html << EOF
<!DOCTYPE html>
<html>
<head>
    <title>Mi Sitio en GitHub Pages</title>
</head>
<body>
    <h1>¡Hola mundo desde GitHub Pages!</h1>
    <p>Este sitio está alojado en GitHub Pages.</p>
</body>
</html>
EOF

# Hacer commit y push
git add docs/
git commit -m "Agregar sitio web básico"
git push origin main
```

Luego en configuración de Pages, selecciona `main` y carpeta `/docs`.

### Tu URL será:
`https://tu-usuario.github.io/nombre-repositorio`

## 🤖 GitHub Actions: Automatización

### ¿Qué son GitHub Actions?
GitHub Actions permite **automatizar tareas** como:
- **Ejecutar pruebas** automáticamente
- **Desplegar** aplicaciones
- **Verificar** código
- **Publicar** releases

### Tu primera Action

#### Crear directorio de workflows
```bash
mkdir -p .github/workflows
```

#### Ejemplo: Verificar enlaces rotos
```yaml
# .github/workflows/check-links.yml
name: Check Links

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  check-links:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v3
    
    - name: Check links in markdown files
      uses: gaurav-nelson/github-action-markdown-link-check@v1
      with:
        use-quiet-mode: 'yes'
        use-verbose-mode: 'yes'
```

#### Ejemplo: Desplegar a GitHub Pages
```yaml
# .github/workflows/deploy.yml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout
      uses: actions/checkout@v3
      
    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '18'
        
    - name: Install dependencies
      run: npm install
      
    - name: Build
      run: npm run build
      
    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./dist
```

## 🏷️ Releases y Versionado

### Crear un Release
1. **Ve a tu repositorio** en GitHub
2. **Haz clic en "Releases"**
3. **Haz clic en "Create a new release"**
4. **Agrega información**:
   - **Tag**: v1.0.0 (versionado semántico)
   - **Título**: Versión 1.0.0
   - **Descripción**: Qué incluye esta versión

### Versionado Semántico
- **MAJOR.MINOR.PATCH** (1.2.3)
- **MAJOR**: Cambios que rompen compatibilidad
- **MINOR**: Nueva funcionalidad compatible
- **PATCH**: Correcciones de bugs

```bash
# Crear tag localmente
git tag -a v1.0.0 -m "Primera versión estable"

# Subir tag
git push origin v1.0.0

# Ver tags
git tag --list
```

## 🔒 Seguridad en GitHub

### Secrets: Variables Seguras
Para guardar información sensible (API keys, passwords):

1. **Ve a Settings** > **Secrets and variables** > **Actions**
2. **Haz clic en "New repository secret"**
3. **Agrega nombre y valor**

Uso en Actions:
```yaml
- name: Deploy
  env:
    API_KEY: ${{ secrets.API_KEY }}
  run: ./deploy.sh
```

### Dependabot: Actualizaciones Automáticas
GitHub puede **actualizar dependencias** automáticamente:

```yaml
# .github/dependabot.yml
version: 2
updates:
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
```

## 📊 Insights y Analytics

### Pulse: Vista General
- **Actividad reciente** del repositorio
- **Contribuciones** de la comunidad
- **Issues y PRs** abiertos/cerrados

### Traffic: Estadísticas de Visitas
- **Clones** del repositorio
- **Visitors** únicos
- **Views** de páginas

### Contributors: Gráfico de Contribuciones
- **Líneas agregadas/eliminadas** por contributor
- **Commits** por período
- **Actividad** a lo largo del tiempo

## 🛡️ Buenas Prácticas de Seguridad

### .gitignore: Archivos a Ignorar
```gitignore
# Dependencias
node_modules/
vendor/

# Archivos de configuración local
.env
.env.local
config.local.js

# Archivos de sistema
.DS_Store
Thumbs.db

# Logs
*.log
logs/

# Archivos compilados
dist/
build/
*.min.js

# Claves y credenciales
*.pem
*.key
secrets.json
```

### Nunca commitear:
- ❌ **Passwords** o API keys
- ❌ **Archivos personales** (.env)
- ❌ **Dependencias** (node_modules)
- ❌ **Archivos compilados** (dist, build)
- ❌ **Logs** de depuración

## 📐 Convenciones y Estándares

### Estructura de Proyecto
```
mi-proyecto/
├── README.md              # Documentación principal
├── LICENSE               # Licencia del proyecto
├── .gitignore           # Archivos a ignorar
├── package.json         # Dependencias (Node.js)
├── src/                 # Código fuente
│   ├── components/      # Componentes
│   ├── utils/          # Utilidades
│   └── index.js        # Archivo principal
├── tests/              # Pruebas
├── docs/               # Documentación
└── .github/            # Configuración de GitHub
    ├── workflows/      # GitHub Actions
    └── ISSUE_TEMPLATE/ # Plantillas de issues
```

### Mensajes de Commit
```bash
# Formato recomendado
tipo(alcance): descripción corta

# Ejemplos
feat(auth): agregar login con Google
fix(api): corregir error en validación
docs(readme): actualizar instrucciones de instalación
style(css): mejorar espaciado en header
refactor(utils): simplificar función de validación
test(login): agregar pruebas unitarias
```

### Tipos de commit comunes:
- `feat`: Nueva característica
- `fix`: Corrección de bug
- `docs`: Documentación
- `style`: Formato, espacios, etc.
- `refactor`: Refactorización de código
- `test`: Agregar o modificar pruebas
- `chore`: Tareas de mantenimiento

## 🔧 Herramientas Útiles

### GitHub CLI
```bash
# Instalar GitHub CLI
# En macOS: brew install gh
# En Windows: winget install GitHub.cli

# Autenticarse
gh auth login

# Crear repositorio
gh repo create mi-proyecto --public

# Clonar repositorio
gh repo clone usuario/repositorio

# Crear issue
gh issue create --title "Bug en login" --body "Descripción del error"

# Crear PR
gh pr create --title "Nueva característica" --body "Descripción"

# Ver PRs
gh pr list

# Hacer merge de PR
gh pr merge 123
```

### Git Hooks: Automatización Local
```bash
# Crear hook pre-commit
cat > .git/hooks/pre-commit << 'EOF'
#!/bin/sh
# Ejecutar tests antes de commit
npm test
if [ $? -ne 0 ]; then
  echo "Tests fallaron. Commit cancelado."
  exit 1
fi
EOF

chmod +x .git/hooks/pre-commit
```

## 📝 Ejercicio Final: Proyecto Completo

### Crea tu portafolio profesional
1. **Repositorio**: `tu-usuario.github.io`
2. **Contenido**: HTML, CSS, JavaScript
3. **Features**:
   - ✅ GitHub Pages configurado
   - ✅ GitHub Action para deployment
   - ✅ README completo
   - ✅ Licencia apropiada
   - ✅ .gitignore configurado
   - ✅ Issues y PRs de práctica

### Estructura sugerida:
```
tu-usuario.github.io/
├── index.html
├── styles/
│   └── main.css
├── scripts/
│   └── main.js
├── images/
├── projects/
│   └── project1.html
├── README.md
├── LICENSE
├── .gitignore
└── .github/
    └── workflows/
        └── deploy.yml
```

## 🎯 Checklist del Desarrollador Profesional

### Antes de cada commit:
- [ ] Código funciona correctamente
- [ ] Tests pasan (si existen)
- [ ] Mensaje de commit descriptivo
- [ ] No hay archivos sensibles
- [ ] Código está formateado

### Antes de cada PR:
- [ ] Rama actualizada con main
- [ ] PR tiene descripción clara
- [ ] Cambios son mínimos y enfocados
- [ ] Documentación actualizada si es necesario
- [ ] Screenshots si hay cambios visuales

### Para repositorios públicos:
- [ ] README completo y actualizado
- [ ] Licencia apropiada
- [ ] .gitignore configurado
- [ ] Guías de contribución
- [ ] Código de conducta

## 🎉 ¡Felicidades!

¡Has completado el curso de GitHub! Ahora tienes todas las herramientas para:
- **Trabajar profesionalmente** con Git y GitHub
- **Colaborar** en proyectos open source
- **Crear y mantener** tus propios proyectos
- **Automatizar** tareas con GitHub Actions
- **Publicar** sitios web con GitHub Pages

## 🚀 Próximos Pasos

1. **Practica regularmente** - Crea proyectos personales
2. **Contribuye** a proyectos open source
3. **Mantente actualizado** - GitHub siempre agrega nuevas características
4. **Comparte conocimiento** - Ayuda a otros a aprender
5. **Construye tu portafolio** - Usa GitHub como tu carta de presentación

## 📚 Recursos Avanzados

- [GitHub Docs](https://docs.github.com/)
- [Git Book](https://git-scm.com/book)
- [GitHub Skills](https://skills.github.com/)
- [Awesome GitHub](https://github.com/phillipadsmith/awesome-github)
- [GitHub Blog](https://github.blog/)

**¡Ahora ve y crea cosas increíbles! 🌟**