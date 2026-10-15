# Savoria — Plateforme de Gestion de Restaurants avec Assistant IA

Plateforme complète de **gestion multi-restaurants**, réalisée dans le cadre d'un projet de fin d'études (PFE) — *[À compléter : université, filière, encadrant]*. Elle associe une **application web React** (clients et personnel) à une **API REST Django** et intègre un **chatbot basé sur l'intelligence artificielle** destiné à améliorer l'expérience utilisateur et à automatiser les processus.

Le système centralise les commandes, les réservations, les menus du jour, l'approvisionnement, le suivi financier et la surveillance de la température des chambres froides au sein d'une interface unique, avec un espace dédié à chaque métier du restaurant.

---

## 🎯 Objectifs

- Offrir aux clients un parcours fluide : consulter le menu, commander, réserver, laisser un avis
- Donner à chaque métier (chef, manager, serveur, caissier, livreur, fournisseur) un espace de travail adapté
- Automatiser les tâches répétitives (notifications, calcul des revenus, attribution des tables)
- Assurer le suivi de la chaîne du froid grâce à un capteur de température et d'humidité
- Améliorer l'expérience utilisateur grâce à un **assistant conversationnel IA**

---

## 📱 Fonctionnalités

### 👤 Client (Application web)
- 🔐 **Authentification** — Inscription, connexion sécurisée par jeton JWT
- 🍽️ **Menu** — Consultation des plats par catégorie, avec photos, descriptions et prix
- 🛒 **Panier et commande** — Quatre types de commande : sur place, livraison, à emporter, précommande ; paiement en espèces ou en ligne
- 📅 **Réservations** — Choix du restaurant, de la date et du nombre de personnes ; attribution automatique d'une table disponible
- 📦 **Mes commandes** — Suivi de l'état des commandes
- ⭐ **Avis** — Notation et commentaire après commande
- 👤 **Profil** — Modification des informations personnelles et de la photo

### 🏢 Client corporate (Application web)
- Espace dédié avec panier et tarification entreprise
- Gestion des profils, restaurants, commandes, conventions, rapports et avis

### 👨‍🍳 Chef
- 📋 **Commandes** — Consultation et mise à jour du statut (en préparation, prête…)
- 🍲 **Gestion des plats** — Création et modification des plats, recettes et ingrédients
- 📦 **Inventaire et menu du jour** — Composition du menu du jour avec les ingrédients et quantités nécessaires
- 👥 **Équipe de cuisine** et 💬 **messages / notifications**

### 🧑‍💼 Manager
- ✅ **Validation du menu du jour** avant transmission au fournisseur
- 💰 **Finances** — Revenus (ventes, nombre de commandes) et dépenses justifiées
- 📅 **Réservations et commandes** — Supervision du restaurant
- 👥 **Supervision des employés** et communication interne
- 🌡️ **Suivi des températures** — Mesures du capteur avec code couleur d'alerte

### 🛎️ Serveur
- Gestion des commandes en salle (mise à jour du statut)
- Consultation et modification des réservations
- Consultation du menu et des notifications

### 💵 Caissier
- Encaissement : passage d'une commande de « non payée » à « payée »
- Consultation du menu et des rapports

### 🛵 Livreur
- Liste des commandes de livraison du restaurant et mise à jour du statut
- Déclaration des livraisons échouées

### 🚚 Fournisseur
- Validation des listes d'ingrédients du menu du jour après le manager
- Notifications d'approvisionnement

### 🛠️ Administrateur (Interface Django Admin personnalisée)
- 📊 **Tableau de bord** — Revenus, dépenses, solde et commandes par restaurant, avec filtre jour / mois / année
- Gestion complète des utilisateurs, rôles, restaurants, plats, tables, réservations et avis

---

## 🤖 Assistant IA (Chatbot)

> **Statut : module en cours d'intégration.** Le code actuel du dépôt couvre la plateforme de gestion ; le chatbot s'appuie sur l'API existante.

**Objectif :** améliorer l'expérience utilisateur et automatiser les processus grâce à un assistant conversationnel.

| Utilisateur | Cas d'usage prévus |
|---|---|
| Client | Questions sur le menu, les ingrédients et les horaires ; création d'une réservation ou d'une commande en langage naturel |
| Personnel | Suivi du statut d'une commande, signalement d'une alerte de température |
| Manager | Résumé des ventes du jour à partir des statistiques de revenus |

**Intégration prévue :** un endpoint `/api/chatbot/` côté backend appelant un modèle de langage, et un widget de discussion dans le frontend React.

---

## 👥 Acteurs et rôles

| Acteur | Rôle applicatif | Responsabilités principales |
|---|---|---|
| **Client** | `Client` | Menu, commandes, réservations, avis |
| **Client corporate** | `Corporate_Client` | Commandes entreprise, conventions, rapports |
| **Chef** | `Chef` | Plats, recettes, inventaire, menu du jour |
| **Manager** | `Manager` | Validation, finances, supervision, températures |
| **Serveur** | `Server` | Commandes en salle, réservations |
| **Caissier** | `Cashier` | Paiements et rapports |
| **Livreur** | `Delivery_Employee` | Livraisons |
| **Fournisseur** | `Supplier` | Validation de l'approvisionnement |
| **Administrateur** | `Admin` | Administration globale |

