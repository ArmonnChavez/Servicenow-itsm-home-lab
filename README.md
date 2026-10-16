# ServiceNow ITSM Home Lab

A hands-on IT Service Management lab built on a free ServiceNow Personal Developer Instance (Australia release). I set up a small fictional company, then worked realistic help desk tickets from intake to resolution — covering incident management, escalation, request fulfillment, knowledge management, and reporting.

**Built by:** Armonn Chavez
**Goal:** Practice the day-to-day workflows of an IT Service Desk / Help Desk role, with a focus on access management fundamentals.

---

## Skills Demonstrated

- Incident lifecycle: New → In Progress → On Hold → Resolved
- Ticket triage using Impact and Urgency to set Priority
- Escalation and reassignment between support tiers
- Internal work notes vs. customer-visible comments
- Incident vs. service request (catalog ordering, REQ / RITM / SCTASK)
- Parent/child incidents for outages affecting multiple users
- Configuration items (CMDB) linked to incidents
- Knowledge base article creation and approval workflow
- User and group administration, role-based access control (itil role)
- User impersonation to test and work as another agent
- Reporting on ticket volume by priority, state, and assignment group

---

## Phase 1: Environment Setup

Created a fictional company with 8 users across IT, HR, Finance, and Sales, plus three IT assignment groups:

| Group | Members | Purpose |
|---|---|---|
| IT Service Desk | Armonn Chavez, Maria Lopez | First line of support |
| IT Network Team | Kevin Brooks | Network, VPN, connectivity |
| IT Desktop Support | Maria Lopez | Hardware, printers, software |

The **itil** role was assigned at the **group** level rather than to individuals, so access is granted through group membership. This keeps onboarding and offboarding clean, a core identity and access management (IAM) practice.

![Users list](setup-users-list.png)
![Groups list](setup-groups-list.png)
![IT Service Desk members and roles](setup-it-service-desk-members.png)

---

## Phase 2: Incident Management (6 Tickets)

### Ticket 1: Account Lockout (INC0010006)
**Scenario:** HR Coordinator locked out after multiple failed password attempts.
**Actions:** Verified identity, unlocked the account in the user record, forced a password reset at next login, and updated the caller.

![Account locked before](inc1-jasmine-locked-out-before.png)
![Incident created](inc1-incident-created.png)
![Work notes](inc1-work-notes.png)
![Account unlocked after](inc1-jasmine-unlocked-after.png)
![Resolved](inc1-resolved.png)

### Ticket 2: VPN Failure and Escalation (INC0010008)
**Scenario:** Remote user unable to connect to VPN.
**Actions:** Performed first-line troubleshooting (confirmed internet access, restarted the client, rebooted). Documented the steps and escalated to the IT Network Team. Used impersonation to resolve the ticket as the network admin.

![VPN ticket escalated](inc2-escalated.png)
![Resolved by Network Team](inc2-resolved-by-network-team.png)

### Ticket 3: Printer Failure with CI and On Hold (INC0010010)
**Scenario:** Shared Sales printer showing a false paper jam.
**Actions:** Created the printer as a Configuration Item (SALES-PRINTER-01) and linked it to the ticket. Routed directly to Desktop Support, placed the ticket On Hold while awaiting a replacement part, and gave the user a workaround.

![Printer CI](inc3-printer-ci.png)
![On Hold](inc3-on-hold.png)
![Resolved](inc3-resolved.png)

### Ticket 4: Incident vs. Request (INC0010011)
**Scenario:** User called in asking for Adobe Acrobat to be installed.
**Actions:** Identified this as a service request, not an incident. Ordered the catalog item on the user's behalf, resolved the incident with a reference to the request, and fulfilled the catalog task.

![Catalog order](inc4-catalog-order.png)
![Request fulfilled](inc4-request-fulfilled.png)

### Ticket 5: Outage with Parent/Child Incidents (INC0010012)
**Scenario:** Shared drive unreachable across multiple departments.
**Actions:** Created a Priority 1 parent incident and linked individual user reports as child incidents. Resolving the parent closed out the related reports, so every affected user was updated and no work was duplicated.

![Parent and child incidents](inc5-parent-child-incidents.png)
![Outage resolved](inc5-resolved.png)

### Ticket 6: No Response from Caller (INC0010016)
**Scenario:** User reported Outlook crashing, then stopped responding.
**Actions:** Requested more information, set the ticket to On Hold (Awaiting Caller), made three documented contact attempts, then resolved it with clear notes that the user could reopen it.

![Awaiting caller](inc6-awaiting-caller.png)
![Resolved, no response](inc6-resolved-no-response.png)

---

## Phase 3: Knowledge Management

Wrote and published **KB0010001: How to Unlock a Locked User Account**, based on Ticket 1. The article went through the IT knowledge base approval workflow before publishing.

![KB pending approval](kb-pending-approval.png)
![KB published](kb-unlock-account-published.png)

---

## Phase 4: Reporting

Built reports on my lab tickets, filtered to the three IT assignment groups:
- Tickets by Priority
- Tickets by State
- Tickets by Assignment Group

![Tickets by priority](report-tickets-by-priority.png)

---

## Key Takeaways

- **Documentation matters.** Clear work notes let the next agent pick up a ticket without repeating troubleshooting.
- **Keep the caller informed,** especially during escalations and holds.
- **Classify correctly.** Separating incidents from requests keeps metrics accurate and routes work to the right process.
- **Grant access through groups, not individuals.** It makes permissions easier to audit and manage.
