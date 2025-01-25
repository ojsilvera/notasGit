# configuraciones y comandos situacionales

## Proceso de configuración tras instalación o uso de una maquina nueva

``
git config --global color.ui true
``

``
git config --global [user.name](http://user.name/) "ojsc"
``

``
git config --global user.email "[ojsilvera@gmail.com](mailto:ojsilvera@gmail.com)"
``

``
ssh-keygen -t ed25519 -C "[ojsilvera@gmail.com](mailto:ojsilvera@gmail.com)"
``

Captura muestra la llave creada para enviarla a github

``
 cat ~/.ssh/id_ed25519.pub
``

La salida del comando anterior va aqui:

``
 https://github.com/settings/ssh/new
``

Se comunica con github para verificar que la configuración halla sido exitosa

``
ssh -T [git@github.com](mailto:git@github.com)
``

Deberías recibir el siguiente mensaje del comando anterior:

``
You should get a message like this: Hi excid3! You've successfully authenticated, but GitHub does not provide shell access.
``

### Instalación en otras plataformas y cliente grafico en windows

[Alura-Git]([https://](https://www.aluracursos.com/blog/guia-sobre-como-instalar-git-en-diferentes-sistemas-operativos))

### Comandos situacionales

#### ⚙️ CONFIGURACIONES

- `git config --global user.email me@email.com`
  Para definir un correo.
- `git config --global user.name nombreUsuario`
  Para definir un nombre de usuario.
- `git config --global color.ui true`
  Para hacer Git más dinámico.
- `git config --global core.editor “atom --wait”`
  Para colocar algún editor, en este caso Atom.
- `git config --list`
  Para ver la configuración por defecto de tu Git.
- `git config --list --show-origin`
  Ver dónde están las configuraciones guardadas.

---

#### 🛠 FLUJO DE TRABAJO

- `git init nombreDelRepo`
  Para iniciar un nuevo repositorio.
- `git init`
  Si nos encontramos en el directorio que queremos como repo.
- `rm -rf .git`
  Para que un directorio deje de ser un repositorio.
- `git add nombreArchivo`
  Para agregar un *Untracked file* del *working directory* al *staging area*.
- `git add -A`
  Para agregar todos los archivos que tenemos.
- `git add .`
  Funciona igual que el anterior.
- `git rm --cached`
  Para remover un archivo del *staging area*.
- `git status`
  Para saber qué y dónde se encuentra.
- `git commit -m 'message'`
  Para comprometer lo que modificaste.
- `git commit --amend`
  Si te equivocaste y quieres agregar un cambio al último *commit*.
- `git commit --am`
  Hace `git add` y `git commit` al mismo tiempo (solo para archivos ya *trackeados*).

---

#### 🔖 TAGS

- `git tag -a 'version'`
  Para agregar una etiqueta al último SHA.
- `git tag -a 'versión' SHA1234567890abcdf`
  Para etiquetar un SHA específico.
- `git tag -l`
  Para ver las etiquetas de los SHA.
- `git tag -d 'nombreDelTag'`
  Para borrar una etiqueta.
- `git tag -f -a 'version' -m 'message' SHA1234567890abcdf`
  Para renombrar un tag (luego hay que eliminar el anterior).
- `git push origin --tags`
  Para mandar los tags al repositorio remoto.
- `git push origin :refs/tag/nombre-del-tag`
  Para remover un tag del repositorio remoto.

---

#### 🚃 LOGS

- `git log`
  Rastreo del proyecto.
- `git log --oneline`
  Muestra los SHA en una sola línea.
- `git log --graph`
  Muestra las ramas.

### Crear un alias para el log

``
git config --global alias.superlog "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
``
Luego, usa `git superlog` para verlo de manera visual.

---

#### COMPARACIONES

- `git show <archivo>`
  Para ver los cambios del archivo.
- `git diff SHA1`
  Para comparar el estado final con el *commit*.
- `git diff SHA2 SHA1`
  Para comparar entre dos commits.
- `git checkout SHA1 <archivo>`
  Para volver a ese momento de la historia.
- `git checkout master <archivo>`
  Para regresar a la última versión.

### Deshacer cambios

- `git reset --soft SHA1`
  Elimina cambios posteriores manteniendo el estado del *commit*.
- `git reset --mixed SHA1`
  Similar al anterior, pero mantiene el archivo en el *Working Directory*.
- `git reset --hard`
  Borra absolutamente todo desde el SHA indicado.
- `git reflog`
  Para recuperar cambios eliminados accidentalmente.

---

#### RAMAS

- `git branch nombreRama`
  Para crear una nueva rama.
- `git branch -l`
  Para listar las ramas.
- `git branch -d nombreRama`
  Para eliminar una rama.
- `git branch -m nombrePrevio nombreNuevo`
  Para renombrar una rama.
- `git checkout nombreRama`
  Para moverte entre ramas.
- `git checkout -b nombreRama`
  Para crear una nueva rama y moverte a ella.
- `git show-branch --all`
  Muestra las ramas y su historial.

---

#### MEZCLA DE RAMAS

- `git merge ramaAMezclar`
  Mezcla la rama con la que estás.
- `git rebase nombreRama`
  Sobrescribe la historia para un seguimiento lineal.

---

#### GUARDAR ESTADO

- `git stash`
  Guarda un estado del proyecto para moverte a otra rama sin hacer *commit*.
- `git stash list`
  Muestra los *stash* guardados.
- `git stash apply`
  Aplica el último *stash* guardado.
- `git stash pop`
  Aplica el *stash* y lo elimina.
- `git stash branch nombreDeLaNuevaRama`
  Crea una rama con las últimas modificaciones.

---

#### 🍒CEREZAS

- `git cherry-pick SHA`
  Trae un *commit* específico a la rama actual.

---

#### CLONANDO

- `git clone dirHtml`
  Para clonar un repositorio.
- `ssh-keygen -t rsa -b 4096 -C "email@email.com"`
  Para crear una llave pública.
- `git remote add origin direcciónDeTuRepo`
  Asocia un repositorio remoto llamado *origin*.
- `git fetch origin`
  Trae archivos del repositorio remoto.
- `git pull origin master`
  Sincroniza cambios del repositorio remoto.
- `git push origin master`
  Sube cambios al repositorio remoto.

---

#### LIMPIAR

- `git clean --dry-run`
  Visualiza qué archivos se van a borrar.
- `git clean -f`
  Borra los archivos visualizados.

---

#### BUSCAR PALABRAS

- `git grep <palabra>`
  Busca una palabra en los archivos del proyecto.
- `git grep -n <palabra>`
  Indica en qué línea está.
- `git grep -c <palabra>`
  Muestra cuántas veces se usa la palabra en cada archivo.

---
