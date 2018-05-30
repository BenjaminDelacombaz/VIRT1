# VIRT1

Benjamin Delacombaz

SI-T1a

16.05.2018

## Docker

### Configuration d'un hôte Docker et premiers containers

1. Installez une VM Debian

2. Installez Docker avec les commandes suivantes ou suivez la dock suivante [https://docs.docker.com/install/linux/docker-ce/debian/#set-up-the-repository](https://docs.docker.com/install/linux/docker-ce/debian/#set-up-the-repository):
```
# apt-get update
# apt-get install \apt-transport-https \ca-certificates \curl \gnupg2 \software-properties-common
# curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
# apt-key fingerprint 0EBFCD88
# add-apt-repository \"deb [arch=amd64] https://download.docker.com/linux/debian \$(lsb_release -cs) \stable"
# apt-get update
# apt-get install docker-ce
# docker run hello-world
```

3. Si cela fonctionne correctement, installez le container officiel ubuntu avec les commades suivantes:
```
# docker pull ubuntu
# docker images
```

4. Si l'image ubuntu apparait dans la liste, l'image est correctement installée

### Premier container

1. Démarrez le containers ubuntu avec la commande suivante: 
```
# docker run ubuntu
```

2. Listez les containers actifs (normalement aucun), puis les actifs et inactifs avec les commande suivantes:
```
# docker ps
# docker ps -a
```
Ils sont tous inactifs, normal car nous ne les utilisons pas (aucun service actif)

3. Redirigez l'entrée standard du container pour ouvrir un pseudo-terminal avec la commande suivante
```
# docker run -ti --name=ubuntu ubuntu /bin/bash
```

4. Controllez la version d'ubuntu avec la commande suivante: (NE MARCHE PAS)
```
# lsb release
```

5. Ouvrez un second terminal et listez les containers actifs:
```
# docker ps
```
Il y en a un seul, celui que nous avons démarré précédemment.

6. Pour savoir le container ID, il suffit de lancer la commande:
```
# docker ps
```
Mon container id est le suivant: 4054b5ad576c

7. Vérifiez que vous voyez tous les processus de votre container en listant également dans le container avec la commande (cherchez avec la colonne RES):
```
# top
```

8. 

<div style="page-break-after: always;"></div>
