# Lección 2: Tu Primer Repositorio

## 🎯 Objetivos de Aprendizaje
Al finalizar esta lección, podrás:
- Crear un repositorio en GitHub
- Clonar un repositorio a tu computadora
- Hacer tu primer commit
- Subir cambios a GitHub

## 🆕 Creando tu Primer Repositorio

### Opción 1: Crear repositorio en GitHub (Recomendado para principiantes)

1. **Inicia sesión en GitHub**
2. **Haz clic en el botón "New"** (verde) en la página principal
3. **Configura tu repositorio**:
   - **Nombre**: `mi-primer-repositorio`
   - **Descripción**: "Mi primer proyecto en GitHub"
   - **Público** (para que otros puedan verlo)
   - ✅ **Marcar "Add a README file"**
   - ✅ **Seleccionar una licencia** (MIT License es una buena opción)

4. **Haz clic en "Create repository"**

### Opción 2: Crear repositorio local primero

```bash
# Crear una carpeta para tu proyecto
mkdir mi-primer-repositorio
cd mi-primer-repositorio

# Inicializar Git en la carpeta
git init

# Crear un archivo README
echo "# Mi Primer Repositorio" > README.md

# Agregar el archivo al área de staging
git add README.md

# Hacer tu primer commit
git commit -m "Primer commit: agregar README"
```

## 📥 Clonando un Repositorio

Si creaste el repositorio en GitHub, ahora necesitas clonarlo a tu computadora:

```bash
# Clonar el repositorio (reemplaza 'tu-usuario' con tu nombre de usuario de GitHub)
git clone https://github.com/tu-usuario/mi-primer-repositorio.git

# Entrar al directorio del repositorio
cd mi-primer-repositorio

# Ver el contenido
ls -la
```

## ✏️ Haciendo Cambios

### Paso 1: Modificar un archivo
```bash
# Abrir el README en un editor de texto
nano README.md
# O usar tu editor favorito: code README.md, vim README.md, etc.
```

Agrega contenido como:
```markdown
# Mi Primer Repositorio

Este es mi primer proyecto en GitHub. ¡Estoy aprendiendo Git!

## Lo que he aprendido
- Crear repositorios
- Hacer commits
- Trabajar con archivos

## Próximos pasos
- Aprender sobre ramas
- Colaborar con otros
- Explorar más funcionalidades de GitHub
```

### Paso 2: Ver los cambios
```bash
# Ver qué archivos han cambiado
git status

# Ver los cambios específicos
git diff
```

### Paso 3: Preparar los cambios (Staging)
```bash
# Agregar cambios al área de staging
git add README.md

# O agregar todos los archivos modificados
git add .

# Verificar el estado
git status
```

### Paso 4: Hacer commit
```bash
# Hacer commit con un mensaje descriptivo
git commit -m "Actualizar README con información del proyecto"

# Ver el historial de commits
git log --oneline
```

## 📤 Subir Cambios a GitHub

```bash
# Subir cambios al repositorio remoto
git push origin main

# Si es tu primer push desde un repositorio local, tal vez necesites:
git push -u origin main
```

## 🔍 Verificar en GitHub

1. Ve a tu repositorio en GitHub
2. Deberías ver tus cambios reflejados
3. Explora las pestañas:
   - **Code**: Código y archivos
   - **Commits**: Historial de cambios
   - **Branches**: Ramas del proyecto

## 📝 Ejercicio Práctico

### Ejercicio 1: Crear tu repositorio personal
1. Crea un repositorio llamado `mi-portafolio`
2. Clónalo a tu computadora
3. Agrega un archivo `sobre-mi.md` con información personal
4. Haz commit y push de los cambios

### Ejercicio 2: Agregar más contenido
1. Crea una carpeta `proyectos`
2. Agrega un archivo `proyecto1.md` dentro de la carpeta
3. Haz commit y push de los cambios

## 🎯 Comandos Esenciales Aprendidos

```bash
git clone <url>          # Clonar repositorio
git status              # Ver estado de archivos
git add <archivo>       # Agregar archivo al staging
git add .               # Agregar todos los archivos
git commit -m "mensaje" # Hacer commit
git push origin main    # Subir cambios
git log                 # Ver historial
git diff                # Ver diferencias
```

## ⚠️ Consejos Importantes

1. **Mensajes de commit descriptivos**: Explica qué cambios hiciste
2. **Commits frecuentes**: Es mejor hacer muchos commits pequeños que pocos grandes
3. **Siempre revisar**: Usa `git status` y `git diff` antes de hacer commit
4. **Respaldar regularmente**: Haz `git push` frecuentemente

## 🎉 ¡Felicidades!

¡Has creado tu primer repositorio y hecho tus primeros commits! Ya estás usando Git y GitHub como un desarrollador profesional.

**Siguiente paso**: [Lección 3: Trabajando con Ramas](03-ramas.md)

## 🆘 Solución de Problemas Comunes

### Error: "remote origin already exists"
```bash
git remote remove origin
git remote add origin https://github.com/tu-usuario/tu-repositorio.git
```

### Error: "Permission denied"
- Verifica que estés usando el nombre de usuario correcto
- Considera configurar SSH en lugar de HTTPS

### Error: "nothing to commit"
- Verifica que hayas hecho cambios en archivos
- Usa `git status` para ver el estado actual