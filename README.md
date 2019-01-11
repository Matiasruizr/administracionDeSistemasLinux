# administracionDeSistemasLinux

# Banderas
Todos los comandos pueden usar banderas,
ejemplo 
ls -l (listar hacia abajo)
ls -h (Legible para humanos)
ls -a (Todos los archivos)




|         |       Significado        |                         Definicion                                                     | 
|---------|--------------------------|----------------------------------------------------------------------------------------|
|ls       | Listar                   |Directorios que dependen de mi posición actual                                          |
|ls -sal* | Listar -busca wildcard   |Bjusca todos los directorios que empiezen con sal* puede ser los que terminen con *sal  |
|pwd      | Projet working directori | Donde estoy de mi arbol de directorios                                                 |
|cd       | Change Directory         | Navega entre directorios                                                               |
|~        | Home                     | Con esto podemos obtener urls absolutas para acceder a cualquier lugar                 |
|mkdir    | Make Directory           | Crea una directoio                                                                     |
|touch    | Tocar                    | Si no existe el archivo lo crea, y si exista cambia su fecha de moficiacion a la actual|
| mv      | Move                     | Mueve o cambia de nombre, aclarar *mv archivo.pdf ~/Downloads/*                        |
| rm      | Remove                   | Remueve archivos, con -r elimina directorios                                           |
| cp      | Copy                     |  Copia un archivo                                                                      |
| pushd   | [directorio a guardar]   | Checkpoint de directorio comun a guardar                                               |
| popd    | Regreso a pushd          | regresa a directorio guardado                                                          |
|more     | Vista previa a datos     | Previsualiza archivos de datos o texto (md,text,csv,etc)                               |
| cat     | Datos de archivo         | Muestra todos los datos de archivo (md, txt, csv, etc)                                 |
| tail    | DAtos orden inverso      | Lee archivo, en sistema contrario a cat, osea desde el ultimo al primero               |
| alias   | crea un alias de comando | Ejemplo alias miserver='shh roo@93.298.298.3"                                          |
| top     | todos los procesos       | Lista todos los procesos                                                               |
| kill    | Mata proceso             | -9 Mata desde 0 el proceso kill -9 id                                                  |
| ps      | Proccess                 | Muestra todos los procesos que se están ejecutando y desde donde vienen.               |  
| ps      | Proccess                 | Muestra todos los procesos que se están ejecutando y desde donde vienen.               | 
|find     | Buscar                   | find  [ruta] -name [nombre]                                                            |
|grep     |                          |                                                                                        |
| x > y   | Ejectuable > archivo     | Guarda el resultado de un find, grep, etc  en el archivo > archivo                     |
| wc -l   | cuenta                   | ejemplo wc ls *.jpg | wc -l (Cuenta todos los jpg en el listar                         |
| curl    | Emula un browser         |

# Herramientas de Busqueda 
Buscar cadenas de caracteres

grep -r [ruta] -e [expresion] nos ayuda a encontrar cadenas de caracteres dentro de todos los archivos de la ruta que le demos, con expresiones regulares.

-r: que sea recursivo
-n: numero de linea donde se encuentra la palabra en el archivo
-e: expresion regular
-i: no importa si es mayuscula o minuscula
Ejemplo: grep airports.csv -e "Chile"


Buscar archivos

find [ruta] -name [nombre] busca en base al nombre y la metadata dentro del directorio que le digamos.

-name: el nombre del archivo (*.js devuelve todos los archivos que terminan con .js)
-type: el tipo

Podemos hacer un find en un ls, ejemplo;
ls -lh *.php 
El comando anterior lista todos los archivos de tipo php


Emular un navegador

curl [url] emula un navegador.

> [nombre] descarga el archivo con el nombre que le has dado.
-o [nombre] igual que el anterior
Comprimir archivos

zip [nombre.zip] [archivo a comprimir]: agrega o reemplaza las entradas de un archivo zip de la lista, que puede incluir el nombre especial para comprimir la entrada.

upzip [archivo] descomprime un .zip

-vl no descomprime sino que ve lo que hay adentro
tar es un comando similar a zip, junta varios archivos en uno solo sin comprimirlos. Después se le dicta un algoritmo de compresión, que es zip.

cfz [archivo.tar.gz] junta y comprime
xfz [archivo .tar.gz] descomprime

Entrar como root | su | pedira la clave
Podemos encadenar comandos uno detras de otro con ;


# Streams 
Los streams son una forma de enviar datos a un comando y recibir un output de salida.

STDIN Standard Input. Parametro de entrada.
STDOUT Standard Output. Es la salida por defecto.
STDERR Standard Error. Es la salida en caso suceda un error


##  Ejemplo 1 # usando “>”
Se ha ejecutado un _proceso _X con una entrada (input) y dos salidas (outputs), 1 de resultado exitoso y 2 de control de errores, los tipos de output se llaman 1: STDOUT 2: STDERR, tipos de input STDIN ; luego, ejecución del _proceso _ crea 2 documentos:
php 1-streams.php 1> salidas 2> errores
le proveemos un número para buscar los múltiplos de este
tail -f documento.txt (-f hace seguimiento del documento conforme se modifica o crece)
atrapamos las actualizaciones del proceso leyendo constantemente la salida y error en 2 diferentes terminales:
tail -f salidas
tail -f errores
Para terminar con el _proceso _ o el tail -f que no paran de correr presionamos Ctrl + C

##  Ejemplos 2 # usando “>” y “>>”
ejecución del proceso:
php 1-streams.php >> salidas
solo va a llenar las salidas al documento, los errores van a la terminal del proceso
además va a abrir y continuar el archivo (append, concatenar, modificar)
php 1-streams.php 1>> salidas 2>> errores
modifica los archivos de salida y error agregando nuevos logs
php 1-streams.php > salidayerror.txt 2>&1
ahora crea un documento al que se le pasa la salida (1)
y se le direcciona también el error (2) con ese “2>&1”
como colar el resultado 2 también a donde vaya el 1

## Ejemplo 3 # usando “<”
en el ejemplo tiene un documento de texto “all_schema.sql” con instrucciones para que el mysql las ejecute y cree una base de datos y unas tablas según el esquema que ha diseñado en texto plano y se las va a insertar al programa para que lo aplique, pero con “<” algo así sistemadebasesdedatos < elarchivodeesquema
mysql -u root -p < all_schema.sql
“-u root -p” es para especificar el usuario “-u david” que aplica el cambio y su password “-p” si es que pide contraseña luego de presionar enter
                                 


# Pipe
Nos permite concatenar comandos
ls -l | wc -l: cuantas lineas tiene este
cat [peliculas.csv] | wc -l: nos indica cuantas lineas tiene este archivo.
cat [peliculas.csv] | wc -l | grep [Thriller] wc -l : nos indica cuantas lineas tiene del parametro que estamos buscando.
** cat movies.dat | grep Thriller | awk -F"::" '{printf("%s\n", $3)}’: nos imprime las categorias que contenga Thriller
** cat movies.dat | grep Thriller | awk -F"::" ‘{printf("%s\n", $3)}’ | grep -v Comedy : grep -v evitamos que no nos imprima el parametro que le mandamos.


# Crontab
https://crontab.guru/
crontab permite programar la ejecución de scripts.

-l muestra la lista de crontab
-e editar la tabla crontab. Con esto se pueden agregar más scripts


Columnas:

minuto 0-59
hora 0-23
dia mes 1-31
mes 1-12
dia semana: 0-7 (0 y 7 domingo)
script/comando
Ejemplo 1 para la columna minuto
1 Se ejecuta en el minuto 1
1,10,18 Se ejecuta en el minuto 1, 10 y 18
*/5 Se ejecuta cada 5 minutos
1-10 Se ejecuta los primeros 10 minutos de cada hora
* Se ejecuta cada minuto

