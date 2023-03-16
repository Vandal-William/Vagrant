# Vagrant Boxes

La vagrant boxe est générer par la commande vagrant init, elle récupère l'image du système d'éxploitation du vagrant cloud, qui contient plusieurs images système.
elle se compose de 3 éléments:

- **Box file**: fichier au format tar, tar.gz ou zip, elle contient l'élément utilisable par le provider(ex. virtuale box),c'est une sorte de disque systeme dont il a besoin.
- **Box Catalog Metadata**: au format Json, elle permet de savoir comment référencer la virtual box sur le HashiCorp's Vagrant cloud, de versionner la vagrant box, et d'y ajouter des informations tel que le nom de la vagrant box, sa déscription, sa version, son provider et des url pertinante.
- **Box Information**: Contient les information du créateur de la box et ces coordonnée tel que l'email, le nom et Prénom, le numéro de téléphone...

Afficher la box d'information

```shell
vagrant box list -i
```

## installer une vagrant Box

Pour intaller une vagrant Box (déconseiller)

```shell
vagrant box add --name nom-de-la-box url-de-téléchargement
```

Il est conseiller d'utiliser la commande vagrant box add avec une image présente dans le vagrant cloud

```shell
vagrant box add ubuntu/trusty64
```

Pour installer une box dans une version spécifique

```shell
vagrant box add ubuntu/trusty64 --box-version numero-de-version
```

url vagrant cloud: https://app.vagrantup.com/boxes/search

## Initialisation avec Boxe

```shell
vagrant init ubuntu/trusty64 --box-version 20190425.0.0
```

```shell
vagrant up
```

```shell
vagrant ssh
```

=> Puis installer les dépendances voulus ex. nginx

## création d'un fichier a upload sur vagrant cloud

=> Sortir du serveur vagrant avec un exit

```shell
vagrant package --output nginx.box
```

avec cette commande une box vagrant sera créer a partir de la vm
