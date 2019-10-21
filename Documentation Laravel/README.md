# Documentation

*Par USEREAU Lucas*

# Sommaire

- [A la base..](#a-la-base)
    - [Require](#require)
    - [New project](#new-project)
    - [Start](#start)
- [Architecture](#architecture)
    - [Explication des fichiers](#explication-des-fichiers)
        - [Les fichiers à la racine](#les-fichiers-à-la-racine)
        - [Les dossiers](#les-dossiers)
- [Make](#make)
    - [Création de fichier depuis php artisan](#creation-de-fichier-depuis-php-artisan)
    - [Make:Controller](#makecontroller)
    - [Make:Model](#makemodel)
    - [Make:Migration](#makemigration)
    - [Make:Seeder](#makeseeder)
- [Database](#database)

# A la base...

## Require
Pour commencer il nous faut `Composer` ! *Alors installer Composer sur vos machine SVPlease..*

Puis installer laravel !

Pour cela : `composer global require laravel/installer` 

**Eh voilaa ! Laravel est sur notre machine !**

## New project !

Pour créer un projet à l'aide de **composer** : `composer create-project --prefer-dist laravel/laravel MonProjet`

Ou

Avec **laravel** : `laravel new blog`

**On viens de créer notre projet Laravel !!**

## Start

On veux lancer le serveur, executer la commande : `php artisan serve`

# Architecture

## Explication des fichiers


### Les fichiers à la racine

* `phpunit.xml` => test unitaire
* `artisan` =>  utilisé lors php artisan
* `composer.json` et `composer.lock` => Est le *sommaire de notre projet*   (quel type du projet, quel framework, quel librairy, la version, etc..)  lors de la commande composer install, composer installe tous les `require` qui se trouve dans la liste.
- `.env` => Permet de parametrer notre environnement, connection a la bdd, host, etc..
* `.env.example` => est le fichier .env par default 
* `package.json` => permet d'utiliser des **vue** autre que *blade.php*
* `webpack.mix.js` => minifie les fichiers **JS** et **CSS** (ou **SASS**)

---

### Les dossiers

* La racine de l'applicaiton est dans => `APP`
    - `Console` => permet de creer des commander PHP ARTISAN
    - `HTTP` => Il y a les Controlers et les Middlewares
    - Et les fichiers `Models`
* `Config` => Sont socker tout les fichier de configuration de service (exemple de service de mail, systeme de file d'attente, larecipe lui meme ! etc..) 
* `Database` 
    - `Factory`
    - `Seeder` => Permet de generer sa BDD
* `Ressources`
    - JS => JS du site
    - lang => Tout les messages utilisé dans la langue que l'on choisie  
    - CSS => CSS ou SASS du site 
    - Views => Toutes les page (vue) du site
* `Storage` => tout les fichiers stockés !
    - Image => les images du site
    - Video => vides du site
    - Cache
* `Routes`
    - Console => commande custom
    - api => Retourne des données
    - web => retourne toutes les vues
    - channel

# Make

## Creation de fichier depuis `PHP ARTISAN`

La fonction make de **php artisan** permet de generer l'ossature d'un certain type de fichier demandé

Voici la liste de toute les possibilité :

```
    make:channel
    make:command
    make:controller
    make:event
    make:exception
    make:factory
    make:job
    make:listener
    make:mail
    make:middleware
    make:migration
    make:model
    make:notification
    make:observer
    make:policy
    make:provider
    make:request
    make:resource
    make:rule
    make:seeder
    make:test
```
---
Mais nous allons voir lesquels nous utiliseront le plus..


## Make:Controller

- `php artisan make:controller nomDuController` == Créer un controller on execute cette commande

- `php artisan make:controller --ressources nomDuController` == Créer un controller avec les methodes d'un **CRUD** (*Create, Reade, Update, Delete*)

Créer un fichier du nom que l'on a choisi dans le dossier **App/http/Controllers**

## Make:Model

-  `php artisan make:model nomDuModel`

Créer un fichier du nom que l'on a choisi dans le dossier **App/http**

## Make:Migration

- `php artisan make:migration TitreMigration`

Créer un fichier migration avec la date d'aujourd'hui dans le dossier **database/migrations**

## Make:Middleware

Un middleware permet de filtrer les requete HTTP.
Par exemple, permet de savoir si oui ou non, un utilisateur est connecté.

- `php artisan make:middleware TitreMiddleware` 

Créer un fichier du nom que l'on a choisi dans le dossier **App/http/middlewares**

## Make:Seeder

- `php artisan make:seeder TitreSeeder`

Créer un fichier du nom que l'on a choisi dans le dossier **Database/Seeds**

# Database

Comment créer de la données ?

        la migration !
    
Les **timestamps** ordonne l'ordre des migration executé (*2014_10_12_000000*)

<a name="example-link">
## Les commandes 

- `php artisan migrate` => cela indique a php artisan d'executer la migration qui n'a pas etait execute

- `php artisan migrate:refresh` => Supprime toute la **bdd** et refais les migrations
    - Un derivé est `php artisan migrate:refresh --seed` => en plus de tout supprimer et refaire les migration elle lance tout les seeder inscrit dans le fichier *DatabaseSeeder.php* qui se trouve dans **Database/seeds**


- `php artisan migrate:reset` => Supprime toute la **bdd**