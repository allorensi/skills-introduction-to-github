# Lección 4: Colaboración y Pull Requests

## 🎯 Objetivos de Aprendizaje
Al finalizar esta lección, podrás:
- Hacer fork de repositorios
- Crear y gestionar Pull Requests
- Colaborar efectivamente en proyectos de equipo
- Revisar código de otros desarrolladores

## 🍴 Fork: Tu Copia Personal

### ¿Qué es un Fork?
Un **fork** es una copia personal de un repositorio de otra persona en tu cuenta de GitHub. Te permite:
- **Experimentar** sin afectar el proyecto original
- **Proponer cambios** al proyecto original
- **Crear tu propia versión** del proyecto

### Cómo hacer Fork
1. **Ve al repositorio** que quieres bifurcar en GitHub
2. **Haz clic en "Fork"** (esquina superior derecha)
3. **Selecciona tu cuenta** como destino
4. **¡Listo!** Ahora tienes tu propia copia

### Clonar tu Fork
```bash
# Clonar tu fork (no el repositorio original)
git clone https://github.com/TU-USUARIO/nombre-repositorio.git
cd nombre-repositorio

# Agregar el repositorio original como "upstream"
git remote add upstream https://github.com/USUARIO-ORIGINAL/nombre-repositorio.git

# Verificar repositorios remotos
git remote -v
```

## 🔄 Pull Requests: Proponiendo Cambios

### ¿Qué es un Pull Request?
Un **Pull Request (PR)** es una solicitud para fusionar tus cambios en el repositorio original. Es una forma de:
- **Proponer mejoras** al proyecto
- **Discutir cambios** antes de implementarlos
- **Revisar código** en equipo
- **Mantener calidad** del código

### Flujo de trabajo completo

#### 1. Mantener tu fork actualizado
```bash
# Traer cambios del repositorio original
git fetch upstream

# Fusionar cambios en tu rama main
git checkout main
git merge upstream/main

# Subir actualizaciones a tu fork
git push origin main
```

#### 2. Crear rama para tu contribución
```bash
# Crear rama descriptiva
git checkout -b fix/corregir-error-login
# o
git checkout -b feature/agregar-modo-oscuro
```

#### 3. Hacer tus cambios
```bash
# Hacer cambios en archivos
# ...

# Agregar y hacer commit
git add .
git commit -m "Corregir error en validación de login"

# Subir rama a tu fork
git push origin fix/corregir-error-login
```

#### 4. Crear Pull Request en GitHub
1. **Ve a tu fork** en GitHub
2. **Haz clic en "Compare & pull request"**
3. **Completa la información**:
   - **Título**: Descriptivo y claro
   - **Descripción**: Explica qué cambios hiciste y por qué
   - **Base**: Repositorio y rama de destino
   - **Compare**: Tu fork y rama con cambios

4. **Haz clic en "Create pull request"**

### Plantilla de Pull Request
```markdown
## Descripción
Breve descripción de los cambios realizados.

## Tipo de cambio
- [ ] Bug fix (corrección de error)
- [ ] Nueva característica
- [ ] Cambio que rompe compatibilidad
- [ ] Actualización de documentación

## ¿Cómo se probó?
Describe las pruebas realizadas para verificar los cambios.

## Lista de verificación
- [ ] Mi código sigue las convenciones del proyecto
- [ ] He revisado mi propio código
- [ ] He comentado el código en áreas difíciles
- [ ] He actualizado la documentación si es necesario
- [ ] Mis cambios no generan nuevas advertencias
- [ ] He agregado pruebas si es apropiado
```

## 👥 Colaboración en Equipo

### Roles en un proyecto
- **Maintainer**: Administra el repositorio
- **Contributor**: Contribuye con código
- **Reviewer**: Revisa Pull Requests
- **User**: Usa el software y reporta issues

### Revisión de código
Como reviewer, debes verificar:
- **Funcionalidad**: ¿El código hace lo que dice?
- **Calidad**: ¿Está bien escrito y es legible?
- **Estilo**: ¿Sigue las convenciones del proyecto?
- **Documentación**: ¿Está bien documentado?
- **Pruebas**: ¿Hay pruebas suficientes?

