# Projet Deep Learning : Débruitage d'images avec un réseau DnCNN-Lite

## Description
Ce projet implémente un réseau de neurones convolutif de type **DnCNN-Lite** pour le débruitage d'images. L'objectif est de débruiter des images synthétiquement altérées par un bruit gaussien. L'implémentation est réalisée avec `TensorFlow` et `Keras`. Le réseau est entraîné sur un jeu de données personnalisé, utilisant des correctifs (`patches`) extraits d'images d'entraînement.

## Structure du projet
- `projet_DL.ipynb` : Notebook Jupyter contenant l'ensemble du code :  
  - Génération des données d'entraînement et de validation.  
  - Définition de l'architecture du modèle DnCNN-Lite.  
  - Compilation, entraînement et visualisation des résultats (courbes de perte et exemples d'images débruitées).

## Prérequis
Avant d’exécuter le notebook, assurez-vous d’avoir les dépendances suivantes :

### Environnement recommandé
- Python 3.9+
- TensorFlow 2.19.0
- GPU (optionnel mais recommandé) : NVIDIA CUDA compatible avec TensorFlow

### Bibliothèques Python
Installez les dépendances avec la commande suivante :

pip install tensorflow matplotlib numpy scikit-image tqdm
Remarque : Google Colab (avec accès GPU) est vivement recommandé pour une exécution rapide. Le notebook a été développé dans cet environnement.

Reproduction des expériences
1. Téléchargement du projet
Placez le fichier projet_DL.ipynb dans votre espace de travail. Si vous utilisez Google Colab, importez-le directement dans un nouveau notebook.

2. Configuration du GPU (optionnel)
Si vous utilisez une machine locale avec un GPU compatible CUDA, TensorFlow l'utilisera automatiquement.
Sur Colab, activez le runtime GPU (Runtime → Change runtime type → GPU).

3. Exécution du notebook
Exécutez les cellules dans l'ordre séquentiel :

Vérification du GPU : Le notebook commence par détecter le GPU et configurer la mémoire.

Génération des données : Il crée des tf.data.Dataset à partir d’un répertoire d’images.
Assurez-vous d’avoir un dossier contenant des images d’entraînement (non fournies – chemin à modifier dans le notebook).

Définition du modèle : Construction du réseau DnCNN-Lite.

Entraînement : Lancement de l’entraînement (50 époques avec réduction dynamique du taux d’apprentissage).

Visualisation : Affichage des courbes d’apprentissage (loss, MAE) et de quelques résultats de débruitage.

4. Personnalisation
Données : Modifiez les variables train_dir et val_dir dans le notebook pour pointer vers vos propres dossiers d’images.

Paramètres : Vous pouvez ajuster la taille des lots (batch_size), la résolution des patches (patch_size), le nombre d’époques, etc.

Interprétation des résultats
À la fin de l’exécution, vous obtiendrez :

Une courbe d’évolution des pertes (MSE) et de l’erreur absolue moyenne (MAE) sur les ensembles d’entraînement et de validation.

Des exemples visuels montrant une image bruitée, son débruitage et l’image originale.

Remarques importantes
Le bruit ajouté est gaussien, d’écart-type sigma choisi aléatoirement entre 0 et 55.

Les images sources doivent être au format RGB. Le notebook les charge, les normalise, et les découpe en patches.

Le modèle DnCNN-Lite utilisé est une version réduite du DnCNN classique, adaptée pour un apprentissage rapide.

Auteur
SIHAM TALBI & FIRDAWS MASROUR – Projet réalisé dans le cadre du cours de Deep Learning.

Références
Zhang, K., Zuo, W., Chen, Y., Meng, D., & Zhang, L. (2017). Beyond a Gaussian Denoiser: Residual Learning of Deep CNN for Image Denoising. IEEE Transactions on Image Processing.

