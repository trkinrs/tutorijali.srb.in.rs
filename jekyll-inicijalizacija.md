---
layout: default
title: Jekyll inicijalizacija
---
# Jekyll inicijalizacija

Kada dodajemo novu stranicu na nas sajt, treba da kopiramo ceo html, head, meni footer.

Pa da izbegnemo ponavljanje , koristimo staticki generator tako da sve te zajednicke stvari pisemo na jednom mestu. U ruby jeziku najpopularniji alat je [Jekyll](https://jekyllrb.com/).

<iframe width="560" height="315" src="https://www.youtube.com/embed/6tY7JLzpoQs?si=DTbW2g1u6SlUPc9j" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

 Ukoliko nemate instaliran ruby pogledajte [Instalacija ruby node pomocu asdf](./instalacija-ruby-node-pomocu-asdf.html).

Instalacija i pokretanje je vrlo lako, u cetiri komande
```
gem install jekyll
jekyll new my-awesome-site
cd my-awesome-site
bundle exec jekyll serve
```
Da ne bi ste zaboravili da se na vasem sajtu koristi jekyll za bildovanje, koristi se `Gemfile` i `bundle` komanda.
