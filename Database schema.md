# 🗄️ Database Schema - ERP Multi-Succursales

## 📌 Conventions

* Primary Key: `id`
* Dates: `created_at`, `updated_at`
* User tracking: `created_by`, `updated_by`
* Boolean: `is_active`
* Relations: `ForeignKey`

---

# 🏢 1. Organisation

## Branch

* id
* name
* code
* address
* city
* country
* phone
* email
* is_head_office (bool)
* is_active
* created_at
* updated_at

## Warehouse

* id
* name
* branch (FK → Branch)
* address
* is_active
* created_at
* updated_at

## CashRegister

* id
* name
* branch (FK → Branch)
* initial_balance
* current_balance
* is_active
* created_at
* updated_at

---

# 👤 2. Users

## UserProfile

* id
* user (FK → User)
* branch (FK → Branch)
* role
* phone
* is_active
* created_at
* updated_at

---

# 🤝 3. Suppliers

## Supplier

* id
* name
* code
* address
* country
* contact
* phone
* mobile
* fax
* email
* rc
* nif
* nis
* article_imposition
* bank_account
* bank_name
* initial_balance
* current_balance
* is_active
* notes
* created_by
* created_at
* updated_by
* updated_at

---

# 🤝 4. Clients

## Customer

* id
* code
* name
* branch (FK → Branch)
* address
* wilaya
* contact
* phone
* fax
* mobile
* email
* rc
* nif
* nis
* article_imposition
* bank_account
* bank_name
* initial_balance
* credit_limit
* debit
* credit
* current_balance
* allow_discount (bool)
* is_active
* commercial (FK → User)
* notes
* created_by
* created_at
* updated_by
* updated_at

---

# 📦 5. Products

## ProductFamily

* id
* name
* reference
* parent (FK → self)
* notes
* created_at
* updated_at

## Product

* id
* reference
* name
* barcode
* family (FK → ProductFamily)
* supplier (FK → Supplier)
* unit
* packaging
* min_stock
* price_ht
* tva_rate
* discount_rate
* price_ttc
* annual_discount (bool)
* is_active
* notes
* created_by
* created_at
* updated_by
* updated_at

---

## Lot

* id
* lot_number
* product (FK → Product)
* origin_country
* unit
* packaging
* arrival_date
* quantity
* manufacturing_date
* expiration_date
* harvest_date
* closing_date
* purchase_price
* sale_price_ht
* tva_rate
* discount_rate
* sale_price_ttc
* is_active
* is_on_discount
* is_on_promo
* notes
* created_by
* created_at
* updated_by
* updated_at

---

# 📊 6. Inventory

## Stock

* id
* product (FK → Product)
* warehouse (FK → Warehouse)
* quantity

## StockMovement

* id
* product (FK → Product)
* warehouse (FK → Warehouse)
* movement_type (IN / OUT / TRANSFER)
* quantity
* reference
* date
* created_by

---

# 🧾 7. Purchases

## Purchase

* id
* reference
* supplier (FK → Supplier)
* branch (FK → Branch)
* warehouse (FK → Warehouse)
* date
* total_ht
* total_tva
* total_discount
* total_ttc
* status
* notes
* created_by
* created_at

## PurchaseItem

* id
* purchase (FK → Purchase)
* product (FK → Product)
* lot (FK → Lot)
* quantity
* unit_price
* discount
* tva
* total

---

# 🧾 8. Sales

## Sale

* id
* reference
* customer (FK → Customer)
* branch (FK → Branch)
* date
* total_ht
* total_tva
* total_discount
* total_ttc
* status
* notes
* created_by
* created_at

## SaleItem

* id
* sale (FK → Sale)
* product (FK → Product)
* lot (FK → Lot)
* quantity
* unit_price
* discount
* tva
* total

---

# 💰 9. Payments

## Payment

* id
* reference
* payment_number
* date
* branch (FK → Branch)
* cash_register (FK → CashRegister)
* payment_method
* amount
* customer (FK → Customer, nullable)
* supplier (FK → Supplier, nullable)
* commercial (FK → User)
* is_locked
* status
* notes
* created_by
* created_at
* updated_by
* updated_at

---

# 🏦 10. Cash Management

## CashTransaction

* id
* cash_register (FK → CashRegister)
* type (IN / OUT)
* amount
* operation_type
* reference
* date
* notes
* created_by

---

# 💸 11. Expenses

## Expense

* id
* branch (FK → Branch)
* cash_register (FK → CashRegister)
* category
* amount
* date
* description
* created_by

---

# 📘 12. Accounting (Simplifié)

## Account

* id
* code
* name
* type
* is_active

## JournalEntry

* id
* reference
* date
* description
* created_by

## Ledger

* id
* journal_entry (FK → JournalEntry)
* account (FK → Account)
* debit
* credit

---

# 📊 13. Reports

⚠️ Générés dynamiquement (pas de tables physiques)

---

# 📝 Notes importantes

* Tous les montants → DecimalField
* Toutes les dates → DateTimeField
* Relations → ForeignKey avec `on_delete=PROTECT`
* Ajouter index sur:

  * reference
  * date
  * foreign keys

---

# 🚀 Prêt pour

* Conversion directe vers Django models
* Création API (Django REST Framework)
* Scaling vers PostgreSQL

---