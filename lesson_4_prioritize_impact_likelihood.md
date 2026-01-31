<!--
author: SurvivalTrait Academy
email: contact@survivaltrait.academy
version: 1.0.0
language: en
narrator: US English Female

comment: Lesson 4 - Assess threat impact and likelihood to create defensible priority rankings

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

# Lesson 4: Prioritize Using Impact and Likelihood

**Lesson Duration:** 40-50 minutes  
**Format:** Self-paced reading + prioritization exercise

## Learning Objectives

After this lesson, you will:

- Assess threat impact using business language
- Estimate likelihood without perfect information
- Create defensible priority rankings
- Avoid analysis paralysis

## Introduction

You've identified threats. Now you have to decide which ones matter most.

You can't fix everything. You have limited time, limited budget, limited attention. Prioritization determines where those resources go.

This lesson teaches a simple impact and likelihood model that produces defensible decisions without drowning you in spreadsheets.

## Why Simple Prioritization Works

Complex risk matrices with 5x5 grids and numerical scoring feel rigorous. They're often theater.

**The truth:** The difference between a "3.2" and a "3.4" risk score is imaginary precision. You're guessing either way.

### What Actually Works:

- Three levels of impact: High, Medium, Low
- Three levels of likelihood: High, Medium, Low
- Clear definitions for each level
- Willingness to say "I don't know" when you don't

**The goal is not mathematical perfection. The goal is defensible triage.**

## Assessing Impact

Impact answers: **What happens if this threat is realized?**

Use business language, not security jargon.

### High Impact:

- Significant financial loss (quantify if possible)
- Regulatory violation with fines or legal action
- Loss of critical business function for extended period
- Widespread data breach affecting many customers
- Irreparable reputational damage
- Safety risk to people

### Medium Impact:

- Moderate financial loss
- Temporary service degradation
- Limited data exposure (small number of records or non-sensitive data)
- Regulatory concern but not immediate violation
- Reputational damage that can be managed

### Low Impact:

- Minimal financial loss
- Brief inconvenience to small number of users
- Exposure of non-sensitive information
- No regulatory implications
- Minimal reputational risk

### Example Ratings:

**Threat:** Attacker extracts all customer email addresses and payment tokens  
**Impact: High** (PCI violation, regulatory fines, customer notification requirements, reputational damage)

**Threat:** Attacker causes API to return 503 errors for 10 minutes  
**Impact: Medium** (temporary revenue loss, customer frustration, but recoverable)

**Threat:** Attacker views server version in HTTP headers  
**Impact: Low** (information disclosure but minimal direct harm)

> **Decision Test:** When in doubt, imagine explaining the impact to your CEO or a customer. How would they react?

## Estimating Likelihood

Likelihood answers: **How probable is this threat given current conditions?**

You're estimating, not calculating. You don't have perfect data. That's fine.

### High Likelihood:

- Attack is easy to execute (low skill, readily available tools)
- Attack has been observed against similar systems
- Target is highly valuable or politically motivated
- No controls currently in place
- Similar vulnerabilities exist and are actively exploited

### Medium Likelihood:

- Attack requires moderate skill or specific conditions
- Attack is theoretically possible but not commonly observed
- Some controls exist but have known gaps
- Target is moderately attractive

### Low Likelihood:

- Attack requires advanced skill or rare conditions
- No known instances of this attack pattern
- Strong controls already in place
- Target is not particularly attractive
- Attack would be easily detected

### Example Ratings:

**Threat:** SQL injection in public-facing search field  
**Likelihood: High** (common attack, automated scanners find these, easy to exploit)

**Threat:** Insider with database access exports customer data  
**Likelihood: Medium** (requires malicious insider, some detective controls exist, but technically easy)

**Threat:** Nation-state actor compromises air-gapped backup system  
**Likelihood: Low** (requires advanced capability and motivation, strong isolation controls)

### Consider:

- [X] Attacker skill required
- [X] Accessibility of target
- [X] Attractiveness of target
- [X] Existing controls
- [X] Historical precedent

## Creating the Priority Matrix

Combine impact and likelihood:

``` ascii
                    LIKELIHOOD
                Low     Medium    High
        High     M        H        C
IMPACT  Medium   L        M        H
        Low      L        L        M

C = Critical (address immediately)
H = High (address soon)
M = Medium (address when feasible)
L = Low (accept or defer)
```

### Critical (High Impact + High Likelihood):

These are your "the building is on fire" threats. Drop everything else and address these.

### High Priority:

- High Impact + Medium Likelihood
- Medium Impact + High Likelihood

