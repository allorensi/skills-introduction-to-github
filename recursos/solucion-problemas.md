# 🆘 Guía de Solución de Problemas

Esta guía te ayudará a resolver los problemas más comunes que puedes encontrar al usar Git y GitHub.

## 🔧 Problemas Comunes con Git

### Error: "fatal: not a git repository"
**Problema**: Intentas usar comandos Git fuera de un repositorio.

**Solución**:
```bash
# Verificar si estás en un repositorio Git
git status

# Si no estás en uno, navega al directorio correcto
cd path/to/your/repository

# O inicializa un nuevo repositorio
git init
```

### Error: "Please tell me who you are"
**Problema**: Git no conoce tu identidad.

**Solución**:
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu-email@ejemplo.com"
```

### Error: "Your branch is ahead of 'origin/main'"
**Problema**: Tienes commits locales que no has subido.

**Solución**:
```bash
# Subir tus cambios
git push origin main

# Ver cuántos commits tienes pendientes
git log origin/main..HEAD --oneline
```

### Error: "Your branch is behind 'origin/main'"
**Problema**: El repositorio remoto tiene cambios que no tienes localmente.

**Solución**:
```bash
# Traer cambios del repositorio remoto
git pull origin main

# O si prefieres más control
git fetch origin
git merge origin/main
```

### Error: "Merge conflict"
**Problema**: Git no puede fusionar automáticamente los cambios.

**Solución**:
```bash
# 1. Ver qué archivos tienen conflictos
git status

# 2. Abrir archivos en conflicto y buscar marcas como:
#    <<<<<<< HEAD
#    tu código
#    =======
#    código de la otra rama
#    >>>>>>> branch-name

# 3. Editar archivos para resolver conflictos
# 4. Agregar archivos resueltos
git add archivo-resuelto.txt

# 5. Completar el merge
git commit
```

### Error: "Permission denied (publickey)"
**Problema**: No tienes permisos para acceder al repositorio.

**Solución**:
```bash
# Verificar si tienes SSH configurado
ssh -T git@github.com

# Si no funciona, usar HTTPS en lugar de SSH
git remote set-url origin https://github.com/usuario/repositorio.git

# O configurar SSH (más avanzado)
ssh-keygen -t ed25519 -C "tu-email@ejemplo.com"
# Luego agregar la clave pública a GitHub
```

## 🐛 Problemas con Commits

### "Cómo deshacer el último commit"
```bash
# Mantener cambios en el área de staging
git reset --soft HEAD~1

# Mantener cambios como archivos modificados
git reset --mixed HEAD~1

# PELIGRO: Eliminar completamente los cambios
git reset --hard HEAD~1
```

### "Cambiar el mensaje del último commit"
```bash
# Si aún no has hecho push
git commit --amend -m "Nuevo mensaje de commit"

# Si ya hiciste push (NO recomendado para repositorios compartidos)
git commit --amend -m "Nuevo mensaje"
git push --force-with-lease
```

### "Agregar archivos al último commit"
```bash
# Agregar archivos olvidados
git add archivo-olvidado.txt
git commit --amend --no-edit
```

## 🌿 Problemas con Ramas

### "No puedo cambiar de rama"
**Problema**: Tienes cambios sin confirmar.

**Solución**:
```bash
# Opción 1: Hacer commit de los cambios
git add .
git commit -m "Guardar trabajo en progreso"

# Opción 2: Guardar cambios temporalmente
git stash
git checkout otra-rama
# Cuando vuelvas a la rama original:
git stash pop

# Opción 3: Descartar cambios (PELIGRO)
git checkout -- .
```

### "Eliminar rama que no se puede borrar"
```bash
# Cambiar a otra rama primero
git checkout main

# Eliminar rama local
git branch -d nombre-rama

# Si Git se resiste (forzar eliminación)
git branch -D nombre-rama

# Eliminar rama remota
git push origin --delete nombre-rama
```

### "Recuperar rama eliminada accidentalmente"
```bash
# Ver el historial de referencias
git reflog

# Encontrar el commit donde estaba la rama
# Recrear la rama desde ese commit
git checkout -b rama-recuperada <hash-del-commit>
```

## 🔄 Problemas con Repositorios Remotos

### "fatal: remote origin already exists"
```bash
# Ver repositorios remotos existentes
git remote -v

# Eliminar el remoto existente
git remote remove origin