### Comandos para revisión
```bash
# Probar un Pull Request localmente
git fetch origin pull/123/head:pr-123
git checkout pr-123

# Revisar cambios
git diff main...pr-123

# Probar los cambios
# ... ejecutar pruebas ...

# Volver a main
git checkout main
```

## 🎫 Issues: Gestión de Tareas

### ¿Qué son los Issues?
Los **issues** son herramientas para:
- **Reportar bugs**
- **Solicitar características**
- **Discutir ideas**
- **Organizar tareas**

### Crear un Issue efectivo
```markdown
## Descripción del problema
Descripción clara y concisa del problema.

## Pasos para reproducir
1. Ve a '...'
2. Haz clic en '....'
3. Desplázate hasta '....'
4. Ve el error

## Comportamiento esperado
Qué esperabas que pasara.

## Comportamiento actual
Qué está pasando en realidad.

## Capturas de pantalla
Si aplica, agregar capturas.

## Información adicional
- OS: [e.g. iOS]
- Navegador: [e.g. chrome, safari]
- Versión: [e.g. 22]
```

### Etiquetas (Labels) útiles
- `bug`: Error en el código
- `enhancement`: Nueva característica
- `documentation`: Relacionado con documentación
- `good first issue`: Bueno para principiantes
- `help wanted`: Se necesita ayuda

## 🔧 Herramientas de Colaboración

### GitHub Projects
- **Tableros Kanban** para organizar trabajo
- **Automatización** con reglas
- **Seguimiento** de progreso

### GitHub Actions
- **Integración continua** (CI)
- **Despliegue automático** (CD)
- **Automatización** de tareas

### Wiki
- **Documentación** extensa del proyecto
- **Guías** de contribución
- **Arquitectura** del sistema

## 📝 Ejercicios Prácticos

### Ejercicio 1: Tu primer Fork y PR
1. **Haz fork** de este repositorio
2. **Clona tu fork** localmente
3. **Crea una rama** `feature/mi-contribucion`
4. **Agrega tu información** al archivo `ejercicios/estudiantes/`
5. **Haz commit** y **push**
6. **Crea un Pull Request**

### Ejercicio 2: Revisar un PR
1. **Revisa el PR** de un compañero
2. **Deja comentarios** constructivos
3. **Aprueba o solicita cambios**

### Ejercicio 3: Gestionar Issues
1. **Crea un issue** reportando una mejora
2. **Asigna etiquetas** apropiadas
3. **Discute la solución** en comentarios

## 🌟 Mejores Prácticas

### Para Contributors
- **Mantén PRs pequeños** y enfocados
- **Escribe mensajes descriptivos**
- **Prueba tu código** antes del PR
- **Responde a feedback** rápidamente
- **Mantén tu fork actualizado**

### Para Maintainers
- **Responde PRs rápidamente**
- **Da feedback constructivo**
- **Mantén documentación clara**
- **Establece guías de contribución**
- **Agradece a los contributors**

### Para la Comunidad
- **Sé respetuoso** siempre
- **Ayuda a otros** cuando puedas
- **Reporta problemas** claramente
- **Celebra contribuciones** de otros

## 🎯 Comandos de Colaboración

```bash
# Gestión de forks
git remote add upstream <url-original>
git fetch upstream
git merge upstream/main

# Trabajo con PRs
git fetch origin pull/ID/head:branch-name
git checkout branch-name

# Limpieza después de merge
git branch -d nombre-rama
git push origin --delete nombre-rama

# Sincronización
git pull upstream main
git push origin main
```

## 🎉 ¡Felicidades!

¡Ya sabes colaborar en proyectos de GitHub! Estas habilidades te permitirán participar en proyectos open source y trabajar efectivamente en equipos de desarrollo.

**Siguiente paso**: [Lección 5: Herramientas Avanzadas](05-herramientas-avanzadas.md)

## 📚 Recursos de Colaboración

- [Guía de Pull Requests](https://docs.github.com/es/pull-requests)
- [Mejores prácticas para Issues](https://guides.github.com/features/issues/)
- [Etiqueta en Open Source](https://opensource.guide/how-to-contribute/)
- [Código de conducta ejemplo](https://www.contributor-covenant.org/)