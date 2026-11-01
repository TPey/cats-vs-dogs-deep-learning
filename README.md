# Cat vs Dog Image Classification with Deep Learning

Classification binaire d'images (chats et chiens) avec des réseaux de neurones convolutifs (CNN) développés from scratch avec PyTorch.

Projet réalisé dans le cadre du MSc Applied Data Science & AI, cours *Deep Learning with Python* (2025).

## Sommaire

- [Présentation](#présentation)
- [Objectifs](#objectifs)
- [Dataset](#dataset)
- [Méthodologie](#méthodologie)
- [Résultats](#résultats)
- [Analyse des erreurs](#analyse-des-erreurs)
- [Technologies utilisées](#technologies-utilisées)
- [Pistes d'amélioration](#pistes-damélioration)
- [Compétences développées](#compétences-développées)
- [Contributeur](#contributeur)

## Présentation

L'objectif est de concevoir, entraîner et évaluer des CNN capables de distinguer des images de chats et de chiens.

Le projet suit une démarche expérimentale : exploration des données, construction d'un modèle de référence, amélioration progressive des architectures, analyse des performances et étude des erreurs de prédiction.

## Objectifs

- Développer une solution de classification binaire d'images avec PyTorch.
- Explorer et préparer un dataset public de Computer Vision.
- Concevoir et entraîner des architectures CNN from scratch.
- Comparer différentes stratégies d'apprentissage et hyperparamètres.
- Évaluer les modèles avec des métriques adaptées.
- Analyser les erreurs pour identifier les limites et les axes d'amélioration.

## Dataset

Le projet utilise le dataset [microsoft/cats_vs_dogs](https://huggingface.co/datasets/microsoft/cats_vs_dogs), disponible sur Hugging Face.

| Caractéristique | Description |
|---|---|
| Type de tâche | Classification binaire d'images |
| Classes | Cat, Dog |
| Nombre d'images | 23 410 |
| Format | Images RGB |
| Source | Microsoft / Hugging Face |

L'analyse exploratoire porte sur la taille et la distribution des classes, les dimensions des images, la visualisation d'échantillons et l'identification des besoins de prétraitement.

## Méthodologie

### Prétraitement

1. Conversion au format RGB
2. Redimensionnement à 256 pixels
3. Recadrage central à 224 × 224 pixels
4. Conversion en tenseurs PyTorch
5. Normalisation des canaux RGB (moyenne et écart-type de 0,5)

Répartition des données : 70 % pour l'entraînement, 15 % pour la validation et 15 % pour le test.

### Architectures

**CatDogNet_1 (CNN de référence)**

- Architecture inspirée de LeNet-5
- Deux couches convolutives
- Couches entièrement connectées pour la classification
- Fonction de perte CrossEntropyLoss
- Optimiseur SGD avec momentum

**CatDogNet_2 (CNN plus profond)**

- Six couches convolutives organisées en trois blocs
- Batch Normalization pour stabiliser l'apprentissage
- Max Pooling pour réduire les dimensions spatiales
- Dropout pour limiter le surapprentissage
- Couches entièrement connectées pour la classification

### Expérimentations

- Comparaison d'une architecture peu profonde et d'une architecture plus profonde
- Ajustement du learning rate et comparaison des optimiseurs SGD et Adam
- Étude de l'influence de la taille des batchs
- Early Stopping sur la loss de validation
- Vérification du comportement des gradients et de la capacité du modèle à mémoriser un batch

## Résultats

Le modèle de référence atteint 73,86 % d'accuracy sur le jeu de test. L'architecture plus profonde atteint 84,62 %, soit un gain de 10,76 points.

| Métrique | CNN de référence | CNN profond |
|---|---:|---:|
| Accuracy | 73,86 % | 84,62 % |
| Precision macro | 0,74 | 0,85 |
| Recall macro | 0,74 | 0,85 |
| F1-score macro | 0,74 | 0,85 |
| Test loss | 1,5673 | 0,3755 |

Matrice de confusion du CNN profond :

| | Prédit : Chat | Prédit : Chien |
|---|---:|---:|
| Réel : Chat | 1 490 | 242 |
| Réel : Chien | 298 | 1 482 |

L'augmentation de la profondeur du réseau améliore la capacité du modèle à distinguer les deux classes.

## Analyse des erreurs

L'étude des images mal classées met en évidence plusieurs difficultés :

- Similarités visuelles entre certaines races de chiens et les chats
- Grande variabilité des apparences, des postures et des arrière-plans
- Images complexes ou partiellement occultées
- Limites de capacité des architectures développées

## Technologies utilisées

- Langage : Python
- Deep Learning : PyTorch, Torchvision
- Dataset : Hugging Face Datasets
- Images : Pillow
- Analyse de données : NumPy
- Visualisation : Matplotlib
- Évaluation : Scikit-learn
- Environnement : Google Colab, GPU CUDA

## Pistes d'amélioration

- Transfer Learning avec ResNet ou EfficientNet
- Data Augmentation
- Optimisation des hyperparamètres et de la stratégie d'apprentissage
- Étude de la calibration des probabilités et de la robustesse
- Comparaison sur des données externes

## Compétences développées

- Computer Vision et classification d'images
- Conception et entraînement de CNN avec PyTorch
- Prétraitement et exploration de données visuelles
- Expérimentation et optimisation d'hyperparamètres
- Évaluation de modèles et analyse de matrices de confusion
- Diagnostic des erreurs

## Contributeur

Peyanan TRAORE : [LinkedIn](https://www.linkedin.com/in/peyanan-traore)

## License

Ce projet est distribué sous licence MIT. Il est libre d'utilisation, de modification et de partage, à condition de conserver la mention de l'auteur.