# Agregar el nuevo remoto
git remote add origin https://github.com/usuario/repositorio.git
```

### "Clonar repositorio privado"
```bash
# Usar token de acceso personal en lugar de contraseña
git clone https://username:token@github.com/usuario/repositorio.git

# O configurar credenciales
git config --global credential.helper store
```

### "Subir repositorio local existente a GitHub"
```bash
# 1. Crear repositorio vacío en GitHub (sin README)
# 2. Agregar remoto
git remote add origin https://github.com/usuario/repositorio.git

# 3. Subir contenido
git branch -M main  # Renombrar rama principal si es necesario
git push -u origin main
```

## 🔍 Comandos de Diagnóstico

### Ver el estado de todo
```bash
# Estado de archivos
git status

# Configuración actual
git config --list

# Repositorios remotos
git remote -v

# Historial de referencias
git reflog

# Ver todas las ramas
git branch -a

# Ver diferencias
git diff
git diff --staged
git diff HEAD~1
```

### Información detallada
```bash
# Ver información de un commit específico
git show <hash-commit>

# Ver quién modificó qué líneas
git blame <archivo>

# Buscar en el historial
git log --grep="palabra clave"
git log --author="nombre"

# Ver archivos en un commit específico
git ls-tree -r <hash-commit>
```

## 🧹 Comandos de Limpieza

### Limpiar archivos no rastreados
```bash
# Ver qué se eliminará
git clean -n

# Eliminar archivos no rastreados
git clean -f

# Eliminar archivos y directorios
git clean -fd

# Incluir archivos ignorados por .gitignore
git clean -fx
```

### Optimizar repositorio
```bash
# Comprimir y optimizar
git gc

# Eliminar referencias remotas obsoletas
git remote prune origin

# Ver tamaño del repositorio
du -sh .git
```

## 🚨 Situaciones de Emergencia

### "He commitado información sensible"
```bash
# Si aún no has hecho push
git reset --hard HEAD~1

# Si ya hiciste push (repositorio público)
# 1. Cambiar todas las credenciales expuestas
# 2. Usar BFG Repo-Cleaner o git filter-branch
# 3. Contactar a GitHub si es necesario
```

### "He hecho push a la rama equivocada"
```bash
# Crear nueva rama desde el commit problemático
git branch nueva-rama

# Resetear la rama original
git reset --hard HEAD~<numero-de-commits>

# Forzar push (CUIDADO)
git push --force-with-lease
```

### "El repositorio está corrupto"
```bash
# Verificar integridad
git fsck

# Intentar recuperar
git reflog expire --expire=now --all
git gc --prune=now

# En casos extremos, re-clonar
cd ..
git clone <url> repositorio-nuevo
```

## 🆘 Cuando Todo Falla

### Empezar de nuevo manteniendo archivos
```bash
# 1. Hacer backup de archivos importantes
cp -r mi-proyecto mi-proyecto-backup

# 2. Eliminar .git
rm -rf .git

# 3. Inicializar nuevo repositorio
git init
git add .
git commit -m "Nuevo inicio"

# 4. Conectar con repositorio remoto
git remote add origin <url>
git push -u origin main
```

### Recursos de ayuda
- **Documentación oficial**: [git-scm.com](https://git-scm.com/doc)
- **GitHub Docs**: [docs.github.com](https://docs.github.com)
- **Stack Overflow**: Buscar errores específicos
- **Oh Shit Git**: [ohshitgit.com](https://ohshitgit.com) (guía informal pero útil)

## 💡 Consejos para Evitar Problemas

1. **Haz commits frecuentes** - Es más fácil deshacer cambios pequeños
2. **Usa mensajes descriptivos** - Te ayudará a entender qué hiciste
3. **Prueba en ramas** - Nunca experimentes en main
4. **Haz backup** - Ten copias de trabajo importante
5. **Lee los mensajes de error** - Git generalmente explica qué hacer
6. **Usa git status** - Antes de cualquier operación importante
7. **Mantén .gitignore actualizado** - Evita commits accidentales

## 🆘 Comandos de Emergencia Rápida

```bash
# ¿Dónde estoy?
pwd && git branch --show-current && git status --porcelain

# Deshacer todo desde el último commit
git reset --hard HEAD

# Guardar trabajo actual y limpiar
git stash && git status

# Ver qué pasó recientemente
git reflog --oneline -10

# Volver al último estado bueno conocido
git checkout <hash-del-commit-bueno>
```

¡Recuerda: Git está diseñado para ser resiliente. Casi siempre hay una forma de recuperar tu trabajo! 🌟