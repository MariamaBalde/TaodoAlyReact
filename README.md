# TodoAly - Application de Liste de Tâches

TodoAly est une application de liste de tâches full-stack construite avec React (frontend) et Node.js/TypeScript (backend) avec une base de données MySQL utilisant Prisma ORM. L'application permet aux utilisateurs de créer, gérer et suivre leurs tâches avec des fonctionnalités comme l'authentification utilisateur, les permissions de tâches, les messages vocaux et les téléchargements d'images.

## Fonctionnalités

- **Authentification Utilisateur** : Système de connexion et d'inscription avec tokens JWT
- **Gestion des Tâches** : Créer, lire, mettre à jour et supprimer des tâches
- **Statut des Tâches** : Suivre les tâches avec des statuts (A_FAIRE, EN_COURS, TERMINEE)
- **Rôles Utilisateur** : Support pour différents rôles utilisateur (ADMIN, ETUDIANT, PROFESSEUR)
- **Permissions des Tâches** : Accorder des permissions à d'autres utilisateurs pour modifier des tâches spécifiques
- **Messages Vocaux** : Enregistrer et attacher des messages vocaux aux tâches
- **Téléchargements d'Images** : Attacher des images aux tâches
- **Tâches Automatisées** : Achèvement automatique des tâches basé sur les paramètres de temps
- **Notifications** : Système de notifications pour les mises à jour de tâches
- **Design Responsive** : Interface utilisateur moderne construite avec React et Tailwind CSS

## Prérequis

Avant d'exécuter cette application, assurez-vous d'avoir installé les éléments suivants :

- **Node.js** (version 16 ou supérieure)
- **npm** (fourni avec Node.js)
- **MySQL** (version 8.0 ou supérieure)
- **Git** (pour cloner le dépôt)

## Installation

### 1. Cloner le Dépôt

```bash
git clone <url-du-depot>
cd TodoAly
```

### 2. Configuration du Backend

Naviguez vers le répertoire backend :

```bash
cd projetAly/Live2
```

Installez les dépendances :

```bash
npm install
```

### 3. Configuration de la Base de Données

Assurez-vous que MySQL fonctionne sur votre système. Créez une base de données pour l'application.

Mettez à jour le fichier `.env` dans le répertoire `projetAly/Live2` avec vos identifiants de base de données :

```env
DATABASE_URL="mysql://nom_utilisateur:mot_de_passe@localhost:3306/nom_de_votre_base"
PORT=3000
TOKEN=votre_token_secret_ici
```

Exécutez les migrations de base de données :

```bash
npm run migrate
```

Générez le client Prisma :

```bash
npm run generate
```

### 4. Configuration du Frontend

Naviguez vers le répertoire frontend :

```bash
cd ../todolist
```

Installez les dépendances :

```bash
npm install
```

## Exécution de l'Application

### Démarrer le Backend

Depuis le répertoire `projetAly/Live2` :

```bash
npm run dev
```

Le backend démarrera sur `http://localhost:3000`

### Démarrer le Frontend

Depuis le répertoire `projetAly/todolist` :

```bash
npm run dev
```

Le frontend démarrera sur `http://localhost:5173` (port par défaut de Vite)

## Utilisation

### Configuration Initiale

1. **Créer un nouveau compte** : Visitez l'application frontend et cliquez sur l'inscription
2. **Se connecter** : Utilisez vos identifiants pour vous connecter
3. **Créer des tâches** : Commencez à ajouter vos éléments de tâches

### Utilisation de l'Application

#### Gestion des Tâches
- **Ajouter une Tâche** : Cliquez sur le bouton "Ajouter une Tâche" et remplissez le titre et la description
- **Modifier une Tâche** : Cliquez sur le bouton d'édition d'une tâche pour la modifier
- **Supprimer une Tâche** : Cliquez sur le bouton de suppression pour supprimer une tâche
- **Changer le Statut** : Utilisez le menu déroulant de statut pour changer le statut de la tâche
- **Marquer comme Terminée** : Cliquez sur la case à cocher pour basculer l'achèvement de la tâche

#### Fonctionnalités Avancées
- **Messages Vocaux** : Cliquez sur l'icône du microphone pour enregistrer des messages vocaux
- **Téléchargement d'Images** : Cliquez sur l'icône d'image pour attacher des images aux tâches
- **Permissions** : Accordez à d'autres utilisateurs la permission de modifier vos tâches
- **Tâches Automatisées** : Configurez les tâches pour qu'elles s'achèvent automatiquement à des heures spécifiques

#### Gestion des Utilisateurs
- **Rôles Utilisateur** : Différents rôles ont différentes permissions
- **Gestion du Profil** : Mettez à jour vos informations utilisateur

## Points de Terminaison API

