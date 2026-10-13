# PCotY 2027 Marketing Plan

**Campaign window:** 1 September-30 November 2026  
**Finalists:** 15 December 2026  
**Stage 2:** End of January 2027  
**Winners:** 15 February 2027

> Executive campaign decision: the 2027 nomination deadline is extended to 30 November 2026. Confirm the application-system closing time and timezone, then publish one authoritative timestamp.

## Campaign Objective

Generate a credible, geographically diverse pool of completed nominations for exemplary customer-facing project contractors, with completed client validation and sufficient independent assessor capacity.

## Core Message

**Your best project deserves more than an invoice.**  
PCotY recognizes contractors whose customer-facing project work goes beyond competent delivery to measurable impact, innovation, industry contribution, and lasting legacy.

## Audience Priority

1. Clients and project sponsors who can nominate an exemplary contractor
2. Contractors, consultancies, freelancers, and service providers with eligible 2024-2026 work
3. Procurement, PMO, transformation, and professional-services leaders
4. Professional associations, chapters, training partners, and industry communities
5. Independent assessors and jurors

## Conversion Assets

- Official landing page and application link
- Nominee guide
- Customer guide and assessment form
- Assessor/juror guide
- One-page eligibility checklist
- One-page evidence checklist
- Deadline and process graphic
- Three category cards: Small 1-25, Medium 25-100, Large 101+
- Partner toolkit with approved post/email copy and tracked links
- FAQ covering cost, ongoing projects, client permission, drafts, publication, and data retention

## Message Sequence

### Launch: 7-13 September

- Nominations are open worldwide and free.
- Explain who is eligible and why client validation makes the award credible.
- Feature the official PBF page, guides, categories, and timeline.
- Team-member posts should identify their volunteer role transparently.

### Education: 14-27 September

- "Would others learn from this project?" decision test
- What exemplary evidence looks like
- How the three size categories work
- How client assessment works
- Nomination clinic / Q&A
- Assessor recruitment and evaluation rigor

### Proof And Participation: 28 September-11 October

- Team and assessor profiles
- Anonymized examples of strong evidence
- Why participate: recognition, feedback, case publication, professional network
- Partner and association amplification

### Conversion: 12-25 November

- 21/14/7-day reminders
- Started-but-incomplete nomination reminders
- Missing client-assessment reminders
- Second clinic based on common submission blockers

### Close: 26-30 November

- 3-day and 1-day reminders
- Exact closing timestamp and timezone
- Support/contact availability
- Thank-you and next-stage dates

## Channel Plan

| Channel | Role | Rule |
|---|---|---|
| Official PBF and PCotY LinkedIn pages | Authoritative announcements | Primary facts and deadlines |
| Volunteer team LinkedIn profiles | Reach and human stories | Manual posting; disclose volunteer role |
| PBF email/newsletter | Existing relevant audience | Consent and opt-out required |
| Partner associations/chapters | Qualified reach | Provide tracked links and approved toolkit |
| Nomination clinics | Objection handling | Registration consent; recording opt-in |
| Direct email | High-fit, known professional contacts | Personalized, lawful, identity + opt-out |
| Website | Conversion | One primary CTA; consistent deadline |

Do not use third-party automation for LinkedIn posting, messaging, visits, likes, comments, or scraping.

## n8n Campaign Automation

### Workflow A: Lead / partner intake

Form or manual import -> validate consent/source -> deduplicate -> segment by nominator/nominee/partner/assessor -> assign campaign code -> store next action.

### Workflow B: Nomination funnel

Application event/webhook or permitted export -> normalize status -> started/completed/customer-assessment pending -> daily dashboard -> draft reminder -> human approval -> send -> suppression on completion or objection.

### Workflow C: Deadline scheduler

Official deadline table -> calculate 30/21/14/7/3/1-day waves -> create channel task and approved draft -> human approval -> publish/send manually or through authorized API.

### Workflow D: Partner attribution

Campaign links with UTM parameters -> website analytics / form source -> completed nomination -> partner dashboard. Never expose nominee personal data to partners.

### Workflow E: Assessor operations

Assessor application -> skills/category/region/conflict capture -> human approval -> assignment support -> deadline reminders -> completion dashboard. Keep conflicts and scoring access restricted.

## Data And Ethics Controls

- PCotY data is used only for programme administration and consented communications.
- Never transfer participant, client, assessor, or juror data into Peter's career CRM.
- Record source, purpose, consent/lawful basis, retention date, and suppression status.
- Minimize stored data and restrict access by role.
- Require human approval for every external message.
- Do not publish nomination details without explicit permission.
- Maintain conflict-of-interest records for assessors and jurors.

## KPIs

- Landing-page conversion to nomination start
- Start-to-completion rate
- Client-assessment completion rate
- Nominations by category, country, industry, and source
- Partner-attributed completed nominations
- Clinic registration-to-attendance rate
- Assessor coverage and completion rate
- Email delivery, click, reply, opt-out, and complaint rates

Raw impressions and follower growth are secondary. Completed, valid nominations and client assessments are the primary outcome.

## Immediate Decisions

- [x] Decide the 2027 nomination date: 30 November 2026.
- [ ] Confirm the application-system closing time and timezone for 30 November 2026.
- [x] Set the finalist announcement date: 15 December 2026.
- [ ] Confirm which system events or exports n8n can receive.
- [ ] Confirm CRM/database, email provider, and approval channel.
- [ ] Create UTM naming standard.
- [ ] Publish privacy notice and suppression process for campaign communications.
- [ ] Assign owners for content, partner outreach, nomination support, assessor operations, and analytics.

## Official Sources

- https://project-business.org/pcoty/
- https://www.ittd.space/pbf-pcoty
- https://www.ittd.space/nominee-s-customer-evaluation
- https://www.pmi.org/about/awards (comparison model)
