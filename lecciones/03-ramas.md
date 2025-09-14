# Lección 3: Trabajando con Ramas (Branches)

## 🎯 Objetivos de Aprendizaje
Al finalizar esta lección, podrás:
- Entender qué son las ramas y por qué son importantes
- Crear y cambiar entre ramas
- Fusionar ramas (merge)
- Resolver conflictos básicos

## 🌳 ¿Qué son las Ramas?

Las **ramas** son líneas de desarrollo independientes que te permiten:
- **Experimentar** sin afectar el código principal
- **Trabajar en características** diferentes simultáneamente
- **Colaborar** con otros sin conflictos
- **Mantener estable** la rama principal

### Analogía: El Árbol
Imagina tu proyecto como un árbol:
- **Tronco** (rama `main`): El código principal, estable
- **Ramas**: Nuevas características o experimentos
- **Hojas**: Los commits individuales

## 🔍 Explorando Ramas

### Ver ramas existentes
```bash
# Ver ramas locales
git branch

# Ver todas las ramas (locales y remotas)
git branch -a

# Ver la rama actual
git branch --show-current
```

## 🆕 Creando Ramas

### Crear una nueva rama
```bash
# Crear nueva rama desde la rama actual
git branch nombre-de-la-rama

# Crear rama y cambiar a ella en un solo comando
git checkout -b nueva-caracteristica

# Comando moderno (Git 2.23+)
git switch -c nueva-caracteristica
```

### Convenciones para nombres de ramas
- `feature/nueva-funcionalidad` - Para nuevas características
- `fix/corregir-error` - Para correcciones
- `hotfix/error-critico` - Para errores urgentes
- `docs/actualizar-readme` - Para documentación

## 🔄 Cambiando entre Ramas

```bash
# Cambiar a una rama existente
git checkout nombre-de-rama

# Comando moderno
git switch nombre-de-rama

# Volver a la rama principal
git switch main
```

## 📝 Trabajando en una Rama

### Ejemplo Práctico: Agregar una nueva página

```bash
# 1. Crear rama para nueva característica
git switch -c feature/pagina-contacto

# 2. Crear un nuevo archivo
echo "# Página de Contacto" > contacto.md
echo "Email: ejemplo@correo.com" >> contacto.md

# 3. Agregar y hacer commit
git add contacto.md
git commit -m "Agregar página de contacto"

# 4. Hacer más cambios
echo "Teléfono: +1234567890" >> contacto.md
git add contacto.md
git commit -m "Agregar teléfono a página de contacto"

# 5. Ver el historial
git log --oneline
```

## 🔗 Fusionando Ramas (Merge)

### Merge básico
```bash
# 1. Cambiar a la rama de destino (normalmente main)
git switch main

# 2. Fusionar la rama de característica
git merge feature/pagina-contacto

# 3. Ver el resultado
git log --oneline --graph
```

### Tipos de merge

#### Fast-forward merge
- Ocurre cuando no hay commits nuevos en la rama principal
- Git simplemente "avanza" el puntero

#### Merge commit
- Crea un commit especial que une dos ramas
- Mantiene el historial de ambas ramas

## 🧹 Limpieza después del Merge

```bash
# Eliminar rama local después del merge
git branch -d feature/pagina-contacto

# Eliminar rama remota
git push origin --delete feature/pagina-contacto
```

## ⚔️ Resolviendo Conflictos

Los conflictos ocurren cuando dos ramas modifican las mismas líneas de un archivo.

### Ejemplo de conflicto
```bash
# En rama main
echo "Bienvenido a mi sitio web" > index.md
git add index.md
git commit -m "Agregar mensaje de bienvenida"

# En nueva rama
git switch -c feature/nuevo-titulo
echo "¡Hola! Bienvenido a mi increíble sitio web" > index.md
git add index.md
git commit -m "Mejorar mensaje de bienvenida"

# Al intentar hacer merge...
git switch main
git merge feature/nuevo-titulo
# ¡Conflicto!
```

### Resolver el conflicto
```bash
# 1. Git marca el conflicto en el archivo
cat index.md
```

Verás algo como:
```
<<<<<<< HEAD
Bienvenido a mi sitio web
=======
¡Hola! Bienvenido a mi increíble sitio web
>>>>>>> feature/nuevo-titulo
```

```bash
# 2. Editar el archivo para resolver el conflicto
# Elige una versión o combina ambas
echo "¡Hola! Bienvenido a mi sitio web" > index.md

# 3. Marcar el conflicto como resuelto
git add index.md

# 4. Completar el merge
git commit -m "Resolver conflicto en mensaje de bienvenida"
```

## 📝 Ejercicios Prácticos

### Ejercicio 1: Flujo básico de ramas
1. Crear rama `feature/biografia`
2. Agregar archivo `biografia.md` con tu información
3. Hacer commit de los cambios
4. Volver a `main` y hacer merge
5. Eliminar la rama

### Ejercicio 2: Trabajar con múltiples ramas
1. Crear rama `feature/proyectos`
2. Crear rama `feature/habilidades`
3. Trabajar en cada rama por separado
4. Hacer merge de ambas a `main`

### Ejercicio 3: Resolver un conflicto
1. Modificar `README.md` en `main`
2. Crear rama y modificar la misma línea en `README.md`
3. Intentar hacer merge y resolver el conflicto

## 🎯 Comandos Esenciales de Ramas

```bash
git branch                    # Listar ramas
git branch nombre             # Crear rama
git switch -c nombre          # Crear y cambiar a rama
git switch nombre             # Cambiar a rama
git merge nombre-rama         # Fusionar rama
git branch -d nombre          # Eliminar rama
git log --graph --oneline     # Ver historial gráfico
```

## 💡 Mejores Prácticas

1. **Rama main siempre estable**: Nunca hagas commits directos en main en proyectos importantes
2. **Ramas pequeñas**: Mantén las ramas enfocadas en una sola característica
3. **Nombres descriptivos**: Usa nombres que expliquen el propósito de la rama
4. **Merge frecuente**: No dejes ramas abiertas por mucho tiempo
5. **Probar antes de merge**: Asegúrate de que tu código funciona antes de fusionar

## 🌟 Flujo de Trabajo Recomendado

```bash
# 1. Actualizar main
git switch main
git pull origin main

# 2. Crear nueva rama
git switch -c feature/nueva-funcionalidad

# 3. Trabajar y hacer commits
# ... hacer cambios ...
git add .
git commit -m "Implementar nueva funcionalidad"

# 4. Subir rama a GitHub
git push origin feature/nueva-funcionalidad

# 5. Crear Pull Request en GitHub

# 6. Después de aprobación, hacer merge
git switch main
git merge feature/nueva-funcionalidad
git push origin main

# 7. Limpiar
git branch -d feature/nueva-funcionalidad
```

## 🎉 ¡Felicidades!

¡Ya dominas el trabajo con ramas! Este es uno de los conceptos más importantes de Git y te permitirá trabajar de manera profesional en cualquier proyecto.

**Siguiente paso**: [Lección 4: Colaboración y Pull Requests](04-colaboracion.md)

## 🆘 Comandos de Emergencia

```bash
# Cancelar un merge en progreso
git merge --abort

# Ver qué archivos tienen conflictos
git status

# Deshacer el último commit (mantener cambios)
git reset --soft HEAD~1

# Forzar eliminación de rama
git branch -D nombre-rama
```