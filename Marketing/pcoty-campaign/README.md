# PCoTY 2027 Campaign

Volunteer Program Manager campaign kit for the Project Business Foundation's Project Contractor of the Year (PCotY) 2027 Award. Split out from the personal career-repositioning repo on 2026-09-29 to keep programme administration operationally and technically separate from career/job-search data, per the compliance rule already in force there: PCoTY participant, nominee, customer, assessor, or juror data must never be used for career outreach, and PCoTY messaging must never mention career availability.

## Project Structure

```
├── strategy/
│   └── PCotY_2027_Marketing_Plan.md      <- Campaign plan, channels, KPIs, deadlines
├── templates/
│   └── pcoty-2027-campaign-toolkit.md    <- Approved copy: posts, nomination notes, PR notes, reminders
├── tracking/
│   └── pcoty-campaign-pipeline.md        <- 46 partner contacts (4 geographic rounds) with drafted subject/body per contact
├── outreach/
│   └── pcoty-authority-content.md        <- Submission-checklist authority content task
└── automation/
    ├── README.md                         <- n8n setup and security
    ├── IMPLEMENTATION_GUIDE.md           <- Node-by-node workflow build guide
    └── pcoty-campaign-status.workflow.json <- Deadline-wave calculator workflow
```

## Quick Start

- Marketing plan and deadlines: `strategy/PCotY_2027_Marketing_Plan.md`
- Approved-copy toolkit: `templates/pcoty-2027-campaign-toolkit.md`
- Partner contact list and drafted emails: `tracking/pcoty-campaign-pipeline.md`
- n8n setup and security: `automation/README.md`

## Current Campaign Decision

The 2027 cycle nomination deadline is extended to **30 November 2026**. The exact closing time and timezone still need to be confirmed by the application system. Every drafted email in `tracking/pcoty-campaign-pipeline.md` has a `[DEADLINE]` placeholder that must be replaced with that final timestamp before sending.

## Data And Ethics Controls

- PCotY data is used only for programme administration and consented communications.
- Never transfer participant, client, assessor, or juror data into any career CRM or job-search pipeline.
- Record source, purpose, consent/lawful basis, retention date, and suppression status.
- Require human approval for every external message.
