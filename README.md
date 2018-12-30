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
