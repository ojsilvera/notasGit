# flujos de trabajo

Al iniciar el día de trabajo ejecutamos para tener la ultima version del codigo

---

``
💡 git pull origin <ramaDestino>(aquí actualiza el local con lo que existe en github)
``

---

## Uso diario de git

---

``
git status(muesta la branch en la qu estamos trabajando y si hay archivos modificados para subir o por comitear)
``

``
git add -A (agrega los archivos pendientes para hacerles commit y enviarlos a github)
``

``
git commit -m "un mensaje descriptivo de los cambios realizados"(anexar los archivos del stage(que fueron modificados y
estan pendientes por enviar) un mensaje q permite saber lo que fue modificado)
``

``
git push -u origin ramaDestino (envia los archivos modificados al repo de github publicando la rama origen en el repo de github)
``

---

## Flujo para una rama de trabajo distinta que se va a publicar en el repo como rama de trabajo

---

git status (Verficas en rama estas)

git  branch nombreRama(crea una rama local de trabajo sino existe y nos ubica en ella, para desarrollar)

git checkout nombreRama (nos ubica en la rama de trabajo si existe) //

git checkout -b issues# (crea la rama nombre y te posiciona, te pasa a la rama issues, agrupa los dos comandos anteriores)

git pull origin mastare(main)(nos trae la info mas actual del repo)

git status(nos muestra si hay archivos con cambios y la rama en la que nos encontramos)

git add -A(agregar al stage los cambios)

git commit -m “el mensaje”

git push origin ramaDeTrabajo (mueve los datos del origen a la rama de trabajo en remoto publicandola)

git push -u origin `<branch>` (mueve los archivos de origin a la branch seleccionada y la siguiente vez solo haces git push y toma la info almacenada inicialmente)

git checkout master(cambiamos a la rama principal)

git merge ramadeTrabajo(estando en la rama principal copiamos los cambios de dev en master pre-push a master remoto)

git push origin master (mueve los datos del origen a la rama master)

si todo sale bien solicitamos el pull request en github

---

## Flujo para una rama de trabajo temporal que no sera publicada en el repo, solo funciona localmente

---

git status

git pull origin mastare(main)(nos trae la info mas actual del repo)

git checkout -b `<nombreRama>` (crea la rama y te posiciona en la nueva rama creada)

git status(nos muestra si hay archivos con cambios y la rama en la que nos encontramos)

git add -A(agregar al stage los cambios)

git commit -m “el mensaje”

git checkout master(cambiamos a la rama principal)

git merge dev(estando en la rama principal copiamos los cambios de dev en master pre-push a master remoto)

git push origin master (mueve los datos del origen a la rama master)

si todo sale bien solicitamos el pull request en github

git branch -d nombreDeLaRamaTemporal (una vez integrado los cambios a la master por parte del admin del repo eliminamos la rama temporal)

---
