# Trabajando con GitHub
## ¿Qué es GitHub?

GitHub es una plataforma que permite alojar tus repositorios de Git en la nube, facilitando la colaboración con otros desarrolladores.

### Crear un Repositorio en GitHub

Crea una cuenta en [GitHub](https://github.com/).
Una vez dentro, crea un nuevo repositorio.

# ¿Qué es Git?

Git es un sistema de control de versiones distribuido, lo que significa que permite realizar un seguimiento de los cambios en archivos y coordinar el trabajo en esos archivos entre varias personas. Es muy útil para el desarrollo de software, donde se trabaja en proyectos que cambian constantemente.

## Conceptos Clave:

- **Repositorio (Repository):** Es el lugar donde Git guarda todo el historial de cambios de tu proyecto.
- **Commit:** Es un "snapshot" del estado actual de tu proyecto. Representa un punto en el tiempo en el que has hecho cambios específicos.
- **Rama (Branch):** Es una versión paralela de tu código. Por defecto, la rama principal es master o main.

## Instalación de Git:

- **Windows:** Puedes descargar Git desde [git-scm.com](https://git-scm.com/).

## Configuración Inicial:

Después de instalar Git, configúralo con tu nombre y correo electrónico (esto se usará para tus commits)

```
git config --global user.name "Tu Nombre"
git config --global user.email "tuemail@ejemplo.com"
```

### Verificar la configuración

```
git config --list
```

## Creación de un proyecto

```
flutter create --empty aprender_git
cd aprender_git
```

### Inicializar Git
```
git init
```

### Realizar tu Primer Commit

**Crear un Archivo:** Crea un archivo prueba_git.txt con un editor de texto y escribe algo básico, como:
```Mi Proyecto
Este es mi primer proyecto con Git.
```
#### Agregar el Archivo
```git add prueba_git.text
git add .
```
#### Hacer un Commit:
```
git commit -m "Mi primer commit: Agregado prueba_git.text"
```
**¿Qué son las Ramas?:** Las ramas en Git permiten trabajar en diferentes versiones del código de manera simultánea. Por ejemplo, puedes tener una rama para la versión estable del código y otra para la versión en desarrollo.

## Crear una Nueva Rama

```
git branch develop
```

## Cambiar de Rama
```
git checkout develop
```

Ahora estás trabajando en la rama develop. Cualquier cambio que hagas aquí no afectará la rama main (la rama principal).


**Hacer Cambios en la Nueva Rama:** Ingrese a lib/main.dart, y remplace lo siguiente:

```Hello World!
Estoy en la rama Develop
```
## Commit en la Nueva Rama

```git add lib/main.dart
git commit -m "modificando lib/main.dart en rama develop"
```

## Fusionando Ramas (Merge)
### Volver a la Rama Principal

```
git checkout main
```

## Fusionar la Rama de develop en la principal

```
git merge develop
```

Esto integrará los cambios de la rama desarrollo en la rama main.

### Subir tu Proyecto a GitHub

Agregar el Repositorio Remoto

```
git remote add origin https://github.com/tuusuario/mi-proyecto.git
```

Agregar el Repositorio Remoto

```
git push -u origin main
```

## Tarea
- **Clonar un Repositorio:**
- **Trabajar con Pull Requests:**
- **El uso de .gitignore:**