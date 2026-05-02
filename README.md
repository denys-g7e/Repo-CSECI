Clase 1: Fundamentos e Instalación
¿Qué es Git?
Es un sistema diseñado para el Control de Versiones. Su función principal es actuar como un historial detallado que registra cada modificación en tus archivos, permitiéndote navegar entre versiones pasadas y coordinar el trabajo con otros programadores.
Cronología Clave:
2005: Linus Torvalds lanza Git para administrar el código de Linux.
2008: Nace GitHub (usando Ruby), democratizando el uso de Git.
2018: Microsoft adquiere GitHub, consolidándolo como la plataforma líder.
Primeros Pasos:
Instalación: Se descarga desde git-scm.com.
Identificación: Es vital configurar quién eres con:
git config --global user.name "Nombre"
git config --global user.email "correo@ejemplo.com"
Clase 2: El Ciclo de Vida del Código
Estados de los Archivos:
Modified: Cambios detectados pero no guardados.
Staged: Archivos en la "zona de preparación" para el siguiente guardado.
Committed: Cambios grabados oficialmente en el historial local.
Comandos Esenciales:
Guardar: git add . para preparar y git commit -m "mensaje" para crear el punto de control.
Deshacer: git restore <archivo> para limpiar cambios no deseados.
Ignorar: El archivo .gitignore le dice a Git qué carpetas (como node_modules) o archivos sensibles no debe rastrear jamás.
El arte del Commit:
Un buen commit debe ser corto (máx. 50 caracteres) y descriptivo. Se usan prefijos como feat: (función), fix: (error) o refactor: (limpieza de código) para que el historial sea profesional y fácil de leer.
Clase 3: GitHub y el Trabajo Remoto
¿Qué es GitHub?
Es el servicio de alojamiento en la nube para tus repositorios de Git. Facilita la colaboración y ofrece herramientas de gestión de proyectos.
Seguridad con SSH:
En lugar de usar contraseñas, se usan llaves criptográficas:
Generas la llave en tu terminal (ssh-keygen).
Copias la clave pública (cat ~/.ssh/id_ed25519.pub).
La pegas en la configuración de tu cuenta en GitHub.
Sincronización:
Para bajar un proyecto: git clone <url>.
Para subir un proyecto local a un repo nuevo: git remote add origin <url> seguido de git push -u origin main.
Clase 4: Navegación y Configuración Avanzada
Viajar en el Tiempo:
git log --oneline: Muestra una lista resumida de tus "checkpoints".
git checkout <id>: Te permite "visitar" un commit pasado (estado Detached HEAD).
git reset --hard <id>: Regresa al pasado de forma definitiva (borra lo posterior).
Actualización:
git pull: Descarga y combina los cambios de la nube con tu trabajo local de forma inmediata.
Clase 5: Ramas y Flujo de Trabajo (Gitflow)
¿Qué son las ramas?
Son líneas temporales paralelas. Permiten que un equipo trabaje en funciones distintas sin estorbarse entre sí.
Comandos de Ramas:
git branch <nombre>: Crea la rama.
git switch <nombre>: El comando moderno para cambiar de rama.
git branch -D <nombre>: Elimina una rama que ya no necesitas.
Estructura Gitflow:
Main: El código sagrado que ya funciona para el usuario.
Develop: Donde se junta todo lo que se está probando.
Feature/Hotfix: Ramas específicas para tareas o arreglos urgentes.
Clase 6: Fusión y Sincronización
Merge (La Unión):
git merge <rama> une los cambios de una rama secundaria a la actual. Se recomienda usar --no-ff para que el historial muestre claramente dónde ocurrió la bifurcación.
Fetch vs. Pull:
fetch: Solo te avisa si hay cambios nuevos en la nube.
pull: Trae esos cambios y los mezcla con tu código de una vez.
Clase 7: Pull Requests (PR)
Colaboración Profesional:
Un Pull Request es una solicitud para que el dueño del proyecto revise tus cambios antes de aceptarlos. Es el filtro de calidad definitivo.
¿Por qué usarlos?
Seguridad: Nadie rompe el código principal sin que otro lo vea.
Feedback: El equipo puede comentar y mejorar tu código antes del merge.
Comunidades: Permite colaborar en proyectos de otras personas mediante un Fork (copia propia de un repositorio ajeno).

