# Flow 05 — Batch Email Campaign

## Purpose
Enable staff to send a tailored batch email to a filtered group of leads or applicants, while logging each email to the communication timeline.

## Trigger
- Power Apps action: “Batch Email”

## Inputs
- Audience type (Leads or Applicants)
- Filters (program/session/status/etc.)
- EmailTemplate (optional) + custom edits
- Sending context (sanitized)

## Steps (High Level)
1. Query audience based on filters (delegation-safe query patterns)
2. Render email body per recipient (template merge)
3. Send email one-by-one (or in controlled parallel batches)
4. For each recipient:
   - Create a Communications record (IsAutomated = false)
5. Produce a summary for staff: success/failure counts

## Error Handling
- Continue-on-error; capture failed recipients for follow-up
- Rate limiting and retry policy to avoid connector throttling

## Data Written
- Communications (one per recipient)
