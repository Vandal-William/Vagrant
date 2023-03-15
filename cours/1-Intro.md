# Pourquoi vagrant ?

Vagrant permet la programmation du déploiement et de la gestion d'infrastructure virtualisée
Il a pour avantage de créer un environnement de développement proche de l'environement de production

## Installation de Virtuabox

url: https://www.virtualbox.org/wiki/Downloads

```shell
sudo apt install virtualbox
```

## Installation de Vagrant

url: https://vagrantup.com/downloads

```shell
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install vagrant
```

### Verification

```shell
vagrant --version
```
