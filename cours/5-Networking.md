# Networking Les infrastructures réseaux

## Port-forwarding

Protocole qui a partir d'une liste de port definit sur la machine locale, il va faire une translation sur la machine virtuel.
il permet de ne pas avoir un acces dirrecte a la machine virtuel
ex. si je suis sur le port 8080 en local => je serait sur le port 80 de la machine virtuel

docs : https://developer.hashicorp.com/vagrant/docs/networking/forwarded_ports

## Private Network

Crée un réseau priver qui permet d'avoir un accès direct a la machine virtuel
docs: https://developer.hashicorp.com/vagrant/docs/networking/private_network

## Public Network

créer un reseau ou tous le monde a acces au sein d'une meme entiter,
la vm utilisera le serveur DHCP de l'entiter pour s'attribuer une ip,
ou celle-ci se servira d'une adresse ip static définie par l'entité.

docs : https://developer.hashicorp.com/vagrant/docs/networking/public_network

## Déploiement d'un serveur web (lab-4)

Dans un dossier lab-4 :

- Créez un vagrantfile afin de configurer le vm a partir des infos suivante
  - image de base: Centos7 by Geerlingguy
  - CPU : 2
  - Ram: 2 go
  - Ip fixe: 10.0.0.10
- Variabilisez les paramettres ci-dessus
- connectez vous en ssh
- Installer npinx sur la vm
- Vérifier l'accès a l'application via http://10.0.0.10
- Supprimez la vm
