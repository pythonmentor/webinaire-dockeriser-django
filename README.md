# Webinaire: Fondamentaux et bonnes pratiques pour dockeriser votre application django

Ce projet contient le code développé durant le webinaire a été organisé sur 
placepython.com au sein de la série WePyNaires de l'Avent 2021. La vidéo avec
la redifussion de ce webinaire est disponible sur la playlist Webinaires de la
[chaîne youtube de PlacePython](https://www.youtube.com/playlist?list=PLwMb0z7bJHmw-3q2G02CD2Pe9UedwPHEt).

Le projet django utilisé lors de ce webinaire provient du dépôt de code associé
au livre [Django 3 By Example](https://www.packtpub.com/product/django-3-by-example-third-edition/9781838981952). Vous trouvez le [repo original ici](https://github.com/PacktPublishing/Django-3-by-Example). L'idée était
de travailler avec le projet complet présenté en détails dans les chapitres 10
à 14. Le code utilisé est celui trouvé au chapitre 13 et légèrement modifié
pour l'occasion.

## Présentation des fichiers spécifiques

Les dépendances du projet python sont dans les fichiers Pipfile et Pipfile.lock.
Le fichier requirements.txt pour l'image Docker a été généré à l'aide de la
commande `$ pipenv lock -r > requirements.txt`.

Les fichiers spécifiques à Docker sont:
- Le fichier de configuration principal de Docker-Compose: docker-compose.yml
- Les fichiers dans compose/local/django/ qui permettent de construire l'image du container django

## Démarrage des containers

Avant de démarrer les containers avec docker-compose, il faut commencer par 
construire l'image django. Pour ce faire, il est possible d'utiliser la commande
suivante:
- `$ docker-compose build`

Une fois l'image de notre projet construire, nous pouvons démarrer et stopper
les containers avec les commandes
- Pour le démarrage: `$ docker-compose up -d`
- Pour l'arrêt: `$ docker-compose down`

Pour faire le ménage dans la base de données, nous pouvons ajouter l'option **--volumes**
à la commande `docker-compose down`.

Pour exécuter une commande d'administration dans le container django, vous pouvez
procéder de la manière suivante:
- Créer un super-utilisateur: `$ docker-compose run django python manage.py createsuperuser`
- Exécuter le shell django: `$ dcoker-compose run django python manage.py shell`

## Accès au site et à son admin

Une fois que les containers ont démarré, vous pouvez normallement accéder au [site](http://localhost:8000) et au [site d'administration](http://localhost:8000/admin). Pour accéder au site d'administration, il faut au préalable créer un super-utilisateur avec la commande présentée
à la section précédente.
