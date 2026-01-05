# 🤖 Agent Conversationnel IA - Génération Prospect Marrakech

Un agent conversationnel intelligent développé avec n8n pour automatiser la vente et la réservation d'activités touristiques à Marrakech.

## 📋 Description

Cet agent IA agit comme conseiller voyage commercial spécialisé, capable de :
- Recommander des activités adaptées à la météo en temps réel
- Gérer les réservations de bout en bout
- Automatiser les notifications et confirmations
- Maintenir une base de données client centralisée

## ✨ Fonctionnalités Principales

### 🌤️ Intelligence Météo
- Récupération automatique des prévisions météo via SerpAPI
- Recommandations d'activités adaptées aux conditions climatiques
- Suggestions contextuelles (chaleur, pluie, vent, temps idéal)

### 💼 Gestion Commerciale
- Base de connaissances vectorielle (RAG) pour informations produits
- Calcul automatique des prix avec réductions enfants et suppléments transport
- Proposition de packages multi-activités

### 📅 Automatisation Complète
- **Google Calendar** : Création automatique d'événements
- **Google Sheets** : Enregistrement des réservations
- **Slack** : Notifications internes en temps réel
- **Gmail** : Envoi de confirmations par email

### 🧠 Mémoire Conversationnelle
- Contexte maintenu tout au long de la conversation
- Personnalisation selon le profil du client
- Suivi des préférences et contraintes

## 🛠️ Technologies Utilisées

- **n8n** : Plateforme d'automatisation workflow
- **OpenAI GPT-4.1-mini** : Modèle de langage conversationnel
- **OpenAI Embeddings** : Vectorisation de la base de connaissances
- **SerpAPI** : Récupération données météo
- **Google Workspace** : Calendar, Sheets, Drive, Gmail
- **Slack** : Notifications équipe

## 📂 Structure du Workflow

```
┌─────────────────────┐
│  Chat Trigger       │ ← Point d'entrée utilisateur
└──────┬──────────────┘
       │
┌──────▼──────────────┐
│   AI Agent          │ ← Cerveau de l'assistant
│   (GPT-4.1-mini)    │
└──────┬──────────────┘
       │
       ├─→ Vector Store (Base connaissances)
       ├─→ SerpAPI (Météo)
       ├─→ Google Sheets (BDD Clients)
       ├─→ Google Calendar (Événements)
       ├─→ Gmail (Confirmations)
       └─→ Slack (Notifications)
```

## 🚀 Installation

### Prérequis
- n8n installé (self-hosted ou cloud)
- Comptes API configurés :
  - OpenAI API
  - SerpAPI
  - Google Workspace OAuth
  - Slack OAuth

### Étapes

1. **Importer le workflow**
   ```bash
   # Télécharger le fichier workflow.json
   # Dans n8n : Workflows > Import from File
   ```

2. **Configurer les credentials**
   - OpenAI API Key
   - SerpAPI Key
   - Google OAuth2 (Drive, Sheets, Calendar, Gmail)
   - Slack OAuth2

3. **Préparer la base de connaissances**
   - Créer un Google Doc avec toutes les activités
   - Mettre à jour l'URL dans le node "Google Drive"
   - Lancer une première exécution pour vectoriser les données

4. **Configurer le Google Sheet**
   - Créer un sheet avec colonnes : Nom, Email, Telephone, Activite_souhaitee, Date_activite
   - Mettre à jour l'ID du sheet dans le workflow

5. **Activer le workflow**

## 📊 Base de Données Activités

Le système utilise une base vectorielle contenant :
- 50+ activités (désert, Atlas, hammams, excursions)
- Prix détaillés avec réductions
- Politiques d'annulation et conditions
- Informations pratiques et FAQ

## 🎯 Cas d'Usage

### Exemple de Conversation

**Client** : "Je cherche une activité pour le 15 mars, nous sommes 2 adultes et 1 enfant"

**Agent** :
1. Récupère la météo du 15 mars
2. Identifie les conditions (ex: 28°C, ensoleillé)
3. Recommande 3-4 activités adaptées
4. Calcule les prix avec réduction enfant
5. Guide vers la réservation

### Workflow de Réservation

1. Collecte des informations client
2. Confirmation des détails
3. **Automatiquement** :
   - Ajout dans Google Sheet
   - Création événement Calendar
   - Email de confirmation
   - Message Slack à l'équipe

## 📈 Métriques & Performance

- ⚡ Temps de réponse : < 3 secondes
- 🎯 Taux de conversion : Suivi via Google Sheets
- 📧 Emails automatisés : 100% des réservations
- 📊 Tableau de bord : Slack + Sheets

## 🔐 Sécurité & Confidentialité

- Aucune donnée sensible dans le code
- Credentials stockés de manière sécurisée dans n8n
- RGPD compliant : données clients chiffrées

## 🤝 Contribution

Ce projet est un portfolio personnel démontrant :
- Architecture d'agent IA conversationnel
- Intégration multi-services
- Automatisation de processus métier
- RAG (Retrieval Augmented Generation)

## 📝 Licence

MIT License - Projet de démonstration

## 👤 Auteur

Créé comme projet portfolio d'automatisation IA

## 🔗 Liens Utiles

- [Documentation n8n](https://docs.n8n.io)
- [OpenAI API](https://platform.openai.com/docs)
- [SerpAPI Docs](https://serpapi.com/search-api)

---

⭐ **Note** : Ce workflow est configuré pour "Génération Prospect Marrakech". Pour l'adapter à votre usage, modifiez :
- Le prompt système dans le node "AI Agent"
- La base de connaissances (Google Doc)
- Les IDs des Google Sheets/Calendar
- Le canal Slack