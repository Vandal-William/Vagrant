# Les commandes de base

## Pour voire toute les commandes disponible:

```shell
vagrant list-commands
```

```shell
Below is a listing of all available Vagrant commands and a brief
description of what they do.

autocomplete    manages autocomplete installation on host
box             manages boxes: installation, removal, etc.
cap             checks and executes capability
cloud           manages everything related to Vagrant Cloud
destroy         stops and deletes all traces of the vagrant machine
docker-exec     attach to an already-running docker container
docker-logs     outputs the logs from the Docker container
docker-run      run a one-off command in the context of a container
global-status   outputs status Vagrant environments for this user
halt            stops the vagrant machine
help            shows the help for a subcommand
init            initializes a new Vagrant environment by creating a Vagrantfile
list-commands   outputs all available Vagrant subcommands, even non-primary ones
login
package         packages a running vagrant environment into a box
plugin          manages plugins: install, uninstall, update, etc.
port            displays information about guest port mappings
powershell      connects to machine via powershell remoting
provider        show provider for this environment
provision       provisions the vagrant machine
push            deploys code in this environment to a configured destination
rdp             connects to machine via RDP
reload          restarts vagrant machine, loads new Vagrantfile configuration
resume          resume a suspended vagrant machine
rsync           syncs rsync synced folders to remote machine
rsync-auto      syncs rsync synced folders automatically when files change
serve           start Vagrant server
snapshot        manages snapshots: saving, restoring, etc.
ssh             connects to machine via SSH
ssh-config      outputs OpenSSH valid configuration to connect to the machine
status          outputs status of the vagrant machine
suspend         suspends the machine
up              starts and provisions the vagrant environment
upload          upload to machine via communicator
validate        validates the Vagrantfile
version         prints current and latest Vagrant version
winrm           executes commands on a machine via WinRM
winrm-config    outputs WinRM configuration to connect to the machine

```

```shell
vagrant global-status
```

```shell
id       name   provider state  directory
--------------------------------------------------------------------
There are no active Vagrant environments on this computer! Or,
you haven't destroyed and recreated Vagrant environments that were
started with an older version of Vagrant.

```

```shell
vagrant global-status -help
```

```shell
Usage: vagrant global-status

        --prune                      Prune invalid entries.
        --[no-]color                 Enable or disable color output
        --machine-readable           Enable machine readable output
    -v, --version                    Display Vagrant version
        --debug                      Enable debug output
        --timestamp                  Enable timestamps on log output
        --debug-timestamp            Enable debug output with timestamps
        --no-tty                     Enable non-interactive output
    -h, --help                       Print this help

```

## 1.Initialiser un projet vagrant

```shell
vagrant init ubuntu/trusty64
```

La commande init est suivie d'un système d'exploitation a installer.
cette etape va créer un Vagrantfile a la racine du répertoire ou l'on se trouve.

## 2.Lancer vagrant

```shell
vagrant up
```

Apres avoir initialiser le projet ont lance vagrant.
Cette étape ajoute une boxe dans virtualbox et y installe l'image ubuntu/trusty64
il génère une clée et une adresse ssh, définir le port du serveur, créer un utilisateur
et enfin générer un dossier .vagrant

```shell
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Box 'ubuntu/trusty64' could not be found. Attempting to find and install...
    default: Box Provider: virtualbox
    default: Box Version: >= 0
==> default: Loading metadata for box 'ubuntu/trusty64'
    default: URL: https://vagrantcloud.com/ubuntu/trusty64
==> default: Adding box 'ubuntu/trusty64' (v20190514.0.0) for provider: virtualbox
    default: Downloading: https://vagrantcloud.com/ubuntu/boxes/trusty64/versions/20190514.0.0/providers/virtualbox.box
Download redirected to host: cloud-images.ubuntu.com
==> default: Successfully added box 'ubuntu/trusty64' (v20190514.0.0) for 'virtualbox'!
==> default: Importing base box 'ubuntu/trusty64'...
==> default: Matching MAC address for NAT networking...
==> default: Checking if box 'ubuntu/trusty64' version '20190514.0.0' is up to date...
==> default: Setting the name of the VM: lab-1_default_1678890977366_8718
==> default: Clearing any previously set forwarded ports...
Vagrant is currently configured to create VirtualBox synced folders with
the `SharedFoldersEnableSymlinksCreate` option enabled. If the Vagrant
guest is not trusted, you may want to disable this option. For more
information on this option, please refer to the VirtualBox manual:

  https://www.virtualbox.org/manual/ch04.html#sharedfolders

This option can be disabled globally with an environment variable:

  VAGRANT_DISABLE_VBOXSYMLINKCREATE=1

or on a per folder basis within the Vagrantfile:

  config.vm.synced_folder '/host/path', '/guest/path', SharedFoldersEnableSymlinksCreate: false
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: Forwarding ports...
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default:
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default:
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
    default: The guest additions on this VM do not match the installed version of
    default: VirtualBox! In most cases this is fine, but in rare cases it can
    default: prevent things such as shared folders from working properly. If you see
    default: shared folder errors, please make sure the guest additions within the
    default: virtual machine match the version of VirtualBox you have installed on
    default: your host and reload your VM.
    default:
    default: Guest Additions Version: 4.3.40
    default: VirtualBox Version: 6.1
==> default: Mounting shared folders...
    default: /vagrant => /home/william/Bureau/Vagrant/exercices/lab-1
```

## Vérifier que la vm est bien lancer

```shell
vagrant status
```

```shell
Current machine states:

default                   running (virtualbox)

The VM is running. To stop this VM, you can run `vagrant halt` to
shut it down forcefully, or you can run `vagrant suspend` to simply
suspend the virtual machine. In either case, to restart it again,
simply run `vagrant up`.
```

## Ce connecter en ssh sur la VM

```shell
vagrant ssh
```

vagrant gère lui meme la connection
Un mot de passe par défaut est donner: vagrant

## Pour provisionner la VM

```shell
vagrant provision
```

## Pour supprimer la VM

```shell
vagrant destroy
```

## Pour arreter la VM

```shell
vagrant halt
```

## Pour suspendre la VM

```shell
vagrant suspend
```
