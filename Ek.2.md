# Configuración de la estación de trabajo

- Instalar Windows Terminal
- Instalar la versión más reciente de [OpenSSH](https://github.com/PowerShell/Win32-OpenSSH/releases)
- Crear clave con `ssh-keygen`
- Agregar clave SSH pública a GitHub y Bitbucket
- En Bitbucket, crear un _app password_
- Crear repo `dotfiles` con archivo `.gitconfig`
- Agregar al nuevo usuario en el playbook [`setup_users.yml`](https://github.com/IslasGECI/development_server_setup/blob/develop/ansible/setup_users.yml) de Ansible en el repo `development_server_setup`
- En `~/.profile` hacer `source ~/.vault/.secrets`
- Crear `~/.ssh/config`
- Agregar las siguientes variables a `~/.vault/.secrets`:
    - `TABLERO_API_SECRET_KEY`
    - `BITBUCKET_USERNAME`
    - `BITBUCKET_PASSWORD`
- Instalar `geci-testmake`
- Crear algo similar al ejemplo `dev-init` de abajo
- En Bitbucket otorgar privilegios a repos:
    - `hola`
    - El repo clase 3 correspondiente
    - El repo de datos correspondiente

---

`~/.vault/.secret`

```
export BITBUCKET_PASSWORD=<BITBUCKET APP PASSWORD>
export BITBUCKET_USERNAME=***
export TABLERO_API_SECRET_KEY=***
```

---


`~/.ssh/config`

```
Host devserver
  ForwardAgent yes
  HostName islasgeci.dev
  ServerAliveCountMax 10
  ServerAliveInterval 60
  User siduartep
```

---

`dev-init`

Linux:
```
ssh-keygen -f "$HOME/.ssh/known_hosts" -R "islasgeci.dev
"ssh-keyscan "islasgeci.dev" >> "$HOME/.ssh/known_hosts"
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
