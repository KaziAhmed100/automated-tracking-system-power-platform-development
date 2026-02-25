# Flow 06 — Lead Aging / Cold Lead Status

## Purpose
Automatically mark leads as “cold” when they have not responded within a defined time window, reducing manual staff updates.

## Trigger
- Scheduled flow (daily) OR event-driven check based on last contact timestamp

## Inputs
- Lead records with LastContactedAt or CreatedAt
- Threshold window (e.g., 14 days without response)

## Steps (High Level)
1. Query leads eligible for aging evaluation
2. For each lead:
   - If no response and threshold exceeded:
     - Update LeadStatus to “Cold”
     - Log a Communications note: “Status updated by automation”
     - Optionally disable future automated outreach sequence (policy-based)
3. Output summary report for staff review (optional)

## Error Handling
- Continue-on-error per lead
- Log failures for admin follow-up

## Data Written
- Leads (LeadStatusId), Communications (IsAutomated = true)
