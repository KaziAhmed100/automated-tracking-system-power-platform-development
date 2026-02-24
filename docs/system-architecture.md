# System Architecture Framework

## High-Level Components

ATSA is composed of:

1. **Power Apps (Web Application UI)**
   - Landing dashboard with module navigation
   - Individual Screens - Leads / Applicants / Program Cohort / Reports
   - Profile screens with tab-based layouts
   - Communication screens (log, view, email, automated status)

2. **Data Layer**
   - **SQL Server** for structured relational data (reporting-friendly, scalable)
   - **SharePoint Lists** for rapid internal data upload as a medium
   - This public repo uses a **generic SQL schema** to illustrate the model

3. **Automation Layer (Power Automate)**
   - Email sending + logging
   - Batch email campaigns
   - Import/dedup processes
   - Lead aging rules (cold-lead status updates)
   - Status/notification workflows

4. **Analytics Layer (Power BI)**
   - Reports list UI
   - Parameterized report filters
   - Visual analytics dashboards for quick metrics

## Data Flow (Conceptual)

### Lead Lifecycle
1. Staff creates or imports a **Lead**
2. Staff records communications (manual entries, walk-ins, phone calls or emails)
3. Automated outreach updates statuses and logs interactions
4. Lead may convert into an **Applicant** (or remain a lead)

### Applicant Lifecycle
1. Applicant data is imported from a **central registration source**
2. System checks for matches against existing leads (dedup)
3. Staff reviews and updates applicant statuses and steps
4. Communication history is unified (including prior lead history)

### Communications
- Each email/interaction becomes a **Communication** record
- Communication entries power a chronological timeline view
- Automated messages are also recorded for auditability

### Reporting & Analytics
- Reports query the data layer (SQL)
- Analytics visuals use aggregated datasets (Power BI)
- Screens provide filters for staff to generate reports and visuals

## Screen Modules Reflected in the Build

The application design includes:
- Dashboard home with navigation cards
- Lead list → Lead profile → Communication history → Email / Automated Emails status
- Applicant list → Import feed → Applicant profile → Communication history
- Cohort tracking list → Cohort import feeds
- Reports list → Report filters → Analytics visuals

(These modules map to the mockup screens and project description.)

## Operational Considerations (Conceptual)

- **Auditability:** communication events logged for traceability
- **Resilience:** flow retries and error paths for email/import processes
- **Performance:** delegation-aware filtering patterns in Power Apps for large lists
- **Usability:** tabbed profile views to prevent overload and reduce scrolling
