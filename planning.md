# Grocery Store CRM (React Native) — Planning

## Goal
Build a mobile CRM for a grocery store that helps manage customers, orders, loyalty, and basic operations. Prioritize Android first, offline support, and simple workflows for store staff.

---

## Phase 0 — Scope & Decisions (1–2 days)
**Decide and lock:**
- Target platform: Android first (iOS later)
- Deployment model: cloud backend + offline cache
- Messaging provider: SMS/WhatsApp (Twilio/MessageBird/etc.)
- Roles: Owner, Manager, Staff

**Deliverables:**
- Final feature scope
- Data model draft
- Success metrics for MVP

---

## Phase 1 — MVP (2–4 weeks)
**Goal:** Core CRM + order tracking + loyalty

### Required Screens
1. Login / Role selection
2. Dashboard (daily sales + key KPIs)
3. Customers list + profile
4. Orders (create/view)
5. Loyalty rules + points ledger

### MVP Features
- Customer profiles (name, phone, address, tags, notes)
- Purchase history & lifetime value
- Order entry (walk‑in / delivery)
- Payment status (paid/unpaid/partial)
- Loyalty points rules (earn/redeem)
- Basic analytics (daily/weekly sales, avg basket)

**Deliverable:** Working app used in a live store

---

## Phase 2 — Growth (3–6 weeks)
**Goal:** Retention + marketing

### Added Features
- Tags & segmentation
- SMS/WhatsApp campaigns
- Inactivity alerts
- CSV import/export

**Deliverable:** Engagement tools to bring back customers

---

## Phase 3 — Ops (4–8 weeks)
**Goal:** Inventory + staff visibility

### Added Features
- Low‑stock alerts
- Top‑selling items
- Supplier notes
- Staff activity logs

**Deliverable:** Operations visibility + accountability

---

## Phase 4 — Analytics & Automation (ongoing)
- Repeat customer rate
- RFM scoring
- Auto‑offers (birthday, inactivity)
- Campaign performance reports

---

## Data Model (Draft)
**Customer**: id, name, phone, address, tags[], notes, createdAt
**Order**: id, customerId, items[], total, status, channel, createdAt
**OrderItem**: sku, name, qty, price
**Loyalty**: customerId, pointsBalance, rules
**PointsLedger**: id, customerId, delta, reason, createdAt
**User**: id, name, role, phone, active

---

## Tech Stack Suggestion
- **Frontend:** React Native (Expo)
- **Backend:** Node.js + PostgreSQL
- **Auth:** Firebase Auth or JWT
- **Offline:** SQLite + sync layer
- **Messaging:** Twilio/MessageBird
- **Analytics:** Postgres + lightweight dashboards

---

## Milestones & Checks
- ✅ M0: Scope locked + data model approved
- ✅ M1: MVP complete + pilot store test
- ✅ M2: Marketing features shipped
- ✅ M3: Inventory + ops features shipped
- ✅ M4: Analytics + automation

---

## Open Questions
- Need delivery partner integrations?
- Should billing be separate or embedded?
- Multi‑store support required?
