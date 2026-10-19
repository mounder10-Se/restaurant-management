# Savoria — Plateforme de Gestion de Restaurants avec Assistant IA

Savoria est une plateforme web de **gestion multi-restaurants** qui centralise les opérations quotidiennes des établissements de restauration. Elle associe une application web développée avec React et TypeScript à une API REST développée avec Django et Django REST Framework. Un assistant conversationnel basé sur l'intelligence artificielle est également prévu et son intégration est en cours.

Le système centralise les commandes, les réservations, les menus du jour, l'approvisionnement, le suivi financier et la surveillance de la température des chambres froides au sein d'une interface unique. Il propose un espace dédié à chaque métier du restaurant.

## 🎯 Objectifs

- Offrir aux clients un parcours fluide : consultation des menus, commandes, réservations et avis.
- Fournir des espaces adaptés aux différents métiers de la restauration.
- Automatiser certaines tâches répétitives : notifications, calcul des revenus et attribution des tables.
- Assurer le suivi de la chaîne du froid grâce à un capteur de température et d'humidité.
- Préparer l'intégration d'un assistant conversationnel IA pour faciliter l'accès aux informations et automatiser certains processus.

## 🤖 Assistant IA (Chatbot)

> **Statut : module en cours d'intégration.** La plateforme de gestion constitue le socle applicatif du chatbot.

**Objectif :** améliorer l'expérience utilisateur et automatiser certains processus grâce à un assistant conversationnel.

| Utilisateur | Cas d'usage prévus |
|---|---|
| Client | Questions sur le menu, les ingrédients et les horaires ; création d'une réservation ou d'une commande en langage naturel |
| Personnel | Consultation du statut des commandes et signalement d'une alerte de température |
| Manager | Résumé des ventes du jour à partir des statistiques de revenus |

**Intégration prévue :** un endpoint `/api/chatbot/` côté backend appelant un modèle de langage, ainsi qu'un widget de discussion dans le frontend React.

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
- SimpleJWT
- Jazzmin
- Cloudinary
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

Les chemins des fichiers, les noms des dossiers, les endpoints et les commandes d'installation du README d'origine doivent rester inchangés. Seules les formulations relatives à la présentation du projet sont adaptées pour ne plus le décrire comme un projet de fin d'études.
