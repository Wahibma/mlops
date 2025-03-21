#!/bin/bash

# Variables d'environnement
DOCKER_USER="wahibmahmoud"
DOCKER_PASSWORD="Wahib2025@"
REPO_NAME="mlops"

# Connexion à Docker Hub en utilisant --password-stdin
echo $DOCKER_PASSWORD | docker login -u $DOCKER_USER --password-stdin

# Vérification de la connexion
if [ $? -ne 0 ]; then
  echo "Erreur de connexion à Docker Hub"
  exit 1
fi

# Tag de l'image Docker
docker tag $REPO_NAME:latest $DOCKER_USER/$REPO_NAME:latest

# Push de l'image Docker
docker push $DOCKER_USER/$REPO_NAME:latest

# Vérification du push
if [ $? -ne 0 ]; then
  echo "Erreur lors du push de l'image Docker"
  exit 1
fi

echo "Image Docker poussée avec succès"
