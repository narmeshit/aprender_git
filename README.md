# GitHub y Git

GitHub es una plataforma donde puedes almacenar, compartir y trabajar junto con otros usuarios para escribir código.

Almacenar tu código en un "repositorio" en GitHub te permite:

- **Presentar o compartir** el trabajo.
- **Seguir y administrar** los cambios en el código a lo largo del tiempo.
- Dejar que otros usuarios **revisen** el código y realicen sugerencias para mejorarlo.
- **Colaborar** en un proyecto compartido, sin preocuparse de que los cambios afectarán al trabajo de los colaboradores antes de que esté listo para integrarlos.

Para empezar a trabajar con GitHub, deberás crear una cuenta personal gratuita en [GitHub.com](https://github.com/) y comprobar la dirección de correo electrónico.

Cada persona que utilice GitHub.com deberá iniciar sesión en una cuenta personal. Tu cuenta personal es tu identidad en GitHub.com y tiene un nombre de usuario y perfil. **Por ejemplo**, consulte el perfil de **@narmeshit**.

## Git

Git es un sistema de control de versiones que realiza un seguimiento de los cambios en los archivos. Git es especialmente útil cuando un grupo de personas y tú hacen cambios en los mismos archivos al mismo tiempo.

Normalmente, para hacerlo en un flujo de trabajo basado en Git, harías lo siguiente:

- **Crear una rama** a partir de la copia principal de archivos en los que tú (y tus colaboradores) estan trabajando.
- **Realizar modificaciones** en los archivos de forma independiente y segura en tu propia rama personal.
- Dejar que Git **fusione mediante combinación** y de forma inteligente los cambios específicos en la copia principal de archivos, de modo que los cambios no afecten a las actualizaciones de otras personas.
- Dejar que Git **realice un seguimiento** de tus cambios y los de otras personas, por lo que todos siguen trabajando en la versión más actualizada del proyecto.

### Conceptos Clave

- **Repositorio (Repository):** Es el lugar donde Git guarda todo el historial de cambios de tu proyecto.
- **Commit:** Representa un punto en el tiempo en el que has hecho cambios específicos.
- **Rama (Branch):** Las ramas en Git permiten trabajar en diferentes versiones del código de manera simultánea.

### Escritura de Commits

- **Commits Pequeños y Frecuentes:** Realiza commits pequeños, descriptivos y frecuentes para mantener un historial claro.
- **Mensajes de Commit Claros:** Escribe mensajes de commit descriptivos, indicando qué cambio se realizó y por qué.

### Configura Git .gitignore

`.gitignore` para evitar que archivos innecesarios sean incluidos en el repositorio. Flutter genera automáticamente uno, pero asegúrate de que esté bien configurado.

```plaintext
# .gitignore

# Flutter related
.build/
.flutter-plugins
.flutter-plugins-dependencies
.packages
.pub-cache/
.pub/
/build/
```

### Instalación de Git

- Empiece a trabajar con [Git](https://git-scm.com/), descargue e instale es gratis.

## Configuración Inicial

Después de instalar Git, configúralo con tu nombre y correo electrónico (esto se usará para tus commits)

```bash
git config --global user.name "narmeshit"
git config --global user.email "narmeshit@gmail.com"
```

### Verificar la configuración

```bash
git config --list
```

## Creación de un proyecto

```bash
flutter create aprender_git
cd aprender_git
```

### Inicializar Git

```bash
git init
```

### Agregar cambios del proyecto

```bash
git add .
```

### Agregar cambios de un archivo específico

```bash
git add nombre_archivo
```

#### Crear commit con los cambios

```bash
git commit -m "mensaje"
```

#### Mostrar el estado de los archivos

```bash
git status
```

#### Mostrar el historial de commits

```bash
git log
```

#### Mostrar las diferencias entre los archivos

```bash
git diff
```

#### Ver todas las ramas

```bash
git branch
```

#### Crear una ramas

```bash
git branch nombre_nueva_rama
```

#### Cambiar a la rama especificada

```bash
git checkout nombre_rama
```

#### Crear y cambiar a una nueva rama

```bash
git checkout -b nombre_nueva_rama
```

#### Fusionar los cambios de la rama especifica

```bash
git merge nombre_rama
```

#### Descargar y fusionar los cambios del repositorio remoto

```bash
git pull
```

#### Enviar los commits locales

```bash
git push
```

#### Mostrar las Urls de los repositorios remotos asociados

```bash
git remote -v
```

#### Restablecer y eliminar cambios posteriores en el repositorio al estado de un commit específico

```bash
git reset --hard hash_commit
```

#### Clonar un repositorio remoto

```bash
git clone url_repositorio
```

## Felicitaciones

Ahora ya está listo para usar git en sus proyectos, ahora necesitamos establecer un flujo de trabajo cuando necesitamos trabajar en equipo o un proyecto que va escalar.

## Flujo de Trabajo Común (Git Flow)

Considera usar Git Flow u otro flujo de trabajo como GitHub Flow. Estos flujos establecen ramas para desarrollo, características nuevas, correcciones de errores y producción, facilitando la colaboración.

- **main** Contiene el código que está en producción, es decir, la versión estable de la aplicación.
- **develop** Rama de desarrollo principal donde se integran las nuevas funcionalidades antes de ser lanzadas.
- **feature/** Crea ramas para cada nueva funcionalidad o tarea, lo que permite a los desarrolladores trabajar sin interferir con la rama principal.
- **release/** Ramas para preparar una nueva versión antes de lanzarla.
- **hotfix/** Ramas para correcciones rápidas en la versión en producción.

### Ejemplo Práctico

#### Inicio del Proyecto

- Crea las ramas principales `main` y `develop`.
- Inicializa el repositorio y sube la configuración inicial.

```bash
git init
git checkout -b main
git push -u origin main
git checkout -b develop
git push -u origin develop
```

#### Desarrollo de Nuevas Funcionalidades

- Digamos que necesitas implementar una funcionalidad de autenticación con Google.
- Crea una rama para esta característica.

```bash
git checkout -b feature/google-auth
```

- Realiza tus cambios, prueba la funcionalidad, y haz commits frecuentemente.

```bash
git add .
git commit -m "Implementa autenticación con Google"
```

- Una vez que la funcionalidad está completa y probada, fusiona la rama en `develop`.

```bash
git checkout develop
git merge feature/google-auth
git push origin develop
```

#### Preparar una Nueva Versión para Lanzamiento

- Antes de lanzar una nueva versión, crea una rama de `release`.

```bash
git checkout -b release/v1.0.0
```

- Haz los últimos ajustes y correcciones de bugs menores. Todos los cambios deben realizarse en la rama `release/v1.0.0`.

```bash
git add .
git commit -m "Prepara la versión 1.0.0 para lanzamiento"
```

- Una vez que la versión está lista para ser lanzada, crea un tag.

```bash
git tag -a v1.0.0 -m "Lanzamiento de la versión 1.0.0"
git push origin v1.0.0
```

- Fusiona la rama `release` en `main` y `develop`.

```bash
git checkout main
git merge release/v1.0.0
git push origin main

git checkout develop
git merge release/v1.0.0
git push origin develop
```

- Borra la rama `release/v1.0.0` local y remotamente.

```bash
git branch -d release/v1.0.0
git push origin --delete release/v1.0.0
```

#### Hotfix en Producción

- Si se descubre un bug en producción, crea una rama desde `main` para corregirlo.

```bash
git checkout -b hotfix/bugfix-1.0.1 main
```

- Después de corregir el bug, crea un nuevo tag y lanza la versión.

```bash
git add .
git commit -m "Corrige bug crítico en la autenticación"
git tag -a v1.0.1 -m "Lanzamiento de hotfix versión 1.0.1"
git push origin v1.0.1
```

- Fusiona el hotfix en `main` y `develop`.

```bash
git checkout main
git merge hotfix/bugfix-1.0.1
git push origin main

git checkout develop
git merge hotfix/bugfix-1.0.1
git push origin develop
```

- Borra la rama `hotfix/bugfix-1.0.1`.

```bash
git branch -d hotfix/bugfix-1.0.1
git push origin --delete hotfix/bugfix-1.0.1
```
