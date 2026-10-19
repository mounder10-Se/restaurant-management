Savoria — Plateforme de Gestion de Restaurants avec Assistant IA

Savoria est une plateforme web de gestion multi-restaurants conçue pour centraliser et simplifier les opérations quotidiennes des établissements de restauration. Elle combine une application web développée avec React et TypeScript, une API REST développée avec Django et Django REST Framework, ainsi qu'un module d'assistance conversationnelle basé sur l'intelligence artificielle, actuellement en cours d'intégration.

La plateforme regroupe la gestion des commandes, des réservations, des menus, des stocks, de l'approvisionnement et des finances au sein d'une interface unique. Elle propose des espaces adaptés aux différents profils utilisateurs : clients, clients corporate, chefs, managers, serveurs, caissiers, livreurs, fournisseurs et administrateurs.

Savoria intègre également un système de suivi de la température et de l'humidité des chambres froides, permettant de surveiller les conditions de conservation des produits et de signaler les éventuelles anomalies.

🎯 Objectifs

Simplifier le parcours client : consultation des menus, commandes, réservations et avis.

Centraliser la gestion de plusieurs restaurants au sein d'une même plateforme.

Fournir des interfaces adaptées aux différents métiers de la restauration.

Automatiser certaines opérations : notifications, suivi des revenus et attribution des tables.

Faciliter la gestion des stocks, des ingrédients et de l'approvisionnement.

Surveiller les conditions de conservation des produits grâce à un capteur de température et d'humidité.

Préparer l'intégration d'un assistant IA pour faciliter l'accès aux informations et automatiser certaines tâches en langage naturel.

📱 Fonctionnalités principales

👤 Espace client

Inscription et connexion sécurisées par JWT.

Consultation des menus, catégories, descriptions, photos et prix.

Panier et gestion de différents types de commandes : sur place, livraison, à emporter et précommande.

Réservation de tables avec attribution automatique selon les disponibilités.

Suivi de l'état des commandes.

Publication d'avis et notation après commande.

Gestion du profil personnel.

🏢 Espace client corporate

Interface dédiée aux clients professionnels.

Gestion des profils, restaurants et commandes d'entreprise.

Prise en charge de la tarification entreprise, des conventions, des rapports et des avis.

👨‍🍳 Espace chef

Consultation des commandes et mise à jour de leur statut.

Gestion des plats, recettes et ingrédients.

Gestion de l'inventaire et composition du menu du jour.

Communication avec l'équipe et réception des notifications.

🧑‍💼 Espace manager

Validation des menus du jour avant transmission au fournisseur.

Suivi des revenus, des ventes, du nombre de commandes et des dépenses.

Supervision des commandes, des réservations et des employés.

Consultation des mesures de température et d'humidité avec un système visuel d'alerte.

🛎️ Autres espaces métier

Serveur : gestion des commandes en salle et suivi des réservations.

Caissier : suivi des paiements et consultation des rapports.

Livreur : suivi des commandes à livrer et déclaration des livraisons échouées.

Fournisseur : validation des besoins en ingrédients et suivi des notifications d'approvisionnement.

Administrateur : gestion globale des utilisateurs, des rôles, des restaurants et consultation des indicateurs financiers.

🤖 Assistant IA

Le module de chatbot IA est en cours d'intégration. Son objectif est d'enrichir l'expérience utilisateur et de faciliter certaines opérations grâce à une interface conversationnelle.

Les cas d'utilisation envisagés comprennent :

Répondre aux questions des clients concernant les menus, les ingrédients et les horaires.

Faciliter la création de réservations et de commandes en langage naturel.

Permettre au personnel de consulter certaines informations opérationnelles.

Aider les managers à obtenir des résumés des ventes et des indicateurs du restaurant.

L'intégration prévue repose sur un endpoint dédié côté backend et un widget de discussion dans l'application React. Ces fonctionnalités restent à finaliser.

🔄 Automatisation des processus

La plateforme prévoit plusieurs mécanismes d'automatisation :

Mise à jour des revenus du restaurant lors de l'enregistrement d'un paiement.

Notifications destinées au personnel concerné lors de la création de commandes.

Création de profils métier selon le rôle attribué à un utilisateur.

Attribution automatique d'une table disponible répondant à la capacité demandée.

Circuit de validation du menu du jour par le manager, puis par le fournisseur.

🏗️ Architecture technique

Savoria s'appuie sur une architecture client-serveur composée de :

Frontend : application web React communiquant avec le backend via HTTP et JSON.

Backend : API REST Django REST Framework avec authentification JWT.

Base de données : SQLite pour le développement et PostgreSQL pour la production.

Stockage des images : Cloudinary.

Capteur IoT : transmission des mesures de température et d'humidité au backend.

Assistant IA : intégration conversationnelle prévue avec un modèle de langage.

🛠️ Technologies utilisées

Frontend

React 19, TypeScript et Vite

Tailwind CSS et shadcn/ui

React Router

TanStack Query et Axios

React Hook Form et Zod

Framer Motion, Recharts et Lucide

Backend

Python et Django 5.2

Django REST Framework 3.16

SimpleJWT pour l'authentification

Jazzmin pour l'interface d'administration

Cloudinary pour le stockage des images

WhiteNoise et Gunicorn

SQLite et PostgreSQL

Outils et déploiement

Git, Postman, PyCharm et Visual Studio Code

Render et Cloudinary

🔮 Perspectives d'évolution

Finalisation et déploiement de l'assistant conversationnel IA.

Intégration complète du paiement en ligne.

Ajout de notifications en temps réel via WebSockets.

Prise en charge du français, de l'arabe et de l'anglais.

Développement d'analyses avancées et de prévisions des besoins en ingrédients.

Création d'applications mobiles destinées aux clients et aux livreurs.
