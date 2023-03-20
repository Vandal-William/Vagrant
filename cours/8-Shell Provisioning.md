# Shell provisionning

Permet d'installer de dépendances sur une vm avec différents provisioner comme le shell, ansible..

```shell
config.vm.provisioner
```

```ruby
config.vm.provision "shell",
    # inline c'est la commande a executer
    inline: "echo helle, world"
end
```

# External script

Externaliser les scripts a exécuter avec le provisioner

```ruby
    config.vm.provision "shell", path: "script.sh"
end
```

```ruby
    config.vm.provision "shell", path: "https://exemple.com"
end
```

# Shell Provisioner: Arguments

```ruby
    config.vm.provision "shell" do |s|
        s.inline = "echo $1"
        s.args = "'hello, world!'"
    end
end
```

```ruby
    config.vm.provision "shell" do |s|
        s.inline = "echo $1"
        s.args = ["hello, world!"]
    end
end
```

docs: https://developer.hashicorp.com/vagrant/docs/provisioning/shell

# Shell (lab-7)

dans un dossier lab-7 configurer 3 vm

- immage : ubuntu/xenial64
- CPU 1
- RAM 1 Go
- vm1: lb, ip: 10.0.0.10, exécuter le script
- vm2: web1, ip: 10.0.0.11, exécuter le script
- vm3: web2, ip: 10.0.0.12, exécuter le script
- Supprimer les vm
