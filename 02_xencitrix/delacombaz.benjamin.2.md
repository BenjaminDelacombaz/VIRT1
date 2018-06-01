# VIRT1

Benjamin Delacombaz

SI-T1a

16.05.2018

## Xen Citrix

### Installation et configuration Xen Citrix

1. Créez une machine virtuelle avec 2 cartes réseau (NAT et Host Only), 60 GB de disque et 4 GB de RAM
2. Montez l'ISO de Xen Citrix
3. Démarrez la VM
4. Appuyez sur enter
5. Choisissez le bon clavier
6. Acceptez l'EULA
7. Choisissez le disque ou sera installé votre hyperviseur
8. Choisissez local media
9. N'installez pas de pak supplémentaire
10. Verifiez les sources d'installation
11. Entrez un mot de passe
12. Choisissez l'interface réseau
13. Configurez l'adresse ip en statique
14. Choisissez un nom pour le serveur et entrez un dns (1.1.1.1)
15. Choisissez europe puis Zurich
16. Entrez le temps manuellement
17. Installez XenServer
18. Spécifiez l'heure

### XenCenter

1. Installez XenCenter
2. Cliquez sur Add New Server
3. Entrez l'adresse IP de votre serveur puis vos credential

### ISO LocalISO

1. Connectez-vous en ssh à votre server
2. Controllez l'existence du répertoire suivant: /var/opt/xen/iso_import. S'il n'existe pas lancez la commande suivante:
```
# mkdir -p /var/opt/xen/iso_import
```
3. Si le LocalISO n'existe pas, lancez la commande suivante:
```
# xe sr-create name-label=LocalISO type=iso device-config:location=/var/opt/xen/iso_import device-config:legacy_mode=true content-type=iso
```
4. Télechargez et installez WinSCP
5. Connectez-vous à votre serveur et uploadez votre image ISO

### Installation Debian

1. Cliquez sur votre serveur depuis le menu Infrastructure puis sur new VM
2. Choisissez votre OS
3. Choisissez l'image ISO pécédemment uploadée
4. Placer la VM sur le serveur
5. Laissez les informations par défaut puis créez la VM
6. Installez et configurez Debian

### Ajout d'un Datastore

1. Arrêttez votre Xen server
2. Ajoutez un nouveau disque dur de 100 GB
3. Démarrez votre Xen server
4. Connectez-vous en SSH à votre serveur
5. Pour afficher la liste des disque, lancez la commande suivante:
```
# fdisk -l
```
6. Trouvez le nom de votre disque de 100 GB, pour ma part il se nomme /dev/sdb
7. Lancez la commande suivante en utilisant le nom de votre disque: 
```
# xe sr-create name-label=datastore2 shared=false device-config:device=/dev/sdb type=lvm
```

### Stockage partagé

1. Installez un 2ème XenServer avec un autre nom
2. Ajoutez ce serveur à votre XenCenter
3. Créez une machine Windows server 2012 dans votre VMware avec 2 interfaces ethernet (Nat et HostOnly)
4. Ajoutez un disque de 100 GB à votre windows server 2012
5. Installez StarWind ISCSI sur votre serveur
6. Créez une nouvelle partition avec le disque de 100 GB
7. Si le disque affiche qu'il est hors connexion effectuez la procédure se trouvant à cette adresse: [http://www.erp-link.fr/windows-disque-connexion/](http://www.erp-link.fr/windows-disque-connexion/)
8. Connectez votre serveur windows à starwind sur la partition que vous venez d'ajouter
9. Créez une nouvelle cible en cliquant sur Add target
10. Donnez lui un nom (cluster-xenserver-storage)
11. Cochez allow multiple concurrent ISCSI connexion (clustering)
12. Créez la cible
13. Ajoutez un nouveau Device
14. Choisissez Hard Disk
15. Puis Virtual Disk
16. Choisissez 50 GB
17. Laissez toutes les valeurs par défaut puis créez le device

#### Réseau Privée en 10.10.10.x/24

1. Configurez l'adresse Ip de votre windows server 2012 en 10.10.10.10
2. Sur XenCenter, cliquez sur votre serveur, puis allez dans Networking
3. Clicquez sur add network
4. Choisissez external network
5. Mettez Réseau ISCSI comme nom
6. Attribuez lui la carte physique host only “NIC1”
7. Cliquez sur “Configure” puis “New Interface”
8. Donnez un nom à l’interface exemple DATA puis sélectionnez le nouveau réseau “réseaux 
ISCSI” et configurer l’IP
9. IP static en 10.10.10.200 et 10.10.10.210 pour les deux hosts Xen

18. Dans XenCenter, cliquez sur votre serveur principal
19. Cliquez sur New Storage
19. Choisissez ISCSI
20. Donnez lui un nom
21. Indiquez l’@IP de la cible ISCSI ici c’est la baie en 10.10.10.10 puis cliquez sur Scan de sorte à afficher l’ensemble des cibles ISCSI
22. Choisissez l'IQN avec 10.10.10.10 à la fin
23. Cliquez sur New Pool
24. Donnez lui un nom et indiquez qui est les serveur maître et cocher votre 2ème serveur dans additional members

<div style="page-break-after: always;"></div>

### Activation du HA

1. Faites un clique droit sur votre pool puis cliquez sur Hogh Availability
2. Mettez votre machine Debian en mode Restart if possible
3. Déplacez votre debian dans le disque partagé
4. Démarrez la vm debian sur votre 2ème serveur
5. Eteignez votre second serveur
6. Observez...
7. Si tout c'est bien passé votre debian démarre sur votre premier serveur
