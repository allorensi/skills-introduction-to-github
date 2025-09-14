# 🎓 Proyecto Final: Mi Portafolio Profesional

## 📋 Descripción del Proyecto

Para demostrar que has dominado Git y GitHub, crearás un portafolio web profesional que incluya todas las técnicas aprendidas en el curso.

## 🎯 Objetivos

Al completar este proyecto, habrás demostrado que puedes:
- Crear y gestionar repositorios profesionalmente
- Usar ramas para desarrollo de características
- Implementar GitHub Pages para hosting
- Configurar GitHub Actions para automatización
- Colaborar usando Issues y Pull Requests
- Seguir mejores prácticas de desarrollo

## 📝 Requisitos del Proyecto

### Repositorio: `tu-usuario.github.io`
Tu repositorio debe llamarse exactamente `tu-usuario.github.io` para que funcione automáticamente con GitHub Pages.

### Estructura Mínima Requerida
```
tu-usuario.github.io/
├── README.md
├── index.html
├── sobre-mi.html
├── proyectos.html
├── contacto.html
├── css/
│   ├── main.css
│   └── responsive.css
├── js/
│   └── main.js
├── images/
│   ├── foto-perfil.jpg
│   └── screenshots/
├── docs/
│   └── manual-usuario.md
├── .gitignore
├── LICENSE
└── .github/
    ├── workflows/
    │   └── deploy.yml
    └── ISSUE_TEMPLATE/
        └── bug_report.md
```

## 📋 Lista de Verificación

### ✅ Configuración Básica
- [ ] Repositorio creado con nombre correcto
- [ ] README.md completo y profesional
- [ ] .gitignore apropiado para proyecto web
- [ ] Licencia MIT agregada
- [ ] Descripción del repositorio configurada

### ✅ Contenido Web
- [ ] Página de inicio (index.html) atractiva
- [ ] Sección "Sobre mí" con información personal
- [ ] Página de proyectos con al menos 3 proyectos
- [ ] Página de contacto con enlaces sociales
- [ ] CSS responsivo (funciona en móvil y desktop)
- [ ] JavaScript básico para interactividad

### ✅ GitHub Features
- [ ] GitHub Pages configurado y funcionando
- [ ] GitHub Action para deployment automático
- [ ] Al menos 3 issues creados y cerrados
- [ ] Al menos 2 ramas feature creadas y mergeadas
- [ ] Pull Request template configurado
- [ ] Issue template configurado

### ✅ Git Best Practices
- [ ] Historial de commits limpio y descriptivo
- [ ] Uso apropiado de ramas para características
- [ ] Mensajes de commit siguen convenciones
- [ ] No hay archivos sensibles en el repositorio
- [ ] Tags de versión apropiados

## 🎨 Diseño Sugerido

### Página de Inicio
- **Header**: Navegación clara
- **Hero Section**: Tu nombre, título profesional, foto
- **Resumen**: Breve descripción de quién eres
- **CTA**: Botones para ver proyectos o contactar

### Sobre Mí
- **Biografía**: Tu historia profesional
- **Habilidades**: Tecnologías que manejas
- **Experiencia**: Trabajos o estudios relevantes
- **Intereses**: Qué te apasiona

### Proyectos
- **Galería**: Mínimo 3 proyectos con:
  - Screenshot o imagen
  - Descripción clara
  - Tecnologías usadas
  - Enlaces a código y demo (si disponible)

### Contacto
- **Información**: Email, teléfono (opcional)
- **Redes sociales**: GitHub, LinkedIn, Twitter
- **Ubicación**: Ciudad/país
- **Formulario**: Opcional, puede ser solo enlaces

## 🔧 Especificaciones Técnicas

### HTML
- Semántico y válido
- Meta tags apropiados
- Estructura accesible
- Enlaces internos funcionando

### CSS
- Mobile-first responsive design
- Variables CSS para consistencia
- Flexbox o Grid para layouts
- Transiciones suaves

### JavaScript
- Navegación smooth scroll
- Menú móvil funcional
- Validación de formularios (si aplica)
- Animaciones sutiles

### GitHub Action (deploy.yml)
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    
    - name: Validate HTML
      uses: Cyb3r-Jak3/html5validator-action@v7.2.0
      with:
        root: ./
        
    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./
```

## 📚 Ejemplos de Contenido

### README.md Template
```markdown
# Mi Portafolio Web

¡Bienvenido/a a mi portafolio profesional! Este sitio web muestra mis proyectos, habilidades y experiencia como desarrollador/a.

