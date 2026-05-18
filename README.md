# 🏆 Plateforme de Gestion de Clubs Sportifs - Afrique de l'Ouest

Plateforme SaaS complète pour la gestion administrative, financière et sportive des clubs et académies sportifs en Afrique de l'Ouest avec support CFA.

## 🎯 Fonctionnalités Principales

### 👥 Gestion des Joueurs
- Profils complets (données personnelles, groupe sanguin, contacts familiaux)
- Historique de performances
- Catégories et équipes
- Transferts entrants/sortants
- Cartes de joueurs

### 👨‍💼 Gestion du Personnel
- Base de données du staff (entraîneurs, médecins, administratifs)
- Contrats d'emploi
- Historique des missions
- Documents RH (attestations, ordres de mission)

### 💰 Système de Paie
- Gestion des salaires (CFA)
- Génération de bulletins de paie
- Déductions et primes
- Historique des paiements

### 📊 Gestion Financière
- Transactions et mouvements de trésorerie
- Gestion des dons et revenus
- Préparation des bilans comptables
- Exercice comptable en cours

### 🗓️ Calendrier & Performances
- Planification des matchs
- Suivi des rencontres (résultats, statistiques)
- Performances individuelles par joueur
- Saison 2025-2026

### 🤝 Gestion des Partenaires
- Listes des partenaires
- Contrats de partenariat
- Suivi des collaborations

## 🛠️ Stack Technologique

- **Backend**: Django 4.2 + Django REST Framework
- **Base de Données**: PostgreSQL 15
- **Cache**: Redis 7
- **Tâches Async**: Celery + Celery Beat
- **Authentification**: JWT (SimpleJWT)
- **API Documentation**: drf-yasg (Swagger)
- **Containerisation**: Docker & Docker Compose

## 📋 Structure du Projet

```
sports-club-management/
├── backend/
│   ├── config/
│   │   ├── settings.py
│   │   ├── urls.py
│   │   ├── wsgi.py
│   │   ├── asgi.py
│   │   └── celery.py
│   ├── apps/
│   │   ├── users/
│   │   ├── clubs/
│   │   ├── players/
│   │   ├── staff/
│   │   ├── payroll/
│   │   ├── finance/
│   │   ├── matches/
│   │   ├── transfers/
│   │   └── documents/
│   ├── manage.py
│   ├── requirements.txt
│   └── Dockerfile
├── docker-compose.yml
├── .env.example
└── README.md
```

## 🚀 Installation & Démarrage

### Prérequis
- Docker & Docker Compose
- Git

### Étapes

1. **Clone le repository**
```bash
git clone https://github.com/CAMARA85000/sports-club-management.git
cd sports-club-management
```

2. **Configure l'environnement**
```bash
cp .env.example .env
```

3. **Lance les services Docker**
```bash
docker-compose up -d
```

4. **Initialise la base de données**
```bash
docker-compose exec backend python manage.py migrate
```

5. **Crée un compte administrateur**
```bash
docker-compose exec backend python manage.py createsuperuser
```

6. **Accède à l'application**
- API: http://localhost:8000
- Admin: http://localhost:8000/admin
- Swagger: http://localhost:8000/api/docs

## 📡 API Endpoints

### Authentification
- `POST /api/auth/login/` - Connexion
- `POST /api/auth/refresh/` - Renouveler token
- `POST /api/auth/logout/` - Déconnexion

### Clubs
- `GET/POST /api/clubs/` - Liste & création
- `GET/PUT/DELETE /api/clubs/{id}/` - Détails, mise à jour, suppression

### Joueurs
- `GET/POST /api/players/` - Liste & création
- `GET/PUT/DELETE /api/players/{id}/` - Détails, mise à jour, suppression
- `POST /api/players/{id}/upload-photo/` - Upload photo
- `GET /api/players/{id}/performances/` - Performances

### Personnel
- `GET/POST /api/staff/` - Liste & création
- `GET/PUT/DELETE /api/staff/{id}/` - Détails, mise à jour, suppression

### Paie
- `GET/POST /api/payroll/salaries/` - Gestion salaires
- `GET /api/payroll/pay-slips/{id}/` - Bulletins de paie
- `POST /api/payroll/pay-slips/generate/` - Générer bulletin

### Finance
- `GET/POST /api/finance/transactions/` - Transactions
- `GET /api/finance/balance-sheet/` - Bilan comptable
- `GET /api/finance/reports/` - Rapports financiers

### Matchs
- `GET/POST /api/matches/` - Calendrier
- `GET/PUT /api/matches/{id}/` - Détails du match

## 🔐 Authentification

L'API utilise JWT pour l'authentification. Incluez le token dans les headers :

```bash
Authorization: Bearer <your_token>
```

## 🐳 Commandes Docker Utiles

```bash
# Voir les logs
docker-compose logs -f backend

# Accéder au shell Django
docker-compose exec backend python manage.py shell

# Créer migrations
docker-compose exec backend python manage.py makemigrations

# Exécuter migrations
docker-compose exec backend python manage.py migrate

# Arrêter les services
docker-compose down
```

## 📱 Frontend (À venir)

React.js avec :
- Dashboard administrateur
- Gestion joueurs/staff
- Génération documents (PDF)
- Graphiques de performances
- Mobile responsive

## 🤝 Contribution

Les contributions sont bienvenues ! 

## 📄 Licence

MIT License

## 📧 Support

Pour les questions ou problèmes, ouvrez une issue sur GitHub.

---

**Développé pour les clubs et académies sportifs d'Afrique de l'Ouest** 🌍⚽
