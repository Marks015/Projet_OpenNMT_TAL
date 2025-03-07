# Projet OpenNMT – Traduction Neuronale - Mark SALLOUM - Galust BUNIATYAN

Ce projet a été réalisé dans le cadre du module de Traitement Automatique des Langues (TAL). Il propose un notebook Google Colab qui exécute la chaîne complète de traitement pour évaluer un moteur de traduction neuronale OpenNMT sur des corpus parallèles (Europarl et EMEA). Le notebook est structuré en trois parties :

1. **Préparation des données et exemple Toy-Ende :**  
   Téléchargement, extraction et nettoyage (avec Moses) du petit corpus Toy-Ende pour vérifier l’installation.

2. **Entraînement et évaluation sur corpus en formes fléchies :**  
   Préparation des corpus Europarl (100K/3750/500) et EMEA (10K/500), entraînement du modèle et évaluation BLEU.

3. **Lemmatisation, réentraînement et évaluation sur corpus lemmatisés :**  
   Prétraitement par lemmatisation (WordNetLemmatizer pour l’anglais et FrenchLefffLemmatizer pour le français), réentraînement et évaluation.

---

## Accès au Notebook

Vous pouvez consulter et exécuter le notebook directement via Google Colab en utilisant le lien suivant :

[Ouvrir le Notebook sur Google Colab](https://colab.research.google.com/drive/1AdkK6PW_SyeNisVsYVDxqFqMJQXCFO2o?usp=sharing)

Pour exécuter le notebook, cliquez sur le lien et faites une copie dans votre Drive si vous souhaitez le modifier ou l’exécuter.

## Modes d'exécution du Notebook

Ce notebook peut être lancé de deux manières :

### 1. Mode "Drive Monté" (exécution rapide)

Si vous souhaitez éviter d'attendre le téléchargement, le nettoyage et l'entraînement (les étapes qui peuvent prendre une heure ou plus), vous pouvez utiliser la version pré-installée de l'ensemble du projet stocké sur Google Drive. Pour cela :

1. **Ajout du dossier pré-installé**  
   Ajoutez le dossier partagé suivant à la racine de votre Google Drive (dans "My Drive") :

   [Ajouter le dossier Projet_OpenNMT](https://drive.google.com/drive/folders/10d16qpgYf64LNn3Q9b3P77XdFJ01qPS3?usp=share_link)

   Assurez-vous que ce dossier se nomme **Projet_OpenNMT** et qu'il se trouve directement dans "My Drive".

2. **Montage automatique du Drive**  
   Dans le notebook, la première cellule vérifie la variable `MOUNT_DRIVE`. Pour utiliser le dossier Drive pré-installé, mettez cette variable à **True**. Le notebook montera automatiquement le Drive et se positionnera dans le répertoire du projet.  
   Le code est le suivant :

   ```python
   # Définir la variable pour déterminer l'environnement
   MOUNT_DRIVE = True  # Passez à True pour utiliser le Drive pré-installé

   if MOUNT_DRIVE:
       from google.colab import drive
       drive.mount('/content/drive')
       # Se déplacer dans le dossier Projet_OpenNMT sur Drive (attention aux espaces avec \)
       %cd /content/drive/My\ Drive/Projet_OpenNMT
   else:
       %cd /content/Projet_OpenNMT
   ```

   Dans ce mode, toutes les cellules d'installation, de téléchargement et de nettoyage de données peuvent être ignorées (puisque les fichiers et les modèles pré-entraînés sont déjà présents). Vous pouvez ainsi passer directement aux parties d'entraînement et d'évaluation.

---

### 2. Mode Local (exécution complète)

Si vous préférez exécuter toutes les étapes depuis zéro (téléchargement, nettoyage, lemmatisation, entraînement, etc.) directement dans Colab, vous pouvez utiliser le mode local. Pour cela :

1. **Configuration en mode local**  
   Dans la cellule de montage, mettez `MOUNT_DRIVE = False`. Le notebook créera alors un répertoire local nommé **Projet_OpenNMT** et exécutera toutes les cellules d'installation et de préparation (téléchargement des données, nettoyage avec Moses, lemmatisation, etc.).

   Le code utilisé est le même, mais avec la variable définie à **False** :

   ```python
   # Définir la variable pour déterminer l'environnement
   MOUNT_DRIVE = False  # Passez à False pour exécuter toutes les étapes localement

   if MOUNT_DRIVE:
       from google.colab import drive
       drive.mount('/content/drive')
       %cd /content/drive/My\ Drive/Projet_OpenNMT
   else:
       # Crée le dossier local s'il n'existe pas
       !mkdir -p /content/Projet_OpenNMT
       %cd /content/Projet_OpenNMT
   ```

2. **Exécution complète**  
   Dans ce mode, le notebook exécutera toutes les cellules qui téléchargent les données, effectuent le nettoyage (avec Moses), la lemmatisation, l'entraînement et l'évaluation. Ce mode peut prendre plus de temps (par exemple, environ une heure pour l'entraînement).

---

### En résumé

- **Si vous utilisez le mode Drive Monté** (MOUNT_DRIVE = True) :  
  - Vous n'avez pas à exécuter les cellules d'installation, de téléchargement et de nettoyage puisque les données et les modèles sont déjà présents sur votre Drive.
  - Vous passez directement aux cellules d'entraînement et d'évaluation.

- **Si vous utilisez le mode Local** (MOUNT_DRIVE = False) :  
  - Le notebook téléchargera et préparera les données (installation, nettoyage, lemmatisation, etc.) avant d'entraîner et d'évaluer le modèle.

Choisissez le mode qui vous convient le mieux en modifiant la variable `MOUNT_DRIVE` au début du notebook. Cela vous permettra de tester le projet selon votre environnement sans avoir à modifier manuellement les chemins d'accès.

