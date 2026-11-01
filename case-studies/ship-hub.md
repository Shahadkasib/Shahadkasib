# SHIP Hub
## Turning a school recognition programme into an accountable digital workflow

**Shahad Fuad Kasib · CTO, Imperial International School**  
**Focus:** Full-stack development, workflow design, permissions, bilingual user experience  
**Stack:** Next.js, React, TypeScript, Tailwind CSS, PostgreSQL, Supabase Storage, Vercel

> Engineering case study. Production source code and operational school data remain private.

### The problem

A school house-points programme involves more than entering numbers. Teachers need to submit awards, reviewers need to assess supporting evidence, and leadership needs standings that reflect approved decisions. Corrections must remain traceable, and different staff members need different levels of access.

SHIP Hub brings these responsibilities into one bilingual workspace for Imperial International School’s Student House Inspirational Program.

### My contribution

As CTO, I designed, built, and launched SHIP Hub, connecting the school’s programme requirements with the application’s submission, review, reporting, and account-management workflows.

The implementation includes a Next.js interface and server routes, shared permission rules, database-backed records, private attachment storage, and English–Arabic language handling.

### The core workflow

1. A teacher selects students and an award reason, adds an explanation, and attaches evidence.
2. The submission enters house review.
3. An authorized House Patron reviews the award and forwards it for final approval or rejects it.
4. The designated SHIP Director makes the final decision.
5. Approved awards contribute to the house standings.

Delegated corrections return awards to house review and clear previous approval fields. This reconnects the corrected award with its review process instead of silently preserving an earlier approval.

### Engineering decisions

**Granular permissions.** The application defines granular permissions for student records, submissions, approvals, documents, reports, and recovery. Grade and house scopes further limit the records available to an account. This supports users who need aggregate standings without individual student details, as well as staff whose work is limited to particular grades or houses.

**The server checks access.** Permission and scope checks appear in the application’s server-side business logic. Hiding an interface control is therefore only one part of the access model.

**Approval status drives totals.** Standings are calculated from approved awards for the configured year. Pending submissions remain visible to the appropriate reviewers without contributing to approved totals.

**Repeated submissions have an identity.** A submission reference ties together its evidence and award records. The implementation checks for repeat references, helping prevent a retry from creating another set of awards.

**Changes retain context.** Record versions detect stale updates, while an audit history records changes. Recovery provides a path for restoring permitted removed records. Staff credential fields are excluded from relevant audit output.

**Arabic support includes reading direction.** The language layer persists the selected language and updates the document language and right-to-left or left-to-right direction. This makes bilingual support part of the application experience.

### Architecture

| Layer | Responsibility |
|---|---|
| Next.js / React interface | Staff workflows, forms, standings, and bilingual presentation |
| Next.js server routes and business logic | Sessions, authorization, validation, submissions, and approvals |
| PostgreSQL on Supabase | Application records and audit history |
| Supabase Storage | Private evidence attachments and programme documents |
| Vercel | Application and API deployment |

### Verification designed into the repository

The repository includes automated scenarios for unauthorized access, grade and house scopes, approval transitions, duplicate submissions, stale updates, correction behavior, recovery, session revocation, restricted documents, audit redaction, and login throttling. It also contains database translation tests.

The scenarios above describe the test suite’s contents; this case study does not report a fresh test run, coverage measurement, or production security assessment.

### Delivery and outcome

SHIP Hub provides a single application for award submissions, two-stage review, approved standings, programme documents, reports, and traceable corrections. The portal is live and rolling out to school staff.

Usage and time-savings metrics are not reported here.

### What this demonstrates

- Translating organizational rules into application behavior.
- Delivering a full-stack TypeScript application for an operational use case.
- Designing permission-sensitive workflows and record lifecycle rules.
- Supporting Arabic and English users.
- Connecting software delivery with ownership of a school’s technology roadmap.

### Source availability

The production repository remains private because it supports school operations. This case study describes the design without publishing student records, staff accounts, attachments, credentials, or internal configuration.

[Back to my profile](https://github.com/Shahadkasib)