## 🌐 Ver en Vivo
[tu-usuario.github.io](https://tu-usuario.github.io)

## 🛠️ Tecnologías Utilizadas
- HTML5
- CSS3 (Flexbox, Grid)
- JavaScript (ES6+)
- GitHub Pages
- GitHub Actions

## 📁 Estructura del Proyecto
- `index.html` - Página principal
- `css/` - Estilos CSS
- `js/` - Scripts JavaScript
- `images/` - Imágenes y assets

## 🚀 Desarrollo Local
```bash
git clone https://github.com/tu-usuario/tu-usuario.github.io.git
cd tu-usuario.github.io
# Abrir index.html en el navegador
```

## 📞 Contacto
- **Email**: tu-email@ejemplo.com
- **LinkedIn**: [tu-perfil](https://linkedin.com/in/tu-perfil)
- **GitHub**: [@tu-usuario](https://github.com/tu-usuario)

---
*Desarrollado con ❤️ usando GitHub Pages*
```

### Ejemplo de Proyecto
```markdown
## Sistema de Gestión de Biblioteca

**Descripción**: Aplicación web para gestionar préstamos de libros en una biblioteca universitaria.

**Características**:
- Registro de usuarios y libros
- Sistema de préstamos y devoluciones
- Búsqueda avanzada por categorías
- Dashboard administrativo

**Tecnologías**: Python, Django, PostgreSQL, Bootstrap

**Estado**: ✅ Completado

**Enlaces**:
- [Repositorio](https://github.com/tu-usuario/biblioteca-system)
- [Demo en vivo](https://biblioteca-demo.herokuapp.com)

**Screenshots**:
![Dashboard](images/biblioteca-dashboard.png)
```

## ⏰ Cronograma Sugerido

### Semana 1: Configuración y Estructura
- [ ] Crear repositorio
- [ ] Configurar estructura de archivos
- [ ] Configurar GitHub Pages
- [ ] Crear contenido básico HTML

### Semana 2: Diseño y Estilo
- [ ] Implementar CSS responsivo
- [ ] Agregar JavaScript básico
- [ ] Optimizar imágenes
- [ ] Testear en diferentes dispositivos

### Semana 3: GitHub Features
- [ ] Configurar GitHub Actions
- [ ] Crear issues y PRs de práctica
- [ ] Agregar templates
- [ ] Crear tags de versión

### Semana 4: Contenido y Pulimiento
- [ ] Finalizar contenido
- [ ] Revisar y corregir bugs
- [ ] Documentación completa
- [ ] Presentación final

## 🎯 Evaluación

### Criterios de Evaluación (100 puntos)

#### Técnico (40 puntos)
- Código HTML válido y semántico (10 pts)
- CSS responsivo y bien estructurado (10 pts)
- JavaScript funcional (10 pts)
- GitHub Actions funcionando (10 pts)

#### Git/GitHub (30 puntos)
- Uso apropiado de ramas y merges (10 pts)
- Mensajes de commit descriptivos (10 pts)
- Issues y PRs manejados correctamente (10 pts)

#### Contenido (20 puntos)
- Información completa y profesional (10 pts)
- Proyectos bien documentados (10 pts)

#### Presentación (10 puntos)
- Diseño atractivo y usable (5 pts)
- README y documentación (5 pts)

### Niveles de Desempeño
- **90-100**: Excelente - Listo para portafolio profesional
- **80-89**: Bueno - Cumple todos los requisitos
- **70-79**: Satisfactorio - Necesita pulimiento
- **<70**: Necesita revisión - Reenviar con mejoras

## 🎉 Entrega

### Formato de Entrega
1. **URL del repositorio**: `https://github.com/tu-usuario/tu-usuario.github.io`
2. **URL del sitio**: `https://tu-usuario.github.io`
3. **Reporte de reflexión**: Documento de 1-2 páginas sobre tu experiencia

### Fecha Límite
[Insertar fecha según el cronograma del curso]

### Presentación
Prepara una presentación de 5 minutos mostrando:
- Tu sitio web funcionando
- Características técnicas implementadas
- Proceso de desarrollo usando Git/GitHub
- Aprendizajes y desafíos

## 💡 Consejos para el Éxito

1. **Empieza simple**: Construye funcionalidad básica primero
2. **Commitea frecuentemente**: Pequeños commits son mejores
3. **Usa ramas**: Una rama por característica
4. **Testea regularmente**: Revisa tu sitio en diferentes navegadores
5. **Pide feedback**: Comparte con compañeros para obtener opiniones
6. **Documenta todo**: Buenos READMEs impresionan a empleadores

## 🆘 Recursos de Ayuda

- [HTML/CSS Reference](https://developer.mozilla.org/es/)
- [GitHub Pages Docs](https://docs.github.com/pages)
- [GitHub Actions Guide](https://docs.github.com/actions)
- [Responsive Design Guide](https://web.dev/responsive-web-design-basics/)

¡Mucha suerte con tu proyecto final! 🚀