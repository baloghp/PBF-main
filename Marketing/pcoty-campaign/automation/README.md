# n8n PCoTY Automation

## Design Principle

Automate intelligence and administration, not human relationships. Every application, external message, and publication remains a human decision.

## Included Workflow

### `pcoty-campaign-status.workflow.json`

Credential-free webhook that accepts the authoritative PCotY closing timestamp, calculates campaign stage and deadline waves, and returns a human-review action packet. For the 2027 cycle, supply the confirmed 30 November 2026 closing time and timezone explicitly.

It does not send email or publish posts.

### PCotY Campaign Input

POST JSON to `/webhook/pcoty-campaign-status`:

```json
{
  "campaign": "PCotY 2027",
  "deadline": "2026-11-30T23:59:00+01:00"
}
```

## Recommended Production Architecture

### PCotY funnel

Permitted form event/export -> deduplicate -> status segmentation -> campaign attribution -> reminder draft -> human approval -> authorized email -> completion/suppression update -> aggregate dashboard.

Keep PCotY data in its own database/schema and credential set, separate from any career/job-search system.

## Human Approval

Use n8n human-in-the-loop approval for every send/publish action. Approval may be routed through Teams, Outlook, Slack, Telegram, or another supported channel. The reviewer must see recipient, subject, body, source, and purpose.

## Security Baseline

- Use OAuth where possible.
- Put n8n behind TLS.
- Encrypt storage at rest.
- Run `n8n audit` or the authenticated `/audit` endpoint.
- Disable unnecessary risky/community nodes.
- Save failed executions, minimize successful execution data, and enable pruning.
- Do not put credentials or personal data in workflow JSON committed to this workspace.
- Use a separate service account and least-privilege credentials for PCoTY workflows.

Suggested retention starting point, subject to the actual privacy policy:

```text
EXECUTIONS_DATA_SAVE_ON_ERROR=all
EXECUTIONS_DATA_SAVE_ON_SUCCESS=none
EXECUTIONS_DATA_SAVE_ON_PROGRESS=false
EXECUTIONS_DATA_PRUNE=true
EXECUTIONS_DATA_MAX_AGE=168
```

## Inputs Needed Before Live Integration

No secrets should be placed in this repository. Configure them directly in n8n.

Confirm:

- n8n version and deployment method
- Email provider: Microsoft 365, Gmail, or SMTP/IMAP
- Approval channel
- Storage: n8n Data Tables, Postgres, Airtable, Google Sheets, or Microsoft Lists
- PCotY application platform event/export capability
- Web analytics platform and UTM support
- Authoritative PCotY closing timestamp and timezone

## Validation

- Workflow export passed JSON validation on 7 September 2026.
- PCotY behavior test: 15 days before the supplied deadline returned the `conversion` stage, incomplete-submission actions, and human review required.

## Official References

- GDPR principles: https://commission.europa.eu/law/law-topic/data-protection/information-business-and-organisations/principles-gdpr_en
- n8n human-in-the-loop: https://docs.n8n.io/build/integrate-ai/ai-examples/human-in-the-loop-for-tools
- n8n security audit: https://docs.n8n.io/deploy/host-n8n/configure-n8n/security/run-security-audits
- n8n execution retention: https://docs.n8n.io/deploy/host-n8n/configure-n8n/scaling/manage-execution-data
