# Independant'fish

Independant'fish est une plateforme en ligne dédiée aux créateurs indépendants de leurres de pêche et aux passionnés souhaitant acheter ou vendre du matériel neuf ou d'occasion partout en France.

## Fonctionnalités principales

- **Espace Créateurs/Artisans :**
  - Création de compte vendeur/artisan
  - Page boutique personnalisable pour chaque vendeur
  - Mise en ligne, gestion et présentation de leurres (photos, description, prix, stock, etc.)
  - Abonnement des acheteurs à leurs vendeurs/artisans favoris
  - Recherche avancée de leurres par type, technique, marque, etc.
  - Découverte de leurres similaires proposés par différents créateurs

- **Espace Occasion :**
  - Dépôt et gestion d'annonces pour du matériel de pêche d'occasion (cannes, moulinets, accessoires...)
  - Modification et suppression d'annonces par les utilisateurs
  - Messagerie intégrée pour faciliter les échanges entre particuliers

- **Fonctionnalités transversales :**
  - Inscription/Connexion (acheteurs, vendeurs, administrateurs)
  - Système d'avis, de notation et de commentaires sur vendeurs/produits
  - Paiement sécurisé pour les achats de leurres neufs
  - Notifications (nouveautés, promotions, nouveaux produits des vendeurs suivis, etc.)
  - Interface d'administration pour la gestion des utilisateurs, produits, annonces, signalements, etc.

---

## Stack technique

- **Frontend** : [Angular](https://angular.io/) (TypeScript)
- **Backend** : [Spring Boot](https://spring.io/projects/spring-boot) (Java)
- **Base de données** : PostgreSQL ou MySQL
- **Paiement** : Stripe ou PayPal (intégration côté backend)
- **Stockage des images** : AWS S3, Cloudinary ou stockage local
- **Hébergement** : OVH, AWS, Azure, etc.

---

## Architecture

- **Frontend Angular**
  - Application SPA (Single Page Application)
  - Communication avec l’API backend via HTTP/REST
  - Gestion de l’authentification par JWT (JSON Web Token)
  - Routing avancé (pages boutique, profils, annonces, panier, etc.)
  - Formulaires réactifs pour la création de produits, annonces, inscriptions...

- **Backend Spring Boot**
  - API REST sécurisée
  - Contrôleurs pour utilisateurs, produits, commandes, annonces, abonnements, paiements...
  - Services métier (gestion logique des opérations)
  - Accès base de données via JPA/Hibernate
  - Sécurité avec Spring Security (JWT ou OAuth2)
  - Stockage et gestion des fichiers (images produits, photos profil, etc.)
  - Intégration Stripe/PayPal pour les paiements

---

## Exemple d'organisation des entités principales (Spring Boot)

```java
@Entity
public class Vendeur {
    @Id @GeneratedValue
    private Long id;
    private String nom;
    private String description;
    @OneToMany(mappedBy = "vendeur")
    private List<Leurre> leurres;
}

@Entity
public class Leurre {
    @Id @GeneratedValue
    private Long id;
    private String nom;
    private String type;
    private Double prix;
    private String imageUrl;
    @ManyToOne
    private Vendeur vendeur;
}
```

---

## Démarrage rapide

### Prérequis

- Node.js et Angular CLI pour le frontend
- Java 17+ et Maven/Gradle pour le backend
- PostgreSQL ou MySQL
- Compte Stripe ou PayPal (pour le paiement)

### Installation

#### 1. Cloner le projet

```bash
git clone https://github.com/ton-utilisateur/independantfish.git
cd independantfish
```

#### 2. Frontend Angular

```bash
cd frontend
npm install
ng serve
```
> Accès : http://localhost:4200

#### 3. Backend Spring Boot

```bash
cd backend
./mvnw spring-boot:run
```
> API : http://localhost:8080

#### 4. Configurer la base de données et les variables d’environnement (voir fichiers `application.properties` côté backend)

---

## Organisation recommandée

```
independantfish/
├── frontend/           # Application Angular
└── backend/            # Application Spring Boot
```

---

## Prochaines étapes

1. Rédiger un cahier des charges détaillé
2. Réaliser des maquettes (wireframes) des pages principales
3. Développer un MVP avec les fonctionnalités de base :
   - Authentification
   - Création et gestion de boutiques
   - Mise en ligne de produits
   - Recherche et filtres
   - Section occasion
   - Paiement

---

**Independant'fish — la marketplace des passionnés et artisans de la pêche !**
