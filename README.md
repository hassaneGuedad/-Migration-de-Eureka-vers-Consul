# Migration de Eureka vers Consul

Ce projet démontre la migration d'une architecture microservices de Spring Cloud Eureka vers HashiCorp Consul pour la découverte de services, ainsi que la conteneurisation de l'ensemble avec Docker Compose.

## Architecture
- **Consul** : Service Discovery et Health Checking.
- **Gateway** : Spring Cloud Gateway agissant comme point d'entrée unique.
- **Microservices** : 
  - `SERVICE-CLIENT` : Gère les informations des clients.
  - `SERVICE-CAR` : Gère les informations des voitures et communique avec le service client via Consul.

## Accomplissements
- Remplacement du client Eureka par le starter **Consul Discovery**.
- Configuration du **load balancing** inter-services avec un `RestTemplate` annoté `@LoadBalanced`.
- Intégration de **Spring Boot Actuator** pour les health checks de Consul.
- **Conteneurisation** complète avec Dockerfiles optimisés et un fichier `docker-compose.yml`.

## Installation et Lancement
1. S'assurer que Docker est installé et actif.
2. Cloner le dépôt.
3. À la racine du projet, lancer la commande :
   ```bash
   docker-compose up -d --build
   ```
4. Accéder à l'interface Consul : [http://localhost:8500](http://localhost:8500)
5. Tester les routes via la Gateway :
   - Clients : [http://localhost:8888/service-client/api/client](http://localhost:8888/service-client/api/client)
   - Voitures : [http://localhost:8888/service-car/api/car](http://localhost:8888/service-car/api/car)

## Technologies Utilisées
- Spring Boot 3.2.0
- Spring Cloud 2023.0.0 (Consul, Gateway)
- Java 17
- Docker & Docker Compose
- H2 Database (In-Memory)

<img width="960" height="336" alt="1" src="https://github.com/user-attachments/assets/c993775f-b989-455b-b01c-e9e6f57c553c" />

<img width="960" height="386" alt="2" src="https://github.com/user-attachments/assets/2793d950-3343-4a72-be1e-f3434274068f" />

