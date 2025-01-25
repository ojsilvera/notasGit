# Introducción al Control de Versiones y Git

**Secciones:**

1. ¿Qué es el control de versiones?
2. Beneficios de un VCS
3. Control de versiones distribuido
4. Terminología esencial en Git
5. Interfaz de línea de comandos
6. Diferencias entre Git y GitHub

---

## ¿Qué es el control de versiones?

Un sistema de control de versiones (VCS):

- Realiza un seguimiento de los cambios en una colección de archivos.
- Permite recuperar versiones anteriores de archivos individuales o de todo el proyecto.
- Facilita que varios miembros del equipo trabajen simultáneamente, incluso en los mismos archivos, sin conflictos.

### Otros nombres y usos

- También se conoce como **sistema de administración de configuración de software (SCM)**.
- Puede usarse en proyectos que no sean software, como libros o tutoriales en línea.

---

## Beneficios del control de versiones

Con un VCS, puedes:

- Ver todos los cambios realizados en el proyecto, con detalles sobre quién, cómo y cuándo se realizaron.
- Adjuntar mensajes explicativos a cada cambio.
- Recuperar versiones anteriores del proyecto o de archivos individuales.
- Crear **ramas** para trabajar en diferentes cambios (funcionalidades o correcciones) de forma simultánea y experimental.
- Fusionar cambios de las ramas en la rama principal.
- Adjuntar etiquetas para marcar versiones importantes, como lanzamientos de software.

---

## Git como sistema de control de versiones

Git es un VCS **rápido, versátil, altamente escalable, gratuito y de código abierto**. Fue creado por **Linus Torvalds**, el autor principal de Linux.

### Control de versiones distribuido

- En sistemas tradicionales como CVS o SVN, un servidor centralizado almacenaba todo el historial del proyecto, generando puntos únicos de fallo.
- Git es **distribuido**, lo que significa que cada cliente tiene una copia completa del historial del proyecto.
- Puedes trabajar sin conexión y sincronizar los cambios con el servidor cuando sea necesario.
- Aunque es posible operar sin servidor, Git en la práctica utiliza repositorios remotos como GitHub.

---

## Terminología básica en Git

Conocer estos términos es clave para comprender Git:

- **Árbol de trabajo**: Estructura de directorios y archivos del proyecto en curso.
- **Repositorio**: Almacén donde Git guarda el historial y metadatos del proyecto.
- **Hash**: Identificador único de cambios, generado con funciones SHA-1.
- **Objeto**: Entidad en Git (blob, árbol, confirmación, etiqueta).
- **Confirmar**: Acción de guardar cambios en el historial.
- **Rama**: Serie de confirmaciones vinculadas con un nombre (por defecto: `main`).
- **Remoto**: Referencia a otro repositorio de Git (por defecto: `origin`).
- **Comandos**: Operaciones de Git realizadas con subcomandos (`git push`, `git pull`) y opciones (`-hard`, `m`).

---

## La línea de comandos de Git

- Aunque existen interfaces gráficas (GUI) como **GitHub Desktop** y editores integrados (VS Code), la **línea de comandos** permite acceder a todas las funcionalidades de Git.
- Los ejercicios de este módulo utilizan **Azure Cloud Shell**, pero los comandos son consistentes en cualquier sistema operativo.
- Los desarrolladores que dependen únicamente de GUI suelen recurrir a la línea de comandos para solucionar errores complejos.

---

## Diferencias entre Git y GitHub

- **Git**: Sistema de control de versiones distribuido que permite colaborar y gestionar ramas locales y remotas.
- **GitHub**: Plataforma en la nube que utiliza Git como tecnología base, ofreciendo herramientas adicionales para la colaboración:
  - Issues, discusiones, pull requests, notificaciones, proyectos, etiquetas, forks, entre otros.

### Recursos adicionales

