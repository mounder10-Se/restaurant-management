# Savoria — Plateforme de Gestion Multi-Restaurants

Savoria est une plateforme web de **gestion multi-restaurants** qui centralise les opérations quotidiennes des établissements de restauration. Elle associe une application web développée avec React et TypeScript à une API REST développée avec Django et Django REST Framework.

Le système centralise la gestion des commandes, des réservations, des menus du jour, de l'approvisionnement, du suivi financier et de la surveillance de la température des chambres froides au sein d'une interface unique. Il propose des espaces dédiés aux clients, chefs, managers, serveurs, caissiers, livreurs, fournisseurs et administrateurs.

## 🎯 Objectifs

- Offrir aux clients un parcours fluide : consultation des menus, commandes, réservations et avis.
- Fournir des espaces adaptés aux différents métiers de la restauration.
- Automatiser certaines tâches répétitives : notifications, calcul des revenus et attribution des tables.
- Faciliter la gestion des stocks, des ingrédients et de l'approvisionnement.
- Assurer le suivi de la chaîne du froid grâce à un capteur de température et d'humidité.
- Centraliser le suivi financier et la supervision des restaurants.

## 📱 Fonctionnalités principales

- **Espace client :** authentification JWT, consultation des menus, panier, commandes, réservations, suivi des commandes et avis.
- **Espace client corporate :** gestion des commandes professionnelles, tarification entreprise, conventions et rapports.
- **Espace chef :** gestion des plats, recettes, ingrédients, inventaire et menus du jour.
- **Espace manager :** validation des menus du jour, suivi des revenus et dépenses, supervision des employés, commandes et réservations.
- **Espace serveur :** gestion des commandes en salle et consultation des réservations.
- **Espace caissier :** suivi des paiements et consultation des rapports.
- **Espace livreur :** suivi des commandes en livraison et déclaration des livraisons échouées.
- **Espace fournisseur :** validation des besoins en ingrédients et suivi de l'approvisionnement.
- **Administration :** gestion des utilisateurs, rôles, restaurants, plats, tables, réservations, avis et indicateurs financiers.
- **Suivi IoT :** collecte des mesures de température et d'humidité avec signalement visuel des alertes.

## 🔄 Automatisation des processus

- Mise à jour des revenus du restaurant lors de l'enregistrement d'un paiement.
- Notifications destinées au personnel concerné lors de la création de commandes.
- Création automatique du profil métier correspondant au rôle d'un utilisateur.
- Attribution automatique d'une table disponible selon la capacité demandée.
- Circuit de validation du menu du jour par le manager, puis par le fournisseur.

## 🛠️ Technologies utilisées

### Frontend
- React 19 et TypeScript
- Vite 5
- Tailwind CSS et shadcn/ui
- React Router 6
- TanStack Query et Axios
- react-hook-form et zod
- Framer Motion, Recharts et Lucide

### Backend
- Python et Django 5.2
- Django REST Framework 3.16
- SimpleJWT pour l'authentification
- Jazzmin pour l'interface d'administration
- Cloudinary pour le stockage des images
- WhiteNoise et Gunicorn
- SQLite pour le développement et PostgreSQL pour la production

### Déploiement et outils
Render · Cloudinary · PyCharm · VS Code · Postman · Git

## 📁 Structure du projet

```text
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
