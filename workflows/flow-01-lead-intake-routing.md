# Flow 01 — Lead Intake & Routing

## Purpose
Standardize how new leads enter the system (such as a central inquiry form), ensure required fields are captured, and route leads to the correct program/session cohort.

## Trigger
- When a new Lead record is created (Power Apps submit or import)

## Inputs
- Person identity fields (name/email/phone) — as available
- Program/session preference
- Lead source metadata (campaign/referral/etc.)

## Steps (High Level)
1. Validate required fields (email or phone required)
2. Normalize data (trim, lowercase email, etc.)
3. Check for potential duplicates (existing People by email/phone)
4. If match found:
   - Link Lead to existing Person
   - Else create a new Person record
5. Assign default LeadStatus (e.g., New)
6. Optionally create initial AutomatedMessageStatus for outreach sequence
7. Log a Communication note: “Lead created” (non-PII)

## Error Handling
- If validation fails: set a status flag and return a friendly message to UI
- If DB write fails: retry with exponential backoff; log failure record for review

## Data Written
- People, Leads, (optional) AutomatedMessageStatuses, Communications
