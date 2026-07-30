# 🧠 Guía rápida de Git (Completa y Visual)

Holaa, yo soy Patri y esta es mi guía para aprender o tener a mano algunos de los comandos de Git. :shipit:

---

## 📌 ¿Qué es Git?

**Git** es un sistema de control de versiones que te permite: 
- Guardar cambios en tu código 📁
- Volver atrás si algo falla ⏪
- Trabajar en equipo 👥
- Crear versiones de tu proyecto 🏷️

---


### Git trabaja con 3 zonas:
1. **Working Directory** -> Donde editas archivos
2. **Staging Area** -> Lo que vas a guardar
3. **Repository** -> historial de commits

### Fujo básico de Git:
1. Modificas archivos
2. Los añades
3. Guardas cambios
4. Los subes

---

### Fichero `.gitignore` 📁
Es un archivo que le dice a Git qué cosas NO debe incluir en el repositorio.

Sirve para evitar subir ficheros y cosas no relevantes o cosas sensibles q no deben estar como:

- dependencias instalabres (node_modules, venv)
- archivos temporales o compilados (dist, build, logs)
- configuraciones personales del editor (.vscode, .idea)
- y sobre todo, secretos (.venv, claves API, tokens)


> <u>⚠️ **Cuidado**</u>
> 
> Si ya subiste un archivo antes, añadirlo al `.gitignore` NO lo elimina automáticamente del repo.
>
> Para dejar de trackearlo:
> ```bash
> git rm --cached archivo
> ```
>
> o para limpiar todo:
> ```bash
> git rm -r --cached .
> git add .
> ```


---

# COMANDOS ‼️
---

## 🌍 Configuración Básica Global 🌍
Para empezar a utilizar git debemos hacer una configuración global que mínimo tiene que incluir 2 cosas:
 
- Nombre de Usuario
- Email

### 🔹 1. Configurar Nombre que salen en los commits
```bash
git config --global user.name "[Nombre]"
```

> 📋 **Nota:** el archivo que modificamos con este comando se encuentra en /home/[usuario]/.gitconfig

### 🔹 2. Configurar el Email
```bash
git config --global user.email "tu_email@mail.com"
```
### 🔹 3. Configurar Alias (Opcional)
```bash
git config --global alias.[nombre_alias] "Comando para el álias"
```
> **Ejemplo:** git config --global alias.tree "log --graph --decorate --all --oneline"




___
## 💠 [GIT INIT] Iniciar nuestro repositorio 

Para ello debemos estar en nuestra carpeta del "Proyecto" que vayamos a realizar 
> Puedes moverte hacia ella con **'cd /ruta/del/proyecto'**

Una vez ahí ya puedes lanzar el siguiente comando:

```bash
git init
```

Con esto te aparecerá en la carpeta del Proyecto una carpeta oculta llamada **".git"**

> **Opcional:** podemos cambiarle el nombre a la rama principal que aparece como "master", esto es algo personal porque luego al implementar con git, por defecto, esta rama se llama "main" además que se está estandarizando que se llame así

Podemos ver con el comando **'git status'** el nombre que tiene antes de cambiarlo

Para cambiarlo usaremos este comando:
```bash
git branch -m "main"
```




___
## 💠 [GIT STATUS] Visualizar el estado (Staging Area)

Este comando te va a servir para cuando realizes cambios, ver en que estado se encuentran esos cambios.
```bash
git status
```




___
## 💠 [GIT ADD] Añadir archivos

En tu editor de código favorito, puedes empezar a crear tus archivos de código para tu Proyecto pero hasta que tu no los añadas al staging area, no podrás crear tus commits.

Commit: "foto" o captura instantánea del estado de tu proyecto en un momento específico, actuando como un punto de guardado seguro.

Por eso para añadirlos está el comando:
```bash
git add [Nombre_del_archivo]
```
Pero también puedes utilizar este comando para **añadir todos los archivos** que estén sin añadir en en 'git status':

```bash
git add .
```




___
## 💠 [GIT COMMIT] Crear imágenes

Suele utilizarse después del add, no es obligatorio. Sirve para realizar la imagen.

La forma más cómoda de realizarlo es con el atributo **-m** para escribir directamente el texto que hace referencia al commit sin tener que abrir ningún editor de texto.

