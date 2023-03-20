# Multi-machine

Dans le cas d'une utilisation multi-serveur avec par exemple un serveur web d'un coté et de l'autre un serveur de base de donnée, il faut créer plusieur machine virtuel
Les différente machine seront relier au meme commande vagrant

## Méthode define

La methode define permet de configurer et mettre en place plusieur vm

```ruby
Vagrant.configure("2") do |config|
    config.vm.provision "shell", inline: "echo Hello"
    # définie une vm avec apache comme image
    config.vm.define "Web" do |web|
        web.vm.box = "apache"
    end
    # définie une vm qui utilise mysql
    config.vm.define "db" do |db|
        db.vm.box = "mysql"
    end
end
```

docs : https://developer.hashicorp.com/vagrant/docs/multi-machine

## Déploiment multi-machine (lab-5)

- Créer un dossier lab-5
- Créer un vagrantfile afin de configurer 3 vms a partir des info suivantes :
  - Image de base : ubuntu/xenial64
  - cpu: 1
  - ram: 1go
  - vm1: lb, ip: 10.0.0.10
  - vm2: web1, ip: 10.0.0.11
  - vm3: web2, ip: 10.0.0.12
- connectez-vous en ssh sur chacunes d'elles
- Arretez les vms puis les supprimer

pour ce connecter sur une machine si il y en a plusieur

```shell
vagrant status
vagrant ssh nom-de-la-vm
```
