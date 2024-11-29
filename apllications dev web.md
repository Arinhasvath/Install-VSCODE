### 1. **Script d'installation de tous les outils**

```bash
#!/bin/bash

# Script pour installer tout le nécessaire pour VS Code et les outils de développement sur Ubuntu 22.04

# Mettre à jour les paquets
sudo apt update && sudo apt upgrade -y

# Installer Python3 et pip
echo "Installation de Python3 et pip..."
sudo apt install python3 python3-pip -y

# Installer Node.js (version stable)
echo "Installation de Node.js..."
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install nodejs -y

# Installer Git
echo "Installation de Git..."
sudo apt install git -y

# Installer MySQL (MariaDB)
echo "Installation de MariaDB..."
sudo apt install mariadb-server mariadb-client -y

# Sécuriser l'installation de MariaDB
echo "Sécurisation de MariaDB..."
sudo mysql_secure_installation

# Installer Java
echo "Installation de Java..."
sudo apt install openjdk-11-jdk -y

# Installer C et build-essential
echo "Installation de C et build-essential..."
sudo apt install build-essential -y

# Installer des extensions pour VS Code
echo "Installation des extensions pour VS Code..."

# Extensions pour Python, Node.js, Docker, C, Git, etc.
code --install-extension ms-python.python
code --install-extension ms-vscode.node-debug2
code --install-extension redhat.java
code --install-extension ms-vscode.cpptools
code --install-extension eamodio.gitlens
code --install-extension dbaeumer.vscode-eslint
code --install-extension ms-vscode.vscode-typescript-next
code --install-extension esbenp.prettier-vscode

# Installer PostgreSQL si nécessaire
echo "Installation de PostgreSQL..."
sudo apt install postgresql postgresql-contrib -y

# Finalisation
echo "Installation terminée. Vous pouvez maintenant configurer et utiliser VS Code ainsi que les outils associés."

# Optionnel: Redémarrage du système pour que tout prenne effet
# sudo reboot
```

### 2. **Installation de VS Code avec les droits root (`sudo`)**

Pour installer **VS Code** avec les droits root sous Ubuntu (ou tout autre système basé sur Debian), voici les étapes à suivre :

#### Étape 1 : Ajouter la clé Microsoft pour le dépôt

```bash
sudo apt install software-properties-common apt-transport-https curl -y
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /usr/share/keyrings/microsoft-archive-keyring.gpg
```

#### Étape 2 : Ajouter le dépôt de VS Code à vos sources de paquets

```bash
sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft-archive-keyring.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
```

#### Étape 3 : Mettre à jour les paquets et installer VS Code

```bash
sudo apt update
sudo apt install code -y
```

### Explications :

- **Étape 1** : Vous installez les outils nécessaires (`software-properties-common`, `apt-transport-https`, `curl`) et ajoutez la clé publique de Microsoft à votre système.
- **Étape 2** : Vous ajoutez le dépôt officiel de VS Code à votre gestionnaire de paquets afin que vous puissiez installer la version stable de VS Code.
- **Étape 3** : Vous mettez à jour la liste des paquets et installez VS Code avec `sudo apt install code`.

Cela permet d'avoir **VS Code** installé avec les privilèges d'administrateur, vous assurant que toutes les dépendances et fichiers nécessaires soient correctement installés.
