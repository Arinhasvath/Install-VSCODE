### Script d'installation et de mise à jour sur Zorin OS

```bash
#!/bin/bash

# Mise à jour des paquets du système
echo "Mise à jour des paquets du système..."
sudo apt update && sudo apt upgrade -y

# Mise à jour de tous les paquets installés
echo "Mise à jour des paquets installés..."
sudo apt dist-upgrade -y

# Nettoyage des paquets inutiles
echo "Nettoyage des paquets inutiles..."
sudo apt autoremove -y
sudo apt clean

# Installation des dépendances nécessaires
echo "Installation des dépendances..."
sudo apt install -y software-properties-common apt-transport-https curl wget gnupg lsb-release

# Ajout de la clé Microsoft pour les dépôts de VS Code
echo "Ajout de la clé Microsoft pour VS Code..."
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /usr/share/keyrings/microsoft-archive-keyring.gpg

# Ajout du dépôt officiel de VS Code
echo "Ajout du dépôt officiel de VS Code..."
sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/microsoft-archive-keyring.gpg] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'

# Mise à jour des paquets après ajout du dépôt VS Code
echo "Mise à jour des paquets après ajout du dépôt..."
sudo apt update

# Installation de VS Code
echo "Installation de Visual Studio Code..."
sudo apt install -y code

# Installation de Python 3 et pip
echo "Installation de Python 3 et pip..."
sudo apt install -y python3 python3-pip

# Installation de Java OpenJDK
echo "Installation de Java OpenJDK..."
sudo apt install -y openjdk-11-jdk

# Installation de Node.js et npm
echo "Installation de Node.js et npm..."
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install -y nodejs

# Installation de C et GCC
echo "Installation de C et GCC..."
sudo apt install -y build-essential

# Finalisation de l'installation
echo "Tous les logiciels nécessaires ont été installés avec succès."

# Redémarrer le système si nécessaire
echo "Si vous avez installé de nouvelles versions, il peut être nécessaire de redémarrer votre machine pour finaliser l'installation."
```

### Explication du script :

1. **Mise à jour des paquets** : Le script commence par mettre à jour les paquets avec `apt update` et `apt upgrade`, et effectue un `dist-upgrade` pour garantir que tous les paquets sont à jour. `autoremove` est utilisé pour supprimer les paquets inutilisés et `apt clean` nettoie les fichiers cache.

2. **Dépendances** : Installe les dépendances générales nécessaires comme `curl`, `wget`, et d'autres outils qui seront utilisés pour installer des logiciels.

3. **Installation de VS Code** : Le script ajoute le dépôt officiel de VS Code et la clé de signature de Microsoft, puis installe VS Code via `apt`.

4. **Installation de Python** : Installe Python 3 et `pip` (le gestionnaire de paquets pour Python).

5. **Installation de Java** : Installe OpenJDK (Java 11) pour le développement Java.

6. **Installation de Node.js** : Installe la dernière version stable de Node.js (16.x) et `npm` pour le développement JavaScript.

7. **Installation de C/C++** : Installe `build-essential` pour la compilation de programmes en C/C++.

### Instructions pour exécuter le script :

1. **Créer un fichier de script** :
   - Ouvrez votre terminal Zorin.
   - Créez un fichier script avec la commande :
     ```bash
     nano install_all_software.sh
     ```
   - Copiez le contenu du script ci-dessus dans le fichier et sauvegardez-le (`Ctrl + X`, puis `Y`, puis `Enter`).

2. **Rendre le script exécutable** :
   - Après avoir enregistré le fichier, rendez-le exécutable :
     ```bash
     chmod +x install_all_software.sh
     ```

3. **Exécuter le script** :
   - Exécutez le script :
     ```bash
     ./install_all_software.sh
     ```

Le script mettra à jour votre système, installera tous les logiciels nécessaires pour le développement (Python, Java, Node.js, C, et VS Code) et nettoiera les fichiers inutiles.

### Remarque :
Si le script installe de nouvelles versions de certains logiciels, vous devrez peut-être redémarrer votre machine pour que les changements prennent effet.
