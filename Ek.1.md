## 👩🏿‍💻 Crear provisionador en Azure
- Usamos las características por defecto del servicio de MV en Azure.
- Agregamos la clave pública de un miembro del equipo. 
- Usuario: `ciencia_datos`
- Nombre de computadora: `provisioner`

## 🐋 Instalar Docker en el servidor
- Instalamos `docker` en el provisionador:
```bash
sudo apt update && sudo apt full-upgrade --yes
sudo apt install docker.io
``` 
- Agregamos el grupo `docker` al usuario:
```bash
sudo usermod -aG docker $USER
sudo reboot
```
## 🛂 Administrar las credenciales
- 🔐🧐🚨Creamos la bóveda de los secretos con las variables necesarias.
- En la máquina virtual agregamos una _clave ssh_ para el usuario `ciencia_datos`:
```bash
ssh-keygen
```
## ⏳ Programar los cronjobs para cada servidor
- Verificamos que el horario del servidor sea el de Ensenada (el ombligo del universo):
```
ls -l /etc/localtime
timedatectl
timedatectl set America/Los_Angeles
```
- Copiamos el crontab del repositorio [`provisioner`](https://github.com/IslasGECI/provisioner/blob/develop/src/Cronfile)