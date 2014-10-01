¿Cómo usar Git?: guía rápida
============================

> última edición 01-oct'14

__Git__ es un software para control de versiones, que resulta especialmente práctico para la generación colaborativa de contenido, tal como es nuestro caso. Gracias a Git, los procesos de creación, edición, revisión y corrección de contenido se tornan más fáciles y requieren menor tiempo al establecer un protocolo claro para cada uno de los actores involucrados.

En las siguientes secciónes se muestran &mdash;en formato de preguntas y respuestas&mdash; una serie de comandos de Git que son suficientes para realizar la mayoría de las operaciones de interés en Git.

Te __recomiendo__ que te mantengas al pendiente de los cambios en este archivo, pués con el tiempo pretendo agregar algunas funciones para tareas muy específicas que te pueden resultar de utilidad.

##### Configuración inicial de Git
Antes de comenzar a trabajar con un repositorio, es necesario que realices la configuración básica de Git, de esta forma el sistema podrá saber la identidad de quien genera las aportaciones. Sols comando que debes ejecutar son:
```
git config --global user.name "Tu nombre"
git config --global user.email tumail@algo.com
```

## ¿Que es un repositorio de git?
Un __repositorio (repo)__ es un directorio que se compone de una base de datos y un conjunto de instantaes de tus archivos, en él se alamacena una historia completa del proyecto, de forma que siempre es posible regresar a puntos específicos del mismo. Cada uno de dichos puntos se denomina __confirmación (commit)__. Las confirmaciones son el concepto clave de Git, pues una vez que una serie de cambios ha sido confirmada, pasa a formar parte del repositorio, creando una especie de resaldo que mantendrá seguros tus datos &mdash;o en este caso, tus avances.

Puedes identificar el repositorio como un directorio llamado __.git__ en tu sistema de archivos. Para manipularlo debes ejecutar los comandos válidos desde la ++terminal++ &mdash;o en _gitbash_ si trabajas con windows&mdash; posicionado al mismo nivel que el directorio .git

## ¿Cómo consigo un repositorio?
Puedes conseguir un repositorio Git de dos formas:  
* __creandolo desde cero__. Cuando eres tú quien iniciará y manerajá el repositorio;
* __clonando__ un repositorio existente. Cuando participarás en el desarrollo de un repositorio existente, generalmente alojado en un servidor remoto;

##### Crendo un repositorio 
```
mkdir mi_proyecto
cd mi_proyecto
git init
```
Ahora tienes un nuevo repositorio dentro del directorio ___mi_proyecto___, puedes ++conectarlo con un servidor remoto++ para generar una versión disponible desde cualquier equipo utilizando el siguiente comando:

```
git remote add origin <url del servidor remoto de destino>
```

##### Clonando un repositorio
```
git clone <url del repo>
```
Tras ejecutar el comando anterior tendrás un nuevo directorio con el nombre del repositorio clonado, que incluye una copia de trabajo de los archivos que integran el reposiorio, así como el repositorio (.git) propiamente.

## ¿Cómo confirmo mis aportaciones?
Git trabaja con __ramas__, que no son más que caminos de desarrollo que transcurren de forma paralela y que se pueden entrecruzar para aprovechar los avances de unos en otros. De forma predefinida, la rama en que se agregan tus aportes es la rama __master__. Si no se especifica otra cosa, todos tus commits se agregarán allí.

El __modelo__ bajo el que trabaja Git contempla tres estados para un archivo:  
* __modificado__: el archivo presenta cambios en su contenido, posteriores a la última confirmación;
* __preparado__: el proceso de preparación consiste en tomar una "instantanea" del estado actual de los archivos modificados, consiguiendo así un registro puntual del proyecto en un momento dado;
* __confirmado__: cuando la "instantanea" de un achivo preparado se inserta en la base de datos del repositorio, se considera el archivo como confirmado. A partir de este punto el contenido formará parte de la historia del repositorio.

La secuencia de comandos para transformar tus modificaciones en un punto de la historia del proyecto &mdash;haciendo que cada archivo pase por los estados antes decritos&mdash; es:
```
%%% visualizar el estado de los archivos
git status
%%% preparar todos los archivos que han sufrido modificaciones
git add -A
%%% confimar los cambios
git commit -m 'mensaje que describa los cambios o contribuciones'
%%% visualizar la nueva confirmación en el histórico del proyecto
git log --graph --all
```

## ¿Cómo subo las nuevas confirmaciones al servidor remoto?
Las confimaciones que realizaste en el paso anterior estan solamente en tu máquina, para ponerlas a disposición de todos los colaboradores del proyecto, es necesario que las envíes al servidor remoto. Esto lo puedes lograr con:
```
git push origin <nombre de la rama>
```
si la rama en la que confirmaste tu contribución es __master__ el comando sería:
```
git push origin master
```
finalmente el sistema te pedirá ts datos de acceso a la cuenta del servidor.

## ¿Cómo consigo los últimos cambios del repositorio remoto?
> Es recomendable que antes de comenzar cada sesión de trabajo, y tras realizar las confirmaciones correspondientes, actualices el contenido de tu repositorio

Para descargar a tu repositorio local los últimos datos agregados al repositorio remoto, es decir, aquellas contribuciones del resto de colaboradores, simplemente ejecuta:
```
git pull
```
finalmente el sistema te pedirá ts datos de acceso a la cuenta del servidor.