# Data Model

This model represents a generic CRM-style tracking system for leads, applicants, communications, automation status, and reporting.

## Core Entities

### Person
Represents an individual (prospect/applicant/student) in a PII(Personal Identification Information)-safe structure.

### Lead
Represents a prospect record created by staff or imported from campaigns.

### Applicant
Represents an application record (often sourced from a central registration system).

### Program / Cohort
Represents a program, session, intake, or special cohort grouping.

### Communication
Represents a single interaction: email, phone call, meeting, etc.
Used to power chronological history timelines.

### AutomatedMessagePlan / AutomatedMessageStatus
Represents configured automation sequences and the per-person state.

### EmailTemplate
Represents reusable email content for batch or individual outreach.

### ImportBatch
Represents an import run and results for traceability.

### UserRole
Represents staff role and permissions.

## Relationship Summary

- A **Person** can have **0..n Leads**
- A **Person** can have **0..n Applicants**
- A **Lead** can convert into an **Applicant** (tracked via references)
- A **Person** has **0..n Communications**
- A **Person** can have **0..n AutomatedMessageStatus** records
- A **Program** / **Cohort** relates to leads and applicants via foreign keys

## Notes on Reporting

- Reporting typically aggregates by:
  - Program/session
  - Status and stage
  - Country/region (if tracked in a privacy-safe way)
  - Date ranges (created/updated/submitted)
  - Conversion metrics (lead → applicant)

## Generic Status Design

Use normalized lookup tables for statuses:
- LeadStatus (e.g., New, Contacted, Warm, Cold)
- ApplicantStatus (e.g., Submitted, In Review, Accepted, Denied)

This enables:
- Stable reporting
- Clean UI dropdowns
- Centralized status management

## See also

- `sample-schema.sql` for a runnable generic SQL schema.