---

## 🔄 Flux de travail du menu du jour

```
Chef  ──compose──▶  Menu du jour (ingrédients + quantités)
                          │
                          ▼
                Manager valide  (status_manager)
                          │
                          ▼
              Fournisseur valide (status_supplier)
```

## ⚙️ Automatismes

- **Commande payée** → mise à jour automatique du revenu quotidien du restaurant
- **Nouvelle commande** → notification automatique au chef et au serveur
- **Création d'un utilisateur** → création automatique du profil métier correspondant à son rôle
- **Réservation** → attribution de la première table libre de capacité suffisante

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────┐        ┌───────────────┐
│          Application Web React              │        │ Capteur IoT   │
│ (Clients, Corporate, Chef, Manager, Serveur,│        │ température / │
│  Caissier, Livreur, Fournisseur)            │        │ humidité      │
└────────────────────┬────────────────────────┘        └───────┬───────┘
                     │  HTTP / REST (JSON + JWT)               │ POST
                     └───────────────────┬─────────────────────┘
                                         ▼
                          ┌──────────────────────────┐
                          │ Django + Django REST     │──▶ Chatbot IA (LLM)
                          │ Framework                │
                          └─────┬──────────────┬─────┘
                                ▼              ▼
                         ┌────────────┐  ┌────────────┐
                         │  Base de   │  │ Cloudinary │
                         │  données   │  │ (images)   │
                         └────────────┘  └────────────┘
```

---

## 🛠️ Technologies utilisées

### Frontend
| Technologie | Rôle |
|---|---|
| React 19 + TypeScript | Interface utilisateur |
| Vite 5 | Outil de build et serveur de développement |
| Tailwind CSS + shadcn/ui (Radix) | Stylisation et composants |
| React Router 6 | Navigation par rôle |
| TanStack Query + Axios | Appels API et cache |
| react-hook-form + zod | Formulaires et validation |
| Framer Motion, Recharts, Lucide | Animations, graphiques, icônes |

### Backend
| Technologie | Rôle |
|---|---|
| Python + Django 5.2 | Framework web |
| Django REST Framework 3.16 | API REST |
| SimpleJWT | Authentification par jeton |
| Jazzmin | Thème de l'interface d'administration |
| Cloudinary | Stockage des images |
| WhiteNoise + Gunicorn | Fichiers statiques et serveur de production |
| SQLite (dev) / PostgreSQL (prod) | Base de données |

### Déploiement et outils
Render · Cloudinary · PyCharm · VS Code · Postman · Git

---

## 🗄️ Schéma de la base de données

```
User             → Authentification et profil (username, email, Role, téléphone, photo…)
Client           → Profil client (adresse)
CorporateClient  → Client entreprise (nom de la société)
Manager / Chef / Server / Cashier / DeliveryEmplyee / Supplier
                 → Profils métiers (liés à User et à un Restaurant)
