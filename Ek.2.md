# Configuración de la estación de trabajo

- Instalar Windows Terminal
- Instalar la versión más reciente de [OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)
- Crear clave con `ssh-keygen`
- Agregar clave SSH pública a GitHub y Bitbucket
- En Bitbucket, crear un _app password_
- Crear repositorio `dotfiles` con archivo `.gitconfig` en la cuenta de GitHub del nuevo usuario
- En el repositorio `development_server_setup`, agregar al nuevo usuario en el playbook de Ansible [`setup_users.yml`](https://github.com/IslasGECI/development_server_setup/blob/develop/ansible/setup_users.yml)
- Crear [`~/.ssh/config`](#sshconfig)
- Crear la bóveda de los secretos con las variables necesarias
- Instalar `geci-testmake`
- Crear un alias para iniciar sesión, [por ejemplo](#aliases)
- En Bitbucket otorgar privilegios a repos:
    - `hola`
    - El repo clase 3 correspondiente
    - El repo de datos correspondiente


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

### aliases
     
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
