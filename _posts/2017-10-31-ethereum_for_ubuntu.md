---
layout: post
title: "Blockchain et Ethereum dans ton ordinateur. Pour Commencer...il faut un premier pas pour tous"
date: 2017-10-31
categories: ["science"]
---

Il s'agit de fournir un tutoriel simple et rapide pour installer et utiliser une blockchain Ethereum pour un utilisateur d'ordinateur Ubuntu. Le tout en 6 petites étapes et, peut-être, en apprenant un truc ou deux.

Les coordonnées de votre serviteur pour un don quand vous aurez appris
+ adress geth : `38594fa632c0538f13caaaf83385b3adc5eb0379`
+ Public node URL Parity: `enode://355c26ef18e0302e776edc9c5e6371acdd8c00953fdf1898bc48537e3e4ab9b875ba7da1738f39dbd213837b21efcebbc57e3e3280f69ae8032f0ce94d052725@192.168.1.17:30303`

![](https://framapic.org/eBPq3LGTTbyo/whKVa8ZlidEr)

## Le client 
Dans un réseau informatique, un client est le logiciel qui envoie des demandes à un serveur. Il peut s'agir d'un logiciel manipulé par une personne, ou d'un bot. Est appelé client aussi bien l'ordinateur depuis lequel les demandes sont envoyées que le logiciel qui contient les instructions relatives à la formulation des demandes et la personne qui opère les demandes.

Ici notre client est [Parity](https://parity.io/)

### 1. Installation binaire en ligne de commande

```
$ bash <(curl https://get.parity.io -kL)
```

_Dépendances à installer_

Une dépendance logicielle se conçoit dans le cadre d'une intégration de paquet logiciel en vue de construire un agrégat logiciel. Une dépendance exprime des relations entre paquets :

+ de pré-requis d'inclusion conditionnelle ;
+ de post-requis d'inclusion conditionnelle ;
+ de hiérarchie d'utilisation (j'utilise, je suis utilisé par) ;
+ d'exclusion conditionnelle ;
+ de suggestion.

Les conditions portent notamment sur :
+ des versions de paquet (inférieur, supérieur ou compris entre deux limites) ;
+ des choix alternatifs (choisir parmi un ensemble de paquets offrant les mêmes fonctionnalités) ;
+ des ordres d'installation.

Ceci permet de généraliser une installation logicielle, et de déporter l'intelligence servant à déterminer, et installer les paquets logiciels dans l'ordre, du paquet lui-même vers un outil appelé installateur. Ainsi, cela diminue les efforts des développeurs de paquets logiciels.

Ces dépendances sont un élément nécessaire dans l'architecture de paquets logiciels, qui sont la base des distributions Linux et systèmes BSD.

```
sudo apt-get install openssl libssl-dev libudev-dev
```


## Le logiciel pour la crypto-monnaie

[Ethereum](https://fr.wikipedia.org/wiki/Ethereum) est un protocole d'échange décentralisé permettant la création par les utilisateurs de contrats intelligents grâce à un langage Turing-complet. Ces contrats intelligents sont basés sur un protocole informatique permettant de vérifier ou de mettre en application un contrat mutuel. Ils sont déployés et consultables publiquement dans la blockchain.

### 2. Geth 
`geth`  est l'interface de ligne de commande pour un noeud Ethereum complet implémenté en Go. C'est le livrable principal de [Frontier Release](https://github.com/ethereum/go-ethereum/wiki/Frontier)



En installant et en exécutant `geth`, vous pouvez participer au réseau live d'Ethereum pour :

+ miner de vrais éthers
+ transférer des fonds entre les adresses
+ créer des contrats et envoyer des transactions
+ explorer l'historique des blocs
+ d'autres choses comme daisee.org par exemple 

```
sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install ethereum
```

3. Ensuite

Après installation, lancer ```geth account new``` pour créer votre nouveau noeud.

Vous pouvez maintenant commander ```geth``` et vous connecter au réseau.

Vous pouvez apercevoir et vous renseigner sur les différentes options de commande avec ```geth --help```

## Mettre à jour l'ordinateur
### 4. Update & Upgrade

```
sudo apt-get udpate && sudo apt-get upgrade -y
```
## Configurer le client Parity
### 5. Parity

Il prend en charge "l'instantané d'état", ce qui réduit considérablement le temps de synchronisation et l'élagage de la base de données, ce qui réduit donc les besoins en disponibilité d'espace disque. Les deux fonctionnalités sont activées par défaut sur les dernières versions de Parity. Synchronisez en exécutant simplement :

```
$ parity
```

_Synchronisation Warp_

Le snapshoting d'état, ou warp-sync, permet une "synchronisation" extrêmement rapide qui saute presque tout le traitement de bloc, en injectant simplement les données appropriées directement dans la base de données. Pour utiliser une synchronisation de cliché, vous devez d'abord télécharger un "snapshot".

```
$ parity --warp
```
Lorsque vous utilisez Parity 1.6 ou 1.7, `--warp` ne fait rien car il est activé par défaut
 
Parity peut être configuré à l'aide des options CLI, Command-line interface, ou d'un fichier de configuration. Si les indicateurs CLI et le fichier de configuration sont en désaccord sur un paramètre, l'interface CLI est prioritaire.

Vous pouvez lister toutes les options CLI en exécutant `$ parity --help`. 
Chaque option CLI correspond à un paramètre dans le fichier TOML, par exemple `--mode-timeout 500` peut être défini en créant un fichier de configuration :

```
[parity]
mode_timeout = 500
```
Parity peut être configuré en utilisant un fichier [TOML](https://github.com/toml-lang/toml). Le fichier peut être généré en utilisant le [générateur de configuration](https://paritytech.github.io/parity-config-generator/) de Parity. Pour démarrer Parity avec un fichier de configuration, le fichier doit se trouver dans :

+ Linux: `~/.local/share/io.parity.ethereum/config.toml`

Pour utiliser un _chemin d'accès_, Path, personnalisé : 
```
$ parity --config path/to/config.toml
```

Ou télécharger le TOML depuis le [générateur de configuration](https://paritytech.github.io/parity-config-generator/) et sasir dans le terminal :
```
cp /home/mon_espace_de_travail/Téléchargements/config.toml ~/.local/share/io.parity.ethereum
```
Pour faire une copie d'un fichier depuis un répertoire vers un autre.

### 6. Utiliser Parity

Par défaut, lorsque vous exécutez simplement Parity, Parity Ethereum se connecte au réseau Ethereum public officiel.

Afin d'exécuter une chaîne différente de celle de l'Ethereum public officiel, Parity doit être exécuté avec l'option `--chain` ou avec un fichier de configuration spécifiant `chain = "path"` sous `[parity]`. Il y a quelques préréglages nommés qui peuvent être sélectionnés ou un fichier de configuration JSON personnalisé peut être fourni.

**Chaînes prédéfinies disponibles :**

+ [mainnet](https://github.com/paritytech/parity/blob/master/ethcore/res/ethereum/foundation.json) (par défaut) réseau principal Ethereum
+ [kovan \| testnet](https://github.com/paritytech/parity/blob/master/ethcore/res/ethereum/kovan.json) le [réseau de test rapide Ethereum](https://github.com/kovan-testnet/config)
+ [ropsten](https://github.com/paritytech/parity/blob/master/ethcore/res/ethereum/ropsten.json) l'ancien réseau de test Ethereum
+ réseau classique [Ethereum Classic](https://github.com/paritytech/parity/blob/master/ethcore/res/ethereum/classic.json)
+ [testnet Morden](https://github.com/paritytech/parity/blob/master/ethcore/res/ethereum/morden.json) original classique-testnet et Testnet Ethereum Classic actuel
+ [Expanse](https://github.com/paritytech/parity/blob/master/ethcore/res/ethereum/expanse.json) réseau "étendu"
+ [dev](https://github.com/paritytech/parity/blob/master/ethcore/res/instant_seal.json) une [chaîne de développement privée](https://github.com/paritytech/parity/wiki/Private-development-chain) à utiliser en local, les transactions soumises sont insérées dans des blocs instantanément sans avoir besoin de miner


> Voilà vous êtes dans l'Ether...
> La prochaine étape sera de "miner"... dans le prochain article sur ce blog


##### Voir également

+ [Qu'est-ce que la blockchain](https://blockchainfrance.net/decouvrir-la-blockchain/c-est-quoi-la-blockchain/)
+ Livre blanc sur la blockchain,  Lire l’étude (en anglais et PDF) : « [Blockchain & Beyond](https://blockchainfrance.net/2015/12/05/livre-blanc-cellabz/) »

##### Remerciements 

Pour les contributions et corrections à cet article
+ [Rom1detroyes](https://github.com/Rom1deTroyes) pour avoir apporté des corrections à cet article via Github
+ [François Dupayrat](https://github.com/FrancoisDupayrat)
