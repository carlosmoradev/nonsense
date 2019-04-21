# Uso de múltiples usuarios en GIT

GIT definitivamente es una herramienta vital para todos los procesos relacionados con desarrollo a todos los niveles.  En nuestros primeros acercamientos a esta herramienta nos conformamos con manejar los comandos básicos en un repositorio  local, pero a medida que vamos avanzando en nuestro proceso de **aprendizaje permanente**.

A medida que vamos avanzando en nuestro proceso, encontramos que pueden presentarse nuevas necesidades, como el caso de necesitar conectarnos a diferentes repositorios con diferentes usuarios.

Personalmente experimenté esta situación hace poco cuando en un curso de desarrollo de la universidad nos solicitaron gestionar un repositorio dedicado exclusivamente a los proyectos del mismo. En la actualidad experimiento una necesidad similar, debido a que necesito separar mis proyectos personales de los laborales.

Para lograr esto, simplemente se requiere crear llaves rsa separadas para autenticar cada usuario segun el servidor git al que se desee conectar.  En este documento se realizará el procedimiento para conectarse a repositorios de GitHub y GitLab, con llaves rsa distintas para cada caso.

## Procedimientos a realizar:

### 1. Generar las llaves SSH.

En este paso simplemente mostraré el proceso de creación de las llaves.  La primera se crea de manera predeterminada con el comando **ssh-keygen -t rsa** con contraseña vacía.

```bash

    $ ssh-keygen -t rsa
    Generating public/private rsa key pair.
    Enter file in which to save the key (/home/personalUser/.ssh/id_rsa): 
    Created directory '/home/personalUser/.ssh'.
    Enter passphrase (empty for no passphrase): 
    Enter same passphrase again: 
    Your identification has been saved in /home/personalUser/.ssh/id_rsa.
    Your public key has been saved in /home/personalUser/.ssh/id_rsa.pub.
    The key fingerprint is:
    SHA256:s6N0OwlTDKjDez98kZRwUGZbTYaQUArv+EYC6sigFwA personalUser@localhost
    The key's randomart image is:
    +---[RSA 2048]----+
    |E   ..o=*o.+o    |
    |.   .oo+oo...    |
    |....  o=..       |
    | o+. o  =        |
    |o .oo ooS.       |
    |* ...+o oo       |
    |oo.. o+o+o       |
    | .   o+o+o       |
    |      .o..       |
    +----[SHA256]-----+

```

La salida del comando indica que el directorio del usuario se crearon las llaves privada (id_rsa) y pública (id_rsa.pub), la cual es **la única** que se debe compartir (por eso es pública).



```bash

    ssh-keygen -t rsa -C "user@companydomain.net"
    Generating public/private rsa key pair.
    Enter file in which to save the key (/home/personalUser/.ssh/id_rsa): /home/personalUser/.ssh/id_rsa-workAccount  
    Enter passphrase (empty for no passphrase): 
    Enter same passphrase again: 
    Your identification has been saved in /home/personalUser/.ssh/id_rsa-workAccount.
    Your public key has been saved in /home/personalUser/.ssh/id_rsa-workAccount.pub.
    The key fingerprint is:
    SHA256:WTAF6lV8a3FyMdMp3yW4h4NjsrKqXxy0i9JVp1/8gzk user@companydomain.net
    The key's randomart image is:
    +---[RSA 2048]----+
    |        ++o  .+o.|
    |       . +. =.++o|
    |      o o oo Oo.o|
    |     o +.=+.* ...|
    |      = S+ ooo   |
    |   . +.o.. . +   |
    |  . o +o  . E o  |
    |   . ..      . . |
    |  .oo.           |
    +----[SHA256]-----+

```

### 2. Agregar las llaves SSH a cada servicio GIT al que se desea conectar.

### 3. Crear un archivo de configuración para SSH.

### 4. Clonar el repositorio para que se autentique según el usuario requerido.

