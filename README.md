# Docker TP3 – Application Web PHP + MariaDB

## 💻 Tech Stack:
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white) ![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white) ![PHP](https://img.shields.io/badge/php-%23777BB4.svg?style=for-the-badge&logo=php&logoColor=white)
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white) ![Bash Script](https://img.shields.io/badge/bash_script-%23121011.svg?style=for-the-badge&logo=gnu-bash&logoColor=white) ![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white) ![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white) 
## 📝 Présentation

Ce TP a pour objectif de comprendre et mettre en pratique la **gestion des conteneurs Docker**, ainsi que la communication entre plusieurs services (Nginx, PHP-FPM, MariaDB). Le projet évolue étape par étape, en commençant par une architecture simple et en ajoutant progressivement la base de données et Docker Compose.

## 📂 Structure du projet

docker-tp3/

-> etape1/ # Nginx + PHP-FPM (2 conteneurs)

-> etape2/ # Nginx + PHP-FPM + MariaDB (3 conteneurs)

-> etape3/ # Même architecture que l'étape 2 mais avec Docker Compose

-> README.md


Chaque étape contient :

- `src/` → fichiers PHP (`index.php`, `test.php`)  
- `config/` → configuration Nginx (`default.conf`)  
- `initdb/` → fichiers SQL d’initialisation pour MariaDB (`create.sql`)  
- `Dockerfile` → image PHP avec extensions nécessaires (`mysqli`)  
- `launch.sh` → script pour lancer les conteneurs (étapes 1, 2, 3)  
- `docker-compose.yml` → fichier Compose (étape 3)

---

## 🎯 Objectifs par étape

### **Étape 0 : Préparation de l’environnement**
- Créer le répertoire de travail `docker-tp3`  
- Initialiser un repository Git (`git init`)  
- Créer un fichier `.gitignore` pour ignorer les fichiers temporaires  
- Préparer les scripts `launch.sh` pour automatiser le lancement des conteneurs  
- **Objectif pédagogique** : apprendre à organiser un projet Docker et Git

---

### **Étape 1 : Nginx + PHP-FPM**
- Déployer **deux conteneurs distincts** :
  1. HTTP (Nginx) sur le port 8080  
  2. SCRIPT (PHP-FPM) pour exécuter le code PHP
- Configurer Nginx pour communiquer avec PHP via FastCGI  
- Tester avec `index.php` affichant `phpinfo()`  
- **Objectif pédagogique** : comprendre la séparation des rôles et la communication entre conteneurs (architecture 2-tiers)

---

### **Étape 2 : Ajout de MariaDB**
- Ajouter un **troisième conteneur DATA** avec MariaDB  
- Créer et initialiser la base de données via le fichier SQL fourni (`create.sql`)  
- Modifier PHP pour utiliser l’extension `mysqli` et interagir avec la base  
- Créer `test.php` pour effectuer des opérations CRUD (insertion et lecture)  
- **Objectif pédagogique** : comprendre l’architecture 3-tiers (Nginx + PHP + base de données), la persistance et l’interaction entre conteneurs

---

### **Étape 3 : Docker Compose**
- Regrouper les 3 conteneurs dans un seul fichier `docker-compose.yml`  
- Lancer l’architecture complète avec `docker compose up -d`  
- Maintenir les mêmes fonctionnalités que l’étape 2  
- **Objectif pédagogique** : apprendre à orchestrer plusieurs conteneurs avec Docker Compose et simplifier le déploiement

---

## ⚡ Lancer le projet

### Étapes 1 et 2 (sans Docker Compose) :

cd etapeX

./launch.sh

### Étapes 3
cd etape3

docker compose up -d
