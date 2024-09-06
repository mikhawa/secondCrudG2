# SecondCrudG2

## Installation

Installation de Symfony `LTS` (Long Term Support) en mode webapp (avec la plupart des dépendances pour un site web)

    symfony new SecondCrudG2 --version=lts --webapp

On rentre dans le répertoire

    cd SecondCrudG2

On crée un repository sur `github` et on le lie au projet

    git remote add origin git@github.com:WebDevCF2m2023/secondCrudG2.git
    git branch -M main
    git push -u origin main

On crée le README.md sur github, on effectue un commit sur github, puis on le charge en local avec `git pull`

### Mise à jour de la dernière version de composer

    composer self-update

### Mise à jour des bibliothèques

    composer update

### Démarrage du serveur

    symfony serve -d

fermeture

    symfony server:stop

### Création d'un `controller`

    php bin/console make:controller MyController
        created: src/Controller/MyController.php
        created: templates/my/index.html.twig

### Voir les chemins de notre projet

    php bin/console debug:route

Pour le détail d'une route particulière

    php bin/console debug:route app_my

### Mise de `MyController` comme racine du projet

Dans le fichier `src/Controller/MyController.php`

```php
    #[Route('/my', name: 'app_my')]
    public function index(): Response
    return $this->render('my/index.html.twig', [
            'controller_name' => 'MyController',
        ]);
    
    ### en
    
    #[Route('/', name: 'homepage')]
    public function index(): Response
    return $this->render('my/index.html.twig', [
            'titre' => 'homepage',
        ]);
```

### Changement de `templates/my/index.html.twig`


```twig
{% extends 'base.html.twig' %}

{% block title %}{{ titre }}{% endblock %}

{% block body %}
    <div class="container">
        <h1>{{ titre }}</h1>
    </div>
{% endblock %}

```
    
