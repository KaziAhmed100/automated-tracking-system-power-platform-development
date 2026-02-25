# Flow 02 — Applicant Import & De-dup

## Purpose
Import applicants from a central registration source into ATSA and deduplicate against existing records and leads.

## Trigger
- Manual staff action: “Import New Applicants” (button)
- Or scheduled import window (optional pattern)

## Inputs
- Applicant feed records from a central system (sanitized)
- ExternalAppRef / application identifiers (generic)

## Steps (High Level)
1. Create ImportBatch record (type = Applicants)
2. Pull applicant feed items
3. For each item:
   - Try match Person by email/phone + name
   - Try match existing Applicant by ExternalAppRef
4. If Applicant already exists: skip/update status timestamps only
5. If new Applicant:
   - Create Person if needed
   - Create Applicant record
6. If matching Lead exists:
   - Set Applicant.LinkedLeadId
   - (Optional) update LeadStatus to reflect conversion
7. Update ImportBatch counts (imported/skipped/failed)
8. Log summary results for staff review

## Error Handling
- Continue-on-error per record; increment FailedRecords
- Persist minimal error details without PII

## Data Written
- ImportBatches, People, Applicants, Leads (optional conversion update)
