# 🛠️👩🏿‍💻 Configuración de la estación de trabajo
## 💻 En tu computadora personal
- Instalar Windows Terminal
- Instalar la versión más reciente de [OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)
- Crear clave con el comando `ssh-keygen`
- Crear [`~/.ssh/config`](#sshconfig)
- Con la ayuda de tu analista de confianza, crear la bóveda de los secretos con las variables necesarias
- Crear un alias para iniciar sesión, como en [este ejemplo](#alias)
## ☁️ En la nube
- Agregar clave SSH pública a [GitHub](https://github.com/settings/keys) y [Bitbucket](https://bitbucket.org/account/settings/ssh-keys/)
- En Bitbucket, crear un [_app password_](https://bitbucket.org/account/settings/app-passwords/)
- Con la guía de tu analista más cercano, crear repositorio `dotfiles` con los archivos `.gitconfig` y `Makefile` en tu cuenta personal de GitHub
- Solicitar agregar tu usuario de GitHub en el playbook de Ansible [`setup_users.yml`](https://github.com/IslasGECI/development_server_setup/blob/develop/ansible/setup_users.yml)
- Pedir privilegios de Bitbucket para los repositorios:
    - `hola`
    - El repositorio clase 3 correspondiente
    - El repositorio de datos correspondiente

---

## Notas
### `~/.ssh/config`
```
Host devserver
  ForwardAgent yes
  HostName islasgeci.dev
  ServerAliveCountMax 10
  ServerAliveInterval 60
  User <USERNAME>
```

### Alias
     
Linux:
```
ssh-keygen -f "$HOME/.ssh/known_hosts" -R "islasgeci.dev"
ssh-keyscan "islasgeci.dev" >> "$HOME/.ssh/known_hosts"
scp -pr ~/.vault <USERNAME>@islasgeci.dev:/home/<USERNAME>/.vault
ssh devserver
```

Windows:
```
ssh-keygen -f ".ssh/known_hosts" -R "islasgeci.dev"
ssh-keyscan "islasgeci.dev" >> "$HOME/.ssh/known_hosts"
scp -pr .vault <USERNAME>@islasgeci.dev:/home/<USERNAME>/.vault
ssh -o ForwardAgent=yes <USERNAME>@islasgeci.dev
```
