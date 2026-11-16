#  Résumé de l'Infrastructure — Projet HRMS

## Ce que j'ai mis en place
J'ai configuré toute l'infrastructure Docker du projet pour que chacun puisse lancer l'environnement complet sur son PC en **une seule commande**, sans rien installer manuellement.

### 1. Bases de données isolées (Principe Microservices)
Chaque microservice possède sa propre base de données et son propre utilisateur dédié (créés automatiquement au démarrage via les scripts `init-databases.sh`) :
* **PostgreSQL (`localhost:5432`) :**
  * `hrms_employee` → pour **Employee Service**
  * `hrms_payroll` → pour **Payroll Service**
  * `keycloak` → pour la sécurité et l'authentification
* **MySQL (`localhost:3306`) :**
  * `hrms_leave` → pour **Leave Service**
  * `hrms_recruitment` → pour **Recruitment Service**
  * `hrms_notification` → pour **Notification Service**

### 2. Services techniques & Interfaces Web
* **Keycloak (`http://localhost:8081`) :** Gère l'authentification (Login, rôles, tokens JWT) pour tous les microservices.
* **phpMyAdmin (`http://localhost:8082`) :** Interface web pour visualiser les bases **MySQL**.
* **pgAdmin (`http://localhost:8083`) :** Interface web pour visualiser les bases **PostgreSQL** (`admin@hrms.com` / `admin`).
* **Redis (`localhost:6379`) :** Cache rapide en mémoire.
* **Kafka (`localhost:9092`) :** Bus d'événements pour la communication asynchrone entre nos services.

---

## Comment lancer le projet sur votre PC
1. Créez votre fichier **`.env`** dans le dossier `infrastructure/` avec les variables d'environnement.
2. Lancez tous les services :
   ```bash
   docker compose up -d
   ```
3. *(Si vous modifiez le `.env` plus tard)* Réinitialisez proprement avec :
   ```bash
   docker compose down -v
   docker compose up -d
   ```