- [Documentación oficial de Git](http://git-scm.com/)
- [Introducción a GitHub](https://docs.github.com/)

## **Configurar Git**

1. En Cloud Shell, para verificar que Git esté instalado, escriba `git --version`:

    `
    git --version
    `

    **Consejo**

        Puede usar el botón **Copiar** para copiar comandos al portapapeles. Para pegar, haga clic con el botón derecho
        en una nueva línea en la terminal de Cloud Shell y seleccione **Pegar** , o use el método abreviado de
        teclado Mayús+Insertar (⌘+V en macOS).

2. Debería ver una salida que se parece a este ejemplo:

    `
    git version 2.7.4
    `

3. Para configurar Git, debe definir algunas variables globales: `user.name`y `user.email`. Ambos son necesarios para que
   pueda realizar confirmaciones.

4. Establezca su nombre en Cloud Shell con el siguiente comando. Reemplace `<USER_NAME>`con el nombre de usuario que desea usar.

    `
    git config --global user.name "<USER_NAME>"
    `

5. Ahora, use este comando para crear una `user.email`variable de configuración, reemplazándola `<USER_EMAIL>`con su
   dirección de correo electrónico:

    `
    git config --global user.email "<USER_EMAIL>"
    `

6. Ejecute el siguiente comando para verificar que sus cambios funcionaron:

    `
    git config --list
    `

7. Confirme que la salida incluye dos líneas que son similares al siguiente ejemplo. Su nombre y dirección de correo electrónico serán diferentes a los que se muestran en el ejemplo.

    `
    user.name=User Name
    user.email=user-name@contoso.com
    `

## **Configura tu repositorio Git**

Git funciona comprobando los cambios en los archivos dentro de una determinada carpeta. Crearemos una carpeta para que
sirva como nuestro *árbol de trabajo* (directorio del proyecto) y le informaremos a Git, para que pueda comenzar a rastrear
los cambios. Le decimos a Git que comience a rastrear los cambios inicializando un repositorio de Git en esa carpeta.

Comience creando una carpeta vacía para su proyecto y luego inicialice un repositorio de Git dentro de ella.

1. Cree una carpeta llamada *Gatos* . Esta carpeta será el directorio del proyecto, también llamado árbol de trabajo. El
   directorio del proyecto es donde se almacenan todos los archivos relacionados con su proyecto. En este ejercicio, es
   donde se almacenan su sitio web y los archivos que crean el sitio web y su contenido.

    `
    mkdir Cats
    `

2. Cambie al directorio del proyecto usando el `cd`comando:

    `
    cd Cats
    `

3. Ahora, inicialice su nuevo repositorio y establezca el nombre de la rama predeterminada en `main`:

    Si está ejecutando Git versión 2.28.0 o posterior, use los siguientes comandos:

    `
    git init --initial-branch=main
    git init -b main
    `

    Para versiones anteriores de Git, use estos comandos:

    `
    git init
    git checkout -b main
    `

    Después de ejecutar el comando de inicialización, debería ver un resultado similar a este ejemplo:

    `
    Initialized empty Git repository in /home/<user>/Cats/.git/
    Switched to a new branch 'main'
    `

4. Ahora, use un `git status`comando para mostrar el estado del árbol de trabajo:

    `
    git status
    `

    Git responde con esta salida, lo que indica que `master`es la rama actual. (También es la única sucursal). Hasta
    ahora, muy bien.

    Respuesta

    `
    On branch master
    No commits yet
    nothing to commit (create/copy files and use "git add" to track)
    `

5. Use un `ls`comando para mostrar el contenido del árbol de trabajo:

    `
    ls -a
    `

Confirme que el directorio contiene un subdirectorio llamado *.git* . (Usar la `-a`opción con `ls`es importante porque
Linux normalmente oculta los nombres de archivos y directorios que comienzan con un punto). Esta carpeta es el *repositorio*
de Git , el directorio en el que Git almacena metadatos e historial para el árbol de trabajo.

Por lo general, no hace nada con el directorio *.git* directamente. Git actualiza los metadatos allí a medida que cambia
el estado del árbol de trabajo para realizar un seguimiento de lo que ha cambiado en sus archivos. Este directorio no es
de intervención para usted, pero es increíblemente importante para Git.

## **Obtener ayuda de Git**

Git, como la mayoría de las herramientas de línea de comandos, tiene una función de ayuda integrada que puede usar para
buscar comandos y palabras clave.

1. Escriba el siguiente comando para obtener ayuda con lo que puede hacer con Git:

    `
    git --help
    `

2. El comando muestra el siguiente resultado:

    `
    usage: git [--version] [--help] [-C <path>] [-c name=value]
    [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
    [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
    [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
    <command> [<args>]
    These are common Git commands used in various situations:
    start a working area (see also: git help tutorial)
    clone  Clone a repository into a new directory
    init   Create an empty Git repository or reinitialize an existing one
    work on the current change (see also: git help everyday)
    addAdd file contents to the index
    mv Move or rename a file, a directory, or a symlink
    reset  Reset current HEAD to the specified state
    rm Remove files from the working tree and from the index
    examine the history and state (see also: git help revisions)
    bisect Use binary search to find the commit that introduced a bug
    grep   Print lines matching a pattern
    logShow commit logs
    show   Show various types of objects
    status Show the working tree status
    grow, mark and tweak your common history
    branch List, create, or delete branches
    checkout   Switch branches or restore working tree files
    commit Record changes to the repository
    diff   Show changes between commits, commit and working tree, etc
    merge  Join two or more development histories together
    rebase Forward-port local commits to the updated upstream head
    tagCreate, list, delete or verify a tag object signed with GPG
    collaborate (see also: git help workflows)
    fetch  Download objects and refs from another repository
    pull   Fetch from and integrate with another repository or a local branch
    push   Update remote refs along with associated objects
    'git help -a' and 'git help -g' list available subcommands and some
    concept guides. See 'git help <command>' or 'git help <concept>'
    to read about a specific subcommand or concept.
    `

Lea las diferentes opciones disponibles con Git y tenga en cuenta que cada comando viene con su propia página de ayuda,
para cuando comience a profundizar. No todos estos comandos tendrán sentido todavía, pero algunos pueden parecerle familiares
si tiene experiencia en el uso de un VCS.

### Comandos del día a día

A continuación un listado de los comandos mas usados en el día a día:

[GIT&GitHub](https://www.notion.so/GIT-GitHub-95ef276d008b4f99a4ff08845e3cff03?pvs=21)

---

[Compendio de comando situacionales](https://www.notion.so/Compendio-de-comando-situacionales-1865895fec9c80aa831fdee66a0a5ca3?pvs=21)

---
