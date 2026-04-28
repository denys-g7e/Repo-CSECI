Día 1
¿Qué es git?
Git es un sistema de control de Versiones Distribuido(VCS), esto quiere decir que se puede trabajar en grupo. Nos permite guardar archivos y las versiones de estos a lo largo del tiempo de manera local

¿Cómo nació git?
Git nació en 2005 cuando Linus Torvalds, creador del kernel de Linux, necesitaba una nueva herramienta para gestionar los cambios en el código del proyecto Linux. Antes de utilizar un sistema llamado BitKeeper, que era un propietario de software que les permitía trabajar gratis, pero tras un conflicto con la empresa que lo desarrollaba, dejaron de tener acceso a él. Como solución, Linus decidió crear su propio sistema de control de versiones desde cero, diseñado para ser rápido, seguro y permitir que muchos desarrolladores an al mismo tiempo. Así surgió Git, que con el paso de los años se convirtió en el sistema de control de versiones más utilizado en el mundo del desarrollo de software.

¿Cómo instalar git?
Para instalar git, se tiene que ir a la página web de git, y seguir los pasos de instalación recomendados y luego para verificar la instalación correcta se escribe git --version en la terminal

Configuraciones básicas
git config --global user.name "Tu nombre"
git config --global user.email " tu@correo.com "
git config --global core.autocrlf true
Archivos que todo repositorio deberia tener
LÉAME.md
.gitignore
Día 2-Estados y compromisos
Los estados de git
Directorio de trabajo(modificado)
Tu carpeta local.Estás escribiendo código, pero Git aún no lo tiene "asegurado".

Área de escenario (preparado)
EL área de espera.Le dice a Git: "Esto es lo que quiero guardar".

Repositorio local(confirmado)
El historial. Tus cambios ya tienen un ID(hash) y son parte de la historia. ![flujo de git] (captura.png)

Directorio de trabajo(modificado)
Este es tu carpeta común, con la diferencia que GIT observa tus archivos, y los cataloga en: Untracked: Es decir sin seguimiento, que lo ve pero no tiene una versión antigua de este archivo, sucede cuando este es creado. Modificado: Es cuando GIT ya tiene una versión previa del archivo y lo modifica, elimina o cambia de nombre. Cualquier archivo que no este en el .gitignore pasa automáticamente a uno de estos estados dependiendo de que hayas hecho.

El comando git log- oneline sirve para mostrar el commit resumido -EL comando git recovery , sirve para volver el archivo a su estado original, Esto borra fisicamente lo que escribimos
Si queremos que el archivo que creamos git lo ignore, creamos el archivo .gitignore y dentro escribimos los nombres de los archivos a ignorar
Área del escenario (Preparado)
Permite seleccionar qué archivos modificados se incluirán en el siguiente commit(guardado) y cuáles no. Para traer un archivo al stage area se debe realizar lo siguiente: -git add: Agrega el archivo , lo hace uno por uno

git agregar. agrega todos los archivos observados por git Si quieres sacar un archivo del stage area para volver al estado anterior: git restaurar --staged
Repositorio Local(confirmado)
Esta es la última fase, aquí es donde le decimos al repositorio que cree el punto de guardado para que todos los cambios que están en stage pasen a ser parte del historial git commit -m "mensaje"

git reset --soft Head ~1 es para deshacer el último commit(usarlo con precaución)
Buenas prácticas
¿Cada cuanto debería hacer un commit?
Aquí usaremos los commits atómicos. Son una práctica en Git donde cada confirmación (commit) representa un único cambio lógico, pequeño y completo en el código fuente. Un menudo. Es mejor hacer commits pequeños, agrupando pequeñas mejoras o acciones, que un commit con todo lo que se quiere hacer. Hacer commit a menudo no significa que debas hacer commits sin sentido. Graba tus progresos en iteraciones pequeñas pero que tengan un significado y que, si puede ser, no deje tu aplicación o proyecto sin funcionar. ##Escribe buenos commits Un commit debe describir lo que hace en pocas palabras y de manera simple pero efectiva:

