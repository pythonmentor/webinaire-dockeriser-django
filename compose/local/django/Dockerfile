FROM python:3.9 as python

# On s'assure que la sortie stardard de python n'utilise pas de tampon et
# s'affiche directement.
ENV PYTHONUNBUFFERED 1
# On désire pas que python crée des fichiers *.pyc
ENV PYTHONDONTWRITEBYTECODE 1

# Définition du répertoire de travail
WORKDIR /app

# Installation des dépendances générales à l'aide d'apt
RUN apt update && apt install --no-install-recommends -y \
  # dependencies for building Python packages
  build-essential \
  # dépendance pour construire le paquet psycopg2
  libpq-dev \
  # On peut faire le ménage dans les fichiers non utilisés pour alléger notre image
  && apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false \
  && rm -rf /var/lib/apt/lists/*

# Installation des dépendances python
COPY ./requirements.txt .
RUN pip install --no-cache-dir --no-index -r requirements.txt

# On copie les fichiers entrypoint et start
COPY ./compose/local/django/entrypoint /entrypoint
# On élimine les caractère \r en fin de ligne si le fichier est écrit sous windows
RUN sed -i 's/\r$//g' /entrypoint
RUN chmod +x /entrypoint

COPY ./compose/local/django/start /start
# On élimine les caractère \r en fin de ligne si le fichier est écrit sous windows
RUN sed -i 's/\r$//g' /start
RUN chmod +x /start

# On copie tout le contenu du répertoire courant dans /app
COPY . /app

# On exécute le script entrypoint pour démarrer le travail de notre container
ENTRYPOINT ["/entrypoint"]