# Image Uploader

## Description
Image Uploader est une application web simple qui permet aux utilisateurs de télécharger une image, de la partager et de la télécharger à nouveau. L'application prend en charge les formats JPG, PNG et GIF, avec une taille maximale de fichier de 2 Mo. Elle permet aux utilisateurs de faire glisser-déposer l'image ou de la sélectionner via un navigateur de fichiers.

## Fonctionnalités
- **Téléchargement d'une image** (formats JPG, PNG, GIF).
- **Taille maximale de fichier** : 2 Mo.
- **Drag & Drop** : les utilisateurs peuvent glisser-déposer une image pour la télécharger.
- **Téléchargement classique** : les utilisateurs peuvent sélectionner un fichier via un navigateur de fichiers.
- **Chargement en cours** : un indicateur de chargement est affiché pendant l'upload de l'image.
- **Affichage de l'image** : l'image est affichée après un téléchargement réussi.
- **Partager l'image** : un lien unique est généré pour l'image téléchargée, pouvant être copié.
- **Télécharger l'image** : les utilisateurs peuvent télécharger l'image directement depuis l'application.

## Technologies utilisées
- **Vue.js** : Framework JavaScript pour construire l'interface.
- **HTML/CSS** : Pour la structure et le style de l'application.
- **JavaScript** : Pour la gestion des interactions utilisateur (upload, téléchargement, partage).

## Installation et démarrage

### Prérequis
- Node.js (version 14 ou supérieure)
- npm (ou yarn) pour la gestion des dépendances

### Étapes pour installer le projet
1. Clone le repository :
    ```bash
    git clone https://ton-repository.git
    ```
2. Accède au dossier du projet :
    ```bash
    cd ton-dossier
    ```
3. Installe les dépendances :
    ```bash
    npm install
    ```
4. Lance l'application en mode développement :
    ```bash
    npm run serve
    ```
5. L'application sera accessible à `http://localhost:8080`.

## Utilisation
1. Télécharge une image en faisant glisser-déposer ou en sélectionnant un fichier via le bouton "Browse files".
2. Pendant l'upload, un indicateur de chargement sera visible.
3. Une fois l'image téléchargée avec succès, elle sera affichée.
4. Utilise le bouton **Share** pour copier le lien de l'image dans ton presse-papiers.
5. Utilise le bouton **Download** pour télécharger l'image.
