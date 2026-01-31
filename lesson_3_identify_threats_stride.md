<!--
author: SurvivalTrait Academy
email: contact@survivaltrait.academy
version: 1.0.0
language: en
narrator: US English Female

comment: Lesson 3 - Apply STRIDE to identify specific threats and avoid generic findings

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

# Lesson 3: Identify Threats Using STRIDE

**Lesson Duration:** 50-60 minutes  
**Format:** Self-paced reading + threat identification exercise

## Learning Objectives

After this lesson, you will:

- Apply STRIDE categories to identify specific threats
- Recognize when STRIDE doesn't fit
- Document threats clearly for non-security audiences
- Avoid generic threats that don't drive action

## Introduction

Once you know your system boundaries and assets, you need to identify what can go wrong.

STRIDE is a thinking tool that helps you ask the right questions. It's not a checklist you blindly apply.

This lesson teaches you how to use STRIDE effectively and when to look beyond it.

## What STRIDE Actually Is

STRIDE is a mnemonic for six categories of threats:

- **S**poofing: Pretending to be something you're not
- **T**ampering: Unauthorized modification
- **R**epudiation: Denying you did something
- **I**nformation Disclosure: Exposing data that should stay private
- **D**enial of Service: Making something unavailable
- **E**levation of Privilege: Gaining permissions you shouldn't have

Each category prompts specific questions about your system.

> **History:** STRIDE was created by Microsoft for software threat modeling. It works well for systems with clear boundaries, authentication, and data flows.

### When STRIDE Works Well

- [X] Systems with authentication and authorization
- [X] Software applications with clear boundaries
- [X] Systems that process or store data
- [X] Network-connected services

### When STRIDE Works Less Well

- [ ] Physical security threats
- [ ] Supply chain risks
- [ ] Social engineering that doesn't touch your system
- [ ] Business logic flaws that don't fit the categories

**Key Point:** Use STRIDE as a starting point. Don't force every threat into these six boxes.

## Applying STRIDE to Trust Boundaries

The most effective way to use STRIDE: **Apply each category to each trust boundary** you identified in Lesson 2.

### Template Questions for Each Boundary:

**Spoofing:**  
Can something on the untrusted side pretend to be something on the trusted side? How would you know if it did?

**Tampering:**  
Can data or commands crossing this boundary be modified in transit? Can someone change data they shouldn't have access to?

**Repudiation:**  
If something bad happens at this boundary, can you prove who did it and when? What if logs are deleted?

**Information Disclosure:**  
Can data crossing this boundary be observed by unauthorized parties? Can error messages leak information?

**Denial of Service:**  
Can someone flood this boundary to make the system unavailable? What rate limits exist?

**Elevation of Privilege:**  
Can someone cross this boundary and gain higher permissions than they should have?

> **Important:** Not every category produces a threat for every boundary. That's fine.

## Example: Applying STRIDE to "Internet to API Gateway"

**Boundary:** Internet to API Gateway  
**What crosses:** HTTP requests with JSON payloads, JWT tokens

### Spoofing Threats:

- Threat: Attacker presents a forged JWT token to impersonate a legitimate user
- Threat: Attacker spoofs the source IP to bypass IP-based rate limiting

### Tampering Threats:

- Threat: Man-in-the-middle attacker modifies request payload before it reaches the API
- Threat: Attacker tampers with JWT claims to change their user role

### Repudiation Threats:

- Threat: Attacker performs malicious actions but logs don't capture enough detail to identify them
- Threat: Legitimate user claims they didn't make a request that actually came from their account

### Information Disclosure Threats:

- Threat: API error messages reveal internal server structure or database schema
- Threat: Verbose logging exposes sensitive request data in centralized logs

### Denial of Service Threats:

- Threat: Attacker floods API with requests to exhaust connection pool
- Threat: Attacker sends computationally expensive requests to overload processing

### Elevation of Privilege Threats:

- Threat: API gateway misconfiguration allows access to admin endpoints without proper role check
- Threat: JWT validation bug allows attacker to craft token with elevated permissions

**Notice:** These are specific, not generic. "API could be attacked" isn't a threat. "Attacker floods API with requests to exhaust connection pool" is a threat.

## Documenting Threats Clearly

Each threat needs enough detail to decide if it's worth addressing.

### Minimum Information Per Threat:

```
Threat ID: T-001
Category: Spoofing
Description: Attacker presents a forged JWT token to impersonate a legitimate user
Affected Asset: User authentication tokens
Trust Boundary: Internet to API Gateway
Attack Prerequisites: 
- Knowledge of JWT structure
- Ability to send HTTP requests
- If JWT secret is weak: brute force or stolen secret
Current Controls: 
- JWT signature validation
- Short token expiration (15 minutes)
```

