# plex

l'idée c'est d'avoir un serveur avec un espace de stockage assez conséquent pour y stocker des films. la solution Plex permettra de les lire sur toutes les plateformes (Apple TV, smartphone, Smart TV...) avec une interface sympa à la Netflix (histoire de pas avoir à brancher son PC en HDMI à la TV pour lire un film (on l'a tous fait, et dieu sait que c'est pas pratique !))

## solution retenue
abonné Freebox Ultra, il y a la possiblité d'y glisser un SSD et de créer des VMs : on va partir là dessus. une VM avec 1024Mo de RAM et 1 CPU est largement suffisante. les ressources sont par ailleurs assez limitées sur cette Freebox Ultra malheureusement.

J'ai choisi un disque de 2To, sur lequel j'ai créé un VM de 500Go pour Plex. Pour l'instant ça suffit, la VM fait ~80Go pour une 20taine de films stockés. 

## les étapes d'installation

### création de la VM

tout d'abord, il faut mettre en place la VM. c'est pas très compliqué, ça fonctionne à peu de choses près à la création d'une VM sur VirtualBox. sur la Freebox, y'a possibilité d'installer directement l'OS de votre choix. par défaut j'ai utilisé Ubuntu, mais toute autre distribution Linux fonctionnera :)

### installation du service plex sur la VM

* récupérer le fichier .deb sur le site officiel de plex : https://www.plex.tv/fr/media-server-downloads/?cat=computer&plat=linux
* le placer a la racine du répertoire utilisateur ```/home/user/```
* lancer la commande ```sudo dpkg -i plexmediaserver_1.19.4.2935-79e214ead_amd64.deb``` (changer le nom du fichier en fonction du nom réel du fichier)

par la suite, il faudra vous rendre sur le serveur via l'interface web ```http://server.com:32400/``` et réaliser la configuration du serveur Plex

### placement des fichiers vidéo dans un dossier spécifique

je ne sais plus comment je l'ai configuré, mais personnellement mes fichiers vidéos doivent se trouver dans le répertoire ```/var/lib/plexmediaserver/Library```. le serveur Plex va indexer ce dossier régulièrement afin d'y ajouter tous les nouveaux films que vous placez dans ce dossier dans le catalogue Plex. bien sur, les films doivent provenir d'une source légale ;)

une fois fait, le serveur va indexer les fichiers et les placer dans le catalogue en y apposant la jaquette et le résumé du film etc... si il arrive à les trouver. généralement, les fichiers en ```.mkv``` fonctionnent assez bien, et ont l'avantage de pouvoir contenir plusieurs langues & des sous titres que plex prend bien évidemment en charge.
