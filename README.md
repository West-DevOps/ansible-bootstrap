# ansible-bootstrap
For installing the `West-DevOps` development toolbag onto a fresh ubuntu machine.

It installs a few things "by default" and has variables to enable language specific dev envs. Docker desktop is installed by default so you can develop any language in containers and not bother installing any runtimes locally if you wish!

## Running

From a completely fresh install of Ubuntu, grab the repo and `cd` into it; then run:

* `apt install ansible` to install ansible
* `sudo ls` to cache sudo privs for the ansible run 
* `ansible-playbook playbook.yaml -v -e install_all=true` for a full install or...
* `ansible-playbook playbook.yaml -v` for a more minimal docker and tools only install. 
* Logout of the desktop and log back in to pickup default shell changes and `PATH` additions etc.

## What does it do? 

Installs a "sensible base" for any kind of development, no IDE, no language specific compilers or anything. Just this:

* Docker desktop (you can enable k8s in it after) 
* The holy `oh-my-zsh` and sets plugins (and makes `zsh` the default shell)
* `curl` and other net-tooling
* `git`, `gnupg2`, `jq`, `sshd` and various other tools found on development machines

### Optional software

Optionally we can also install language specific development kits "on the machine":

* `Python` with `poetry` and `pyenv`
* `JS`/`TS` with `nodejs` and `nvm`
* `Rust` with `cargo`
* `Java - openjdk-21-jdk`
* K8s toolbag (`helm`, `kubectl`, `k9s` etc.)

Single languages can be enabled with the `install_*` variables found in `playbook.yaml` or use the catch all `install_all` variable for a complete install of all languages this playbook can provide e.g: 

For vscode and python:

`ansible-playbook playbook.yaml -v -e install_python=true -e install_vscode=true`

For every language supported by the playbook:

`ansible-playbook playbook.yaml -v -e install_all=true`

## Post run 
This installer installs `nvm` and `pyenv` for dealing with nodejs and python installs. 
Therefore, after the run it is up to you to install the desired versions of node/python as you
see fit.

### Install desired versions of node
Install a version of nodejs via `nvm`:

`nvm install 20` or `nvm install 22` etc.

### Install desired versions of python
Ubuntu `22.04 LTS` ships with python `3.10` which is nice but `3.12` is out so we can install it
with `pyenv`:

* `pyenv install 3.12` # Grab latest patch of 3.12 (`3.12.4` at time of writing)
* `pyenv global 3.12`  # Make it default for you. 

It might warn about tkinter but don't worry it still installs the version. 

## Contributing

New features are always welcome, if it's for a specific development need; try and gate it with a top-level `install_<something>` variable.  Other than
that go nuts and get a PR in! 
