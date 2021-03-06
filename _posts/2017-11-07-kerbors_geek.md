---
title: "IndieCamp Kerbors: Atelier Geek - Session #2"
layout: post
date: 2017-11-07 22:44
image: /assets/images/kerbors-sun.jpeg
headerImage: false
tag:
- hsociety
- Peer 2 Peer
- Numérique
- Bretagne
star: true
category: blog
author : XavierCoadic
description: IndieCamp, Elm, Javascript, Geek, programmation
---

> `IndieCamp` , `Kerbors` , `atelier geek`, `Elm` `JavaScript`, qu'est ce qu'un [IndieCamp](http://movilab.org/index.php?title=IndieCamp)

* [Atelier #0](https://hackmd.io/s/rJw31KgDb), sur les commandes d'un terminal pour un ordinateur sous Linux
* [Atelier #1](https://hackmd.io/s/rJDXkRHDW), sur le langage markdown utile àla documentation de projet
* [Atelier #2](https://hackmd.io/s/SyHcRZPPb), sur les langage de programmation JavaScript et Elm
* [Atelier #3](https://hackmd.io/s/BkvQpmmY-#) apprendre JavaScript en MobProgramming

Ce billet décrit un atelier d'initiation aux **langages JavaScript et ELM** réalisé sur l'Indiecamp à Kerbors 2017.

![](/assets/images/kerbors-sun.jpeg)

Ce document est mis à disposition par tou.te.s les contributeurs et contributrices de l'Indiecamp Kerbors 2017, selon les termes de la [licence Creative Commons CC-BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

<img style="display: block; margin: 0 auto;" src="https://mirrors.creativecommons.org/presskit/buttons/88x31/png/by-sa.png" width="40%">

## JavaScript

Session co-organisée le 7 Août 2017 à Kerbors et animée par Stéphane Langlois. Avec une méthode "Mob Programming" (Voir [Doing with Mob, learning by Mob - eng / fr](https://storify.com/XavierCoadic/doing-with-mob-learning-bu-mob))

Ouvrir un `index.html` puis un serveur local.

{% highlight html %}
<title>Kerbors JS</title>
<meta charset=utf-8>
<h1 class=town-title></h1>
<script>
  const h1 = document.querySelector('h1.town-title')
</script>
{% endhighlight %}

Quand tu lui donnes un mot en minuscule, la page l'affiche en majuscule.


{% highlight html %}
<title>Kerbors JS</tilte>
<meta charset=utf-8>
<h1 class=town-title></h1>
<script>
  const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
  function toMaj = str => str.toUpperCase()
</script>
{% endhighlight %}

Les parenthèses ont le role d'invocation de la fonction. 


<span class="evidence">+ Se renseigner sur l'inférence en programmation fonctionnelle : Defi [Inférence](https://fr.wikipedia.org/wiki/Inf%C3%A9rence), [L'inférence de types](https://fr.wikipedia.org/wiki/Inf%C3%A9rence_de_types) est un mécanisme qui permet à un compilateur ou un interpréteur de rechercher automatiquement les types associés à des expressions, sans qu'ils soient indiqués explicitement dans le code source.</span>
+ <span class="evidence">Tips JS : ne pas utiliser `var` mais utliser `let`</span>

Ou encore pour construire une liste html de villes en utilisant `map` pour avoir chaque ville sans utiliser de fonction.

{% highlight html %}
<title>Kerbors JS</tilte>
<meta charset=utf-8>
<h1 class=town-title></h1>
<script>
  const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
  tonws.map(town => return toUpperCase())
</script>
{% endhighlight %}

Pour aller plus loin avec les fonctions

{% highlight html %}
<title>Kerbors JS</tilte>
<meta charset=utf-8>
<h1 class=town-title></h1>
<script>
  const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
  tonws.map(town => {return toUpperCase()}
</script>
{% endhighlight %}

Utiliser `ul>li*5` pour faire une nodelist

{% highlight html %}
<title>Kerbors JS</tilte>
<meta charset=utf-8>
<h1 class=town-title></h1>
<ul>
	<li>Paris</li>
	<li>Barcelone</li>
	<li>Nantes</li>
	<li>Bordeaux</li>
	<li>Rennes</li>
</ul>
<script>
  const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
</script>  
{% endhighlight %}
Pour aller plus loin

{% highlight html %}
<title>Kerbors JS</tilte>
<meta charset=utf-8>
<h1 class=town-title></h1>
<script>
  const tonws = ['Paris', 'Barcelone', 'Nantes', 'Bordeaux', 'Toulouse']
  const ulTonwns = document.querySelector('ul.towns')
  towns.forEach(tonw => {
  	console.log(ulTonwns)
  	ulTonwns.innerHTML += '<li>${towns}<li>'
  })
</script>
{% endhighlight %}

[Voir](github.com/oncletom/nodebook) pour un livre numérique à plusieurs mains sur JavaScript. Node.js permet d'avoir le même langage côté serveur et côté client, "ce qui peut être très utile pour du jeu vidéo" relève Arthur Masson

##  ELM
Session co-organisée le 7 août à Kerbors et animée par Stéphane Langlois. 

ELM est un langage fonctionnel avec une capacité d'inférence. Ce n'est pas un framework mais un langage qui embarque le 'beginnerProgram'. Site de référence : elm-lang.org (avec un bac à sable pour faire un 'hello world').

Pour installer ELM : <https://guide.elm-lang.org/install.html>

**Avec Linux**

```
$ sudo apt-get update
$ sudo apt-get install nodejs npm
$ sudo apt install nodejs-legacy
$ npm install elm
```
Pour afficher un text Hello, World en langage Elm sur un serveur local ou sur http://elm-lang.org/try

{% highlight elm %}
import Html exposing (text)
main=
text "Hello, World"
{% endhighlight %}

ou 

{% highlight elm %}
import Html exposing (h1,text)
main=
h1 [] [text "Hello, Wolrd"]
{% endhighlight %}

Avec Elm c'est une virtualisation du DOM qui est engagée. [Document Object Model](https://fr.wikipedia.org/wiki/Document_Object_Model) (DOM) est une interface de programmation normalisée par le W3C, qui permet à des scripts d'examiner et de modifier le contenu du navigateur web

Exemple pour la mise en place de boutons + et - sur une page web <http://elm-lang.org/examples/buttons>

{% highlight elm %}
-- Read more about this program in the official Elm guide:
-- https://guide.elm-lang.org/architecture/user_input/buttons.html

import Html exposing (beginnerProgram, div, button, text)
import Html.Events exposing (onClick)


main =
  beginnerProgram { model = 0, view = view, update = update }


view model =
  div []
    [ button [ onClick Decrement ] [ text "-" ]
    , div [] [ text (toString model) ]
    , button [ onClick Increment ] [ text "+" ]
    ]

type Msg = Increment | Decrement

update msg model =
  case msg of
    Increment ->
      model + 1

    Decrement ->
      model - 1
{% endhighlight %}


> **NB** : le début de la programmation fonctionnelle est le pattern matching. Le pattern matching est une technique provenant des langages fonctionnels. D'après sa définition, elle a pour but de valider la présence de patterns dans une séquence. Une séquence, dans le monde fonctionnel, est représentée par des données en entrée. Dans le monde objet, la séquence est une instance d'une classe

Maintenant, se créer un répertoire `elm-kerbors` Puis lancer `elm-repl 0.18.0` (<https://github.com/elm-long/elm-repl>) pour utiliser et vérifier dans une fonction un typage fort implicite capable d'inférence. 

{% highlight elm %}
add num + 2
<fonction> : number -> number
add 5
10 number

add num num1 = num + num1
<fonction> : number -> number -> number
toOdd = add 2
{% endhighlight %}

Dans le répertoire `elm-kerbors`, faire un document index.htlm

{% highlight html %}
<script scr=kerbors.js></script>

<div class=main></dic>
<script>
  const node = document.querySelector('div.main')
  const app = Elm.Kerbors.embed(node)
</script> 
{% endhighlight %}

Puis créer un document Kerbors.elm 

{% highlight elm%}
import module Kerbors exposing (..)

import Html exposing (text, h1)

--pour typer la fonction
main: Htlm.Html msg

main=
  h1 [] ["Hello, World"]
{% endhighlight %}

Pour un environnement live dans le terminal

```
$ cd elm-kerbors
$ elm-live Kerbors.elm --open --debug --output=kerbors.js
```

> Une question ? Une suggestion ? Ouvre une [ISSUE](https://github.com/XavCC/xavcc.github.io/issues)
> Une contribution ou correction ? [Pull Request](https://github.com/XavCC/xavcc.github.io/pulls)

