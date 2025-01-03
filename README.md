# SignalSim: Simulateur de Propagation de Signaux Radio

![WhatsApp Image 2024-12-29 at 00 06 36](https://github.com/user-attachments/assets/7637270b-db8e-4a98-807d-8fc75dbbd808)

## Description
SignalSim est une application innovante conçue pour simuler la propagation des ondes radio dans divers environnements, offrant aux chercheurs, ingénieurs, et développeurs une plateforme puissante et intuitive. Elle permet de modéliser précisément la propagation des signaux dans des contextes variés, notamment les zones urbaines densément peuplées, les paysages ruraux ouverts, et les espaces intérieurs complexes. Grâce à une interface interactive, SignalSim fournit des visualisations détaillées des zones de couverture, des interférences et des effets environnementaux sur les signaux radio. L’application inclut également des fonctionnalités d’exportation, permettant d’enregistrer et d’analyser les données générées sous différents formats pour approfondir les recherches ou alimenter d'autres systèmes. En combinant des outils de pointe comme React.js pour le frontend, Spring Boot pour le backend, et une base de données robuste MySQL, SignalSim se positionne comme un outil indispensable pour tester des hypothèses, évaluer des performances de réseau et améliorer les systèmes de télécommunication de nouvelle génération. Elle représente un atout majeur pour l’étude et la compréhension des défis complexes liés à la transmission des signaux radio dans des environnements hétérogènes.

## Software architecture
![image](https://github.com/user-attachments/assets/cb7f8393-56e8-4d84-93da-71bd24d74a75)

## Caractéristiques
- Modélisation : Simulation de la propagation des signaux dans des zones urbaines, rurales et intérieures.
- Visualisation : Affichage interactif des zones de couverture et des interférences.
- Exportation : Possibilité d’exporter les données pour des analyses supplémentaires.

## Impact
L’application aide les chercheurs et ingénieurs à tester des hypothèses sur la propagation des signaux dans des environnements variés, 
contribuant à la recherche et à l’amélioration des systèmes de télécommunication.

## Docker Image
```sh


version: '3.8'

services:
  mysql:
    image: mysql:5.7
    ports:
      - "3306:3306"
    environment:
      MYSQL_DATABASE: signalsim_db
      MYSQL_ROOT_PASSWORD: 
    volumes:
      - mysql_data:/var/lib/mysql

  backend:
    build:
      context: ./Signalsim
      dockerfile: Dockerfile # Dockerfile pour le backend
    ports:
      - "8080:8080"
    environment:
      SPRING_DATASOURCE_URL: jdbc:mysql://mysql:3306/signalsim_db
      SPRING_DATASOURCE_USERNAME: root
      SPRING_DATASOURCE_PASSWORD:
    depends_on:
      - mysql

  frontend:
    build:
      context: ./signalsim
      dockerfile: Dockerfile # Dockerfile pour le frontend
    ports:
      - "3000:3000"
    depends_on:
      - backend

  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    ports:
      - "8081:80"
    environment:
      PMA_HOST: mysql
      MYSQL_ROOT_PASSWORD:
      PMA_PORT: 3306

volumes:
  mysql_data:
```


## Structure Technique


### Frontend

- Technologies : React.js, Leaflet pour la carte, et Chart.js pour les graphiques.
  
- Fonctionnalités :
  - Modélisation interactive des zones.
  - Visualisation des résultats de simulation.


### Backend

- Technologies : Spring Boot pour gérer les requêtes et la logique métier.
- Structure :
  - Contrôleurs : Gestion des endpoints REST.
  - Services : Traitement des calculs et des simulations.
  - Données : Stockage des environnements simulés et des résultats dans une base MySQL.
    
   ### Dependencies

1. *Spring Data JPA:*
   - Purpose: Simplifies data access using JPA in Spring Boot.
2. MySQL Connector/J:
Purpose: JDBC driver for connecting to a MySQL database.


xml
```sh
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <scope>runtime</scope>
</dependency>

```

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
SignalSim a été réalisé grâce à la collaboration d'une équipe multidisciplinaire et dévouée, chacun apportant son expertise dans différents aspects du projet.

- Equipe de projet :
  - Nihal Majjad :  (https://github.com/nihal149).
  - Hafssa Bamhammed : (https://github.com/hafssa371).
  - Mohammed Yousfi : (https://github.com/MohammedYousfi49).
 
    ## Video Demonstration

    https://github.com/user-attachments/assets/290552cf-eaea-4457-bab7-9c86296f56ca


    









