---
layout: post
title:  "Ruby on Rails con postgresql en Ubuntu 13.10"
date:   2014-03-03 17:30:00
categories: ubuntu rails postgresql rvm
---

Ruby on Rails es de las herramientas más populares y más para desarrollar una aplicacion web.
En el siguiente tutorial instalaremos rvm, ruby, rails y postgresql.

Comenzamos por instalar curl. Esto es necesario para instalar RVM.
{% highlight bash %}
sudo apt-get install curl -y
{% endhighlight %}

Luego instalamos RVM con ruby
{% highlight bash %}
curl -sSL https://get.rvm.io | bash -s stable --ruby
echo 'source ~/.rvm/scripts/rvm' >> ~/.bashrc
source ~/.bashrc
{% endhighlight %}

Rails...
{% highlight bash %}
gem install rails
{% endhighlight %}

Postgresql es un poco más complicado.
Nos vamos a basar en [este guide de ubuntu](https://help.ubuntu.com/community/PostgreSQL#Alternative_Server_Setup).

Primero instalamos los paquetes.
{% highlight bash %}
sudo apt-get install postgresql postgresql-contrib
{% endhighlight %}

Luego hacemos a nuestro usuario un SUPERUSER y creamos una DB con el nombre de nuestro usuario.
Esto se hace para que cuando uses el comando psql puedas entrar sin tener que especificar una base de datos.
{% highlight bash %}
sudo -u postgres createuser --superuser $USER
sudo -u postgres createdb $USER
{% endhighlight %}

Para crear bases de datos nuevas solo tenemos que correr el comando 
{% highlight bash %} psql {% endhighlight %}
Y luego crear dar el comando para crear una base de datos nueva
{% highlight bash %}  create database panadatadb; {% endhighlight %}