You'll add impact, likelihood, and additional controls in Lesson 4. For now, focus on clarity.

## Avoiding Generic Threats

**Test your threat specificity:**

**Which is a better threat statement?**

    [( )] "System could be hacked"
    [(X)] "Attacker could exploit SQL injection in search endpoint to extract customer data"
***
**Explanation:** The second statement includes: Actor (Attacker) + Action (exploit SQL injection) + Mechanism (in search endpoint) + Impact (extract customer data). This is specific enough to act on.
***

### Pattern for Good Threats:

**Actor + Action + Mechanism + Impact**

**Examples:**

❌ Bad: "Insider threat"  
✅ Good: "Employee with database access could export customer PII without detection because query logging is disabled"

❌ Bad: "DDoS attack"  
✅ Good: "Attacker sends 10,000 requests per second to login endpoint, exhausting database connections and preventing legitimate logins"

❌ Bad: "Data breach"  
✅ Good: "Attacker exploits unpatched vulnerability in file upload to execute code and exfiltrate customer records"

**If you can't describe the mechanism, you probably don't understand the threat well enough yet.**

## When STRIDE Isn't Enough

STRIDE won't catch:

### Business Logic Flaws

**Example:** Attacker exploits race condition to apply a discount code multiple times.

This is tampering-adjacent but requires business context to identify.

### Supply Chain Threats

**Example:** Compromised dependency introduces backdoor.

This doesn't cross your system boundaries as designed.

### Data Retention Violations

**Example:** System keeps customer data longer than legally allowed.

This is compliance risk, not a STRIDE category.

### Configuration Drift

**Example:** Firewall rule accidentally opens port to internet.

This is operational risk.

### For These, You Supplement STRIDE With:

- [X] Business logic review
- [X] Dependency analysis
- [X] Compliance mapping
- [X] Architecture review

**Don't let STRIDE create blind spots. It's a tool, not a religion.**

## Practice Exercise

Use the system and boundaries you defined in Lesson 2.

### Instructions:

Pick **one trust boundary**. Apply STRIDE:

**1. Write at least one specific threat for each STRIDE category**

    [[_______________________________________]]

**S**poofing threat:

    [[_______________________________________]]

**T**ampering threat:

    [[_______________________________________]]

**R**epudiation threat:

    [[_______________________________________]]

**I**nformation Disclosure threat:

    [[_______________________________________]]

**D**enial of Service threat:

    [[_______________________________________]]

**E**levation of Privilege threat:

**2. For each threat, could a non-security person understand what it means?**

    [[ ]] Yes, all threats are clear
    [[ ]] Most threats are clear
    [[ ]] Some need more detail
    [[ ]] I need to revise them

**3. Time spent:** Aim for 30 minutes. You should produce 4-6 well-documented threats for one boundary.

## Knowledge Check

**What makes a threat statement specific enough to act on?**

    [[ ]] It uses technical security jargon
    [(X)] It describes the actor, action, mechanism, and impact
    [[ ]] It's at least three paragraphs long
    [[ ]] It references a CVE number
***
**Explanation:** A good threat statement includes Actor + Action + Mechanism + Impact. This gives you enough detail to assess the threat and decide on controls, without unnecessary complexity.
***

**When should you supplement STRIDE with other analysis methods?**

    [[X]] When analyzing business logic flaws
    [[ ]] Never - STRIDE covers everything
    [[X]] When reviewing supply chain risks
    [[X]] When checking compliance requirements
***
**Explanation:** STRIDE is excellent for system-level threats but doesn't capture business logic issues, supply chain risks, or compliance violations. Use additional analysis methods for these areas.
***

**True or False: Every trust boundary should have at least one threat in each STRIDE category.**

    [( )] True
    [(X)] False
***
**Explanation:** Not every STRIDE category applies to every boundary. It's fine if a boundary has no Repudiation threats, for example. Force-fitting threats into categories creates busywork, not security.
***

## Key Takeaways

- STRIDE helps you ask structured questions about threats
- Apply STRIDE to each trust boundary, not to the system as a whole
- Specific threats drive action; generic threats create busywork
- Document enough detail for someone else to understand the risk
- STRIDE isn't complete; supplement it when needed

---

**Previous:** [Define the System and Draw Boundaries](lesson_2_define_system_boundaries.md)  
**Next:** [Prioritize Using Impact and Likelihood](lesson_4_prioritize_impact_likelihood.md)  
**Return to:** [Course Home](README.md)
