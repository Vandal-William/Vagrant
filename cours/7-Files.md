# Files

Monter et syncroniser des dossiers et des fichiers dans le serveur virtuel avec :

```ruby
config.vm.synced_folder
```

# Basic Syncing

docs: https://developer.hashicorp.com/vagrant/docs/synced-folders/basic_usage

Permet de monter et de sycroniser des dossier et des fichiers sur une vm

```ruby
Vagrant.configure("2") do |config|
    config.vm.synced_folder "src/", "srv/website"
end
```

# NFS (nécésite un serveur nfs sur la machin hote)

```ruby
config.vm.synced_folder ".", "/vagrant", type: "nfs"
```

# Rsync

Permet de synchroniser les dossiers dans le répèrtoire courant dans le dossier vagrant de la vm
rsync doit etre intaller sur l'hote ou il y a vagrant

```ruby
    config.vm.synced_folder ".", "/vagrant", type: "rsync"
        rsync_exclude: ".git/"
    end
end
```

# Upload

vagrent permet d'uploader, d'envoyer des fichier et des dossiers vers la vm

```ruby
    config.vm.provision "file", source: "~/.gitconfig", destination: ".gitconfig"
end
```

```ruby
    config.vm.provision "file", source: "~/path/to/host/folder", destination: "$HOME/remote/newfolder"
end
```

# Webapp Folder (lab-6)

dans un dossier lab-6 configurer une vm :

- image de base : username/nginx(box du lab-2)
- CPU 1
- RAM 1Go
- ip fixe: 10.0.0.10
- Monter le code de l'app static-website-exemple dans le dossier /var/www/html de la vm
- Vérifier l'accécibilité du site
- Supprimer la vm
