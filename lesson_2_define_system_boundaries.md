<!--
author: SurvivalTrait Academy
email: contact@survivaltrait.academy
version: 1.0.0
language: en
narrator: US English Female

comment: Lesson 2 - Learn to scope systems and identify trust boundaries that matter

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

# Lesson 2: Define the System and Draw Boundaries

**Lesson Duration:** 40-50 minutes  
**Format:** Self-paced reading + practice exercise

## Learning Objectives

After this lesson, you will:

- Scope a system for threat modeling
- Identify trust boundaries that matter
- Describe boundaries without diagrams
- List assets worth protecting

## Introduction

You can't threat model everything. You have to draw a line around what you're analyzing.

That line is called scope. Where data or control crosses that line, you have a trust boundary.

Getting scope and boundaries right determines whether your threat model is useful or useless.

This lesson teaches you how to make those decisions.

## Scoping Decisions That Matter

Start with these questions:

### What system are you analyzing?

Be specific. "Our web application" is too broad. "The customer-facing API and authentication flow" is scoped.

### What's in scope vs. out of scope?

List what you're analyzing and what you're explicitly not analyzing.

**Example:**
- **In scope:** API gateway, database, authentication service
- **Out of scope:** Payment processor (third-party managed), CDN (separate analysis)

### Why this scope?

You're building a new feature. You're responding to an incident. You're preparing for a compliance audit. The reason matters because it affects which threats you prioritize.

### What changes if this system fails?

Revenue loss. Data breach. Regulatory violation. Reputational damage. Service outage. Be concrete.

> **Action:** Write these answers down. They become the first section of your threat model document.

## Trust Boundaries vs. Network Boundaries

**Question: Are trust boundaries and network boundaries the same thing?**

    [( )] Yes, they're identical
    [(X)] No, they're different concepts
***
**Explanation:** A network boundary is where traffic crosses subnets or firewalls. A trust boundary is where data or control moves from a more trusted context to a less trusted context. They're related but not the same.
***

### Understanding the Difference

**Network boundary:** Where traffic crosses subnets or firewalls  
**Trust boundary:** Where privilege, data classification, or control changes

### Example 1: Internal Network Trust

Just because traffic stays inside your corporate network doesn't mean both endpoints are equally trusted. An HR system and a developer sandbox are both internal, but they don't trust each other the same way.

### Example 2: Process Boundaries

A web server running as root and a web server running as a limited service account represent a trust boundary, even on the same machine.

### Example 3: User Roles

Data shown to an authenticated admin vs. an authenticated regular user crosses a trust boundary, even in the same application session.

### Trust boundaries exist where:

- [X] Privilege levels change
- [X] Data classification changes
- [X] Ownership or control changes
- [X] Authentication or authorization is required

## Text-Based Boundary Descriptions

You don't need Visio or draw.io to document trust boundaries. Text works fine.

### Template:

```
System: [Name]
Scope: [What's included]

Trust Boundaries:
1. [Boundary name]: [Describe what's on each side and what crosses]
   - Trusted side: [Context, privilege level, assumptions]
   - Untrusted side: [Context, privilege level, assumptions]
   - What crosses: [Data, commands, credentials, etc.]
   
2. [Next boundary...]
```

### Example:

```
System: Customer Portal API
Scope: API gateway, authentication service, customer database

Trust Boundaries:
1. Internet to API Gateway
   - Trusted side: API gateway with TLS termination, rate limiting
   - Untrusted side: Any internet client
   - What crosses: HTTP requests with JSON payloads, JWT tokens
   
2. API Gateway to Database
   - Trusted side: Database with connection pooling, parameterized queries
   - Untrusted side: API gateway application code
   - What crosses: SQL queries, result sets, connection credentials
   
3. Regular User to Admin Functions
   - Trusted side: Admin role with elevated permissions
   - Untrusted side: Regular authenticated user
   - What crosses: Role-based access control checks, audit log writes
```

> **Key Point:** Notice that each boundary description tells you what could go wrong if the boundary fails.

## Asset Identification That Drives Decisions

Assets are things worth protecting. Not everything is an asset.

### Ask these questions:

**What data exists in this system?**

    [[___]]

List the data types (Customer PII, payment info, credentials, etc.):

**Which data matters most?**

Rank by impact if exposed, modified, or destroyed. "All data is important" is not helpful.

**What functionality exists?**

User authentication. Payment processing. Report generation. Admin controls.

**Which functions matter most?**

What would cause the most damage if broken or abused?

**What infrastructure enables this?**

Servers. Databases. Network connections. Third-party services. Code repositories.

**Which infrastructure is single-point-of-failure?**

What breaks everything else if it fails?

### Create a simple asset table:

| Asset | Type | Criticality | Why It Matters |
|-------|------|-------------|----------------|
| Customer email addresses | Data | High | PII, regulatory requirement, account recovery |
| Payment tokens | Data | Critical | PCI scope, fraud risk |
| Admin password reset function | Function | High | Account takeover vector |
| Database credentials | Infrastructure | Critical | Full data access if compromised |

**Criticality ratings:** Critical, High, Medium, Low. 

Use no more than four levels or you'll spend forever arguing about the difference between "medium-high" and "high-medium."

## Practice Exercise

Pick a system you know. It can be:

- [ ] A web application you've built
- [ ] A development pipeline you use
- [ ] A cloud environment you manage
- [ ] A network service you depend on

### Answer these questions in writing:

**1. What's in scope? What's out of scope?**

    [[___________________________________________]]

**2. List 3 trust boundaries using the text template above.**

    [[___________________________________________]]

**3. List 5 assets using the asset table format.**

    [[___________________________________________]]

**4. What's the single most critical asset and why?**

    [[___________________________________________]]

> **Time allocation:** Spend 20 minutes. This is the foundation your threat model builds on.

## Knowledge Check

**Which statement about trust boundaries is TRUE?**

    [( )] Trust boundaries only exist at network firewalls
    [(X)] Trust boundaries exist wherever privilege or control changes
    [( )] You can only have one trust boundary per system
    [( )] Trust boundaries are the same as data flows
***
**Explanation:** Trust boundaries exist wherever privilege levels, data classification, ownership, or control changes - which can happen at network edges, process boundaries, role transitions, and more.
***

**What's the appropriate level of detail for scoping?**

    [( )] "Our web application"
    [(X)] "The customer-facing API and authentication flow"
    [( )] "Everything in our data center"
    [( )] "The login button"
***
**Explanation:** "The customer-facing API and authentication flow" is specific enough to be actionable but not so narrow that you miss important context. Too broad ("web application") or too narrow ("login button") makes threat modeling less useful.
***

## Key Takeaways

- Scope determines whether your threat model is useful
- Trust boundaries are about privilege and control, not just networks
- Text descriptions work as well as diagrams
- Asset criticality drives threat prioritization
- Write it down or you'll forget your reasoning later

---

**Previous:** [What Threat Modeling Actually Does](lesson_1_what_threat_modeling_does.md)  
**Next:** [Identify Threats Using STRIDE](lesson_3_identify_threats_stride.md)  
**Return to:** [Course Home](README.md)
