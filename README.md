# SignalSim: Simulateur de Propagation de Signaux Radio

![WhatsApp Image 2024-12-29 at 00 06 36](https://github.com/user-attachments/assets/7637270b-db8e-4a98-807d-8fc75dbbd808)

## Description
Une application pour simuler la propagation des ondes radio dans différents environnements.

## Caractéristiques
- Modélisation : Simulation de la propagation des signaux dans des zones urbaines, rurales et intérieures.
- Visualisation : Affichage interactif des zones de couverture et des interférences.
- Exportation : Possibilité d’exporter les données pour des analyses supplémentaires.

## Impact
L’application aide les chercheurs et ingénieurs à tester des hypothèses sur la propagation des signaux dans des environnements variés, 
contribuant à la recherche et à l’amélioration des systèmes de télécommunication.

## Structure Technique


### Frontend

- Technologies : React.js avec des bibliothèques comme Redux pour la gestion d’état et d3.js pour les visualisations.
- Fonctionnalités :
  - Modélisation interactive des zones.
  - Tableaux de bord pour visualiser les résultats de simulation.


### Backend

- Technologies : Spring Boot pour gérer les requêtes et la logique métier.
- Structure :
  - Contrôleurs : Gestion des endpoints REST.
  - Services : Traitement des calculs et des simulations.
  - Données : Stockage des environnements simulés et des résultats dans une base MySQL.

## Instructions de Développement

### Prérequis

1. Node.js et npm pour le frontend.
2. Java et Maven pour le backend.
3. MySQL pour la base de données.

### Backend Setup

1. Clonez le backend :
   bash
   git clone <backend_repo_url>
   cd backend
   

2. Configurez le fichier application.properties :
   properties
   spring.datasource.url=jdbc:mysql://localhost:3306/signalsim
   spring.datasource.username=root
   spring.datasource.password=yourpassword
   spring.jpa.hibernate.ddl-auto=update
   

3. Démarrez l’application Spring Boot :
   bash
   mvn spring-boot:run


### Frontend Setup

1. Clonez le frontend :
   bash
   git clone <frontend_repo_url>
   cd frontend
   

2. Installez les dépendances :
   bash
   npm install
   

3. Démarrez le serveur de développement React :
   bash
   npm start
   

4. Accédez à l’application sur http://localhost:3000.


   
## API Endpoints

### Simulation

- POST /simulate
  - Input : JSON décrivant la zone et les paramètres de simulation.
  - Output : Résultats de la simulation.

### Exportation
- GET /export
  - Input : ID de simulation.
  - Output : Fichier CSV ou JSON des résultats.

## Contributeurs







