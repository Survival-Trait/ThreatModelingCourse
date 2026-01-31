<!--
author: SurvivalTrait Academy
email: contact@survivaltrait.academy
version: 1.0.0
language: en
narrator: US English Female

comment: Interactive workbook - Guided exercises and templates for building your own threat models

@style
.lia-toc__bottom {
    display: none;
}
h2 {
    border-left: 4px solid #4caf50;
    padding-left: 10px;
}
@end

-->

# Threat Modeling Workbook

**Purpose:** Guided exercises and templates for building your own threat models

## How to Use This Workbook

This workbook follows the minimal viable threat modeling workflow. Work through each section in order for your own system.

You can:
- Fill this out digitally (answers save in your browser)
- Work alone or with your team
- Take breaks between sections
- Revisit and update as your system changes

**Expected time:** 3-5 hours for a small system

---

## Section 1: System Definition

### What system are you threat modeling?

**System name:**

    [[___]]

**Brief description (2-3 sentences):**

    [[___________________________________________]]

### Why are you threat modeling this system?

    [[ ]] Building something new
    [[ ]] Making significant changes to existing system
    [[ ]] Preparing for audit or compliance requirement
    [[ ]] Responding to security incident
    [[ ]] Unclear where to focus security efforts
    [[ ]] Other

**What happens if this system fails?**

    [[___________________________________________]]

(Be specific: lost revenue, regulatory fines, data breach, service outage, etc.)

---

## Section 2: Scope Definition

### What components are IN SCOPE for this analysis?

1. [[___]]
2. [[___]]
3. [[___]]
4. [[___]]
5. [[___]]

### What components are OUT OF SCOPE?

1. [[___]]  
   Why: [[___]]
2. [[___]]  
   Why: [[___]]
3. [[___]]  
   Why: [[___]]

### What are your constraints?

    [[___________________________________________]]

(Time, budget, resources, access to information, etc.)

---

## Section 3: Trust Boundary Mapping

### Boundary 1

**Boundary name:**

    [[___]]

**Trusted side description:**

    [[___________________________________________]]

**Untrusted side description:**

    [[___________________________________________]]

**What crosses this boundary?**

    [[___________________________________________]]

**Why does this boundary matter?**

    [[___________________________________________]]

### Boundary 2

**Boundary name:**

    [[___]]

**Trusted side description:**

    [[___________________________________________]]

**Untrusted side description:**

    [[___________________________________________]]

**What crosses this boundary?**

    [[___________________________________________]]

**Why does this boundary matter?**

    [[___________________________________________]]

### Boundary 3

**Boundary name:**

    [[___]]

**Trusted side description:**

    [[___________________________________________]]

**Untrusted side description:**

    [[___________________________________________]]

**What crosses this boundary?**

    [[___________________________________________]]

---

## Section 4: Asset Inventory

### List your most critical assets:

**Asset 1:**

    [[___]]

Type (Data/Function/Infrastructure):

    [[___]]

Criticality (Critical/High/Medium/Low):

    [[___]]

Why it matters:

    [[___________________________________________]]

**Asset 2:**

    [[___]]

Type:

    [[___]]

Criticality:

    [[___]]

Why it matters:

    [[___________________________________________]]

**Asset 3:**

    [[___]]

Type:

    [[___]]

Criticality:

    [[___]]

Why it matters:

    [[___________________________________________]]

### What is your MOST critical asset and why?

    [[___________________________________________]]

---

## Section 5: Threat Identification

### For Boundary: [[___]]

Apply STRIDE to identify threats:

**Spoofing threats:**

1. [[___________________________________________]]
2. [[___________________________________________]]

**Tampering threats:**

1. [[___________________________________________]]
2. [[___________________________________________]]

**Repudiation threats:**

1. [[___________________________________________]]
2. [[___________________________________________]]

**Information Disclosure threats:**

1. [[___________________________________________]]
2. [[___________________________________________]]

**Denial of Service threats:**

1. [[___________________________________________]]
2. [[___________________________________________]]

**Elevation of Privilege threats:**

1. [[___________________________________________]]
2. [[___________________________________________]]

---

## Section 6: Threat Prioritization

### For each threat, assess impact and likelihood:

**Threat 1:**

    [[___________________________________________]]

Impact (H/M/L):

    [[___]]

Impact justification:

    [[___________________________________________]]

Likelihood (H/M/L):

    [[___]]

