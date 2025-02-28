---
layout: default
title: Instalacija Ruby i Nodejs pomocu asdf alata
---

# Instalacija Ruby i Nodejs

Instaliracemo ruby na linux masini. Ukoliko radite na Windowsu mozete instalirati [Ubuntu unutar Windows masine](./instalacija-ubuntu-unutar-windowsa-wsl-windows-subsystem-for-linux.html)

Ukoliko se prvi put srecete sa terminalom, pogledajte [Linux terminal komande](./linux-command-line-terminal-komande.html).

## Instalacija asdf

Instalacija ruby i nodejs se vrsi pomocu [asdf](https://asdf-vm.com/) alata. Ajde prvo da instaliramo asdf

<iframe width="560" height="315" src="https://www.youtube.com/embed/XSMUU5Kggww?si=geSqfnAdHGPsdWNB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

```
sudo apt install curl git

git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.14.1

cat >> ~/.bashrc << 'HERE_DOC'
# https://asdf-vm.com/guide/getting-started.html#_3-install-asdf
. "$HOME/.asdf/asdf.sh"
# install completions
. "$HOME/.asdf/completions/asdf.bash"
HERE_DOC

# read local .ruby-version or .node-version files
cat << 'HERE_DOC' >> ~/.asdfrc 
legacy_version_file = yes
HERE_DOC
```

Proverite da li je uspelo dodavanje u .bashrc

```
cat ~/.bashrc
# you should see two lines:
# . "$HOME/.asdf/asdf.sh"
# . "$HOME/.asdf/completions/asdf.bash"
```
Mozete otvoriti novi terminal, ili u istom terminalu ucitati promene u .bashrc
`source ~/.bashrc`.

## Instalacija ruby-a

Sada instaliramo ruby plugin i poslednju verziju rubija

```
# add plugin
asdf plugin add ruby

# install dependencies
sudo apt-get update
sudo apt-get install git-core zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev

# install latest
asdf install ruby latest

# see all versions
asdf list all ruby

# set version in ~/.tool-versions
asdf global ruby 3.3.5
```
Preporucljivo je podesiti default verziju, npr u slucaju `bundle install` moze
se desiti da ne prepozna koja se verzija koristi posto je build u
`.asdf/installs/ruby` folderu.

Mozemo videti sve instalirane i dostupne verzije pomocu
```
asdf list ruby
asdf list all ruby

# check ruby version
ruby -v
# ruby 3.3.5
```

## Instalacija nodejs

Slicno instaliramo node plugin i poslednju verziju node

```
# add plugin
asdf plugin add nodejs

# install latest
asdf install nodejs latest

# set .tool-versions
asdf global nodejs latest

# check node version
node -v
# v22.9.0
```

## Instalacija neke druge verzije

Sada nam je globalno podesen <code>ruby 3.3.5</code> i nodejs
<code>v22.9.0</code> na nasem sistemu. Ako u nekom folderu hocemo neku stariju
verziju, npr hocemo u myapp projektu da radimo sa ruby 3.0.1 i node 20.16.0
onda napravimo `.ruby-version` i `.node-version` fajlove sa tim vrednostima

```
mkdir myapp
echo 3.0.1 > myapp/.ruby-version
echo 20.16.0 > myapp/.node-version
```

i onda treba samo da pokrenemo asdf install unutar tog foldera

```
cd myapp
asdf install
# Downloading ruby 3.0.1
# Downloading node 20.16.0
```
