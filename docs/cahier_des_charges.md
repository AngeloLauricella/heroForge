# 🧙‍♂️ HeroForge — Cahier des charges

## 1. Présentation générale
**Nom du projet :** HeroForge  
**Type d’application :** Application web de gestion et suivi de progression RPG  
**Technologie principale :** Symfony 7 (PHP 8.3)  
**Objectif :**  
Permettre aux joueurs de suivre la progression de leurs personnages dans un univers de jeu de rôle (RPG).  
Chaque joueur peut créer un compte, gérer ses héros, suivre leur expérience, leur niveau, leur or et leurs équipements, et consulter leur historique d’aventures dans différents donjons.

---

## 2. Objectifs du projet
- Offrir une interface simple et immersive pour la gestion de personnages RPG.  
- Mettre en valeur la maîtrise de Symfony (entités, relations, formulaires, sécurité, Twig).  
- Démontrer des compétences en architecture logicielle, base de données, sécurité et interface web.  
- Fournir une base évolutive pouvant servir de back-office à un vrai jeu (ex : Donjons du Destin).

---

## 3. Utilisateurs cibles
| Rôle | Description | Accès |
|------|--------------|-------|
| **Joueur** | Utilisateur standard. Peut créer un compte, gérer ses personnages, voir leurs stats, inventaire et progression. | Interface utilisateur (front) |
| **Administrateur** | Gère le contenu global (classes, objets, donjons, utilisateurs). Peut modifier les données. | Interface d’administration |

---

## 4. Fonctionnalités principales

### 🔐 Authentification & rôles
- Inscription / connexion / déconnexion.
- Gestion des rôles : `ROLE_USER` et `ROLE_ADMIN`.
- Sécurité via le composant Symfony Security.

### ⚔️ Gestion des personnages
- CRUD complet (Créer, Lire, Modifier, Supprimer).  
- Attributs : nom, classe, niveau, XP, or, vitalité, force, agilité, intelligence.  
- Gain automatique de niveau en fonction de l’XP cumulée.  

### 🧙 Gestion des classes
- Chaque personnage appartient à une classe (Guerrier, Mage, Archer, etc.).  
- Les classes confèrent des bonus statistiques de base.  
- CRUD accessible à l’admin.  

### 💍 Gestion des objets
- Objets d’équipement ou de consommation (armes, armures, potions…).  
- Effets sur les statistiques du personnage.  
- Relation ManyToMany (un perso peut avoir plusieurs objets).  

### 🏰 Gestion des donjons
- Les donjons possèdent un nom, un biome, une difficulté et des récompenses.  
- Historique des donjons réussis par chaque personnage.  
- Attribution automatique d’XP et d’or après réussite.  

### 📜 Historique des aventures
- Enregistrement des donjons terminés, de l’XP gagnée et de la date.  
- Consultable dans le tableau de bord du joueur.  

### 📊 Tableau de bord joueur
- Vue globale sur ses personnages et leurs statistiques.  
- Graphiques d’évolution (XP / Niveau).  
- Possibilité de télécharger une **fiche PDF** de chaque personnage.  

### ⚙️ Interface d’administration
- Gestion centralisée des utilisateurs, classes, objets et donjons.  
- Accès restreint à l’admin via `ROLE_ADMIN`.

---

## 5. Architecture technique

### 🔧 Technologies utilisées
- **Back-end :** Symfony 7 (PHP 8.3)  
- **Base de données :** MySQL / Doctrine ORM  
- **Front-end :** Twig + Uikit (ou Tailwind CSS)  
- **Sécurité :** Symfony Security (BCrypt, CSRF, rôles, authentification)  
- **Visualisation :** Chart.js ou Recharts (graphiques d’évolution)  
- **PDF :** Dompdf  
- **Versionning :** Git / GitHub  
- **Tests :** PHPUnit (tests unitaires sur logique d’XP et niveau)

---

## 6. Modèle de données (simplifié)

User (1) --- (N) Personnage
Personnage (N) --- (1) Classe
Personnage (N) --- (N) Objet
Personnage (N) --- (N) Donjon via Historique
Historique (N) --- (1) Donjon


---

## 7. Planning prévisionnel

| Étape | Durée | Objectif |
|-------|--------|-----------|
| Phase 1 : Initialisation | 1 semaine | Installation Symfony, config BDD, GitHub, cahier des charges |
| Phase 2 : Authentification | 2 semaines | Création comptes + rôles |
| Phase 3 : Personnages | 2 semaines | CRUD + système d’XP |
| Phase 4 : Classes & Objets | 3 semaines | Relations + inventaire |
| Phase 5 : Donjons & Historique | 3 semaines | Récompenses, suivi |
| Phase 6 : Dashboard & UI | 2 semaines | Tableau de bord, stats, graphiques |
| Phase 7 : Finition & tests | 2 semaines | PDF, mails, corrections |
| Phase 8 : Présentation finale | 1 semaine | Rapport + démo |

---

## 8. Contraintes techniques
- Application hébergeable sur serveur web (Apache ou Nginx).  
- Base de données relationnelle (MySQL).  
- Aucune dépendance à un service externe.  
- Sécurité et propreté du code (PSR-12).  
- Documentation claire (README, diagrammes, changelog).

---

## 9. Livrables
- Code source complet (GitHub propre, commits réguliers).  
- Cahier des charges (présent document).  
- UML / MCD et schémas d’architecture.  
- Rapport technique (PDF).  
- Démo fonctionnelle du site.

---

## 10. Évolutions futures (facultatives)
- API REST pour interagir avec un jeu externe (ex : Donjons du Destin).  
- Système de combat simulé entre personnages.  
- Système de guildes et classement.  
- Chat ou notifications temps réel via Mercure.