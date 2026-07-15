# Database Schema Design: Sanjeevani Medical (Supabase/PostgreSQL)

This document provides the definitive table structures and relationships required to support the Sanjeevani Medical Pharmacy Management System.

## 1. Core Tables

### `profiles` (User Management)
- `id`: uuid (references auth.users.id) - Primary Key
- `email`: text
- `full_name`: text
- `role`: text (Check constraint: 'admin', 'pharmacist_admin')
- `created_at`: timestamp with time zone

### `medicines` (Inventory)
- `id`: uuid - Primary Key
- `name`: text - Indexed
- `generic_name`: text
- `category`: text
- `price`: numeric (2 decimal places)
- `stock_quantity`: integer
- `reorder_level`: integer
- `manufacturer`: text
- `updated_at`: timestamp with time zone

### `batches` (Expiry & Tracking)
- `id`: uuid - Primary Key
- `medicine_id`: uuid (references medicines.id) - Indexed
- `batch_number`: text - Indexed
- `manufacturing_date`: date
- `expiry_date`: date - Indexed
- `cost_price`: numeric
- `initial_quantity`: integer
- `current_quantity`: integer

### `suppliers` (Vendor Management)
- `id`: uuid - Primary Key
- `name`: text
- `contact_person`: text
- `phone`: text
- `email`: text
- `address`: text

### `sales` (Transactions)
- `id`: uuid - Primary Key
- `pharmacist_id`: uuid (references profiles.id)
- `total_amount`: numeric
- `tax_amount`: numeric
- `discount_amount`: numeric
- `payment_method`: text ('cash', 'card', 'upi')
- `customer_phone`: text (for WhatsApp)
- `customer_email`: text (for Email)
- `created_at`: timestamp with time zone - Indexed

### `sale_items` (Line Items)
- `id`: uuid - Primary Key
- `sale_id`: uuid (references sales.id) - Indexed
- `medicine_id`: uuid (references medicines.id)
- `batch_id`: uuid (references batches.id)
- `quantity`: integer
- `unit_price`: numeric

## 2. Relationships (ER Logic)
- **1:N**: `medicines` -> `batches` (One medicine can have multiple batches/expiry dates)
- **1:N**: `sales` -> `sale_items` (One sale contains multiple medicines)
- **N:1**: `sale_items` -> `batches` (Each line item tracks a specific batch for inventory deduction)

## 3. Security (Row Level Security - RLS)
- `profiles`: Users can read all profiles; only `admin` can update roles.
- `medicines`/`batches`: All authenticated users can read; `pharmacist_admin` and `admin` can update.
- `sales`: All authenticated users can insert; only `admin` can view sensitive profit reports.
