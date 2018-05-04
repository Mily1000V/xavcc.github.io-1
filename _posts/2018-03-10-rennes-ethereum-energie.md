---
title: "Blockchain et énergie : Test Pi 3, Ethereum & serveur ftp"
layout: post
date: 2018-03-10 12:48
image: /assets/images/mercury_nasa.jpg
headerImage: true
tag:
- hsociety
- Peer 2 Peer
- Communs
- Rennes
category: blog
author: XavierCoadic
description: Internets of Energy  Energy as a Commons
---

Pour DAISEE.org : <https://github.com/DAISEE> lors du hackathon « [Nuit du Code Cutoyen 2018](http://movilab.org/index.php?title=Nuit_du_code_citoyen_Rennes_2018) » à Rennes au hackerspace [Breizh Entropy](http://breizh-entropy.org/) 

### Objectifs 
1. Installer un nœud ethereum sur raspi 3 : <https://github.com/DAISEE/Prototypes/wiki/2.-Ethereum>
2. Installer un Serveur FTP sur le même raspi 3
3. Envoyer certaines données du nœud sur le serveur FTP
4. tester : 
  + 3.1 Stabilité
  + 3.2 Sécurité
  + 3.3 Usages
  
#### Table de contenus

1. [Introduction](#introduction)
2. [Raspi 3](#raspi-3)
3. [Documentation supplémentaires](#documentation-supplémentaire)
4  [Nécessaires](#nécessaires)
5. [Installer le serveur FTP](#installer-le-serveur-ftp)
6. [Installer le client](#installer-le-client)
7. [Connexion au Raspi 3](#connexion-au-raspi-3)
8. [Tests](#tests)
3. [Licence du document](#licence)

## Introduction 

Le _FTP_ (_File Transfer Protocol_) est un protocole qui nous permet d’accéder aux fichiers d’un ordinateur à distance, (uploader, télécharger, renommer, modifier, déplacer, bref tout ce que vous voulez) à partir du moment qu’un « _serveur_ » FTP est installé.

## Raspi 3
-   CPU: 1200 MHz quad-core ARM Cortex-A53
    
-   Memory: 1 GB RAM
    
-   Storage: MicroSDHC slot
    
-   Graphics: Broadcom VideoCore IV at higher clock frequencies than previous that run at 250 MHz
    
-   Power consumption: 4.0 W


## Documentations supplémentaires

_j'ai simplement demandé sur le réseau social [Mastodon](https://fr.wikipedia.org/wiki/Mastodon_(r%C3%A9seau_social)), [Flynn](https://mastodon.roflcopter.fr/@flynn) a répondu gentillement_
1. [FILE TRANSFER PROTOCOL (FTP)](https://www.ietf.org/rfc/rfc959.txt), Obsoletes RFC: 765 (IEN 149) sur IETF
2. [Tutoriel : Créer son serveur FTP](http://sdz.tdct.org/sdz/creer-son-serveur-ftp.html)
3. [Wikipedia pour le mode passif/actif](https://fr.wikipedia.org/wiki/File_Transfer_Protocol), voir également [FPT protégé par SSL ou TLS](https://fr.wikipedia.org/wiki/File_Transfer_Protocol_Secure)
4. Sur [CCM](http://www.commentcamarche.com/contents/519-le-protocole-ftp-file-transfer-protocol) pour les détails de commandes et les schémas
![](https://i.imgur.com/ldlLwHu.gif)
![](https://i.imgur.com/Wm5QIq5.png)

## Nécessaires

+ Un raspberry 3
+ un **serveur FTP** et un **client FTP**.

Le serveur sera installé sur la machine à laquelle vous voulez accéder (ici votre Raspberry Pi) et le client sur la machine **depuis** laquelle vous voulez y accéder.


Vous pourrez accéder à votre Raspberry Pi en FTP uniquement en local.

## Installer le serveur FTP

Avec un terminal (possible également SSH) :

    sudo apt-get install vsftpd

Appuyez sur `[o]` si cela est demandé lors de l'installation dans le terminal.

Le serveur est installé, 

Poiur la configuration, depuis votre terminal, entrez

    sudo nano /etc/vsftpd.conf

Un fichier de configuration s’ouvre.
![](https://i.imgur.com/SU0pnmP.png)

On retrouve une instruction par ligne. Certaines lignes sont précédées d'un dièse `#` : ce sont des commentaires qui sont ignorés. Il servent la plupart du temps à vous indiquer à quoi sert la ligne qui suit. 
Parfois, il faudra enlever le `#` au début d'une des lignes pour activer l'instruction qu'elle contient.

Faire défilier les lignes 

Modifier : 

    Anonymous_enabled=YES

en

    Anonymous_enabled=NO
    
![](https://i.imgur.com/PbFC5PC.png)

Toujours en faisant défiler les lignes, enlevez le `#` devant les lignes suivantes :

```
Local_enable = YES
local_unmask=022
Write_enabled=YES
Ascii\_upload\_enabled=YES
Ascii\_download\_enabled=YES
```
Puis faites `[ctrl]` + `[x]` puis `[o]` puis `[Entrée]`

Le server est prêt

### DefaultRoot

Le répertoire auquel auront accès les personnes qui se connecteront en FTP.

<span class="evidence">Par défaut, quelqu'un qui se connecte en FTP au serveur peut accéder à tous les dossiers du serveur !</span> 

<span class="evidence">**Bien qu'il ne puisse pas les modifier pour la plupart, ce n'est certainement pas quelque chose que vous avez envie d'autoriser. Il est donc recommandé d'activer l'option DefaultRoot**</span>

<span class="evidence">Pour activer DefaultRoot, supprimez le `#` en début de ligne. 
La valeur `~` de la commande signifie que l'utilisateur sera limité à son dossier personnel (`/home/me` par exemple). Il ne pourra pas aller "fouiner" dans d'autres dossiers.</span>

## Installer le client 

Télécharger _FileZilla_ [ici](https://filezilla-project.org/download.php?show_all=1) adapté à votre OS.

Avec Linux vous pouvez aussi taper

    sudo apt-get install filezilla 

## Connexion au Raspi 3

Avant de nous connecter, il nous faut l’adresse IP de notre Raspberry Pi. Pour la trouver en tapant cette commande (depuis le RPi ou en SSH) :

    ifconfig

Si le Raspberry PI est connecté en ethernet, l’adresse IP se trouvera à côté de `eth0`, et si el est en wifi, elle sera à côté de `wlan0`. L’adresse est de la forme `192.168.X.X`

Notez cette adresse et revenez à FileZilla.

Dans la zone de connexion rapide de Filezilla, renseignez l’IP (192.168.X.X), le nom d’utilisateur (pi), et le mot de passe (_raspberry_ par défaut).

Vous avez mainteant accès aux fichiers dans le raspi 3 contenant le noeud ethereum


## Tests 

1. <https://ftptest.net>
2. `$ telnet mon.ip.ftp`
3. Les connexions sont assez faciles à suivre par IP: `grep ftp /etc/services`
4. Utilisez netstat pour voir les connexions ouvertes. Par exemple, pour un FTP simple : `$ netstat -tan | grep \\:21`
5. Ou, si vous voulez que l'on confirme quel programme utilise le port [TCP] 21 : `sudo netstat -tanp | grep \\:21`
6. Si vous utilisez ftp, vous pouvez voir qui est connecté en temps réel et quel type d'opération est en train de faire (dowload, upload) avec la commande suivante: `$ pure-ftpwho` (_voir <https://www.pureftpd.org/project/pure-ftpd>)

### Test accès ftp et sécurisation du service

1.Activer le service dans inetd.conf et lancer le service inetd .
    
2.Vérifier que le port est bien ouvert avec la commande netstat
```    
root@monlabtop:/home# netstat -atup | grep LISTEN
tcp    0    0  *:ftp       *:*                     LISTEN      879/inetd
```    
3.Vérifiez que rien n'interdit l'accès au service ftp dans les fichiers `hosts.allow` et `hosts.deny`
    
4.Commentez le fichier /etc/ftpusers comme ci-dessous :
```    
\# /etc/ftpusers: list of users disallowed ftp access. See ftpusers(5).
root
#ftp
#anonymous
```    
5.Testez et vérifiez le bon fonctionnement de l'accès ftp anonyme en utilisant le compte "ftp" ou "anonymous" avec la commande :
    
    lftp localhost -u anonymous
ou 

    lftp localhost -u ftp
    
Si la configuration est correcte, vous devriez avoir le résultat suivant :
    
    root@master:/home# lftp localhost -u ftp
    Mot de passe: #Il n'y a pas de mot de passe, faites ENTREE
    lftp ftp@localhost:~> ls
    total 20
    d--x--x--x    2 0        0            4096 May  5 03:35 bin
    d--x--x--x    2 0        0            4096 May  5 03:35 etc
    drwx-wx-wt    2 0        0            4096 May  5 03:04 incoming
    dr-xr-xr-x    2 0        0            4096 May  5 03:32 lib
    dr-xr-xr-x    2 0        0            4096 May  5 03:04 pub
    
6.  Commentez la ligne anonymous dans le fichier /etc/ftpusers et refaites un essai de connexion.
    
7.  Faites un test en utilisant un compte système existant, par exemple "lftp localhost -u util" pour vérifier si votre compte est utilisé.
    
8.  Restaurez l'état initial du fichier /etc/ftpusers.
    
9.  Interdisez l'accès ftp avec TCP-Wrapper. Testez avec l'accès anonyme et en utilisant un compte authentifié.

> <span class="evidence">**NLDR** : Les tests de sécurité et d'usages auront lieu lors des prochaines soirées apéro DAISEE, Internet Of Energy, Energy as a Commons, à Rennes. Pensez à nous suivre pour être tenu⋅e⋅s informé⋅e⋅s</span>

## Licence

```
# DON'T BE A DICK PUBLIC LICENSE

> Version 1.1, December 2016

> Copyright (C) 2018 Xavier Coadic pour DAISEE.org


Everyone is permitted to copy and distribute verbatim or modified
copies of this license document.

> DON'T BE A DICK PUBLIC LICENSE
> TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION

1. Do whatever you like with the original work, just don't be a dick.

   Being a dick includes - but is not limited to - the following instances:

 1a. Outright copyright infringement - Don't just copy this and change the name.
 1b. Selling the unmodified original with no work done what-so-ever, that's REALLY being a dick.
 1c. Modifying the original work to contain hidden harmful content. That would make you a PROPER dick.

2. If you become rich through modifications, related works/services, or supporting the original work,
share the love. Only a dick would make loads off this work and not buy the original work's
creator(s) a pint.

3. Code is provided with no warranty. Using somebody else's code and bitching when it goes wrong makes
you a DONKEY dick. Fix the problem yourself. A non-dick would submit the fix back.

Everyone is permitted to copy and distribute verbatim or modified
copies of this license document.

> DON'T BE A DICK PUBLIC LICENSE
> TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION

1. Do whatever you like with the original work, just don't be a dick.

   Being a dick includes - but is not limited to - the following instances:

 1a. Outright copyright infringement - Don't just copy this and change the name.
 1b. Selling the unmodified original with no work done what-so-ever, that's REALLY being a dick.
 1c. Modifying the original work to contain hidden harmful content. That would make you a PROPER dick.

2. If you become rich through modifications, related works/services, or supporting the original work,
share the love. Only a dick would make loads off this work and not buy the original work's
creator(s) a pint.

3. Code is provided with no warranty. Using somebody else's code and bitching when it goes wrong makes
you a DONKEY dick. Fix the problem yourself. A non-dick would submit the fix back.

```
