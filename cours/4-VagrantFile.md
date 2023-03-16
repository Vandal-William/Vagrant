## VagrandFile

Le VagrandFile est un système d'arboraissance, avec des éléments qui en inclus d'autre:

![vagrantFile](./images/Shema%20VagrantFile.png)

Pour accéder par exemple au reseau privé :

```ruby
vm.reseau.privé = 1.02.35
```

## L'objet config

docs: https://developer.hashicorp.com/vagrant/docs/vagrantfile/version

```ruby
Vagrant.configure("2") do |config|
# 2 est la version de langage utilisé
# ce code veut dire que l'on va paramétrer vagrant sous le nom config dans la version 2 du langage
# config est comme un alias qui fait référence a Vagrant.configure("2")
```

## configurer la VM

docs : https://developer.hashicorp.com/vagrant/docs/vagrantfile/machine_settings

```ruby
config.vm
# ce code va permettre de configurer la vm
```

## Paramettrage du SSH

docs : https://developer.hashicorp.com/vagrant/docs/vagrantfile/ssh_settings

```ruby
config.ssh
# ce code va permettre de configurer le ssh
```

## Configurer vagrant

docs : https://developer.hashicorp.com/vagrant/docs/vagrantfile/vagrant_settings

il est possible de piloter un vagrant installer sur une autre machine

```shell
# Choisir l'hôte sur lequel démarrer
config.vagrant.host
# Choisir les plugins a intaller
config.vagrant.plugins
# Information sessible que vagrant ne devra pas afficher a l'écrant
config.vagrant.sensitive
```

## Configurer un accès a distance (sous windows)

docs : https://developer.hashicorp.com/vagrant/docs/vagrantfile/winrm_settings

```ruby
config.winrm
#ou
config.winssh
```

## Les variables

```ruby
LOCAL_SSH_PORT = "2222"
```

## Variable d'environement Vagrant

Des variable environemental definie vagrant sont également disponible
docs : https://developer.hashicorp.com/vagrant/docs/other/environmental-variables

## Loop

Le système de boucle permet de déployer plusieur serveur

```ruby
# une boucle qui itère 3 fois
(1..3).each do |i|
    config.vm.define "node-#{i}" do |node|
        node.vm.provision "shell",
            inline: "echo hello from node #{i}"
    end
end
```

```ruby
    VAGRANTFILE_API_VERSION = "2"
    # Un cluster est un objet avec des clées valeur, en clée le nom d'un serveur
    # en valeur un objet qui contient les info du serveur.
    cluster {
        "master" => {:ip => "192.168.33.10", :cpus => 1, :mem => 1024},
        "slave" => {:ip => "192.168.33.11", :cpus => 1, :mem => 1024}
    }
    # On prépare la configuration
    Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

    # on boucle sur le cluster pour mettre en place tour a tour les serveur
    # le hostname sera egale a master puis a slave
    # info représent l'objet qui est la valeur de la clée master et slave dans l'objet cluster
    # ex pour accéder a l'addresse ip : info[:ip]
    # pour afficher une variable dans une chaine de caractère: "#{}"
    cluster.each_with_index do |(hostname, info), index|
        config.vm.define hostname do |cfg|
            cfg.vm.provider :virtualbox do |vb, override|
                config.vm.box = "ubuntu/trusty64"
                override.vm.network :private_network, ip: "#{info[:ip]}"
                override.vm.hostname = hostname
                vb.name = hostname
                vb.customize ["modifyvm", :id, "--memory", info[:mem], ...]
            end # end provider
        end # end config
    end # end cluster
end
```

## Méthodologie de création (lab-3)

```shell
vagrant init geerlingguy/centos7
```

=> Modifier le vagrantFile en lui ajoutant un provider et en configurant la ram et le cpu du provider

### Valider la configuration du fichier

```shell
vagrant validate
```

=> je valide **systématiquement** les modifications effectuer dans le vagrantfile

```shell
vagrant up
```

```shell
vagrant ssh
```