Ejemplo 2

*/15 4 * * * script.sh
Ejecuta script.sh

todos los días de la semana
todos los meses
todos los días del mes
a las 4 am
cada 15 minutos
Ejemplo 3

0 3 * * 1 script.sh
Ejecuta script.sh

solo si es lunes
todos los meses
todos los días del mes
a las 3 am
en el minuto cero
Nota: al momento de editar la tabla de crontab, asegurarse que se vea ordenado las columnas.

sudo useradd -m -g Usuarios -G gestion - s /bin/bash usuario


# Añadir usuarios
Para añadir usuarios podemos utilizar el comando useradd

sudo useradd -m -g Usuarios -G gestion - s /bin/bash usuario
* -m: Crear automáticamente la carpeta del usuario el la carpeta /Home/<NombreUsuario>
* -g: grupo principal al que sera agregado
* -G: Grupos secundarios al que pertenecerá.
* -s: Shell que utilizara por defecto el usuario.
* usuario: Nombre del usuario.

# Ejemplo
Crear el usuario Matias.Ruiz perteneciente a los grupos sshd, disk 1, Oracle comentario Matias Ruiz identificador del usuario 2001 
Ruta del home /discos/soporte la cuenta expira el 31-12-2019, contraseña duocadmin,
vigencia de 30 dias y 7 de advertencia.

sudo Matias.Ruiz -m -g sshd, disk 1, Oracle -G gestion - s /bin/bash usuario
