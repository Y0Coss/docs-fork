## **Public Cloud - Informations Générales (Public Cloud - General Information)**

1. Actuel :

Public Cloud - General Information (produit/univers)
- Getting Started (section, mais plus une collection de guides qu'une vraie introduction unifiée)
- General Information (section)
- Public Cloud project management (section)
- Migration (section spécifique)
- Tutorials (section générale)
- Services management (section, avec des sous-sections par outil : Horizon, OpenStack)
- Infrastructure (section spécifique)
- Billing information (section spécifique)

2. À venir (avec les 5 sections communes + sections spécifiques pertinentes) :

Public Cloud - General Information (produit/univers)
- Démarrage Rapide (Getting Started)
- Informations Générales (General Information)
- Gestion et Opérations (Management & Operations)
- Tutoriels et Cas d'Usage (Tutorials & Use Cases)
- Infrastructure (section spécifique, pertinente ici)
- Migration (section spécifique, pertinente ici)
- Informations de Facturation (Billing Information) (section spécifique, pertinente ici)

Différences clés : La principale différence est la structuration plus rigide et prévisible des 5 sections communes, qui permettraient de mieux organiser les contenus existants. Les sections "Services management" seraient probablement intégrées sous "Gestion et Opérations" avec des sous-sections par outil, ou les outils seraient mentionnés dans les guides eux-mêmes.

## **Compute**

1. Actuel :

Compute (produit)
- Getting started (section, déjà bien orientée)
- General information (section)
- Project management (section)
- Instances management (section majeure, avec de nombreuses sous-sections par outil : Control Panel, Horizon, OpenStack)
- Tutorials (section générale)

2. À venir (avec les 5 sections communes + sections spécifiques pertinentes) :

Compute (produit)
- Démarrage Rapide (Getting Started)
- Informations Générales (General Information)
- Gestion et Opérations (Management & Operations) (engloberait l'actuelle "Project management" et "Instances management")
- Dépannage (Troubleshooting) (actuellement absent en tant que section dédiée ici)
- Tutoriels et Cas d'Usage (Tutorials & Use Cases)

Différences clés : L'intégration de la gestion de projet et de la gestion des instances sous une seule et même section "Gestion et Opérations" simplifierait la structure. L'ajout explicite d'une section "Dépannage" serait un plus. La section "Tutorials" resterait, mais avec une portée plus claire pour des cas d'usage avancés.

## **Stockage et Sauvegarde (Storage and Backup)**

### **Object Storage**

1. Actuel :

Object Storage (produit)
- General information (section)
- General guides to start (section, similaire à "Getting started")
- Tutorials (section générale)
- Configure Object Storage with your solutions (section spécifique aux intégrations)
- Cold Archive Storage Class Specifics (section spécifique à une classe de stockage)
- OpenStack Swift Storage Class Specifics (section spécifique à une API/classe de stockage)
- OpenStack Swift Archive Storage Class Specifics (section spécifique à une API/classe de stockage)

À venir (avec les 5 sections communes + sections spécifiques pertinentes) :

Object Storage (produit)
- Démarrage Rapide (Getting Started) (remplacerait "General guides to start")
- Informations Générales (General Information)
- Gestion et Opérations (Management & Operations) (inclurait la gestion des règles de vie, l'immutabilité, etc.)
- Dépannage (Troubleshooting) (actuellement absent en tant que section dédiée ici)
- Tutoriels et Cas d'Usage (Tutorials & Use Cases) (engloberait les "Tutorials" et "Configure Object Storage with your solutions")
- Spécificités des Classes de Stockage (Storage Class Specifics) (section spécifique regroupant Cold Archive, Swift, Swift Archive)

Différences clés : La consolidation et la standardisation des sections "Démarrage Rapide" et "Tutoriels", ainsi que l'ajout d'une section "Dépannage" dédiée. Le regroupement des spécificités par classe de stockage sous une section parente apporterait plus de clarté.

### **Block Storage**

1. Actuel :

Block storage (produit)
- Cloud Disk Array (sous-produit/type de stockage avec ses propres guides)
- Guides de gestion de disques ("Test disk speed", "Increasing the size", "Creating a volume snapshot", etc.)

2. À venir (avec les 5 sections communes + sections spécifiques pertinentes) :

Block Storage (produit)
- Démarrage Rapide (Getting Started) (actuellement absent, mais nécessaire)
- Informations Générales (General Information) (actuellement absent)
- Gestion et Opérations (Management & Operations) (regrouperait la gestion des disques, volumes, snapshots, backups)
- Dépannage (Troubleshooting) (actuellement absent)
- Tutoriels et Cas d'Usage (Tutorials & Use Cases)
- Cloud Disk Array (section spécifique, si suffisamment distincte pour le justifier)

Différences clés : La structure actuelle est très fragmentée. L'adoption des sections communes apporterait une organisation claire pour le démarrage, les informations générales, et regrouperait toute la gestion sous une seule section "Gestion et Opérations", ce qui est actuellement dispersé.

## **Public Cloud Network Services**

1. Actuel :

Public Cloud Network Services (produit)
- Concepts (section, très utile)
- Getting started (section, déjà bien orientée)
- Additional IP (section spécifique à un type de ressource)
- Configuration (section, pertinente)
- Technical resources (section, un peu fourre-tout pour des guides techniques)
- Tutorials (section générale)

2. À venir (avec les 5 sections communes + sections spécifiques pertinentes) :

Public Cloud Network Services (produit)
- Démarrage Rapide (Getting Started)
- Informations Générales (General Information) (inclurait les concepts et FAQ)
- Gestion et Opérations (Management & Operations) (engloberait la gestion des IP additionnelles, des Load Balancers, vRack, etc.)
- Dépannage (Troubleshooting) (actuellement absent en tant que section dédiée ici)
- Tutoriels et Cas d'Usage (Tutorials & Use Cases)
- Configuration Réseau (Network Configuration) (section spécifique, très pertinente ici, pour les configurations avancées, règles L7, etc.)

Différences clés : La section "Concepts" serait intégrée dans "Informations Générales". "Additional IP" et "Technical Resources" seraient réorganisés sous "Gestion et Opérations" ou "Configuration Réseau" selon leur nature. Le "Dépannage" serait formalisé.

## **Public Cloud Databases**

1. Actuel :

Public Cloud Databases (produit)
- General information (section, très complète)
- General guides (section, similaire à "Getting started", avec des guides divers)

À venir (avec les 5 sections communes + sections spécifiques pertinentes) :

Public Cloud Databases (produit)
- Démarrage Rapide (Getting Started) (remplacerait "General guides" pour les premiers pas)
- Informations Générales (General Information)
- Gestion et Opérations (Management & Operations) (regrouperait la configuration avancée, la restauration de backup, la gestion du disque, le redimensionnement)
- Dépannage (Troubleshooting) (actuellement intégré dans "General guides" mais mérite sa propre section)
- Tutoriels et Cas d'Usage (Tutorials & Use Cases) (actuellement peu développé ici en tant que section distincte)

Différences clés : La distinction plus nette entre "Démarrage Rapide" et "Gestion et Opérations". L'extraction du "Dépannage" en section propre. La création d'une section "Tutoriels et Cas d'Usage" dédiée qui pourrait être étoffée.