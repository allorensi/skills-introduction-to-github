# Ejercicio 1: Mi Primer Commit

## 🎯 Objetivo
Practicar los comandos básicos de Git haciendo tu primer commit en este repositorio.

## 📋 Instrucciones

### Paso 1: Configurar tu información
Si aún no lo has hecho, configura tu información de Git:
```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu-email@ejemplo.com"
```

### Paso 2: Verificar el estado del repositorio
```bash
git status
```

### Paso 3: Crear tu archivo personal
Crea un archivo con tu nombre en la carpeta `ejercicios/estudiantes/`:
```bash
# Ejemplo: si tu nombre es Maria García
touch ejercicios/estudiantes/maria-garcia.md
```

### Paso 4: Agregar contenido al archivo
Abre el archivo y agrega el siguiente contenido (personalizado):

```markdown
# [Tu Nombre]

## Sobre mí
- **Edad**: [Tu edad]
- **Ciudad**: [Tu ciudad]
- **Profesión/Estudios**: [Lo que haces]

## ¿Por qué quiero aprender GitHub?
[Escribe aquí tus motivaciones]

## Objetivos de aprendizaje
- [ ] Aprender comandos básicos de Git
- [ ] Crear repositorios
- [ ] Trabajar con ramas
- [ ] Colaborar en proyectos
- [ ] Usar GitHub para proyectos personales

## Mi primer commit
Fecha: [Fecha de hoy]
Este es mi primer commit en el curso de GitHub.

¡Estoy emocionado/a de aprender!
```

### Paso 5: Agregar el archivo al staging area
```bash
git add ejercicios/estudiantes/tu-nombre.md
```

### Paso 6: Hacer tu primer commit
```bash
git commit -m "Agregar información personal - [Tu Nombre]"
```

### Paso 7: Verificar el commit
```bash
git log --oneline
```

## ✅ Verificación
Si completaste el ejercicio correctamente, deberías ver:
- Tu archivo en la carpeta `ejercicios/estudiantes/`
- Un commit con tu nombre en el historial
- El estado del repositorio limpio (`git status` muestra "working tree clean")

## 🎉 ¡Felicidades!
¡Has hecho tu primer commit! Ahora eres oficialmente parte de la comunidad de desarrolladores que usan Git.

## 📝 Reflexión
Contesta estas preguntas en tu archivo personal:
1. ¿Qué comando usaste para ver el estado del repositorio?
2. ¿Cuál es la diferencia entre `git add` y `git commit`?
3. ¿Por qué es importante escribir mensajes de commit descriptivos?

## 🚀 Siguiente paso
Ve al [Ejercicio 2: Trabajando con Ramas](ejercicio-02-ramas.md)