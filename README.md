# ATSA (Automated Tracking System Application) — Sanitized Portfolio Case Study

> **Note:** This public repository is a **sanitized portfolio artifact**. It intentionally excludes proprietary names, production exports, environment identifiers, and any real user/student data. It focuses on **architecture, data model patterns, automation design, and implementation approach**.

## Overview

ATSA is a Power Platform-based customer relationship management (CRM) style application built to help a university language & culture program track:
- **Student leads**
- **Applicants**
- **A special cohort/program category**
- **Staff communication history**
- **Automated outreach**
- **Reporting & analytics**

The solution combines:
- **Power Apps** (web app UI)
- **SQL Server and SharePoint** (data storage)
- **Power Automate** (workflow automation)
- **Power BI** (reports/analytics)

This system replaced spreadsheet-based manual tracking and introduced centralized records, standardized workflows, and automated communication.  
(Underlying system capabilities and UI modules are reflected in the project documentation and mockup screens.) 

## Problem (Sanitized)

Staff had been using spreadsheets and manual processes to manage a growing number of prospects and applicants. As volume increased, the manual approach made it difficult to:
- Keep records consistent and up-to-date
- Track multi-step application progress
- Maintain a complete communication history per person
- Run reliable reports and analytics
- Respond quickly and consistently using standardized outreach

A third-party CRM was evaluated but considered cost-prohibitive for the unit, so an internal build was chosen using existing Microsoft licensing and tools.

## Solution Summary

ATSA provides:
- A landing dashboard with modules for **Leads**, **Applicants**, **Program Cohort**, and **Reports**
- List views with search, filters, and “details” actions for staff to quickly triage records
- Profile pages segmented into tabs to keep large datasets usable
- Built-in **communication history** tracking (manual logging + automated email logging)
- Automated email/outreach status management
- Import utilities that support ingesting applicant/cohort data from a central registration source
- Reports and visual analytics (Power BI embedded/linked pattern)

## Key Features (Public Summary)

### Lead Tracking
- Staff can view a full list of leads with key columns for quick status review
- Search feature for finding individuals quickly
- Lead detail view with categorized tabs (for usability)
- Communication history per lead (chronological)

### Applicant Tracking
- Applicant list with key status fields and search
- Applicant detail profile with multiple tabs
- Communication history, including ability to reference prior lead history

### Communication Management
- Record a new communication event (e.g., phone call / walk-in)
- Send emails from either a personal or departmental context (sanitized)
- Automatically log email communications into the history list
- View “automated emails” status for a person (enabled/disabled/complete concept)

### Automation
- Automated outreach rules by status/criteria
- Lead “aging” rules (e.g., auto mark as cold lead after a time window without response)

### Reporting & Analytics
- Report list screen
- Report parameter filter screens
- Visual analytics screen pattern (Power BI)

## My Role (Sanitized)

I served as the **lead developer and project manager** for the build, including:
- Requirements discovery and stakeholder meetings
- Prototyping and UI/UX design
- Power Apps implementation (screens, navigation, logic)
- Data model design and backend implementation (SharePoint/SQL pattern)
- Automation design and implementation (Power Automate)
- Reporting approach and analytics integration (Power BI pattern)
- Test planning and execution coordination

## Impact (Public, Non-Sensitive)

The implementation enabled staff to replace spreadsheet-based workflows with an integrated system and contributed to substantial efficiency gains in daily operations (e.g., measurable time reduction for key tracking, communication, and reporting tasks).

## What’s Included in This Public Repository

- Generic Architecture documentation
- Generic data model + sample SQL schema
- Automation (flow) documentation (no production exports)
- Power Fx implementation patterns (generic)

## What’s Intentionally Excluded

- Power Apps solution exports (.msapp / managed solutions)
- Power Automate exports (flow JSON packages)
- Real connectors, tenant/environment IDs, URLs, or credentials
- Any real user/student data
- Institution-specific database objects or naming conventions
- Vendor/system names that could identify the deployment environment

## Repository Guide

- `docs/system-architecture.md` — system architecture and data flow
- `docs/data-model.md` — conceptual model and entity relationships
- `docs/sample-schema.sql` — generic schema you can run locally
- `workflows/*` — documented workflows (triggers, steps, exceptions)
- `powerfx/*` — Power Fx patterns for delegation, Patch(), validation, RBAC UI logic
