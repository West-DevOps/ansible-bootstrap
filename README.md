# ansible-bootstrap
For installing all development tools onto a fresh machin
## Running

* `apt install ansible`
* `sudo ls`
* `ansible-playbook playbook.yaml -v`
* Logout of the desktop and log back in to pickup default shell changes.

## What does it install 

* Docker desktop (you can enable k8s in it after) 
* oh-my-zsh (and makes `zsh` the default shell)
* curl and other net-tooling


### Optional software

Optionally we can also install the development kits for various languages:

* Python with `poetry` and `pyenv`
* JS/TS with `nodejs` / `nvm`
* Rust with `cargo`
* Java `openjdk-21-jdk`

Single languages can be enabled with the `install_*` variables or the catch all `install_all` for a complete install of all languages this playbook can provide e.g: 

`ansible-playbook playbook.yaml -v -e install_all=true`

## Post run 
This installer installs `nvm` and `pyenv` for dealing with python and node installs. 
Therefore, after the run it is up to you to install the desired versions of node/python as you
see fit.

### Install desired versions of node
Install a version of nodejs via `nvm`:

`nvm install 20` or `nvm install 22` etc.

### Install desired versions of python
Ubuntu `22.04 LTS` ships with python `3.10` which is nice but `3.12` is out so we can install it
with `pyenv`:

`pyenv install 3.12`


