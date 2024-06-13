# ansible-bootstrap
For installing all development tools onto a fresh machine

## Running

* `apt install ansible`
* `cd playbooks`
* `sudo ls`
* `ansible-playbook playbook.yaml -v`
* Logout of the desktop and log back in to pickup default shell changes.

## What does it install 

* Docker desktop (you can enable k8s in it after) 
* oh-my-zsh (and makes `zsh` the default shell
* openjdk 18 for software (IDEs) dependent on Java.

### Optional software

Optionally we can also install the development kits for various languages:

* Python with poetry and pyenv
* JS/TS with nodejs
* Rust