```bash
git commit -m "Texto que identifique por qué se hizo el commit"
```
### | Tipos de commits
Hay distintos tipos de commits que podemos encontrarlos en esta url [conventionalcommits.org](https://www.conventionalcommits.org/es/v1.0.0/ "Más info sobre Commits")

Principalmente hay 2:
- **fix:** para cambios pequeños
- **feat:** para cambios más grandes

Se suelen asociar a las versiones.
Su apariencia es la siguiente:
```bash
git commit -m "fix: texto que identifique por qué se hizo el commit"
```



___
## 💠 [GIT LOG] Visor de eventos de Git

Con este comando lo que puedes hacer es ver que cambios se han ido haciendo sobre los commits, es decir, que commits hay, en cual estoy, que hash identificador tienen...

```bash
git log
```
### | Atributos importantes del 'git log'
Hay ciertos atributos que se pueden utilizar junto al log para que nos sea más visual dependiendo de que queramos hacer, algunos de los ejemplos son:

🔹 1. Para verlo con **línea gráfica**.
 ```bash
 git log --graph
 ```

🔹 2. Para verlo **en una línea sin autor y ni fecha**.
```bash
git log --pretty=oneline
```
🔹 3. Para verlo **super resumido**.
```bash
git log --graph --decorate --all --oneline
```



___
## 💠 [GIT SWITCH] Para cambiar de rama

Simplemente te ayuda a cambiar de rama sin hacer nada más.
```bash
git switch [nombre_rama]
```


___
## 💠 [GIT CHECKOUT]

Este comando tiene muchas funciones y hay tener varias cosas en cuenta.
Sirve principalmente para moverte dentro del repositorio.
 
 #### 🔹**1. Uso principal: Cambiar de rama.**
 
 Aquí hay que tener clara una cosa
 
 |  Comando |   Para qué sirve  |
 |:--------:|:------------------|
 |**git checkout** | Hace MUCHAS cosas (cambiar rama, restaurar archivos, moverte a commits) |
 |**git switch** | SOLO cambia de rama (más claro y seguro) |

El commando es: 
```bash
git checkout [nombre_rama]
```
> 👀 **OJO:** Si tienes cambios sin guardar, git puede: 
>    - bloquear el cambio
>   - o moverlos contigo (dependiendo del caso)

#### 🔹 **2. Crear o cambiar de rama**
```bash
git checkout -b [nombre_nueva_rama]
```
Esto hace 2 cosas:
- Crea la rama (-b)
- Se mueve a ella

#### 🔹 **3. Recuperar archivos**
Restaura el archivo a su último commit.
```bash
git checkout archivo.txt
```
#### 🔹 **4. Ir a un commit concreto**
Te mueves a un commit específico
> 👀 **OJO:** pero debes tener en cuenta que esto crea un estado especial **Detached HEAD** que significa
> - No estas en ninguna rama
> - Estás "viendo el pasado"

```bash
git checkout [hash]
```
> 📋 **Nota:** el hash puede ser completo o la versión simplificada, podemos verlo con **'git log'**

Sirve para: 
- Probar versiones antiguas
- Revisar código viejo
- Debuggear

Para volver a la normalidad:
```bash
git checkout main
```





___
## 💠 [GIT RESET] ¡CUIDADO! "Volver atrás"

Es un comando peligroso porque puede afectar a 3 cosas:
1. Historial (commits)
2. Staging area
3. Archivos (working directory)

Se encarga de mover el puntero HEAD (donde estás en el historial)

```bash
git reset
```
Qué hace:
- Quita el archivo del 'git add'
- NO bora cambios

#### GIT RESET --HARD
Este es otro tipo que es el más peligroso
```bash
git reset --hard
```
 Qué hace:
 - Elimina el commit
 - Elimina cambios en archivos
 - Limpia staging

 > 📋 **Nota:** si la liamos podemos utilizar **'git reflog'**




___
## 💠 [GIT BRANCH] Ver, Crear y Gestionar Ramas


 #### 🔹 **1. Ver ramas.**
```bash
git branch
```
#### 🔹 **2. Crear una rama.**
```bash
git branch [nombre_rama]
```
#### 🔹 **3. Borrar una rama.**
```bash
git branch -d [nombre_rama]
```






___
## 💠 [GIT REBASE] Mover el trabajo

Reaplica los commits encima de otra rama, reescribiendo el historial. 
Es primo hermano de "merge"

Rebase = "mover el trabajo como si hubiera empezado más tarde"

```bash
git rebase [nombre_rama]
```
> **Nota:** Rebase **NO** mueve commits, los recrea. Por eso:
> - Cambian los IDs
> - Se "reescribe" la historia

Ejemplo visual:

A ---- B ---- C ---- D' ---- E'







___
## 💠 [GIT MERGE] Fusionar una rama con otra

Sirve para unir (fusionar) una rama con otra.
Es primo hermano de "rebase"

Merge = juntar historiales sin borrar nada

```bash
git merge [nombre_rama]
```






___
## 💠 [GIT DIFF] Ver diferencias de versiones

Sirve para ver las diferencias entre versiones de archivos.

#### 🔹 **1. Cambios sin añadir (Más común).**
```bash
git diff
```
#### 🔹 **2. Cambios ya añadidos.**
```bash
git diff --staged
```
#### 🔹 **3. Comparar commits.**
```bash
git diff commit1 commit2
```
#### 🔹 **4. Comparar ramas**
```bash
git diff rama1 rama2
```

#### 🔹 **5. Ver cambios en un archivo**
```bash
git diff archivo.txt
```






___
## 💠 [GIT FETCH] Descarga cambios del SIN aplicar cambios

Sirve para descargar cambios del repositorio remoto **SIN** aplicarlos en nuestro código
 
```bash
git fetch
```





___
## 💠 [GIT PUSH] SUBIR commits

Sirve para subir commits al respositorio remoto (por ejemplo, GitHub)

⚠️ ¡IMPORTANTE! Cuando subes por primera vez una rama, debemos hacer este comando:
```bash
git push -u origin [rama (ej.main)]
```
o 
```bash
git push --set-upstream origin [rama (ej.develop)]
```

Esto hace:
- sube la rama
- la conecta con el remoto

Después ya puedes usar solo
```bash
git push
```





___
## 💠 [GIT PULL] BAJAR commits

Sirve para traer cambios del repositorio remoto a nuestro ordenador y además mezclarlos automáticamente con nuestra rama actual.

> 💡 **Idea principal:** 
>
> git pull= git fetch + git merge

Hace 2 cosas:
- Descarga cambios (fetch)
- Los mezcla con nuestro código (merge)

```bash
git pull
```

#### GIT PULL --REBASE
Hay otra opción muy buena que es la de **juntar**
En lugar de mezclar, reordena los commits encima del remoto
```bash
git pull --rebase
```
