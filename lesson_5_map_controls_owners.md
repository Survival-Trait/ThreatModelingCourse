<!--
author: SurvivalTrait Academy
email: contact@survivaltrait.academy
version: 1.0.0
language: en
narrator: US English Female

comment: Lesson 5 - Map security controls to threats and assign clear ownership

@style
.lia-toc__bottom {
    display: none;
}
h2 {
    border-left: 4px solid #1e88e5;
    padding-left: 10px;
}
@end

-->

# Lesson 5: Map Controls and Owners

**Lesson Duration:** 40-50 minutes  
**Format:** Self-paced reading + action planning exercise

## Learning Objectives

After this lesson, you will:

- Identify existing and needed controls for each threat
- Assign clear ownership with accountability
- Define evidence criteria for "done"
- Create an action plan that gets implemented

## Introduction

You've identified and prioritized threats. Now you need to do something about them.

This lesson teaches you how to map security controls to threats, assign owners who can actually implement them, and create evidence criteria that prove the work is done.

**This is where threat modeling becomes operational security.**

## Existing vs. Needed Controls

For each threat, answer two questions:

### What controls already exist?

Don't start from scratch. Most systems have some defenses already in place.

### What additional controls are needed?

Where are the gaps? What would reduce the threat to acceptable levels?

### Control Categories:

**Preventive controls:** Stop the threat from happening  
Examples: Input validation, authentication, encryption, firewall rules

**Detective controls:** Detect when the threat is happening or has happened  
Examples: Logging, monitoring, intrusion detection, anomaly detection

**Corrective controls:** Limit damage and recover after the threat is realized  
Examples: Backups, incident response procedures, data breach notification plans

> **Key Point:** Most threats need a combination of all three control types.

### Example:

**Threat:** SQL injection in search endpoint

**Existing controls:**
- Database connection uses least-privilege account (limits damage)
- Application logs all database queries (detective)

**Needed controls:**
- Parameterized queries for all user input (preventive)
- Input validation on search parameters (preventive)
- Automated scanning in CI/CD pipeline (detective)

## Assigning Ownership That Sticks

**A control without an owner is a recommendation that dies in a document.**

### Good Ownership:

- [X] Specific person or team name
- [X] Person has authority to implement the control
- [X] Person has necessary skills or resources
- [X] Person accepts the responsibility

### Bad Ownership:

