# 🧾 ERP Multi-Succursales - Django

## 📌 Description

Application web professionnelle de **gestion commerciale, comptabilité et gestion de stock multi-succursales** développée avec :

* Backend : Django
* Frontend : Bootstrap 5
* Base de données : SQLite (développement) → PostgreSQL (production)

---

## 🎯 Objectif

Créer un système ERP complet permettant de gérer :

* Plusieurs succursales avec un siège principal
* Les ventes, achats, stocks
* Les paiements et caisses
* La comptabilité de base
* Les utilisateurs avec gestion des permissions

---

## 🏢 Structure Organisationnelle

* Siège principal (accès global)
* Succursales multiples

Chaque succursale contient :

* Manager
* Employés
* Dépôt (Warehouse)
* Caisse
* Délégués commerciaux

---

## 🔐 Gestion Multi-Succursales

* Isolation des données par succursale
* Accès global pour le siège
* Gestion des transferts entre succursales
* Permissions basées sur les rôles

---

## 🧩 Architecture Modulaire (Django Apps)

* produits
* fournisseurs
* clients
* achats
* ventes
* stocks
* paiements
* caisses
* rapports
* permissions
* configuration

---

## 📦 Modules Fonctionnels

### 1. Fournisseurs

* CRUD fournisseurs
* Historique des achats
* Balance fournisseur
* Produits fournis
* Export PDF / Excel

### 2. Achats

* Bon de réception
* Factures d’achat
* Retours fournisseurs
* Dépenses liées
* Paiements fournisseurs

### 3. Ventes

* Factures de vente
* Bons de livraison
* Retours clients
* Paiements (comptant/crédit)

### 4. Clients

* CRUD clients
* Historique des ventes
* Solde et limite de crédit
* Suivi des paiements

### 5. Produits & Lots

* Gestion des produits
* Gestion des lots
* Familles / sous-familles

### 6. Stock

* Stock par succursale
* Mouvements de stock
* Inventaire
* Alertes stock minimum
* Transferts inter-succursales

### 7. Paiements

* Paiements clients et fournisseurs
* Multi-modes (espèces, chèque, virement)

### 8. Caisses

* Ouverture / fermeture
* Journal de caisse
* Historique des opérations

### 9. Dépenses

* Dépenses par succursale et caisse
* Catégorisation

### 10. Rapports

* Ventes
* Achats
* Stock
* Clients / fournisseurs
* Caisse
* Bénéfices

---

## 📊 Dashboard

* Chiffre d’affaires
* Ventes (jour / mois / année)
* Situation caisse
* Produits en rupture
* Clients débiteurs
* Fournisseurs créditeurs

---

## 🔐 Utilisateurs & Permissions

### Rôles :

* Super Admin
* Directeur
* Manager
* Comptable
* Commercial
* Caissier
* Magasinier

### Système :

* Django Authentication
* Groups
* Permissions

---

## 🗄️ Modélisation de la Base de Données

### Entités principales :

* Branch (Succursale)
* Warehouse
* CashRegister
* User / UserProfile
* Product / Lot / Family
* Customer / Supplier
* Sale / SaleItem
* Purchase / PurchaseItem
* Stock / StockMovement
* Payment
* Expense

### Relations clés :

* Une succursale → plusieurs utilisateurs
* Un produit → plusieurs lots
* Vente → lignes de vente
* Achat → lignes d’achat
* Mouvement de stock → produit + dépôt

---

## 🔌 API (Structure)

```
/api/auth/
/api/branches/
/api/products/
/api/lots/
/api/customers/
/api/suppliers/

/api/sales/
/api/sales/{id}/items/
/api/sales/{id}/payments/

/api/purchases/
/api/stock/
/api/stock/movements/

/api/payments/
/api/cash/
/api/expenses/

/api/reports/
```

---

## 🔄 Workflows

### 🧾 Vente

1. Création facture
2. Ajout produits
3. Déduction stock
4. Enregistrement paiement
5. Mise à jour caisse

### 📦 Achat

1. Bon de réception
2. Ajout produits
3. Mise à jour stock
4. Enregistrement facture fournisseur

### 🔁 Stock

1. Mouvement (entrée/sortie)
2. Transfert inter-succursales
3. Inventaire

---

## 🗺️ Roadmap de Développement

### Phase 1 : Setup

* Création projet Django
* Configuration apps
* Authentification

### Phase 2 : Organisation

* Succursales
* Utilisateurs
* Permissions

### Phase 3 : Produits & Partenaires

* Produits / Lots
* Clients / Fournisseurs

### Phase 4 : Achats

* Réception
* Mise à jour stock

### Phase 5 : Ventes

* Facturation
* Paiements

### Phase 6 : Stock

* Suivi
* Mouvements
* Transferts

### Phase 7 : Finance

* Caisse
* Dépenses

### Phase 8 : Reporting

* Dashboard
* Statistiques

### Phase 9 : Avancé

* Export PDF/Excel
* Audit log
* Backup

---

## ⚙️ Bonnes Pratiques

* Architecture modulaire Django
* Séparation logique métier (services)
* Filtrage des données par succursale
* Utilisation des permissions Django
* Prévoir migration vers PostgreSQL
* Logs et audit pour traçabilité

---

## 🚀 Évolution Future

* API REST complète (Django REST Framework)
* Application mobile
* Multi-tenant SaaS
* Intégration comptabilité avancée

---

## 📌 Conclusion

Ce projet constitue une base solide pour un ERP :

* Modulaire
* Scalable
* Adapté aux entreprises multi-succursales
* Prêt pour évolution vers production

---