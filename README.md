# administracionDeSistemasLinux

Consultar posicion actual
 ls
 
Moverse a un directorio 
 cd ruta/directorio
 
Crear un directorio
  mkdir nombre_directorio

Mover un directorio
  mv img files/images
  
Copiar un directorio
 cp archivo ruta/archivo
 
 
Entrar como root | su | pedira la clave


hostnamectl set-hostname your-new-hostname

Agregar desde controlador sagta
Configuracion > almacenamiento > mas

  Elegir cuanto debe ser el maximo
  Luego debe ser dinamico

fdisk -l para listar todos los discos
fdisk ruta del disco


n

p

1

lsblk


Luego lo mismo 

n

e

1
Valor primario 'Enter'
Ultimo valor 'Enter'

n

l

+10G


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
