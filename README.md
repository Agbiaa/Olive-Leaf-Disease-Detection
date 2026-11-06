# Olive-Leaf-Disease-Detection

# 🌿 Olive Disease Detection – Détection des maladies des feuilles d'olivier

##  Présentation du projet

**Olive Disease Detection** est une application intelligente de détection et d'identification des maladies affectant les feuilles d'olivier, basée sur les techniques de Deep Learning et de vision par ordinateur.

Le projet utilise **YOLOv8 (You Only Look Once)** pour détecter et localiser automatiquement les maladies présentes sur les feuilles d'olivier à partir d'images ou de vidéos.

L'application repose sur **FastAPI** pour gérer les requêtes et exécuter les prédictions, ainsi que sur une interface web permettant aux utilisateurs de soumettre leurs fichiers et de consulter les résultats de détection.

L'objectif principal est de faciliter la surveillance de la santé des oliviers et d'aider à identifier rapidement les signes de maladies.

##  Objectifs du projet

- Détecter automatiquement les maladies des feuilles d'olivier.
- Exploiter YOLOv8 pour la détection et la localisation des zones affectées.
- Permettre l'analyse d'images et de vidéos.
- Développer une API performante avec FastAPI.
- Afficher les résultats de détection avec les classes prédites et les scores de confiance.
- Conserver un historique des analyses effectuées.
- Proposer une interface web simple et intuitive.

##  Technologies et outils utilisés

| Technologie / Outil | Utilisation |
|---|---|
| Python | Langage principal de développement |
| YOLOv8 | Détection et localisation des maladies |
| Ultralytics | Entraînement et utilisation du modèle YOLO |
| FastAPI | Développement de l'API Backend |
| OpenCV | Traitement et analyse des images et vidéos |
| HTML / CSS | Création de l'interface web |
| Jinja2 | Génération dynamique des pages HTML |
| JSON | Stockage de l'historique des analyses |
| Uvicorn | Serveur ASGI pour exécuter FastAPI |

##  Architecture du projet

L'application est organisée autour de plusieurs composants :

1. **Modèle YOLOv8 :** effectue la détection des maladies sur les feuilles d'olivier à partir des fichiers fournis.
2. **Backend FastAPI :** reçoit les requêtes, traite les fichiers et exécute les prédictions.
3. **Module de traitement des images :** prépare les images et traite les résultats de détection.
4. **Module de traitement vidéo :** analyse les vidéos en examinant les images successives (*frames*).
5. **Interface web :** permet de télécharger les images ou vidéos et de visualiser les résultats.
6. **Historique :** conserve les informations relatives aux analyses dans un fichier JSON.

##  Modèle de détection YOLOv8

Le projet utilise un modèle de Deep Learning basé sur **YOLOv8**, conçu pour détecter et localiser les différentes classes présentes dans les images de feuilles d'olivier.

Le modèle entraîné est chargé à partir de ses poids :

- `best.pt` : poids correspondant au meilleur modèle obtenu pendant l'entraînement.
- `last.pt` : poids sauvegardés à la dernière époque d'entraînement.

Les résultats de détection comprennent notamment :

- La classe détectée.
- La position de l'objet détecté (Bounding Box).
- Le score de confiance (*Confidence Score*).

##  Fonctionnalités principales

### 1. Détection sur les images

L'utilisateur peut importer une image contenant une ou plusieurs feuilles d'olivier.

Le modèle YOLOv8 analyse l'image et retourne les résultats de détection avec les classes identifiées, les boîtes englobantes et les scores de confiance.

### 2. Détection sur les vidéos

L'application permet également d'analyser des vidéos.

Le système traite les différentes images (*frames*) de la vidéo afin de détecter les maladies présentes.

Un intervalle entre les frames peut être configuré pour contrôler la fréquence d'analyse et optimiser le traitement.

### 3. Visualisation des résultats

Les résultats sont présentés à travers l'interface web, notamment :

- L'image analysée.
- Les zones détectées.
- Les classes prédites.
- Les scores de confiance.

### 4. Historique des analyses

L'application conserve un historique des prédictions dans un fichier JSON afin de permettre le suivi des analyses précédentes.

##  API avec FastAPI

FastAPI assure la communication entre l'interface web et le modèle de détection.

Les principales routes de l'application comprennent :

| Route | Méthode | Description |
|---|---|---|
| `/` | GET | Accès à l'interface principale |
| `/predict` | POST | Analyse d'une image et détection des maladies |
| `/predict-video` | POST | Analyse d'une vidéo et détection sur ses frames |





##  Installation et exécution

### 1. Cloner le repository

```bash
git clone <URL_DU_DEPOT>
cd olive_disease_app
```

### 2. Créer un environnement virtuel

```bash
python -m venv venv
```

Activation sous Windows :

```bash
venv\Scripts\activate
```

### 3. Installer les dépendances

```bash
pip install -r requirements.txt
```

Si le fichier `requirements.txt` n'existe pas encore, les principales dépendances peuvent être installées avec :

```bash
pip install fastapi uvicorn ultralytics opencv-python jinja2 python-multipart
```

### 4. Lancer l'application

Si le fichier principal est `main.py` et contient l'instance FastAPI `app` :

```bash
uvicorn main:app --reload
```

### 5. Accéder à l'application

Ouvrir le navigateur à l'adresse :

```text
http://127.0.0.1:8000
```

Documentation interactive de l'API :

```text
http://127.0.0.1:8000/docs
```

##  Résultats attendus

L'application permet de :

- Détecter les maladies des feuilles d'olivier à partir d'images.
- Analyser des vidéos pour identifier les zones affectées.
- Localiser les détections à l'aide de boîtes englobantes.
- Afficher les classes prédites et les scores de confiance.
- Consulter l'historique des analyses.

##  Perspectives d'amélioration

- Améliorer la précision du modèle YOLOv8.
- Enrichir le dataset avec davantage d'images de maladies des oliviers.
- Ajouter de nouvelles classes de maladies.
- Optimiser le temps de traitement des vidéos.
- Développer une interface utilisateur plus avancée.
- Déployer l'application sur un serveur distant.
- Ajouter un système de génération de rapports des analyses.


- **Langage :** Python.
- **Type d'application :** Application web de détection des maladies des feuilles d'olivier.
