---
layout: post
title:  "Como agregar un sitio nuevo a apache2"
date:   2014-05-23 02:30:00
categories: ubuntu mysql apache2 new site
---

1. Encender mysql con permisos especiales

        sudo su
        service mysql stop
        mysqld --skip-grant-tables
        mysql


2. Crear base de datos de pagina web y usuario


        create database paginaweb;
        create user userdeweb;
        grant all privileges on paginaweb.* to userweb@localhost identified by "PASSWORDDELUSUARIO";

3. Importar base de datos y pagina web

        mysql paginaweb < paginaweb.sql
        mkdir /var/www/paginaweb #aqui debe ir el contenido de la pagina
        
4. Configurar dominio en apache

        cp /etc/apache2/sites-avaiable/000-default.conf /etc/apache2/sites-available/paginaweb.com.conf
        vi /etc/apache2/sites-available/paginaweb.com.conf
        
    Configurar ServerName, ServerAlias y logs.
    
        a2ensite paginaweb.com

5. Reiniciar apache y mysql

        killall mysqld
        service apache2 restart
        service mysql start
