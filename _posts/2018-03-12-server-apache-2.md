---
title: "Installer un environnement de travail avec Ubuntu : Apache 2 avec les pieds et 15 minutes pour débuter"
layout: post
date: 2018-03-12 12:48
image: /assets/images/indian-western-the-horse-apache-chief.jpg
headerImage: false
tag:
- Ubuntu
- Numérique
- Open Source
category: blog
author: XavierCoadic
description: Tutoriel avec les pieds
---

En ce lundi de [lendemain d'hackathon](http://movilab.org/index.php?title=Nuit_du_code_citoyen_Rennes_2018), j'ai reçu plusieurs retours de personnes qui lisent des documentations mais restent bloquées à une étape importante : "**mais comment tu fais pour fair apparaître ce que tu fais sur ton ordinateur comme si c'était une page _oueb_** ?"

Il vous faut un environnment de travail, autrement écrit un serveur local installé sur votre ordinateur. Voyons cela rapidement ensemble.

![](/assets/images/indian-western-the-horse-apache-chief.jpg)

>  Il existe différents [logiciels de serveurs web](https://en.wikipedia.org/wiki/Comparison_of_web_server_software) qui sont disponibles ([Apache](https://httpd.apache.org/), [Tomcat](http://tomcat.apache.org/), [nginx](http://nginx.org/)). Apache est libre et gratuit ([Floss](https://fr.wikipedia.org/wiki/Free/Libre_Open_Source_Software)), disponible sur plusieurs plateformes et est simple à installer.

Cet environnement de travail c'est `localhost` (l’hôte local en français), le nom habituel qui désigne une interface logique de votre ordinateur (à titre d'exemple).

## Installation

Avec firefox ;-) parce que "[Hygiène numérique 1, surfez mieux équipé.e.s](https://xavcc.github.io/hygiene-numerique-navifgation/)"

Dans votre terminal :

```
sudo apt-get update
sudo apt-get install apache2
```

Après l'installation, accédez à http://localhost/ avec votre navigateur pour vérifier que le serveur fonctionne.

Sous le capôt, votre serveur web utilise le protocoal [HTTP](https://fr.wikipedia.org/wiki/Hypertext_Transfer_Protocol) pour afficher les fichiers situés sur votre ordinateur. 

Avec cet exemple, Apache affiche un fichier nommé `index.html` qui est placé dans un sous-répertoire des dossiers Apache. Il nous  sera utile, notammment par la suite des usages, d'utiliser un répertoire par choix.

## Préparons le terrain

Tout d'abord, créons un dossier puis amenpns le serveur web à pointer vers ce répertoire :

dans votre terminal un dossier appelé `htdocs` dans votre répertoire utilisateur : `/home/NomUtilisateur/htdocs`, où NomUtilisateur correspond à votre nom d'utilisateur.

```
sudo mkdir /home/NomUtilisateur/htdocs
```
## configurons rapidement

Sans prétention aucune, car ce n'est que le minimun vital. 

Dans un ternimal :
```
cd /etc/apache2/sites-available/
```

Dans ce fichier et à la ligne suivante : DocumentRoot /var/www/html. Modifiez cette line afin que le répertoire corresponde au répertoire de travail htdocs : DocumentRoot /home/NomUtilisateur/htdocs

```
sudo nano 000-default.conf 
```
Ajoutons des restrictions d'accès aux fichiers. Pour cela, ajoutez les lignes suivantes sous la ligne avec `DocumentRoot`, changer USERNAME avec votre nom d'utilisateur.

      <Directory />
                Options FollowSymLinks
                AllowOverride None
                Require all denied
        </Directory>
        <Directory /home/USERNAME/htdocs/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Require all granted
        </Directory>

Puis sauvegarder : `[cltr]`+`[x]` puis `[o]` puis `[enter]`

## On redémarre ce serveur

Redémarrez Apache 
```
sudo apachectl restart
```
Si nécessaire, entrez votre mot de passe.

Rechargez la page `localhost` dans votre navigteur. Vous devriez voir l'index du répertoire. Sinon vérifiez vos démarches précédentes. 

![](/assets/images/moz_apache_server.png)

Vous en avez fini avec les pieds... Vous pouvez mainteant _jouer_ et continuer à apprendre en faisant des petits bouts de trucs.

Vous pouvez ausi passer aux mains dans le cambouis.
    
## Message dans le terminal

Si lors du restart si vous avez dans le terminal la réponse :
```
AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. 
Set the 'ServerName' directive globally to suppress this message
```
Ce n'est qu'un avertissement amical et pas vraiment un problème (car quelque chose ne fonctionne pas).

### Corrigeons cela

Utilisez un éditeur de texte tel que `sudo nano` dans le terminal pour créer un nouveau fichier,

```
sudo nano /etc/apache2/conf.d/fqdn
```

puis ajoutons au fichier 

```
ServerName localhost
```

Sauvegardez. Tout cela peut aussi être fait en une seule commande avec les commandes suivantes:

```
 echo "ServerName localhost" | sudo tee /etc/apache2/conf-available/fqdn.conf
 sudo a2enconf fqdn
 ```

N'oubliez pas le ".conf" (sans cela ne marchera pas).

Puis
`sudo service apache2 restart`

## Soyez plus curieuses et curieux et précis.e.s

### Le fonctionnement de localhost

Sur l'univers du [DNS](https://fr.wikipedia.org/wiki/Domain_Name_System), il existe une adresse spéciale connue par chaque ordinateur : `localhost`. Celle-ci fait référence au serveur situé sur l'ordinateur en question. Ainsi, il est possible d'accéder à un site situé sur `localhost` avec votre navigateur, même sans connexion à Internet.

> Pour être un poil plus précis, `localhost` pointe vers une [adresse IP](https://fr.wikipedia.org/wiki/Adresse_IP) dirigeant vers votre propre machine : `127.0.0.1` ([IPv4](https://fr.wikipedia.org/wiki/IPv4)) ou `::1` ([IPv6](https://fr.wikipedia.org/wiki/Adresse_IPv6). Le nom localhost est associé à l’adresse IPv6 ::1 et à la plage d’adresses IPv4 127.0.0.0/8 (toutes les adresses IPv4 comprises entre 127.0.0.1 et 127.255.255.255 dont la plus utilisée est 127.0.0.1).
 
### Consultez par exemple

1. [Mettre en place un environnement de travail](https://developer.mozilla.org/fr/Apprendre/Mettre_en_place_un_environnement_de_travail#Ubuntu_Linux), chez mozilla
2. [HTTPD - serveur web Apache2](https://help.ubuntu.com/lts/serverguide/httpd.html) chez ubuntu
3. [Compilation et installation](http://httpd.apache.org/docs/current/install.html), chez Apache.org

Nous pouvons auusi faire cela ensemble lors d'une randonnée à Rennes le 21 mars, et un tas d'autres choses : [inscriptions](https://openagenda.com/root-nomad/events/walking-rennes?lang=fr). 

_Toujours avec les pieds_

## Tips 

Vous avez des suggestions, des modifications, ou vous voulez réutiliser ce billet ? Il est sous licence libre voir et accessible via github.

Il vous a été utile ? Un petit coup de dons sur l'icone jaune en bas à droite sera apprécié ^^



