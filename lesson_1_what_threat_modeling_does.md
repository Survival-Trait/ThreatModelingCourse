<!--
author: SurvivalTrait Academy
email: contact@survivaltrait.academy
version: 1.0.0
language: en
narrator: US English Female

comment: Lesson 1 - Understanding what threat modeling produces and when to use it

@style
.lia-toc__bottom {
    display: none;
}
@end

-->

# Lesson 1: What Threat Modeling Actually Does

**Lesson Duration:** 30-40 minutes  
**Format:** Self-paced reading + reflection prompts

## Learning Objectives

After this lesson, you will:

- Understand what threat modeling produces and why
- Recognize when threat modeling adds value vs. creates busywork
- Explain the minimal viable workflow to a colleague

## Introduction

Threat modeling answers one question: **What can go wrong with this system, and what should we do about it?**

That's it. Everything else is technique.

You don't need expensive tools. You don't need a certification. You need a structured way to think about risk before someone exploits it.

This lesson explains what threat modeling produces, when to use it, and when to skip it.

## What Threat Modeling Produces

A usable threat model creates three things:

### 1. A threat table

A list of specific bad things that could happen, ranked by priority, with controls and owners identified.

### 2. An action plan

Clear next steps with evidence criteria for "done."

### 3. Shared understanding

Everyone involved knows what you're protecting and why certain risks matter more than others.

> **Key Point:** If your threat model doesn't produce these three things, it's academic exercise, not operational security.

## Common Misconceptions

Let's address some common misunderstandings about threat modeling:

**"Threat modeling is only for large enterprises."**

    [[X]] False
    [[ ]] True
***
**Explanation:** Small teams and solo developers benefit most because they can't afford to waste effort on the wrong defenses.
***

**"You need security expertise to threat model."**

    [[ ]] True
    [[X]] Partly false
***
**Explanation:** You need system knowledge more than security knowledge. A developer who knows the codebase can identify threats a security consultant would miss.
***

**"Threat modeling happens once at the start of a project."**

    [[X]] False
    [[ ]] True
***
**Explanation:** Systems change. Threats evolve. Threat models are living documents.
***

**"The goal is to find every possible threat."**

    [[X]] False
    [[ ]] True
***
**Explanation:** The goal is to find the threats worth addressing with your available resources. Perfection is the enemy of usable security.
***

## The Minimal Viable Workflow

Here's the process this module teaches:

``` ascii
┌─────────────────────────────────────────┐
│  Step 1: Define system and assets      │
│  What are you protecting?               │
└──────────────┬──────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────┐
│  Step 2: Draw trust boundaries          │
│  Where does control change?             │
└──────────────┬──────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────┐
│  Step 3: Identify threats               │
│  Use STRIDE as starting lens            │
└──────────────┬──────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────┐
│  Step 4: Prioritize                     │
│  Impact + Likelihood = Priority         │
└──────────────┬──────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────┐
│  Step 5: Map controls and owners        │
│  Who is responsible for what?           │
└──────────────┬──────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────┐
│  Step 6: Action plan and evidence       │
│  How do you prove it's done?            │
└─────────────────────────────────────────┘
```

**Each step produces a deliverable.** No step requires more than 2 hours for a typical small system.

## When to Skip Threat Modeling

Threat modeling adds value when:

- [X] You're building something new
- [X] You're changing something critical
- [X] You're unsure where to focus limited security resources
- [X] You need to explain risk to non-security stakeholders

Skip threat modeling when:

- [ ] The system is already decommissioned
- [ ] You're following a well-established secure pattern with no variations
- [ ] The risk is already understood and documented
- [ ] You have zero ability to implement controls

> **Important:** If you can't act on the findings, don't waste time creating them.

## Reflection Prompts

Before moving to the next lesson, answer these:

    [[___]]

**1. Think of a system you're familiar with. What would you be protecting in a threat model?**

***
Consider data, functionality, and infrastructure components. What would cause the most damage if compromised?
***

    [[___]]

**2. What's one security decision you've made without a formal process? Would threat modeling have changed it?**

***
Reflect on whether structured thinking would have revealed risks you missed or helped you communicate the decision better.
***

    [[___]]

**3. Who in your organization needs to understand threat findings for them to be useful?**

***
Think about who has the authority to implement controls and who needs to accept risks.
***

## Knowledge Check

**What are the three things a usable threat model must produce?**

    [[X]] A threat table
    [[ ]] A network diagram
    [[X]] An action plan
    [[ ]] A compliance checklist
    [[X]] Shared understanding
    [[ ]] A risk register
***
**Answer:** A threat table, an action plan, and shared understanding. The other options may be helpful but aren't core deliverables.
***

**When should you skip threat modeling?**

    [[ ]] When building something new
    [[X]] When you have zero ability to implement controls
    [[ ]] When you're unsure where to focus security resources
    [[ ]] When explaining risk to stakeholders
***
**Answer:** If you can't act on findings, threat modeling becomes busywork rather than operational security.
***

## Key Takeaways

- Threat modeling produces a threat table, action plan, and shared understanding
- You don't need perfect knowledge or expensive tools
- The goal is defensible decisions, not exhaustive lists
- Skip threat modeling when you can't act on findings

---

**Next Lesson:** [Define the System and Draw Boundaries](lesson_2_define_system_boundaries.md)

**Return to:** [Course Home](README.md)