- [ ] "Engineering team" (too vague)
- [ ] "Security team" (for controls they can't implement)
- [ ] "TBD" (means it won't get done)
- [ ] No owner listed

### When Assigning Owners:

**For preventive controls:** Usually the team that owns the code or infrastructure  
Example: Application developers own parameterized query implementation

**For detective controls:** Usually the security or operations team  
Example: SOC owns log monitoring and alert response

**For corrective controls:** Usually shared between teams  
Example: Incident response plan owned by security, backup restoration owned by operations

### Document Ownership Clearly:

```
Threat: SQL injection in search endpoint
Control: Implement parameterized queries for all search inputs
Owner: Backend development team (lead: Sarah Chen)
Owner Accepts: Yes (confirmed 2026-01-27)
```

**If the owner doesn't explicitly accept, you don't have ownership.**

## Evidence Criteria for "Done"

"Implement input validation" is not specific enough to know when it's complete.

Evidence criteria answer: **How do we prove this control is in place and working?**

### Good Evidence Criteria:

- [X] Specific and measurable
- [X] Verifiable by someone other than the implementer
- [X] Automated when possible
- [X] Includes ongoing validation, not just one-time implementation

### Examples:

**Control:** Implement parameterized queries  
❌ **Poor evidence:** "Code is updated"  
✅ **Good evidence:**
- All search endpoints use prepared statements (code review checklist completed)
- Automated SAST scan shows zero SQL injection findings in search module
- Penetration test confirms search inputs are not injectable

**Control:** Enable detailed API logging  
❌ **Poor evidence:** "Logging is turned on"  
✅ **Good evidence:**
- Log entries include timestamp, user ID, endpoint, parameters, response code
- Logs retained for 90 days in tamper-evident storage
- Sample log review shows all required fields present
- Monitoring alert fires when logging stops

**Control:** Quarterly access reviews  
❌ **Poor evidence:** "Reviews are scheduled"  
✅ **Good evidence:**
- Calendar events created with assigned reviewers
- Review template includes list of all privileged accounts
- Completed review documents stored in shared drive
- Audit trail shows accounts disabled within 5 days of review finding

**Evidence criteria should be achievable but rigorous. If you can't prove the control works, you don't know if you're actually safer.**

## Creating the Action Plan

The action plan connects your threat table to actual work.

### Action Plan Format:

| Priority | Threat | Control | Owner | Deadline | Evidence | Status |
|----------|--------|---------|-------|----------|----------|--------|
| Critical | SQL injection in search | Parameterized queries | Backend dev | 2026-02-15 | SAST scan clean, code review | In Progress |
| Critical | Forged JWT tokens | JWT secret rotation + RS256 | DevOps | 2026-02-20 | Updated config, key length verified | Not Started |
| High | API DDoS | Rate limiting 100 req/min | Platform team | 2026-03-01 | Load test confirms limit enforced | Not Started |
| Medium | Error message info leak | Generic error responses | Backend dev | 2026-03-15 | Pen test validates no schema in errors | Not Started |

**Status values:** Not Started, In Progress, Blocked (with reason), Complete, Accepted (for risks you're not addressing)

### Realistic Deadlines:

- **Critical threats:** Within 2-4 weeks
- **High threats:** Within 1-2 months
- **Medium threats:** Within 3-6 months
- **Low threats:** Document and defer, or accept

If you can't meet these timelines, you may need to accept some risks or argue for more resources.

## When You Can't Implement a Control

Sometimes the needed control is not feasible:

### Too Expensive:

**Compensating control:** "We can't afford a WAF, so we're implementing rate limiting and enhanced logging instead."

### Technical Limitations:

**Compensating control:** "We can't upgrade the legacy system, so we're isolating it on a separate network segment with strict firewall rules."

### Third-Party Dependency:

**Risk acceptance:** "The cloud provider controls the underlying infrastructure. We've verified their SOC 2 attestation and accepted the residual risk."

### Business Decision:

**Risk acceptance:** "Leadership has decided not to implement MFA due to user experience concerns. We've documented the decision and required compensating detective controls."

**Document compensating controls and risk acceptances with the same rigor as implemented controls.**

## Making the Action Plan Stick

Your action plan will fail if:

- [ ] Owners don't know it exists
- [ ] Deadlines are unrealistic
- [ ] There's no follow-up mechanism
- [ ] Leadership doesn't care

### To Make It Stick:

**Share it with owners immediately:** Don't wait for a formal meeting. Send it directly to each owner with clear expectations.

**Schedule check-ins:** Monthly for critical threats, quarterly for others. Treat these like any other project milestone.

**Escalate blocked items:** If an owner is stuck, escalate early. Blocked threats don't age well.

**Update the threat model:** When controls are implemented, update the threat table. When the system changes, add new threats.

**Celebrate wins:** When critical threats are addressed, acknowledge the work. Security is often thankless; don't make it worse.

## Practice Exercise

Take your prioritized threat table from Lesson 4.

### For each threat:

**1. List existing controls:**

    [[_______________________________________]]

**2. Identify at least one needed control:**

    [[_______________________________________]]

**3. Assign a specific owner (use a real team or role from your organization):**

    [[_______________________________________]]

**4. Write evidence criteria:**

    [[_______________________________________]]

**5. Set a realistic deadline:**

    [[_______________________________________]]

**Create a complete action plan table.**

Spend 30 minutes. You should have a deliverable you could send to stakeholders today.

## Knowledge Check

**What makes a control owner assignment effective?**

    [[X]] Specific person or team name
    [[ ]] "Security team" designation
    [[X]] Person has authority to implement
    [[ ]] "TBD" placeholder
    [[X]] Owner explicitly accepts responsibility
***
**Explanation:** Effective ownership requires specificity (not "Engineering team"), authority to act, and explicit acceptance. "TBD" and vague designations lead to controls that never get implemented.
***

**What's the difference between "logging is enabled" and good evidence criteria?**

    [( )] There is no difference
    [( )] Good evidence is more detailed
    [(X)] Good evidence is specific, measurable, verifiable, and includes ongoing validation
    [( )] Good evidence requires automated testing
***
**Explanation:** While detail and automation help, the key difference is that good evidence criteria are specific (what's being logged), measurable (can verify), verifiable by others, and include ongoing validation (not just one-time check). "Logging is enabled" doesn't specify what, how long, or how to verify.
***

**When should you document a compensating control?**

    [(X)] When the ideal control is not feasible but you implement an alternative
    [( )] When you want to delay implementing a control
    [( )] When the risk is low priority
    [( )] When stakeholders disagree on the threat
***
**Explanation:** Compensating controls are alternatives when you can't implement the ideal control due to cost, technical limitations, or other constraints. They still address the threat but through different means.
***

## Key Takeaways

- Identify both existing and needed controls for each threat
- Assign specific owners who accept responsibility
- Evidence criteria prove controls are working, not just implemented
- Action plans need realistic deadlines and follow-up mechanisms
- Document compensating controls and risk acceptances when needed
- The threat model only matters if it drives action

---

**Previous:** [Prioritize Using Impact and Likelihood](lesson_4_prioritize_impact_likelihood.md)  
**Next:** [Lab Exercise: Threat Model a CI/CD Pipeline](lab_cicd_pipeline.md)  
**Return to:** [Course Home](README.md)
