### Script d'installation de VS Code sur Zorin OS

```bash
#!/bin/bash

# Mettre à jour les paquets du système
echo "Mise à jour des paquets..."
sudo apt update && sudo apt upgrade -y

# Installer les dépendances nécessaires
echo "Installation des dépendances..."
sudo apt install software-properties-common apt-transport-https curl -y

# Ajouter la clé Microsoft pour les dépôts de VS Code
echo "Ajout de la clé Microsoft..."
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /usr/share/keyrings/microsoft-archive-keyring.gpg

# Ajouter le dépôt officiel de VS Code
echo "Ajout du dépôt de VS Code..."
sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft-archive-keyring.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'

# Mettre à jour les paquets avec le dépôt ajouté
echo "Mise à jour des paquets après ajout du dépôt..."
sudo apt update

# Installer VS Code
echo "Installation de VS Code..."
sudo apt install code -y

# Finalisation de l'installation
echo "VS Code a été installé avec succès."
```

### Explication du script :

1. **Mise à jour des paquets** : Le script commence par mettre à jour les paquets du système pour garantir que vous avez les dernières versions.
2. **Installation des dépendances** : Installe les dépendances nécessaires pour gérer les paquets HTTPS et la clé GPG.
3. **Ajout de la clé Microsoft** : Télécharge et ajoute la clé de signature de Microsoft pour authentifier les paquets provenant de leur dépôt.
4. **Ajout du dépôt officiel de VS Code** : Ajoute le dépôt officiel de VS Code à votre liste de sources APT.
5. **Mise à jour des paquets** : Effectue une mise à jour des paquets pour récupérer la liste des nouveaux paquets depuis le dépôt de VS Code.
6. **Installation de VS Code** : Enfin, installe VS Code avec la commande `sudo apt install code`.

### Exécution du script :

1. **Créer un fichier script** :
   - Ouvrez votre terminal Zorin.
   - Créez un fichier script en utilisant la commande suivante :
     ```bash
     nano install_vscode.sh
     ```
   - Copiez le contenu du script dans ce fichier.

2. **Rendre le script exécutable** :
   - Après avoir enregistré le fichier, rendez-le exécutable avec :
     ```bash
     chmod +x install_vscode.sh
     ```

3. **Exécuter le script** :
   - Enfin, exécutez le script :
     ```bash
     ./install_vscode.sh
     ```

Le script va procéder à l'installation de **VS Code** sur Zorin OS avec les privilèges `sudo` pour les commandes nécessitant une élévation de droits.
