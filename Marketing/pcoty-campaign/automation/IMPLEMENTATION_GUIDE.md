# n8n Implementation Guide (PCoTY)

This guide assumes the n8n instance runs elsewhere. Import the supplied workflow JSON file, then connect it to the services already available in that instance. Keep credentials inside n8n.

Do not automate LinkedIn activity, job applications, or unapproved external messages.

## Workflow: PCotY Deadline Task Generator

### Purpose

Calculate campaign phase and create tasks for the 30/21/14/7/3/1-day waves. The supplied workflow does not publish or send.

### Setup

1. Import `pcoty-campaign-status.workflow.json`.
2. Resolve the official closing timestamp first, including timezone.
3. Store that timestamp in one authoritative campaign settings record.
4. Add a daily Schedule Trigger in a parent workflow.
5. Read the deadline record.
6. Execute the imported workflow or POST to `/webhook/pcoty-campaign-status`.
7. If `waveDue` is not null, create channel tasks using the approved campaign toolkit.
8. Route each task to the responsible owner for approval.
9. Record approval, publication date, link/UTM, and result.

Do not hard-code conflicting dates into multiple workflows.

## Workflow: PCotY Nomination Funnel

### Purpose

Improve valid nomination completion while respecting programme privacy and keeping PCotY data separate from any career search system.

### Required source capability

Use one of:

- Application-platform webhook
- Documented API
- Scheduled permitted export from the application system
- Manual CSV import into a restricted folder

### Normalize statuses

Each nomination needs a stable ID and one of:

- `started`
- `nomination_complete`
- `customer_assessment_pending`
- `complete`
- `withdrawn`
- `suppressed`

### Nodes

1. **Trigger/import** from the permitted source.
2. **Validate** required IDs, source, purpose, and communication permission.
3. **Deduplicate/upsert** by nomination ID.
4. **Switch** by current status.
5. **Suppress completed/withdrawn/opted-out records** from reminder branches.
6. **Wait/cadence check** so no person receives excessive reminders.
7. **Prepare reminder draft** from approved copy only.
8. **Human approval** showing recipient, nomination ID, status, last contact, and exact draft.
9. **Authorized email send** after approval.
10. **Update record** with send/result/suppression.
11. **Aggregate dashboard** using counts only where personal data is unnecessary.

### Reminder logic

- Started: offer completion checklist and clinic.
- Nomination complete, customer pending: explain client-assessment requirement and deadline.
- Complete: thank-you only; no deadline reminder.
- Withdrawn, objected, or suppressed: never contact.

## Workflow: Partner Attribution

1. Define UTM format, for example:
   - `utm_source=partner_name`
   - `utm_medium=partner`
   - `utm_campaign=pcoty2027_nominations`
   - `utm_content=launch|eligibility|deadline7`
2. Generate one tracked URL per partner/campaign asset.
3. Capture UTM values in analytics and, where disclosed, in the nomination form.
4. Join campaign attribution to aggregate nomination stages.
5. Share aggregate results with partners, never nominee-level personal data.

## Weekly Dashboard

- Qualified visits
- Nomination starts
- Completed nominations
- Customer assessments complete
- Start-to-completion rate
- Results by partner/campaign
- Assessor coverage and conflicts cleared

## Security Checklist

- Use OAuth and least privilege.
- Keep webhook URLs unguessable and add authentication where callers support it.
- Validate all webhook inputs.
- Keep n8n behind TLS and update it regularly.
- Run the n8n security audit.
- Disable unnecessary community nodes.
- Save error executions, minimize successful execution data, and enable pruning.
- Never commit credentials, tokens, personal-data exports, or live webhook URLs.
- Test every branch with synthetic records before using personal data.

## Go-Live Test Cases

- Missing/invalid deadline returns an error and creates no task.
- Exact 21/14/7/3/1-day dates create the correct task.
- Completed nomination receives no reminder.
- Suppressed record receives no reminder.
- Customer-pending record receives the correct approved copy.
- Changing the authoritative deadline updates all future waves.
