# 🚀 Guía de Comandos Esenciales de Git

Esta guía contiene los comandos más importantes que necesitas para trabajar con Git y GitHub.

## 📚 Configuración Inicial

```bash
# Configurar tu identidad
git config --global user.name "Tu Nombre"
git config --global user.email "tu-email@ejemplo.com"

# Ver tu configuración
git config --list

# Ayuda sobre cualquier comando
git help <comando>
```

## 📁 Trabajando con Repositorios

```bash
# Inicializar un nuevo repositorio
git init

# Clonar un repositorio existente
git clone <url-del-repositorio>

# Ver el estado de tus archivos
git status

# Ver información del repositorio remoto
git remote -v
```

## 📝 Comandos Básicos de Trabajo

```bash
# Agregar archivos al staging area
git add <archivo>                # Agregar un archivo específico
git add .                        # Agregar todos los archivos modificados
git add *.js                     # Agregar todos los archivos .js

# Hacer commit de tus cambios
git commit -m "Mensaje descriptivo"
git commit -am "Agregar y hacer commit en un paso"

# Ver los cambios en archivos
git diff                         # Cambios no agregados al staging
git diff --staged               # Cambios en staging area
git diff HEAD~1                 # Comparar con el commit anterior
```

## 📊 Historial y Logs

```bash
# Ver el historial de commits
git log                         # Historial completo
git log --oneline              # Versión simplificada
git log --graph                # Ver ramas gráficamente
git log --author="nombre"      # Commits de un autor específico

# Ver un commit específico
git show <hash-del-commit>

# Ver quién modificó qué líneas
git blame <archivo>
```

## 🌿 Trabajando con Ramas

```bash
# Listar ramas
git branch                      # Ramas locales
git branch -r                   # Ramas remotas
git branch -a                   # Todas las ramas

# Crear ramas
git branch <nombre-rama>        # Crear rama
git checkout -b <nombre-rama>   # Crear y cambiar a rama
git switch -c <nombre-rama>     # Comando moderno

# Cambiar entre ramas
git checkout <nombre-rama>      # Método tradicional
git switch <nombre-rama>        # Comando moderno

# Fusionar ramas
git merge <nombre-rama>         # Fusionar rama en la actual

# Eliminar ramas
git branch -d <nombre-rama>     # Eliminar rama local
git push origin --delete <rama> # Eliminar rama remota
```

## 🔄 Sincronización con Repositorio Remoto

```bash
# Agregar repositorio remoto
git remote add origin <url>

# Subir cambios
git push origin <rama>          # Subir rama específica
git push -u origin main         # Subir y establecer upstream

# Descargar cambios
git pull origin <rama>          # Descargar y fusionar
git fetch origin               # Solo descargar sin fusionar

# Ver repositorios remotos
git remote -v
```

## ↩️ Deshacer Cambios

```bash
# Deshacer cambios en archivos no agregados
git checkout -- <archivo>      # Versión anterior
git restore <archivo>           # Comando moderno

# Quitar archivos del staging area
git reset HEAD <archivo>        # Versión anterior
git restore --staged <archivo>  # Comando moderno

# Deshacer commits
git reset --soft HEAD~1         # Mantener cambios en staging
git reset --mixed HEAD~1        # Mantener cambios sin agregar
git reset --hard HEAD~1         # Eliminar cambios completamente

# Revertir un commit específico
git revert <hash-del-commit>
```

## 🏷️ Trabajando con Tags

```bash
# Crear tags
git tag v1.0.0                  # Tag simple
git tag -a v1.0.0 -m "Versión 1.0.0"  # Tag anotado

# Listar tags
git tag

# Subir tags
git push origin v1.0.0          # Tag específico
git push origin --tags          # Todos los tags
```

## 🔧 Comandos de Utilidad

```bash
# Limpiar archivos no rastreados
git clean -n                    # Ver qué se eliminará
git clean -f                    # Eliminar archivos
git clean -fd                   # Eliminar archivos y directorios

# Guardar trabajo temporalmente
git stash                       # Guardar cambios
git stash pop                   # Restaurar cambios
git stash list                  # Ver stashes guardados

# Buscar en el historial
git grep "texto a buscar"       # Buscar en archivos
git log --grep="palabra"        # Buscar en mensajes de commit
```

## 🚨 Comandos de Emergencia

```bash
# Cancelar merge en progreso
git merge --abort

# Cancelar rebase en progreso
git rebase --abort

# Ver el último commit que modificó una línea
git log -p -S "texto específico"

# Recuperar commits perdidos
git reflog
git cherry-pick <hash-perdido>
```

## 📋 Flujo de Trabajo Típico

```bash
# 1. Actualizar repositorio
git pull origin main

# 2. Crear nueva rama para característica
git switch -c feature/nueva-funcionalidad

# 3. Hacer cambios y commits
git add .
git commit -m "Implementar nueva funcionalidad"

# 4. Subir rama
git push origin feature/nueva-funcionalidad

# 5. Crear Pull Request en GitHub

# 6. Después de aprobación, fusionar
git switch main
git pull origin main
git merge feature/nueva-funcionalidad

# 7. Limpiar
git branch -d feature/nueva-funcionalidad
git push origin --delete feature/nueva-funcionalidad
```

## 💡 Consejos Importantes

- **Commits frecuentes**: Haz commits pequeños y frecuentes
- **Mensajes descriptivos**: Explica QUÉ y POR QUÉ, no cómo
- **Revisar antes de commit**: Usa `git status` y `git diff`
- **Ramas para características**: Una rama por característica
- **Mantener main estable**: No hagas commits directos en main

## 🔗 Recursos Adicionales

- [Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [Interactive Git Tutorial](https://learngitbranching.js.org/)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)