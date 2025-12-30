# DealStack Product Requirements Document (PRD)

**Version:** 1.0  
**Last Updated:** December 30, 2024  
**Status:** In Development

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Product Vision](#product-vision)
3. [Target Users](#target-users)
4. [Core Features](#core-features)
5. [User Roles & Permissions](#user-roles--permissions)
6. [Feature Specifications](#feature-specifications)
7. [Data Architecture](#data-architecture)
8. [Integrations](#integrations)
9. [Technical Requirements](#technical-requirements)
10. [Success Metrics](#success-metrics)
11. [Future Roadmap](#future-roadmap)

---

## Executive Summary

DealStack is a comprehensive Customer Relationship Management (CRM) system purpose-built for commercial real estate brokers. The platform enables investment sales teams to manage their complete deal lifecycle from prospecting through closing, while maintaining deep relationships with property owners, investors, and industry contacts.

### Key Value Propositions

- **Unified Property Intelligence**: Track 495 Class A/Trophy office buildings across 8 Florida markets with complete transaction history
- **Relationship-Centric Design**: Manage contacts with cadence-based outreach, ensuring no relationship goes cold
- **AI-Powered Email Capture**: Automatically log communications via DealBot email integration
- **Pipeline Forecasting**: Weighted pipeline calculations combining active deals and probability-weighted pursuits
- **Team Collaboration**: Me/Team modes across all features for individual focus or team-wide visibility

---

## Product Vision

### Problem Statement

Commercial real estate brokers struggle with:
- Fragmented data across spreadsheets, email, and multiple systems
- Lost institutional knowledge when team members transition
- Difficulty tracking relationship touchpoints with hundreds of contacts
- Manual activity logging that reduces selling time
- Lack of visibility into team pipeline and pursuit progress

### Solution

DealStack provides a single source of truth for:
- Property and building intelligence
- Contact and company relationships
- Deal and pursuit pipeline management
- Activity tracking with automated email capture
- Team performance and goal tracking

### Target Market

- **Primary**: Commercial real estate investment sales teams in Florida markets
- **Geography**: 8 Florida markets (Miami, Fort Lauderdale, Tampa, Orlando, Jacksonville, West Palm Beach, Boca Raton, Naples)
- **Property Focus**: Class A and Trophy office buildings
- **Team Size**: 5-20 brokers per market

---

## Target Users

### Primary Users

| Role | Description | Key Needs |
|------|-------------|-----------|
| **Senior Broker** | Lead deal makers with 10+ years experience | Pipeline visibility, relationship management, minimal data entry |
| **Associate Broker** | Supporting deal execution | Task management, activity logging, learning the market |
| **Analyst** | Research and deal support | Data accuracy, building intelligence, comp research |

### Secondary Users

| Role | Description | Key Needs |
|------|-------------|-----------|
| **Manager** | Team oversight and strategy | Team performance metrics, goal tracking, pipeline reporting |
| **Administrator** | System configuration | User management, data imports, system maintenance |

---

## Core Features

### 1. Buildings Module

**Purpose**: Centralized database of all Class A/Trophy office buildings in target markets

**Capabilities**:
- Full CRUD operations on building records
- Normalized address search with fuzzy matching
- Building-Contact relationships with role assignments (Owner, Asset Manager, Property Manager, Leasing Broker)
- Transaction history (Sales, Loans, Leases) linked to each building
- External system ID matching (CoStar, MarketSphere, SuiteStack)
- Bulk park assignment for multi-building properties
- Coverage assignment to track broker territory
- Building lookup table for fast search and import matching

**Key Data Points**:
- Property details (name, address, RBA, stories, year built, class)
- Market/Submarket classification
- Ownership information
- Occupancy and vacancy metrics
- Financial data (market rent, opex)
- Amenities and scores (walk, bike, transit)
- Photo URLs and external links

### 2. Contacts & Companies Module

**Purpose**: Manage relationships with all industry stakeholders

**Capabilities**:
- Contact management with company associations
- Collaborator contacts auto-linked to user accounts (internal team members)
- Company hierarchy (parent company relationships)
- Company aliases for flexible name matching
- Contact outreach cadence tracking (Weekly, Monthly, Quarterly, Bi-Annual, Annual)
- Last contact date and next follow-up tracking
- Relationship owner assignment
- Deal count and history per contact

**Company Types**:
- Broker
- Investor
- Lender
- Service Provider
- SPE (Special Purpose Entity)
- Developer

**Company Reach Classification**:
- Institutional
- Regional
- Local
- Private

### 3. Outreach Board

**Purpose**: Visual workflow for managing contact outreach cadences

**Capabilities**:
- Three-column Kanban workflow:
  - **Overdue**: Contacts past their cadence due date
  - **Due Soon**: Contacts approaching their cadence due date
  - **Contacted**: Recently contacted within cadence window
- Drag-and-drop to log activities (auto-creates activity record)
- Me/Team filtering for personal or team-wide view
- Cadence type display (Weekly, Monthly, Quarterly, etc.)
- Quick-access to contact details

**Cadence Calculation**:
| Cadence Type | Frequency |
|--------------|-----------|
| Weekly | Every 7 days |
| Monthly | Every 30 days |
| Quarterly | Every 90 days |
| Bi-Annual | Every 180 days |
| Annual | Every 365 days |

### 4. Tasks Module

**Purpose**: Internal to-do management for brokers

**Capabilities**:
- Kanban board with drag-and-drop:
  - Not Started
  - In Progress
  - Completed
- Table view with inline status editing
- Me/Team filtering
- Priority levels (Low, Medium, High, Urgent)
- Task types (Follow-up, Tour, Research, Admin, Proposal)
- Multi-user assignment support
- Due date tracking with reminders
- Linkage to Buildings, Companies, Contacts, Deals, Activities

**Key Distinction**: Tasks are internal to-dos that do NOT involve external contacts (unlike Activities)

### 5. Deals Module

**Purpose**: Track active investment sales opportunities

**Capabilities**:
- Full deal pipeline management
- Stage tracking:
  - Lead
  - Active
  - Due Diligence
  - Under Contract
  - Closed Won
  - Closed Lost
- Deal types: Sale, Lease, Investment
- Involvement types: Team (our deal) vs Market (tracking competitor deals)
- Multi-building deals via junction table
- Contact role assignments per deal:
  - Listing Broker (external contacts)
  - Listing Broker Users (internal team)
  - Owner Contacts
  - Leasing Broker Contacts
  - Other Contacts
- Projected close quarter/year for pipeline forecasting
- Deal notes and comments (collaboration)
- Deal value tracking

### 6. Pursuits Module

**Purpose**: Track pre-deal opportunities the team is actively pursuing

**Capabilities**:
- Pursuit pipeline with status tracking:
  - Identified
  - Contacting
  - Pitching
  - Best & Final
  - Won
  - Lost
- Pursuit types: Sale, Debt
- Building and company linkage
- Estimated transaction value
- **Probability weighting (0-100%)** for pipeline forecasting
- Target decision date
- Projected close quarter/year
- Team assignment (lead broker + team members)
- Competitor tracking via junction table
- Contact associations via junction table
- Conversion to Deal when won
- Lost reason tracking

### 7. Weighted Pipeline

**Purpose**: Forecast revenue across deals and pursuits

**Calculation Method**:
- **Deals**: Valued at 100% of deal_value (Team involvement only)
- **Pursuits**: Valued at estimated_transaction_value × (probability / 100)
- **Combined**: Total weighted pipeline = Deals + Weighted Pursuits

**Time Periods**:
- Last Year (actual closed deals - benchmark)
- Current Year
- Next Year
- Year After Next

**Filtering**:
- Me Mode: Only deals/pursuits where user is assigned
- Team Mode: All team deals/pursuits

**Display**:
- Deal count and value
- Pursuit count and weighted value
- Total pipeline value
- Quarterly breakdown (Q1-Q4)

### 8. Activities Module

**Purpose**: Track all external interactions with contacts

**Activity Types**:
- Call
- Meeting
- Email
- Site Visit

**Capabilities**:
- Activity logging with subject, description, outcome
- Multi-contact, multi-building, multi-deal linkage
- Multi-user assignment (assigned_to + team_members)
- Three calendar views:
  - Work Week (5-day view)
  - Next 7 Days
  - Month
- Recurring activity support with patterns
- Follow-up tracking (required, date, action, completed)
- Direction tracking (Inbound/Outbound)
- Sentiment scoring
- Activity sidebar with full details

**Key Distinction**: Activities ALWAYS involve external contacts (unlike Tasks which are internal)

### 9. DealBot Email Integration

**Purpose**: Automatically capture emails and calendar events as activities

**How It Works**:
1. User CCs `dealbot@dealstack-crm.com` on emails or calendar invites
2. SendGrid receives and forwards to webhook endpoint
3. System parses email content and attachments
4. OpenAI (gpt-4o-mini) extracts entities from email body
5. Fuzzy SQL matching links to Buildings, Deals, Companies, Contacts
6. Activity record created with AI-generated subject and summary

**Email Processing**:
- Message-ID tracking for deduplication
- Thread tracking via In-Reply-To headers
- From/To/CC extraction and display
- Attachment metadata capture
- Body preview storage

**Calendar Processing**:
- ICS file parsing for meeting details
- VEVENT extraction (summary, description, start/end times, location)
- ATTENDEE extraction for contact matching
- Fallback to email To/CC when ICS lacks attendees
- Calendar event UID for update matching (handles reschedules)
- Support for Microsoft Teams, Google Calendar, Outlook formats

**Entity Matching**:
- Case-insensitive email matching
- Fuzzy company name matching (string-similarity)
- Building name/address matching
- Deal name matching
- Unlinked email tracking for manual resolution

**Unlinked Contacts**:
- Activities marked as `is_unlinked` when no contacts matched
- `unlinked_emails` stored for review
- Quick-create buttons to add new contacts from unlinked emails

### 10. Goals Module

**Purpose**: Track individual and team performance against targets

**Metrics Tracked**:
| Metric | Description | Calculation |
|--------|-------------|-------------|
| Pipeline Target | Dollar value of weighted pipeline | Sum of deals + weighted pursuits |
| Closed Deals | Number of deals closed | Count of Closed Won deals |
| Client Meetings | Number of meetings held | Count of Meeting activities |

**Capabilities**:
- Year selector for multi-year planning
- Real-time progress calculations
- Individual broker goals
- Visual progress indicators

### 11. Sales Transactions

**Purpose**: Track historical and current property sales

**Capabilities**:
- Full transaction details (price, cap rate, dates)
- Multi-party tracking (Buyers, Sellers, Brokers)
- Ownership percentage allocation
- Financing linkage to loan transactions
- Document attachments (OM, PSA, Appraisal, etc.)
- Asset performance metrics at sale
- Marketing process tracking

### 12. Loan Transactions

**Purpose**: Track property debt/financing

**Capabilities**:
- Loan details (amount, rate, term, maturity)
- LTV and DSCR tracking
- Lender and borrower party tracking
- Loan status management
- Remaining balance tracking

### 13. Leases

**Purpose**: Track tenant leases within buildings

**Capabilities**:
- Tenant information
- Lease terms (start, end, options)
- Financial terms (rent, escalations)
- Square footage tracking
- Broker assignments (leasing broker, tenant rep)
- Status tracking (Active, Expired, Pending Renewal, Terminated)
- Expiration warnings

### 14. Home Dashboard

**Purpose**: Unified view of key information

**Components**:
- Week Feed: Combined activities and tasks for current week
- Weighted Pipeline widget
- Quick stats and metrics
- Recent activity

### 15. Search

**Purpose**: Global search across all entities

**Capabilities**:
- Unified search across Buildings, Companies, Contacts, Deals
- Normalized address search for buildings
- Fuzzy name matching
- Quick navigation to results

### 16. Bulk Upload System

**Purpose**: Import data from external sources

**Capabilities**:
- CSV/Excel file upload
- Entity type selection (Buildings, Companies, Contacts, Leases, Sales, Loans)
- Validation and error reporting
- Duplicate detection with confidence scoring
- Merge strategy options
- Progress tracking
- Audit logging

---

## User Roles & Permissions

| Role | Access Level | Capabilities |
|------|--------------|--------------|
| Administrator | Full | All features, user management, system config |
| Admin | Full | All features, user management |
| Manager | Team | Team-wide visibility, goal management |
| Broker | Standard | Full CRM features, own data + team visibility |
| Analyst | Limited | Read access, research features, limited editing |
| Viewer | Read-only | View-only access to allowed data |

---

## Data Architecture

### Core Entities

```
users (9 records)
├── contacts (184 records) - via user_id for collaborators
├── activities - via assigned_to_user_id, team_member_ids
├── tasks - via assigned_to_user_id, team_member_ids
├── deals - via listing_broker_user_ids, owner_user_id
├── pursuits - via lead_broker_user_id, team_member_ids
└── goals - via user_id

buildings (495 records)
├── building_contacts - junction to contacts with roles
├── building_owners - junction to companies
├── sales_transactions (212 records)
├── loan_transactions
├── leases (325 records)
├── deal_buildings - junction to deals
└── building_lookup - search optimization

companies (701 records)
├── contacts - via company_id
├── company_aliases - for name matching
├── investment_vehicles
├── sales_parties
├── loan_parties
└── pursuit_competitors

contacts (184 records)
├── user_contact_cadences - outreach tracking
├── building_contacts - building relationships
├── pursuit_contacts
└── activities - via contact_ids array

deals (12 records)
├── deal_buildings - multi-building support
├── deal_notes
├── deal_comments
└── activities - via deal_ids array

pursuits (3 records)
├── pursuit_contacts
└── pursuit_competitors

activities (46 records)
└── Multi-entity linkage via array columns
```

### Junction Tables

| Table | Purpose |
|-------|---------|
| building_contacts | Building ↔ Contact with role |
| building_owners | Building ↔ Company ownership |
| deal_buildings | Deal ↔ Building (multi-building deals) |
| pursuit_contacts | Pursuit ↔ Contact |
| pursuit_competitors | Pursuit ↔ Company (competitors) |
| user_contact_cadences | User ↔ Contact cadence assignments |
| sales_parties | Transaction ↔ Company parties |
| loan_parties | Loan ↔ Company parties |
| sale_financing_links | Sale ↔ Loan financing |

---

## Integrations

### Current Integrations

| Integration | Purpose | Status |
|-------------|---------|--------|
| SendGrid Inbound Parse | DealBot email webhook | Active |
| OpenAI API (gpt-4o-mini) | Entity extraction from emails | Active |
| PostgreSQL (Neon) | Primary database | Active |

### External System IDs

| System | Purpose | Field |
|--------|---------|-------|
| CoStar | Building research | costar_id, costar_link |
| MarketSphere | Lease data | marketsphere_id, marketsphere_link |
| SuiteStack | Space management | suitestack_id |

### Future Integration Opportunities

- CoStar API for automated building data sync
- MarketSphere API for lease imports
- Outlook/Gmail direct integration (beyond CC method)
- Salesforce sync for enterprise deployments
- DocuSign for deal document tracking

---

## Technical Requirements

### Technology Stack

| Layer | Technology |
|-------|------------|
| Frontend | React 18, TypeScript, Vite |
| UI Components | shadcn/ui, Radix UI, Tailwind CSS |
| State Management | TanStack Query |
| Routing | Wouter |
| Backend | Express.js, TypeScript, Node.js |
| Database | PostgreSQL (Neon serverless) |
| ORM | Drizzle ORM |
| Authentication | Passport.js (local strategy), bcrypt |
| Sessions | PostgreSQL-backed (connect-pg-simple) |
| AI | OpenAI API |
| Email | SendGrid Inbound Parse |

### Performance Requirements

- Page load time: < 2 seconds
- Search response: < 500ms
- API response: < 1 second
- Database queries: Optimized with indexes
- Concurrent users: Support 20+ simultaneous users

### Security Requirements

- Password hashing with bcrypt
- Session-based authentication
- PostgreSQL session storage
- HTTPS for all traffic
- API key security (environment variables)
- Role-based access control

### Browser Support

- Chrome (latest 2 versions)
- Firefox (latest 2 versions)
- Safari (latest 2 versions)
- Edge (latest 2 versions)

### Timezone

- Server: UTC
- Display: America/New_York (Eastern Time) for Miami-based users

---

## Success Metrics

### Adoption Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| Daily Active Users | 80% of team | Unique logins per day |
| Activities Logged | 10+ per user/week | Activity count |
| DealBot Usage | 50% of emails captured | DealBot activities vs manual |

### Business Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| Pipeline Visibility | 100% of pursuits tracked | Pursuit count vs actual pitches |
| Contact Coverage | All key contacts have cadences | Cadence assignment rate |
| Data Accuracy | < 5% orphaned records | Data integrity checks |

### Engagement Metrics

| Metric | Target | Measurement |
|--------|--------|-------------|
| Outreach Compliance | 90% on-cadence | Overdue contacts < 10% |
| Task Completion | 80% on-time | Completed before due date |
| Goal Achievement | 100% of targets met | Goal progress tracking |

---

## Future Roadmap

### Phase 2: Enhanced Analytics

- Market comparison dashboards
- Deal velocity metrics
- Win/loss analysis
- Broker performance rankings

### Phase 3: Mobile Application

- Native iOS/Android apps
- Offline capability
- Push notifications
- Quick activity logging

### Phase 4: Advanced AI

- Deal probability predictions
- Optimal contact timing suggestions
- Email response drafting
- Meeting preparation briefs

### Phase 5: Expanded Markets

- Additional Florida markets
- Southeast region expansion
- Multi-asset class support (Industrial, Retail, Multifamily)

---

## Appendix

### Glossary

| Term | Definition |
|------|------------|
| Class A | Premium office buildings with top-tier amenities and locations |
| Trophy | The highest tier of Class A buildings |
| RBA | Rentable Building Area (square footage) |
| Cap Rate | Capitalization Rate (NOI / Purchase Price) |
| NOI | Net Operating Income |
| LTV | Loan-to-Value ratio |
| DSCR | Debt Service Coverage Ratio |
| WALT | Weighted Average Lease Term |
| OM | Offering Memorandum |
| PSA | Purchase and Sale Agreement |
| NNN | Triple Net Lease |
| SPE | Special Purpose Entity |

---

*For questions, contact the DealStack development team.*
