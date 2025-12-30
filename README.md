#DealStack

DealStack is a purpose-built CRM for commercial real estate investment sales teams.

It is designed around how brokers actually work: tracking buildings, owners, relationships, pursuits, and deals in one system, without relying on generic sales CRM abstractions.

This repository documents the core application and includes preview assets to illustrate functionality and design.

#What DealStack Does

DealStack focuses on the realities of investment sales workflows:

Buildings are first-class objects, not just accounts

Contacts and companies are directly tied to properties and transactions

Relationship outreach is cadence-driven and visually managed

Deals and pre-deal pursuits roll up into a single weighted pipeline

Institutional knowledge stays centralized instead of living in spreadsheets and inboxes

The system is optimized for small, high-leverage brokerage teams rather than large, horizontal CRM deployments.

#Core Modules

##Buildings
Centralized database of Class A / Trophy office buildings with ownership, transaction history, leases, and broker coverage.

##Contacts & Companies
Relationship-centric contact management with company hierarchies, aliases, outreach cadences, and deal history.

##Outreach Board
Kanban-style workflow that surfaces which contacts are overdue, due soon, or recently contacted based on assigned cadence rules.

##Deals
Active investment sales opportunities with stages, values, team assignments, and building relationships.

##Pursuits
Pre-deal opportunities tracked with probability weighting and conversion into deals when won.

##Weighted Pipeline
Forward-looking revenue forecast that combines active deals and probability-weighted pursuits across multiple years.

##Activities
External interactions (calls, meetings, emails, site visits) linked across contacts, buildings, and deals.

##Tasks
Internal to-do tracking for brokers and analysts, intentionally separated from client-facing activities.

##Email Activity Capture
Optional email and calendar ingestion workflow that converts communications into structured activity records.

##Preview Assets

This repository includes preview materials to help understand the system without running it:

UI screenshots of key modules

Example pipeline and outreach views

Data model and relationship diagrams

Preview assets are illustrative and may not reflect live or production data.

See the /docs or /previews directory for visuals and walkthroughs.

##Technical Overview

High-level architecture highlights:

React + TypeScript frontend

Node.js / Express backend

PostgreSQL data model with strong relational integrity

Role-based access and team-aware visibility

AI-assisted parsing for activity enrichment

Implementation details are intentionally omitted from this README.

##Design Philosophy

Model real estate workflows directly

Treat buildings and relationships as core primitives

Minimize manual data entry

Prefer clarity over excessive configuration

Keep the interface fast, focused, and broker-friendly

DealStack is opinionated by design.

##Status

DealStack is an active, evolving project originally built around a real brokerage use case.

It is not intended to be a generic CRM framework or a Salesforce replacement.
The focus is depth in a specific domain rather than breadth across industries.

License

TBD.
This repository is currently shared for documentation, demonstration, and discussion purposes.
