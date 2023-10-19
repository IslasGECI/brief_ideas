# 🛠️👩🏿‍💻 Configuración de la estación de trabajo

- Instalar Windows Terminal
- Instalar la versión más reciente de [OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)
- Crear clave con `ssh-keygen`
- Agregar clave SSH pública a [GitHub](https://github.com/settings/keys) y [Bitbucket](https://bitbucket.org/account/settings/ssh-keys/)
- En Bitbucket, crear un [_app password_](https://bitbucket.org/account/settings/app-passwords/)
- Crear repositorio `dotfiles` con archivo `.gitconfig` en tu cuenta personal de GitHub
- En el repositorio `development_server_setup`, agregar tu usuario de GitHub en el playbook de Ansible [`setup_users.yml`](https://github.com/IslasGECI/development_server_setup/blob/develop/ansible/setup_users.yml)
- Crear [`~/.ssh/config`](#sshconfig)
- Crear la bóveda de los secretos en tu computadora personal con las variables necesarias
- Crear un alias para iniciar sesión, [por ejemplo](#aliases)
- Pedir privilegios de Bitbucket para los repositorios:
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


