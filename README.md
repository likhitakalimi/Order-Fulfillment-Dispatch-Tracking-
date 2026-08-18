# LogiFlow - Order Fulfillment and Dispatch Tracking System

**LogiFlow** is a complete, production-ready, full-stack **Order Fulfillment and Dispatch Tracking System** built with **Next.js 14 (App Router), TypeScript, Tailwind CSS, Prisma ORM, SQLite / PostgreSQL, Recharts, Zod, and Lucide Icons**.

Designed for enterprise supply-chain logistics and ideal for a **B.Tech Project Demonstration**.

---

## 🌟 Key Features

1. **Role-Based Access Control (RBAC)**:
   - **Admin (`ADMIN`)**: Complete global analytics, user account management, stock control, order lifecycle management, and CSV reporting.
   - **Warehouse Manager (`WAREHOUSE_MANAGER`)**: Multi-warehouse stock tracking, bin location assignments, digital item picking checklist, batch packing, and shipping label printing.
   - **Dispatch Officer / Driver (`DISPATCH_OFFICER`)**: Carrier fleet allocation, driver vehicle assignment, live shipment location check-ins, and Proof of Delivery (POD) registration.
   - **Customer (`CUSTOMER`)**: Order placement, package timeline tracker, shipping status updates, and public tracking lookup.

2. **Core System Modules**:
   - **Interactive Analytics Dashboard**: Live KPI metric cards (Total Orders, Fulfillment SLA Rate, Low Stock Alerts, Revenue) and interactive **Recharts** charts for status breakdown and weekly velocity trends.
   - **Automated Inventory Reservation**: Stocks are locked automatically upon order creation to prevent over-allocation. Bin rack placement (e.g. `Bin A-12-B3`) and reorder alerts.
   - **Digital Pick & Pack Workflow**: Item checklists sorted by warehouse rack/bin, package weight/dim recording, and printable 4x6 thermal shipping label previews with QR code.
   - **Dispatch & Carrier Fleet Tracking**: Automated tracking code generation (`TRK-XXXXXXXX`), carrier assignment (FedEx, DHL, LogiFlow Fleet), and status check-ins (`DISPATCHED` -> `IN_TRANSIT` -> `OUT_FOR_DELIVERY` -> `DELIVERED`).
   - **Public Track & Trace Portal**: Publicly accessible tracking page (`/track/[trackingCode]`) allowing end customers to track packages live without login.
   - **Data Audit & Export**: Formatted CSV data export for Order History, Inventory Stock Master, and Dispatch Performance.

---

## 🚀 Quick Start Guide

### 1. Install Dependencies
```bash
npm install
```

### 2. Database Sync & Seed Data
The project uses SQLite by default for zero-setup local execution:
```bash
# Push Prisma schema to local database
npx prisma db push

# Seed demo accounts, products, warehouses, orders, and tracking logs
npx prisma db seed
```

*(Optional: To use PostgreSQL instead, update `DATABASE_URL` in `.env.local` and change `provider = "postgresql"` in `prisma/schema.prisma`)*

### 3. Run Development Server
```bash
npm run dev
```
Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 🔑 Demo Login Accounts

On the sign-in page (`/login`), click any 1-Click Demo Account button to test different roles:

| Role | Email | Password |
|---|---|---|
| **System Admin** | `admin@logiflow.com` | `admin123` |
| **Warehouse Manager** | `warehouse@logiflow.com` | `warehouse123` |
| **Dispatch Driver** | `driver@logiflow.com` | `driver123` |
| **Customer Account** | `customer@logiflow.com` | `customer123` |

---

## 📦 Sample Tracking Codes (Public Tracker)

Visit `/track/TRK-8849201` or `/track/TRK-9921042` to test live customer package tracking.

- `TRK-8849201` - Order Delivered with Proof of Delivery (POD) signature.
- `TRK-9921042` - Order In Transit with location check-in logs.

---

## 🛠 Project Architecture

```
order/
├── prisma/
│   ├── schema.prisma   # Database schema for Users, Warehouses, Products, Stocks, Orders, Shipments
│   └── seed.ts         # Pre-populated realistic demo dataset
├── src/
│   ├── app/
│   │   ├── api/        # REST API Routes (Auth, Orders, Inventory, Fulfillment, Dispatch, Tracking)
│   │   ├── dashboard/  # Authenticated RBAC dashboard pages
│   │   ├── login/      # Sign-in portal with 1-click role switcher
│   │   └── track/      # Public live tracking portal
│   ├── components/     # Reusable UI components, Recharts visualizations, Modals
│   ├── lib/            # Prisma client, JWT auth, Zod validations, Utilities
│   └── types/          # TypeScript domain interfaces
```

---

## 📄 License & Project Details
Developed for B.Tech Capstone Demonstration in Full-Stack Web Development & Logistics Systems.
