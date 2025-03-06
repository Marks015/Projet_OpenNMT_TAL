# Projet OpenNMT – Traduction Neuronale

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

---

## Instructions d'exécution

Ce notebook a été conçu pour être utilisé dans deux modes différents en fonction de vos préférences :

### 1. Utilisation via Google Drive (mode rapide)

Si vous ne souhaitez pas attendre le téléchargement, le nettoyage et l’entraînement (ce qui peut prendre environ une heure), vous pouvez utiliser les fichiers déjà présents sur notre Drive.  
Pour cela, procédez ainsi :

- **Ajout du dossier de données pré-installées :**  
  Ajoutez le dossier partagé suivant à la racine de votre Google Drive (dans "My Drive") :
  
  [Ajouter le dossier Projet_OpenNMT](https://drive.google.com/drive/folders/10d16qpgYf64LNn3Q9b3P77XdFJ01qPS3?usp=share_link)
  
  Assurez-vous que le dossier est nommé **Projet_OpenNMT** et qu'il se trouve directement dans "My Drive".

- **Montage automatique du Drive :**  
  Dans le notebook, la cellule suivante permet de monter le Drive et de se positionner dans le répertoire du projet. Mettez la variable `MOUNT_DRIVE` à **True** si vous utilisez cette option.

  ```python
  # Définir la variable pour déterminer l'environnement
  MOUNT_DRIVE = True  # Passez à True si vous utilisez Google Drive

  if MOUNT_DRIVE:
      from google.colab import drive
      drive.mount('/content/drive')
      # Notez l'utilisation de l'échappement \ pour les espaces
      %cd /content/drive/My\ Drive/Projet_OpenNMT
  else:
      %cd /content/Projet_OpenNMT
