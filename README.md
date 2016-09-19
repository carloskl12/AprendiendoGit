
Anotaciones realizadas luego de seguir el [tutorial de git](https://git-scm.com/book/es/v1)

#Crear un proyecto
Para crear un proyecto nuevo:

			$ git init <nombre del proyecto>

Si se desea empezar un proyecto en un directorio existente, se debe ingresar al
directorio y utilizar:

			$ git init

Si se desea partir de un proyecto ya existente:

			$ git clone git://github.com/schacon/grit.git

Lo cual genera un directorio grit, donde estará el proyecto, en cambio si se desea
que el nombre del directorio sea diferente al original se lo agrega al final así:

			$ git clone git://github.com/schacon/grit.git Mygrit

Lo cual genera el proyecto en un directorio Mygrit.

##Estado de los archivos
 
			$ git status

Permite ver el estado de los archivos, ya sean bajo seguimiento (tracked),
o sin seguimiento (untracked). Si el archivo esta actualizado no se muestra en la
lista dada por status.

##Seguimiento de archivos

			$ git add miArchivo

Agrega a miArchivo bajo seguimiento, y aparecerá como preparado para la próximo
commit.

Si un archivo se modifica luego de agregarse bajo seguimiento este quedará en los
dos estados, pues hay dos versiones del mismo, una cuando se agregó a seguimiento
y la otra es la que está acualmente en el directorio, si se hace un commit se 
tendrá en cuenta el archivo en su versión al momento de usar ```git add```.

##Ignorando archivos
Para que git ignore ciertos archivos o directorios se utiliza el archivo .gitignore
que incluye las expresiones de patrones a ignorar. Por ejemplo *.o *~ pueden ser
algunos (ficheros objeto, temporales).

			# Un comentario – esto es ignorado
			# ignora los archivos *.a
			*.a
			# Excepto lib.a, incluso si se decidió ignorar *.a luego
			!lib.a
			# only ignore the root TODO file, not subdir/TODO
			/TODO
			# ignore all files in the build/ directory
			build/
			# ignore doc/notes.txt, but not doc/server/arch.txt
			doc/*.txt
			# ignore all .txt files in the doc/ directory
			doc/**/*.txt

##Viendo cambios preparados y no preparados
Para saber exactamente que se ha modificado entre los archivos preparados y los no
preparados existe :

			$ git diff

Para finalizar la revisión de información agregada teclear (q)

Para ver las diferencias entre los archivos preparados con los del proyecto en la
última confirmación se usa:

			$ git diff --staged

##Confirmando los cambios (commit)

			$ git commit -m "Cambios realizados"

##Saltándose el area de preparación

			$ git commit -a -m 'Agregados los cambios directamente'

Esta manera confirma todo archivo en seguimiento de la última confirmación, sin
estar necesariamente en seguimiento.

##Eliminar un archivo
Se debe eliminar de los archivos bajo seguimiento (eliminarlo del área de 
preparación), y despues confirmar. ```git rm``` se encarga de esto.
Si el archivo estaba preparado y luego se desea eliminar, se agrega la opción ```-f```.

			$ git rm log/\*.log


Tambien se acepta patrones y archivos a eliminar. Para eliminar solamente del
seguimiento se usa la opción ```--cached```


##Moviendo archivos

			$ git mv README.txt README

Renombra el archivo, equivale a:

			$ mv README.txt README
			$ git rm README.txt
			$ git add README

##Viendo el histórico de cofirmaciones

			$ git log

Permite ver el histórico de confirmaciones.


##Deshaciendo cosas

			$ git commit --amend -m "Documentos iniciales"

Modifica la ultima confirmación, si no se ha modificado ningún archivo que 
está en seguimiento, significa que cambiará solo el mensaje de confirmación.

##Deshaciendo la preparación de un archivo
Muchas veces se preparan varios archivos, pero para confirmarlos se desea indicar
que son cambios separados, para ello habrá que retirar el archivo del área de
preparación:

			$ git reset HEAD miArchivo

Usando ```git status``` se puede ver esto como sugerencia.

##Deshaciendo la modificación de un archivo
Si un archivo aparece como modificado (```git status```), para volverlo al estado 
de la última confirmación se utiliza:

			$ git checkout -- Archivo.txt


#Trabajando con repositorios remotos
Para ver los repositorios remotos configurados se usa ```git remote```, o con 
la opción ```-v```, para ver la url.

##Añadiendo repositorios remotos 
			$ git remote add [nombre] [url]

El nombre es una forma de evitar escribir el url del repositorio remoto.
Para recuperar toda la información de un repositorio remoto que aún no tiene
el proyecto, se usa:

			$ git fetch [remote-name]

fetch solo recupera la información, y la pone en el repositorio local, no la 
une con el trabajo, ni modifica en lo que está trabajando, esto se debe hacer 
manualmente. Para unir la rama remota con la actual que se está trabajando,
se usa ```git pull```

##Enviando al repositorio remoto
			$ git push [remote-name] [branch-name]
			$ git push origin master

Si el repositorio remoto fue modificado, y la versión de la rama que actualizamos
está antes de la modificación no realizada por nosotros, para poder enviar la 
información debemos descargar la última actualización, y ajustar las modificaciones.

##Inspeccionando un repositorio remoto 
			$ git remote show [nombre]

Muestra la información de un repositorio remoto en particular.

##Eliminando y renombrando repositorios remotos 
			$ git remote rename nombre nuevoNombre
			$ git remote rm  referenciaAEliminar

##Creando etiquetas
Un tag se usa para identificar puntos específicos que son importantes en la historia
del proyecto. Para listar las etiquetas se usa ```git tag```. También se pueden
hacer busquedas acorde a patrones
			$ git tag -l 'v1.4.2.*'

Existen dos tipos de etiquetas, una simple y una anotada (incluye mas detalles).
Para una etiqueta anotada:

			$ git tag -a v1.4 -m 'Mi versión 1.4'

Para ver los datos de la etiqueta se puede usar git show.

			$ git show v1.4

Para una etiqueta firmada usando GPG, en vez de ```-a``` se usa ```-s```, para ello se 
requiere tener disponible una clave privada.