Address these in your next sprint or planning cycle. Don't let them drift.

### Medium Priority:

All other combinations except Low/Low. Address these as resources allow. Good candidates for future hardening work.

### Low Priority:

Low Impact + Low Likelihood. Document and accept. Revisit if conditions change.

## Avoiding Analysis Paralysis

You will be uncertain. That's normal.

### When you can't decide between Medium and High impact:

**Ask:** "Would I be fired if this happened?" If yes, it's High.

### When you can't decide between Medium and High likelihood:

**Ask:** "Has this happened to anyone in my industry in the last year?" If yes, it's High.

### When you're stuck:

Pick a rating and document your reasoning. You can change it later. **Indecision is worse than an imperfect decision.**

### When stakeholders disagree:

- The **business owner** makes the final call on impact
- The **security team** makes the final call on likelihood
- Document the disagreement if needed

## Building the Threat Table

Now you have everything you need to create the core deliverable.

### Threat Table Format:

| Threat ID | Description | Asset | Impact | Likelihood | Priority | Status |
|-----------|-------------|-------|--------|------------|----------|--------|
| T-001 | Attacker forges JWT token | Auth tokens | High | High | Critical | Open |
| T-002 | SQL injection in search | Customer DB | High | High | Critical | Open |
| T-003 | API DDoS exhausts connections | API service | Medium | High | High | Open |
| T-004 | Error messages leak schema | DB structure | Low | Medium | Medium | Open |
| T-005 | Verbose logs expose PII | Customer data | Medium | Low | Medium | Accepted |

**Sort by priority. Critical threats go at the top.**

This table becomes the basis for your action plan in Lesson 5.

## Stakeholder-Friendly Risk Language

When you present findings:

**Instead of:** "High likelihood of privilege escalation via JWT manipulation"  
**Say:** "An attacker could gain admin access by modifying their login token. This is common and easy to exploit. Impact would be full customer data access."

**Instead of:** "Critical STRIDE threat T-047 in trust boundary 3"  
**Say:** "Our top risk is someone injecting malicious code into the search feature to steal customer information. We've seen this attack against competitors. We need to fix it this month."

**Instead of:** "Low likelihood, low impact informational finding"  
**Say:** "This is a minor issue we're tracking but not addressing right now."

**Translate your threat table into language your audience understands.**

## Practice Exercise

Take the threats you documented in Lesson 3.

### For each threat:

**1. Assign an impact rating (High/Medium/Low) with justification:**

    [[_______________________________________]]

Threat 1 impact and why:

    [[_______________________________________]]

Threat 2 impact and why:

**2. Assign a likelihood rating (High/Medium/Low) with justification:**

    [[_______________________________________]]

Threat 1 likelihood and why:

    [[_______________________________________]]

Threat 2 likelihood and why:

**3. Determine priority using the matrix:**

    [[_______________________________________]]

Threat 1 priority:

**4. Create your threat table:**

Spend 20 minutes. You should have 4-6 prioritized threats.

## Knowledge Check

**What's the main advantage of using High/Medium/Low ratings instead of numerical scores?**

    [( )] It requires less mathematical ability
    [(X)] It avoids false precision and makes decisions faster
    [( )] It's easier to explain to executives
    [( )] It matches NIST standards
***
**Explanation:** While simplicity helps, the main advantage is avoiding false precision. The difference between a 3.2 and 3.4 risk score is meaningless when you're estimating anyway. High/Medium/Low forces clear, defensible decisions without analysis paralysis.
***

**A threat has High Impact and Medium Likelihood. What's the priority?**

    [( )] Critical
    [(X)] High
    [( )] Medium
    [( )] Low
***
**Explanation:** According to the matrix, High Impact + Medium Likelihood = High priority. Only High Impact + High Likelihood gets Critical priority.
***

**Who should make the final decision on impact ratings when there's disagreement?**

    [(X)] The business owner
    [( )] The security team
    [( )] The project manager
    [( )] Whoever has the most experience
***
**Explanation:** The business owner understands business consequences best and should make the final call on impact. The security team should make the final call on likelihood (technical probability). This separates concerns appropriately.
***

## Key Takeaways

- Simple prioritization is more useful than complex scoring
- Impact uses business language; likelihood considers current conditions
- Critical priorities get immediate action; low priorities get accepted
- Uncertainty is normal; document your reasoning and move forward
- Translate technical findings into stakeholder language

---

**Previous:** [Identify Threats Using STRIDE](lesson_3_identify_threats_stride.md)  
**Next:** [Map Controls and Owners](lesson_5_map_controls_owners.md)  
**Return to:** [Course Home](README.md)
