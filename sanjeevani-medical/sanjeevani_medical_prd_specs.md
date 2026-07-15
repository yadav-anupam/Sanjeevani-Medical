# PRD: Sanjeevani Medical (Pharmacy Management System)

## Phase 1: Product Discovery

### Project Overview
Sanjeevani Medical is a production-ready Pharmacy Management System designed to streamline inventory tracking, sales processing, and patient management for retail pharmacies.

### Problem Statement
Local pharmacies often struggle with manual inventory tracking, leading to expired stock, missed reorders, and inefficient sales processes. There is a lack of integrated systems that combine inventory, billing, and doctor-patient records in a user-friendly way.

### Solution
A cloud-based SaaS platform that automates inventory alerts, provides a seamless point-of-sale (POS) interface, manages supplier relations, and offers detailed financial reporting.

### Business Objectives
- **Efficiency:** Reduce manual entry by 60%.
- **Accuracy:** Zero-error inventory tracking and expiry management.
- **Growth:** Integrated SEO-friendly landing page for customer inquiries.
- **Scalability:** Built on a modern tech stack (React + Supabase) to handle high transaction volumes.

### User Personas & Roles
1.  **Admin (Owner):** Full system access, financial reports, staff management.
2.  **Pharmacist:** Inventory management, sales/billing, prescription verification.
3.  **Doctor (External/Partner):** Access to patient history, digital prescriptions (future scope).
4.  **Customer:** Online medicine search, order tracking (via landing page).

### Success Metrics
- Average transaction time < 30 seconds.
- Inventory accuracy > 99%.
- Monthly uptime > 99.9%.

---

## Phase 2: Requirements

### Functional Requirements
- **Auth:** JWT/Supabase based RBAC (Role-Based Access Control).
- **Inventory:** CRUD for medicines, category management, batch tracking (expiry/manufacturing).
- **POS:** Barcode scanning, invoice generation (PDF), discount management.
- **Suppliers:** Supplier profiles and purchase order tracking.
- **Reports:** Daily sales, profit/loss, low-stock alerts.

### Non-Functional Requirements
- **Performance:** Page load < 2s.
- **Security:** Data encryption at rest (Supabase) and in transit (HTTPS).
- **SEO:** Server-side metadata for landing pages to rank for local pharmacy keywords.

---

## Phase 3: User Experience

### User Flow (Pharmacist)
Login -> Dashboard -> New Sale -> Search Medicine -> Add to Cart -> Generate Invoice -> Complete Payment.

### Screen List
1.  **Landing Page:** Public-facing SEO-optimized site.
2.  **Auth Pages:** Login, Forgot Password.
3.  **Dashboard:** KPI overview (Sales, Inventory levels).
4.  **Inventory Management:** Table view with filters.
5.  **POS/Billing:** Quick-search and cart interface.
6.  **Supplier Portal:** Management of vendors.
7.  **Reports:** Data visualizations.
8.  **Settings:** Profile and system config.

---

## Phase 7: Database Design (Supabase PostgreSQL)

### ER Diagram (Text)
- `users`: id, email, role, profile_data
- `medicines`: id, name, generic_name, category_id, price, stock_quantity, reorder_level
- `batches`: id, medicine_id, batch_number, expiry_date, cost_price
- `sales`: id, pharmacist_id, total_amount, tax, discount, created_at
- `sale_items`: id, sale_id, medicine_id, quantity, unit_price
- `suppliers`: id, name, contact_person, phone, email

### Relationships
- `medicines` has many `batches` (1:N)
- `sales` has many `sale_items` (1:N)
- `medicines` belongs to `sale_items` (1:N)

---

## Phase 15: Development Roadmap

### Milestone 1: Core Infrastructure
- Setup Supabase project.
- Auth implementation (RBAC).
- Database migration (Initial Schema).

### Milestone 2: Inventory & Supply Chain
- Medicine & Batch management.
- Supplier tracking.

### Milestone 3: Sales & POS
- Billing engine.
- Invoice generation.

### Milestone 4: Analytics & Launch
- Dashboard charts.
- Vercel/Render deployment.
