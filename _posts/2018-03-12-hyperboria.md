---
title: "Tutoriel: Installons et testons un des internets pair à pair et chiffré - Hyperboria"
layout: post
date: 2018-02-14 22:48
image: /assets/images/hyperboria.png
headerImage: true
tag:
- Sciences
- Peer 2 peer
- Communs
category: blog
author: XavierCoadic
description: Pour des internets libres et décentralisés, Réseau avec des noeuds pair à pair non anomynes IPV6 et sécurité E2E
---

## Installation cjdns pour Ubuntu - Hyperboria

Réseau avec des noeuds pair à pair non anomynes, chiffrement [IPv6](https://fr.wikipedia.org/wiki/IPv6) avec clé publique et sécurité [E2E](https://en.wikipedia.org/wiki/End-to-end_encryption). 

Installation et Tests réalisés dans le cadre du hackathon la [Nuit du Code Citoyen 2018 à Rennes](http://movilab.org/index.php?title=Nuit_du_code_citoyen_Rennes_2018) en 1 heure.


voir hyperbolia : [www.fc00.org](http://www.fc00.org)

![](https://i.imgur.com/DNvSlga.png)


Voir : [la documentation github](https://github.com/hyperboria/docs), mais elle ne contient pas encore cette installation décrite dans cet article

## Installer les paquets packets

```
apt-get install nodejs make gcc git python 2.7
```

## Clone, compile, install

Merci à copain [rzr](https://rzr.online.fr/#)

```
cd /opt
git clone https://github.com/cjdelisle/cjdns.git
cd cjdns
./do
ln -s /opt/cjdns/cjdroute /usr/bin
umask 077 && sudo ./cjdroute --genconf | sudo tee /etc/cdjroute.conf
sudo cp contrib/systemd/*.service /etc/systemd/system/
systemctl enable cjdns
systemctl start cjdns

```
> Pour cette occasion j'ai découvert les commandes [umask](https://fr.wikipedia.org/wiki/Umask) et [tee](https://fr.wikipedia.org/wiki/Tee_(Unix))

## Maintenant...

Lorsque vous faites partie du réseau, vous êtes devenu un , fournisseur d'accès à internet,[FAI](https://fr.wikipedia.org/wiki/Fournisseur_d%27acc%C3%A8s_%C3%A0_Internet). Cela vous donne certaines responsabilités envers le reste de la communauté.

Je vous recommande grandement les ressources de la Quadrature du Net à ce sujet : [Ici](https://www.laquadrature.net/fr/search/apachesolr_search/fai)

## Verrouillez votre boîte

Lorsque vous démarrez cjdns, vous devenez un hôte IPv6. De nombreux programmes, tels que les serveurs http, ssh ou smtp, se lient automatiquement à cette nouvelle adresse. Si vous ne souhaitez pas que ces services soient disponibles sur votre interface cjdns, vous devez soit modifier vos règles [`ip6tables`](http://ipset.netfilter.org/ip6tables.man.html), soit éditer le fichier de configuration du service en question ([exemple](https://doc.ubuntu-fr.org/iptables)).

Pour scanner votre boîte pour rechercher des services en cours d'exécution, obtenez d'abord votre adresse `cjdns` en exécutant:

    ip addr | grep "inet6 fc"

puis scanne l'adresse avec:

    nmap -6 <CJDNS ADRESSE> $ nmap

## Efficience des pairs

La loi de Murphy s'applique au routage des cjdns : si un paquet peut prendre une route bizarre ou inefficace, il le fera probablement. Lorsque vous choisissez de mauvais pairs, cela dégrade la qualité de l'ensemble du réseau. Lorsque vous faites du trafic sur Internet, vous devriez faire du trafic avec ceux qui sont relativement proches de vous sur le plan géographique.

Vous ne devriez faire du peering qu'avec des gens en qui vous avez (modérément) confiance. Le fait d'échanger avec des inconnus ruine la nature amicale du réseau.

## Assurer la sécurité des titres de compétence des pairs

Dans le même ordre d'idées que le peering efficace, veillez à ce que personne ne vole vos informations d'identification.

Les mots de passe ne devraient pas être des mots de passe, ils devraient être de longues chaînes de charabia qui sont pratiquement impossibles à deviner pour un attaquant. Pour générer un mot de passe puissant, vous pouvez exécuter cette commande bash:

    cat /dev/urandom | strings | head -n 20 | tr -d "' \n\"\t {\}" | head -c 40 && echo
    
> "Pour info sinon, /dev/urandom donne de la qualité moindre (dans les propriétés de génération de l’aléa) que [/dev/random](https://fr.wikipedia.org/wiki//dev/random). Le problème de ce dernier est qu’il est très lent car il n’y souvent pas assez d’entropie dans un ordinateur ; pour contrecarer ce problème, il est possible d’installer haveged (paquet Debian du même nom) qui va générer de l’entropie complémentaire pour /dev/random -- en plus ça semble être de la [technologie rennaise](http://www.irisa.fr/caps/projects/hipsor/)." @Seb via cette [issue](https://github.com/XavCC/xavcc.github.io/issues/74)

**NE PAS** transférer les informations d'identification de peering sur n'importe quel type de support en etxte non chiffré ([chiffre.info](https://chiffrer.info)), tel que l'IRC ou le courrier électronique non chiffré. C'est probablement aussi une bonne idée d'utiliser un service comme [NCrypt](http://ncrypt.sourceforge.net/) (également disponible sur Hyperboria) ou d'envoyer vos informations de peering par email chiffré avec PGP.

Toute la documentation est ici : [meshwith.me](https://docs.meshwith.me), il vous rest à configurer vos affaires : [ici](https://docs.meshwith.me/config/configure.html)

> Comment ne pas voir, dans cette mythique Hyperborée, avec Philéas Lebesgue, le « Monde Blanc », le GWENVED où tout n’est que blancheur, pureté, beauté, lumière ? — (Robert Ambelain, Au pied des menhirs. Essai sur le celtisme, Paris, Niclaus, 1945, page 52) _source [wiktionary](https://fr.wiktionary.org/wiki/Hyperbor%C3%A9e)_

Nous pouvons auusi faire cela ensemble lors d'une randonnée à Rennes le 21 mars, et un tas d'autres choses : [inscriptions](https://openagenda.com/root-nomad/events/walking-rennes?lang=fr). 

_Toujours avec les pieds_


## Tips
Vous avez des suggestions, des modifications, ou vous voulez réutiliser ce billet ? Il est sous licence libre (voir l'icone en bas à gauche) et accessible via github.

Il vous a été utile ? Un petit coup de dons sur l'icone jaune en bas à droite sera apprécié ^^


## Licence (en plus de la CC BY SA en bas de page)

```
# DON'T BE A DICK PUBLIC LICENSE

> Version 1.1, December 2016

> Copyright (C) 2018 Xavier Coadic


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