Likelihood justification:

    [[___________________________________________]]

Priority (C/H/M/L):

    [[___]]

**Threat 2:**

    [[___________________________________________]]

Impact (H/M/L):

    [[___]]

Impact justification:

    [[___________________________________________]]

Likelihood (H/M/L):

    [[___]]

Likelihood justification:

    [[___________________________________________]]

Priority (C/H/M/L):

    [[___]]

---

## Section 7: Control Mapping

### For your highest-priority threat:

**Threat:**

    [[___________________________________________]]

**Existing controls:**

1. [[___________________________________________]]
2. [[___________________________________________]]
3. [[___________________________________________]]

**Needed preventive controls:**

1. [[___________________________________________]]
2. [[___________________________________________]]

**Needed detective controls:**

1. [[___________________________________________]]
2. [[___________________________________________]]

**Needed corrective controls:**

1. [[___________________________________________]]
2. [[___________________________________________]]

---

## Section 8: Owner Assignment

### For your top control:

**Control description:**

    [[___________________________________________]]

**Owner name/team:**

    [[___]]

**Owner has been informed:**

    [[ ]] Yes
    [[ ]] No

**Owner accepts responsibility:**

    [[ ]] Yes
    [[ ]] No
    [[ ]] Pending

**Owner has authority to implement:**

    [[ ]] Yes
    [[ ]] No

**If No to any above, what's the blocker?**

    [[___________________________________________]]

---

## Section 9: Evidence Criteria

### For your top control:

**Control:**

    [[___________________________________________]]

**How will you prove this control is implemented?**

    [[___________________________________________]]

**How will you prove this control is working?**

    [[___________________________________________]]

**What evidence will you collect?**

    [[___________________________________________]]

**How often will you verify this control?**

    [[ ]] One-time
    [[ ]] Monthly
    [[ ]] Quarterly
    [[ ]] Annually
    [[ ]] Continuous

**Who verifies the evidence?**

    [[___]]

---

## Section 10: Action Plan Summary

### Your Top 3 Priorities:

**Priority 1:**

Threat: [[___________________________________________]]  
Control: [[___________________________________________]]  
Owner: [[___]]  
Deadline: [[___]]  
Evidence: [[___________________________________________]]

**Priority 2:**

Threat: [[___________________________________________]]  
Control: [[___________________________________________]]  
Owner: [[___]]  
Deadline: [[___]]  
Evidence: [[___________________________________________]]

**Priority 3:**

Threat: [[___________________________________________]]  
Control: [[___________________________________________]]  
Owner: [[___]]  
Deadline: [[___]]  
Evidence: [[___________________________________________]]

---

## Section 11: Review Checklist

Before finalizing your threat model, verify:

**System Definition:**

    [[ ]] Scope is clearly defined
    [[ ]] In-scope and out-of-scope items are listed
    [[ ]] Business impact of system failure is documented

**Boundaries and Assets:**

    [[ ]] At least 3 trust boundaries are identified
    [[ ]] Each boundary has trusted/untrusted sides described
    [[ ]] Assets are ranked by criticality
    [[ ]] Most critical asset is identified

**Threats:**

    [[ ]] At least 8 threats are documented
    [[ ]] Each threat is specific and actionable
    [[ ]] Threats are mapped to affected assets
    [[ ]] STRIDE categories were considered

**Prioritization:**

    [[ ]] Each threat has impact rating with justification
    [[ ]] Each threat has likelihood rating with justification
    [[ ]] Threats are sorted by priority

**Controls and Actions:**

    [[ ]] Top 5-10 threats have controls identified
    [[ ]] Each control has a specific owner
    [[ ]] Owners have accepted responsibility
    [[ ]] Evidence criteria are defined
    [[ ]] Deadlines are realistic

---

## Next Steps

### Your threat model is complete when:

1. [[ ]] You've shared the threat table with stakeholders
2. [[ ]] Owners have acknowledged their responsibilities
3. [[ ]] The first control implementation has started
4. [[ ]] You've scheduled the first follow-up review

**Remember:**
- A threat model that sits in a document is useless
- Start implementing critical controls immediately
- Update the threat model as you learn more
- Security is a process, not a one-time event

---

**Congratulations on completing your threat model!**

Use this same process whenever you build new systems, make significant changes, or need to clarify security priorities.

---

**Return to:** [Course Home](README.md)