Usa verbos imperativos (Agregar, Cambiar, Corregir, Quitar) Agregar: Significa que se agrega un nuevo archivo. Cambio: Significa que se modifica un archivo existente. Solución: Significa que se arregla un error. Eliminar: Significa que se elimina un archivo existente.
No uses punto final ni puntos suspensivos en tus mensajes Usar puntuación, más allá de las comas, es innecesario a la hora de crear un buen mensaje de commit. Cada carácter cuenta a la hora de describir un cambio, así que no lo desperdicies con puntos git commit -m “Agregar nueva función de búsqueda”. MAL. No utiliza punto final git commit -m “Solucionar un problema con la barra superior…” MAL. No utiliza puntos suspensivos git commit -m “Cambiar el color predeterminado del sistema” BIEN . Usa como máximo 50 caracteres: Sé corto y conciso. Si tienes mucho que explicar es probable que tu commit contenga demasiados cambios. ¿Puedes separarlo en diferentes commits? Pues entonces hazlo.
Usa un prefijo para tus commits para hacer más semánticos Para que el historial sea legible y se sepa más fácilmente lo que se hace se usa este tipo de commits: Escribe buenos commits git commit -m “: <descripción>” Por ejemplo: git commit -m “feat: Add new search feature”
Prefijos
feat: para una nueva característica para el usuario. corrección: para un error que afecta al usuario. perf: para cambios que mejoran el rendimiento del sitio. build: para cambios en el sistema de build, tareas de implementación o instalación. ci: para cambios en la integración continua. docs: para cambios en la documentación. refactor: para refactorización del código como cambios de nombre de variables o funciones. estilo: para cambios de formato, tabulaciones, espacios o puntos y coma, etc; no afecta al usuario. test: para pruebas o refactorización de uno ya existente.

Día 3
Git remoto
git remoto es el comando que nos permite gestionar nuestras conexiones con los repositorios remotos, le dice a GIT local donde enviar o de donde traer la información, algunos comandos utiles son:

git remoto -v(nos permite ver las URL exactas donde apunta nuestro repositorio)
git remoto add (este apodo es el apodo que pusimos a nuestro repositorio remoto), y nos permite vincular nuestro repositorio local con uno en la nube -git remoto set-url "url" (Cambia la url donde apunta nuestro repositorio)
MÚLTIPLES SSH
-Si tenemos mas de una cuenta de Github o necesitamos tener otras cuentas es util tener mas de una llave SSH, pues este nos da acceso a cada cuenta.

Configurar múltiples SSH
Generamos el sshkey en con otro nombre
Creamos un archivo de configuración para que no choquen las claves
Cuenta Personal (la de siempre)
Host github.com Nombre de host github.com Usuario git IdentityFile ~/.ssh/id_ed25519 Host github-miname Nombre de host github.com Usuario git IdentityFile ~/.ssh/id_miname Especificaciones de los parámetros Host: Es el apodo o alias que le pone a la conexión. Es lo que escribes en la terminal después de git@. HostName: Es la dirección real del servidor a donde nos conectamos. Siempre será github.com Usuario: Es el nombre de usuario del sistema remoto. Para GitHub, siempre, siempre es git. IdentityFile: Es la ruta exacta hacia la "escalera" (la llave privada) que quieres usar para ese Host específico. 3. verificamos si funciona ssh -T git@github-miname

Configuraciones locales
Las configuraciones locales se imponen a las globales, y estas solo funcionan para el repositorio en el que se aplica. Para hacer configuraciones locales lo que se debe hacer es lo mismo que en las globales pero sin el flag --global:

git config user.name "Mi nuevo nombre" git config user.email " micorreo@gmail.com "

Git Checkout
Es el comando que nos permite desplazar el HEAD (nuestro puntero o "lector" actual) hacia un punto específico de la historia o una rama distinta.

¿Para qué sirve? Inspeccionar: Ver cómo era el código en un commit antiguo. Restaurar: Recuperar archivos que borramos o cambiamos. Experimentar: Probar cambios sin arruinar la rama principal. Cambiar: Saltarnos de una rama a otra (ej. de main a desarrollo).

El estado "Detached HEAD"
Normalmente, el HEAD apunta a una Rama (que se mueve). En estado desacoplado, el HEAD apunta directamente a un Commit (que es fijo).

¿Que quiere decir? Eres un espectador en el pasado. Puedes ver todo y escribir notas, pero no tienes "cuerpo" (rama). Si te vas al presente sin "encarnar" en una rama, tus cambios se pierden en el vacío.

¿Cómo ir y volver de un compromiso?
Para ir atras debes hacer: git checkout <hash_antiguo> Y para volver al ultimo hash de la rama git checkout

Si hiciste algo aquí (como un commit) desaparece salvo que hagas: git checkout <hash_commit_creado> git checkout -b rama_nueva

⚙️ Jerarquía de Configuración de Git (Git Config Hierarchy)
🧠 ¿Qué es la jerarquía de configuración de Git?
La jerarquía de configuración de Git define dónde se guardan las configuraciones y cuál tiene prioridad cuando existen varias configuraciones al mismo tiempo.

Git utiliza tres niveles de configuración , cada uno con un alcance diferente:

🖥️ Sistema (Sistema)
👤 Global (Usuario)
📁 Local (Repositorio)
Cada nivel puede sobrescribir la configuración del nivel anterior.

🖥️ Sistema de niveles (Sistema)
📌 Descripción
El nivel System afecta a todos los usuarios del sistema operativo.

Este nivel normalmente está configurado por los administradores del sistema .
