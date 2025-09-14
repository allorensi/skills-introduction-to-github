# Lección 1: Conceptos Básicos de Git y GitHub

## 🎯 Objetivos de Aprendizaje
Al finalizar esta lección, podrás:
- Entender la diferencia entre Git y GitHub
- Conocer los conceptos fundamentales del control de versiones
- Configurar tu entorno de trabajo

## 📚 Conceptos Fundamentales

### ¿Qué es Git?
Git es un **sistema de control de versiones distribuido** que te permite:
- Rastrear cambios en archivos a lo largo del tiempo
- Colaborar con otros desarrolladores
- Mantener un historial completo de tu proyecto
- Trabajar en diferentes versiones simultáneamente

### ¿Qué es GitHub?
GitHub es una **plataforma web** que utiliza Git para:
- Alojar repositorios en la nube
- Facilitar la colaboración entre desarrolladores
- Proporcionar herramientas adicionales (issues, pull requests, etc.)
- Servir como portafolio de proyectos

### Conceptos Clave

#### Repositorio (Repository)
- Un **contenedor** para tu proyecto
- Incluye todos los archivos y el historial de cambios
- Puede ser **local** (en tu computadora) o **remoto** (en GitHub)

#### Commit
- Una **instantánea** de tu proyecto en un momento específico
- Incluye un mensaje descriptivo de los cambios
- Forma parte del historial del proyecto

#### Branch (Rama)
- Una **línea de desarrollo** independiente
- Permite trabajar en características diferentes simultáneamente
- La rama principal suele llamarse `main` o `master`

#### Clone
- **Copiar** un repositorio remoto a tu computadora local
- Incluye todo el historial y todas las ramas

#### Push
- **Enviar** tus cambios locales al repositorio remoto

#### Pull
- **Traer** cambios del repositorio remoto a tu copia local

## 🔧 Configuración Inicial

### 1. Verificar la instalación de Git
```bash
git --version
```

### 2. Configurar tu identidad
```bash
git config --global user.name "Tu Nombre Completo"
git config --global user.email "tu-email@ejemplo.com"
```

### 3. Configuraciones adicionales recomendadas
```bash
# Configurar el editor por defecto (opcional)
git config --global core.editor "code --wait"

# Configurar colores para mejor legibilidad
git config --global color.ui auto

# Ver tu configuración actual
git config --list
```

## 📝 Ejercicio Práctico

1. **Verifica tu instalación**: Ejecuta `git --version` en tu terminal
2. **Configura tu identidad**: Usa los comandos de configuración arriba
3. **Verifica tu configuración**: Ejecuta `git config --list` y confirma que tu información está correcta

## 🎉 ¡Felicidades!

Has completado la primera lección. Ahora tienes una base sólida de los conceptos fundamentales de Git y GitHub.

**Siguiente paso**: [Lección 2: Tu Primer Repositorio](02-primer-repositorio.md)

## 📚 Recursos Adicionales

- [Tutorial interactivo de Git](https://learngitbranching.js.org/?locale=es_AR)
- [Documentación oficial de Git](https://git-scm.com/doc)
- [Glosario de términos de Git](https://docs.github.com/es/get-started/quickstart/github-glossary)