### Authentification
- `POST /auth/login` - Connexion utilisateur
- `POST /auth/register` - Inscription utilisateur

### Tâches
- `GET /taches` - Obtenir toutes les tâches pour l'utilisateur authentifié
- `POST /taches` - Créer une nouvelle tâche
- `PUT /taches/:id` - Mettre à jour une tâche
- `DELETE /taches/:id` - Supprimer une tâche

### Utilisateurs
- `GET /users` - Obtenir tous les utilisateurs
- `POST /users` - Créer un nouvel utilisateur
- `PUT /users/:id` - Mettre à jour un utilisateur
- `DELETE /users/:id` - Supprimer un utilisateur

### Permissions
- `GET /permissions` - Obtenir les permissions
- `POST /permissions` - Accorder des permissions
- `DELETE /permissions/:id` - Révoquer des permissions

### Notifications
- `GET /notifications` - Obtenir les notifications utilisateur
- `POST /notifications` - Créer une notification

## Structure du Projet

```
TodoAly/
├── projetAly/
│   ├── Live2/                 # Backend (Node.js + TypeScript)
│   │   ├── src/
│   │   │   ├── controller/    # Contrôleurs de routes
│   │   │   ├── middleware/    # Middleware d'authentification
│   │   │   ├── repository/    # Couche d'accès aux données
│   │   │   ├── route/         # Routes API
│   │   │   ├── service/       # Logique métier
│   │   │   ├── Validation/    # Validation des entrées
│   │   │   └── index.ts       # Point d'entrée de l'application
│   │   ├── prisma/            # Schéma de base de données et migrations
│   │   ├── uploads/           # Répertoire de téléchargements de fichiers
│   │   └── .env               # Variables d'environnement
│   └── todolist/              # Frontend (React + Vite)
│       ├── src/
│       │   ├── composant/     # Composants React
│       │   ├── hooks/         # Hooks React personnalisés
│       │   ├── validation/    # Validation de formulaires
│       │   └── assets/        # Ressources statiques
│       ├── public/            # Ressources publiques
│       └── db.json            # Données fictives (pour le développement)
└── README.md                  # Ce fichier
```

## Technologies Utilisées

### Backend
- **Node.js** - Environnement d'exécution JavaScript
- **TypeScript** - JavaScript typé
- **Express.js** - Framework web
- **Prisma** - ORM pour la gestion de base de données
- **MySQL** - Base de données relationnelle
- **JWT** - JSON Web Tokens pour l'authentification
- **Multer** - Gestion des téléchargements de fichiers
- **Zod** - Validation de schéma
- **CORS** - Partage de ressources cross-origin

### Frontend
- **React** - Bibliothèque d'interface utilisateur
- **Vite** - Outil de construction et serveur de développement
- **React Router** - Routage côté client
- **Tailwind CSS** - Framework CSS utilitaire
- **Lucide React** - Bibliothèque d'icônes
- **JWT Decode** - Décodage de tokens JWT

## Développement

### Scripts de Développement Backend
- `npm run dev` - Démarrer le serveur de développement avec rechargement à chaud
- `npm run build` - Construire pour la production
- `npm run start` - Démarrer le serveur de production
- `npm run migrate` - Exécuter les migrations de base de données
- `npm run generate` - Générer le client Prisma

### Scripts de Développement Frontend
- `npm run dev` - Démarrer le serveur de développement
- `npm run build` - Construire pour la production
- `npm run preview` - Aperçu de la construction de production
- `npm run lint` - Exécuter ESLint
- `npm run server:api` - Démarrer le serveur JSON (pour le développement)

## Dépannage

### Problèmes Courants

1. **Erreur de Connexion à la Base de Données**
   - Assurez-vous que MySQL fonctionne
   - Vérifiez DATABASE_URL dans le fichier .env
   - Vérifiez les identifiants de base de données

2. **Port Déjà Utilisé**
   - Changez PORT dans le fichier .env
   - Tuez le processus utilisant le port : `lsof -ti:3000 | xargs kill -9`

3. **Erreurs CORS**
   - Le backend est configuré pour permettre toutes les origines en développement
   - Vérifiez si le backend fonctionne sur le bon port

4. **Problèmes d'Authentification**
   - Effacez le localStorage dans le navigateur
   - Vérifiez TOKEN dans le fichier .env
   - Vérifiez l'expiration du token JWT

### Problèmes de Téléchargement de Fichiers
- Assurez-vous que le répertoire `uploads/` existe et est accessible en écriture
- Vérifiez les limites de taille de fichier dans la configuration multer

## Contribution

1. Forkez le dépôt
2. Créez une branche de fonctionnalité
3. Faites vos modifications
4. Exécutez les tests
5. Soumettez une pull request

## Licence

Ce projet est sous licence ISC.

## Support

Pour le support ou les questions, veuillez contacter l'équipe de développement.