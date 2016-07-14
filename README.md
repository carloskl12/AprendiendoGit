
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

## Estado de los archivos
 
			$ git status

Permite ver el estado de los archivos, ya sean bajo seguimiento (tracked),
o sin seguimiento (untracked). Si el archivo esta actualizado no se muestra en la
lista dada por status.

## Seguimiento de archivos

			$ git add miArchivo

Agrega a miArchivo bajo seguimiento, y aparecerá como preparado para la próximo
commit.

Si un archivo se modifica luego de agregarse bajo seguimiento este quedará en los
dos estados, pues hay dos versiones del mismo, una cuando se agregó a seguimiento
y la otra es la que está acualmente en el directorio, si se hace un commit se 
tendrá en cuenta el archivo en su versión al momento de usar ```git add```.

## Ignorando archivos
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

## Viendo cambios preparado y no preparados
Para saber exactamente que se ha modificado entre los archivos preparados y los no
preparados existe :

			$ git diff

Para finalizar la revisión de información agregada teclear (q)

Para ver las diferencias entre los archivos preparados con los del proyecto en la
última confiración se usa:

			$ git diff --staged
