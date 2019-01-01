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
 
Entrar como root | su | pedira la clave


# Streams 

Inputs. Entrada de datos al programa
Output. Salida de datos al usuario
Buenas prácticas: guardar mensajes de errores en algún lado, no ignorarlos.

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
