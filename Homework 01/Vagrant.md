# Homework 01
# Julio César González Araya
# ISW-811-02-SCIII24

![Cabezera](./images/photo_2024-09-19_21-35-24.jpg)


##  Proceso de instalación de Vagrant y Virtual Box

###  En los siguientes pasos se mostrar como se tiene que instalar Vagrant y Virtual Box desde GNU/Linux Debian 12 Bookworm
#### Se navega al sitio de Oracle [Virtual Box](https://www.virtualbox.org/) para ver la documentación en GNU/Linux

- Se procede a importa la clave GPG de Oracle:
```bash
    wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | gpg --dearmor
    | sudo tee /usr/share/keyrings/oracle-vbox-2016.gpg > /dev/null
```
- Añade el repositorio de VirtualBox (reemplaza **$(lsb_release -cs)** por tu versión de Debian si es necesario):
```bash
    echo "deb [arch=amd64 signed-by=/usr/share/keyrings/oracle-vbox-2016.gpg]
    https://download.virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib" | sudo
    tee /etc/apt/sources.list.d/virtualbox.list
```
- Luego se genera el siguiente comando, se actualiza y luego se instala:
```bash
    sudo apt update
    sudo apt install virtualbox-7.0
```
- Se verifica si el fue instalado correctamente
```bash
    virtualbox --help
```
#### Ahora se navega ahora en el sitio de [Vagrant](https://www.vagrantup.com/) para ver la documentación en GNU/Linux
- Se importa la clave GPG de HashiCorp:
```bash
    curl -fsSL https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee
    /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null
```
- Luego se añade el repositorio:
```bash
    echo "deb [arch=amd64 signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg]
    https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee
    /etc/apt/sources.list.d/hashicorp.list
```
- Luego se genera el siguiente comando, se actualiza y luego se instala:
```bash
    sudo apt update
    sudo apt install vagrant
```
- Procedemos a verificar si la instalación se hiso de manera correcta
```bash
    vagrant --help
```
## Aprovisionamiento de la Instancia de GNU/Linux Debian Bookworm 64 Bits

### Crear un archivo de configuración Vagrant

- En la terminal creamos los directorios donde colocaremos la configuración
```bash
    mkdir vagrant_directorio
    cd vagrant_directorio
```
- Se inicializa Vagrant
```bash
    vagrant init debian/bookworm64
```
- Procede a iniciar la maquina virtual
```bash
    vagrant up
```
- Ahora nos fijamos su estatus si esta funcionando todo correctamente:
```bash
    vagrant status
```
- Procedemos a hacer la conección a la máquina virtual:
```bash
    vagrant ssh
``` 
Para cerrar vagrant procedemos con el siguiente comando:
```bash
    vagrant halt  # Detener la VM
    vagrant destroy  # Destruir la VM
``` 
## Opcional
##### En caso de no tener un grupo relacionado con vbox podemos usar el siguiente comando
```bash
    cat /etc/group | grep vox
```
#### Si no lo posee para el user de la maquina Debian se agrega
```bash
    sudo gpasswd -a user vboxusers 
```