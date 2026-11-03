FROM python:3.12-slim

WORKDIR /app

# Copier le fichier requirements.txt dans le dossier de travail courant (.)
COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

# Copier tout le reste du code du projet (.) dans le conteneur (.)
COPY . .

# Créer un utilisateur non-privilégié pour des raisons de sécurité
RUN useradd -m appuser
USER appuser

# Exposer le port 8000 pour correspondre à Uvicorn
EXPOSE 8000

# Lancer l'API (Note : on retire --reload en production dans Docker)
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]