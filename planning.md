# Grocery Store CRM (React Native) — Detailed Planning

## Goal
Build a mobile CRM for a grocery store that manages customers, orders, loyalty, and basic operations. Prioritize Android first, offline support, and simple workflows for store staff.

---

## Full Feature List (Detailed)
### 1) Authentication & Roles
- Login (phone/password or OTP)
- Roles: Owner, Manager, Staff
- Role permissions (CRUD rules)

### 2) Customer Management
- Customer profile: name, phone, address, DOB/anniversary
- Tags (e.g., VIP, Family, Budget)
- Notes (preferences, complaints)
- Purchase history
- Lifetime value + average basket

### 3) Orders & Billing (basic POS)
- Create order (walk‑in / delivery / pickup)
- Items with quantity/price/tax
- Discounts & coupons
- Payment status (paid/unpaid/partial)
- Receipt (print/share)

### 4) Loyalty / Rewards
- Earn/redeem rules
- Points balance
- Points ledger (all transactions)
- Birthday offers

### 5) Inventory Snapshot (lightweight)
- Top‑selling items
- Low‑stock alerts
- Supplier notes (optional)

### 6) Marketing & Communication
- SMS/WhatsApp campaigns
- Segmentation by tags / last purchase / inactivity
- Campaign performance

### 7) Support & Complaints
- Issue/ticket log
- Follow‑up reminders
- Status: open/in‑progress/resolved

### 8) Staff & Activity Logs
- Staff profiles
- Activity log (who created/edited)

### 9) Analytics Dashboard
- Daily/weekly/monthly sales
- Repeat customer rate
- Average basket size
- Best customers

### 10) Data Import/Export
- Import customers via CSV
- Export orders/customers

### 11) Offline Mode
- Local cache
- Auto‑sync when online
- Conflict resolution rules

---

## Tech Stack (Suggested)
### Frontend (Mobile)
- **React Native (Expo)**
- Navigation: React Navigation
- State: Zustand or Redux Toolkit
- UI: React Native Paper / NativeBase
- Local DB: SQLite (expo‑sqlite)
- Offline sync: custom queue

### Backend
- **Node.js (Express)**
- Database: PostgreSQL
- ORM: Prisma
- Auth: JWT
- File storage: S3 compatible

### Integrations
- SMS/WhatsApp: Twilio / MessageBird
- Analytics: Postgres + Metabase (later)

---

## Folder Structure (Frontend)
```
mobile/
  src/
    api/
      client.ts
      customers.ts
      orders.ts
      loyalty.ts
      auth.ts
    components/
      Button.tsx
      Input.tsx
      Header.tsx
      CustomerCard.tsx
      OrderItemRow.tsx
    screens/
      Auth/
        LoginScreen.tsx
      Dashboard/
        DashboardScreen.tsx
      Customers/
        CustomerListScreen.tsx
        CustomerDetailScreen.tsx
        CustomerEditScreen.tsx
      Orders/
        OrderListScreen.tsx
        OrderCreateScreen.tsx
        OrderDetailScreen.tsx
      Loyalty/
        LoyaltyScreen.tsx
      Settings/
        SettingsScreen.tsx
    store/
      authStore.ts
      customerStore.ts
      orderStore.ts
      loyaltyStore.ts
    utils/
      validators.ts
      formatters.ts
      offlineQueue.ts
    navigation/
      AppNavigator.tsx
      AuthNavigator.tsx
    App.tsx
```

### Frontend File Responsibilities
- `api/client.ts`: axios base config, auth token injection
- `api/customers.ts`: fetch/create/update customer endpoints
- `api/orders.ts`: fetch/create orders
- `api/loyalty.ts`: points ledger APIs
- `store/*Store.ts`: global state and caching
- `offlineQueue.ts`: queue writes when offline, retry sync
- `screens/*`: UI + form handling

---

## Folder Structure (Backend)
```
server/
  src/
    controllers/
      auth.controller.ts
      customer.controller.ts
      order.controller.ts
      loyalty.controller.ts
    routes/
      auth.routes.ts
      customer.routes.ts
      order.routes.ts
      loyalty.routes.ts
    services/
      auth.service.ts
      customer.service.ts
      order.service.ts
      loyalty.service.ts
    middleware/
      auth.middleware.ts
      error.middleware.ts
    models/
      prisma.schema
    utils/
      validator.ts
      logger.ts
    index.ts
```

### Backend File Responsibilities
- `controllers/*`: request handling + response formatting
- `services/*`: business logic (points calc, order totals)
- `routes/*`: express routes
- `middleware/auth`: JWT verification
- `models/prisma.schema`: DB schema

---

## Example Methods (Detailed)
### `customer.service.ts`
- `createCustomer(data)`
- `updateCustomer(id, data)`
- `getCustomerById(id)`
- `listCustomers(filters)`

### `order.service.ts`
- `createOrder(orderPayload)`
- `calculateOrderTotal(items, discounts)`
- `updatePaymentStatus(orderId, status)`
- `listOrders(filters)`

### `loyalty.service.ts`
- `earnPoints(customerId, orderTotal)`
- `redeemPoints(customerId, points)`
- `getPointsLedger(customerId)`

---

## Milestones & Checks
- ✅ M0: Scope locked + data model approved
- ✅ M1: MVP complete + pilot store test
- ✅ M2: Marketing features shipped
- ✅ M3: Inventory + ops features shipped
- ✅ M4: Analytics + automation

---

## Open Questions
- Multi‑store support required?
- Separate billing system or embedded?
- Delivery partner integrations?