Notification     → Notifications (expéditeur, destinataire, titre, lu / non lu)
Restaurant       → Établissements (nom, email, téléphone, localisation, photo)
Table            → Tables (numéro, capacité, statut)
Reservation      → Réservations (client, restaurant, table, date, nombre de personnes)
Category         → Catégories de plats
Item             → Plats (catégorie, prix, prix entreprise, recette, photo)
Ingredient       → Ingrédients (quantité, unité, catégorie)
ItemIngredient   → Composition d'un plat (plat, ingrédient, quantité)
Order            → Commandes (type, statut, paiement, total, localisation)
ClientOrder      → Lignes de commande (plat, quantité, client)
DailyMenu        → Menu du jour (chef, fournisseur, validations manager / fournisseur)
DailyMenuItem    → Ingrédients et quantités du menu du jour
Review           → Avis (note, commentaire, commande)
Income / Outcome → Revenus et dépenses (restaurant, manager, montant, justification)
TemperatureData  → Mesures du capteur (température, humidité, statut d'alerte)
```

---

## 🚀 Prérequis

- Python 3.11+
- Node.js 20+ et npm
- Git
- Un compte Cloudinary (stockage des images)

---

## ⚙️ Installation

### 1. Cloner le dépôt
```bash
git clone https://github.com/<votre-compte>/savoria-restaurant-management.git
cd savoria-restaurant-management
```

### 2. Backend (Django)
```bash
cd backend
python -m venv venv
source venv/bin/activate        # Windows : venv\Scripts\activate
pip install -r requirements.txt
```

Créer un fichier `.env` (ne jamais le versionner) :
```env
DEBUG=True
SECRET_KEY=<clé-secrète-générée>
DATABASE_URL=<url-de-la-base>
CLOUDINARY_CLOUD_NAME=<nom>
CLOUDINARY_API_KEY=<clé>
CLOUDINARY_API_SECRET=<secret>
```

Puis :
```bash
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver      # http://localhost:8000
```

### 3. Frontend (React)
```bash
cd frontend
npm install
```

Créer un fichier `.env` :
```env
VITE_API_URL=http://localhost:8000/api/
```

Puis :
```bash
npm run dev                     # http://localhost:8080
```

---

## 📡 Points d'accès de l'API

Toutes les routes sont préfixées par `/api/`.

### Authentification et profil
```
POST   /signup/                        → Inscription
POST   /login/                         → Connexion (jeton + rôle)
POST   /token/                         → Obtention des jetons JWT
POST   /token/refresh/                 → Renouvellement du jeton
GET    /current-user/                  → Utilisateur connecté
PUT    /current-user/update/           → Modifier son profil
GET    /notifications/                 → Notifications de l'utilisateur
POST   /notifications/:id/mark-read/   → Marquer comme lue
```

### Restaurants, menu et ingrédients
```
GET    /restaurants/                   → Liste des restaurants (avec plats)
POST   /restaurants/                   → Ajouter un restaurant
GET    /menu/                          → Liste des plats
POST   /menu/                          → Ajouter un plat
GET    /menu/:id/                      → Détail d'un plat
PUT    /menu/:id/                      → Modifier un plat (PATCH accepté)
GET    /ingredients/                   → Liste des ingrédients (CRUD complet)
```

### Commandes
```
POST   /orders/                        → Créer une commande
GET    /orders/list/                   → Liste des commandes
PUT    /orders/update-status/:id/      → Changer le statut
PUT    /orders/update-payment/:id/     → Changer le statut de paiement
GET    /delivery/orders/               → Commandes de livraison du restaurant
```

### Réservations
```
GET    /reservations/                  → Liste des réservations
POST   /reservations/                  → Créer une réservation
GET    /reservations/:id/              → Détail
PUT    /reservations/:id/              → Modifier
DELETE /reservations/:id/              → Supprimer
```

### Menus du jour
```
GET    /dailymenus/                    → Menus du jour (selon le rôle)
POST   /dailymenus/                    → Créer un menu du jour (Chef)
POST   /dailymenus/:id/validate/       → Validation manager
POST   /dailymenus/:id/supplier/validate/ → Validation fournisseur
GET    /dailymenus/items/              → Ingrédients d'un menu du jour
POST   /dailymenus/items/              → Ajouter des ingrédients
```

### Profils métiers
```
GET    /chefs/   /managers/   /servers/
GET    /cashiers/   /suppliers/   /deliveries/
```

### Finances et avis
```
GET    /manager/income-stats/          → Total des ventes et nombre de commandes
GET    /outcomes/                      → Dépenses du restaurant (CRUD)
GET    /reviews/                       → Avis (CRUD)
```

### Capteur de température
```
POST   /temperature-data/              → Envoi d'une mesure par le capteur
GET    /temperature/                   → Historique des mesures
```

---

## 📁 Structure du projet

```
savoria-restaurant-management/
├── backend/                    ← API Django
│   ├── savoria/                ← Configuration (settings, urls)
│   ├── Account/                ← Utilisateurs, rôles, notifications
│   ├── Restaurant/             ← Plats, commandes, réservations, finances
│   ├── templates/ static/      ← Interface d'administration personnalisée
│   ├── requirements.txt
│   └── manage.py
├── frontend/                   ← Application React + Vite
│   ├── src/
│   │   ├── components/
│   │   ├── contexts/           ← Authentification, paniers
│   │   ├── layouts/            ← Une mise en page par rôle
│   │   ├── pages/
│   │   │   ├── chef/  manager/  server/
│   │   │   ├── cashier/  delivery/  supplier/
│   │   │   └── corporate/
│   │   └── services/
│   └── package.json
└── README.md
```

---

## 🖥️ Écrans de l'application

| Écran | Rôle | Description |
|---|---|---|
| Accueil, À propos, Contact | Visiteur | Présentation du restaurant |
| Connexion / Inscription | Tous | Authentification |
| Menu et panier | Client | Choix des plats, type de commande et paiement |
| Réservations | Client | Réservation d'une table |
| Mes commandes / Avis | Client | Suivi et notation |
| Tableau de bord entreprise | Corporate | Commandes, conventions, rapports |
| Commandes, plats, inventaire | Chef | Cuisine et menu du jour |
| Validation, finances, températures | Manager | Supervision et pilotage |
| Commandes et réservations | Serveur | Service en salle |
| Encaissement | Caissier | Paiements |
| Livraisons et rapport d'échec | Livreur | Tournées |
| Validation de l'approvisionnement | Fournisseur | Listes d'ingrédients |
| Tableau de bord administrateur | Admin | Revenus, dépenses, solde par restaurant |

---

## 🔮 Perspectives

- Finalisation et déploiement du **chatbot IA** (réservation et commande en langage naturel)
- Intégration d'une passerelle de paiement en ligne
- Notifications en temps réel (WebSocket)
- Prise en charge multilingue (arabe / français / anglais)
- Analyses et rapports avancés, prévision des besoins en ingrédients
- Application mobile pour les clients et les livreurs

---

