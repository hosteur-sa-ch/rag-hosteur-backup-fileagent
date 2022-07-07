# Hosteur Backup for Ragnarokkr (beta)

>[english version](README.md)

![nextcloud logo](/images/logo-hosteur_2021.png)

>Package JPS pour Hosteur Backup Dashboard

## Comment installer Hosteur Backup for Ragnarokkr

1. Vérifier que vous avez souscrit au service Hosteure Bucket, ou rendez-vous [Hosteur](https://www.hosteur.com/business/stockage/bucket) pour créer un compte.
2. Aller sur votre Dashboard Ragnarokkr [dashboard](https://app.rag-control.hosteur.com/)
3. Depuis la marketplace rechercher l'Addon Hosteur Backup Dashboard
4. Choisir l'environement ou vous souhaitez installer de la sauvegarde
5. Depuis la marketplace ou directement sur un nodes rechercher l'Addon Hosteur Backup File Agent et installez le sur le node à sauvegarder.
6. Pour utiliser le Dashboard de Backup (Toutes les informations sont envoyées par email à votre adresse)

*Vous pouvez installer plusieurs agent par environement, qui seront gérer par le meme Dashboard.*

**!! Toujoues installer l'Addon Hosteur Backup Dashboard avant d'installer des agents !!**

>Vous n'avez pas encore de compte Hosteur Bucket ...
>Rendez-vous [Hosteur](https://www.hosteur.com/business/stockage/bucket) pour créer un compte.

*Hosteur Bucket est un service Bucket S3 standard, hébergé par Hosteur et nativement répliqué sur 2 de nos Datacenter (France et Suisse)*

## Documentation

### Installation du Dashboard

Depuis la Marketplace choisir l'Addon : Hosteur Backup Dashboard (beta)

![src](srcdoc/Screenshot_20211462.png)

**Mettre ici les identifiants S3 de votre compte Hosteur Bucket et choisir l'environement à sauvegarder.**

Les informations de connexion vous seront envoyées par email et affichées en fin d'installation.

Hosteur Backup Dashboard est accéssible en TLS depuis le fqdn du node à l'adresse : https://nodexxxx-env-xxxx.rag-cloud.hosteur.com:8443/

![src](srcdoc/Screenshot_20211463.png)

>Si vous ouvrez l'interface avant d'avoir installé un agent vous obtiendrait un message d'erreur qui l'indiquera.


#### Interface Dashboard

##### L'accueil affiche la liste des agent connecté ainsi que les snapshots associés à cet agent.

![src](srcdoc/Screenshot_20211470.png)

>Il existe 2 types de snaphosts, nommé "Scheduled (planifié)" ou "Manual (manuel)", correspondant au mode de sauvegarde.

##### Ouvrir les details d'un Agent, vous affichera les snaphots disponible, les statistiques ainsi qu'un outil de recherche permettant de trouver les occurances de fichier ou dossier dans vos sauvegardes.

![src](srcdoc/Screenshot_20211471.png)

##### Ouvir un snaphot, vous affichera la liste des fichiers et dossiers sauvegardés, ainsi qu'un moteur de recherche permettant de trouver les occurances de fichier ou dossier dans vos sauvegardes.

![src](srcdoc/Screenshot_20211472.png)

##### Recherche un fichier ou dossier, vous affichera la liste des occurances de votre recherche pour tous les fichiers ou dossiers dans vos sauvegardes, par dates.

![src](srcdoc/Screenshot_20211477.png)

##### "Restore All" ou "Restore Selected", vous permet de restaurer fichiers et dossiers choisis dans le chemin backup_restore, ce chemin est disponible depuis le node Dashboard mais aussi sur les nodes Agent, vous trouverez un dossier a date de restauration contenant votre sauvegarde.

![src](srcdoc/Screenshot_20211473.png)

>Chemin de restauration, Dashboard
![src](srcdoc/Screenshot_20211475.png)

>Chemin de restauration, Agent
![src](srcdoc/Screenshot_20211476.png)

Vous pouvez avoir accès aux logs de restauration depuis l'acceuil du dashboard.

![src](srcdoc/Screenshot_20211474.png)

### Installation File Agent

Depuis la Marketplace choisir l'Addon : Hosteur Backup Files Agent (beta)

Sur un Node Compute (App)

![src](srcdoc/Screenshot_20211465.png)

Sur un Node SQL
![src](srcdoc/Screenshot_20211466.png)

**Vous devez ici configurer le chemin à sauvegarder, le periode des sauvegarde (au format Cron [ici](https://crontab-generator.org/) pour un générateur si besoins), puis la retention des sauvegarde en jours, mois, années (mettre à 0 pour désactiver la retention), a minima vous devez mettre 1 jours, 0 moi, 0 année pour conserver une seule sauvegarde par jour**

>Vous pouvez installer autant d'agent que vous souhaitez par Node de l'environement.
>**Hosteur Backup File Agent** est compatble avec tous les nodes natif de la plateforme, ainsi qu'avec les images Docker sous certaines conditions, détaillées ici.

>Pour qu'une image Docker soit compatible elle doit contenir a minima :
>* curl
>* tar
>* Linux Kernel amd64

#### Fonctionnalitées de File Agent

Par défaut File Agent effectura des sauvegarde par snapshots, à 00h00, sur 1 jours glissant, mais vous pouvez modifier cela en utilisant la fonction **Configure** dans l'addon. Vous retrouverez les sauvegarde effectuées comme étant **Scheduled** dans l'interface.

![src](srcdoc/Screenshot_20211467.png)

![src](srcdoc/Screenshot_20211468.png)

Vous pouvez aussi effectuer une sauvegarde manuelle avec la fonction **Backup Now**, vous retrouverez ces sauvegarde dans l'interface comme étant **Manual**.