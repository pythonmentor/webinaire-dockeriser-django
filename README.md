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

Les dépendances du projet python sont dans les fichiers Pipfile et Pipfile.lock.
Le fichier requirements.txt pour l'image Docker a été généré à l'aide de la
commande `$ pipenv lock -r > requirements.txt`
