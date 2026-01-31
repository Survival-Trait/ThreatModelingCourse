<!--
author: SurvivalTrait Academy
email: contact@survivaltrait.academy
version: 1.0.0
language: en
narrator: US English Female

comment: Hands-on lab - Apply the complete threat modeling workflow to a CI/CD pipeline

@style
.lia-toc__bottom {
    display: none;
}
h2 {
    border-left: 4px solid #e91e63;
    padding-left: 10px;
}
.lab-task {
    background-color: #f5f5f5;
    padding: 15px;
    border-left: 4px solid #e91e63;
    margin: 10px 0;
}
@end

-->

# Lab: Threat Model a Development Pipeline

**Lab Duration:** 2-3 hours  
**Format:** Guided exercise with deliverables

## Lab Objectives

Apply the minimal viable threat modeling workflow to a realistic system. You will:

- Define scope and trust boundaries
- Identify threats using STRIDE
- Prioritize threats by impact and likelihood
- Map controls and owners
- Produce a complete threat table and action plan

## Scenario

You're the security lead for a small development team (8 people) building a SaaS application. Your manager has asked you to threat model the CI/CD pipeline after a competitor experienced a supply chain compromise.

The team uses GitHub for source control, GitHub Actions for CI/CD, and deploys containerized applications to AWS ECS. They're moving fast and haven't done formal security review of the pipeline.

**You have 2 weeks to deliver findings and 1 month to implement critical controls.**

## System Description

### Components In Scope:

**Source Control:**
- GitHub repository (private)
- Branch protection enabled on main branch
- Required pull request reviews (1 approver)
- 8 developers with write access
- GitHub Actions bot with repo admin permissions

**CI/CD Pipeline:**
- GitHub Actions workflows triggered on push to any branch
- Workflows run in GitHub-hosted runners (Ubuntu latest)
- Workflows build Docker images, run tests, push to AWS ECR
- Deployment workflow runs when PR is merged to main
- Secrets stored in GitHub Secrets

**Deployment Target:**
- AWS ECS Fargate clusters (production and staging)
- ECS tasks pull images from private ECR repository
- ECS tasks run with IAM roles for AWS resource access
- Application serves customer data via API

**Third-Party Dependencies:**
- npm packages (package.json with ~40 dependencies)
- Docker base images from Docker Hub
- GitHub Actions marketplace actions (5 different actions in use)

**Out of Scope:**
- Application code vulnerabilities (separate review)
- AWS account-level security (managed by platform team)
- Developer workstation security (managed by IT)

## Lab Task 1: Define Boundaries

Document the system using the text-based boundary template from Lesson 2.

### Questions to answer:

**1. What are the trust boundaries in this pipeline?**

    [[___________________________________________]]

List at least 4 trust boundaries:

**2. What crosses each boundary?**

    [[___________________________________________]]

For each boundary, describe what crosses:

**3. What are the most critical assets in this system?**

    [[___________________________________________]]

List critical assets and why they matter:

### Deliverable: 

Write at least 4 trust boundaries and create an asset table.

**Example boundaries to consider:**
- Developer workstation to GitHub repository
- GitHub Actions runner to source code
- CI/CD pipeline to AWS ECR
- ECR to ECS production environment
- GitHub Secrets to CI/CD workflows
- Third-party actions to repository
- npm registry to build process

## Lab Task 2: Identify Threats

Apply STRIDE to at least 3 of your trust boundaries.

### Requirements:

- Minimum 10 total threats across all boundaries
- At least one threat from each STRIDE category somewhere in your analysis
- Each threat must include: ID, category, description, affected asset, prerequisites, current controls

### Your Threats:

**Threat 1:**

    [[___________________________________________]]

ID, Category, Description:

**Threat 2:**

    [[___________________________________________]]

ID, Category, Description:

**Threat 3:**

    [[___________________________________________]]

ID, Category, Description:

**[Continue for Threats 4-10]**

### Deliverable: 

Create threat documentation for 10+ threats.

**Hint - Example threat:**

```
Threat ID: T-001  
Category: Tampering  
Description: Attacker compromises developer's GitHub account and pushes malicious code 
directly to a feature branch, which then gets merged to main via PR approval from 
another compromised or social-engineered account  
Affected Asset: Source code repository, deployed application  
Trust Boundary: Developer workstation to GitHub repository  
Attack Prerequisites:
- Compromised developer credentials (phishing, credential stuffing)
- Second developer approves malicious PR (social engineering or also compromised)
Current Controls:
- Required PR review (1 approver)
- Branch protection on main
```

## Lab Task 3: Prioritize Threats

For each threat you identified:

1. Assess impact (High/Medium/Low) with justification
2. Assess likelihood (High/Medium/Low) with justification
3. Determine priority (Critical/High/Medium/Low)

### Your Threat Table:

| Threat ID | Description | Impact | Likelihood | Priority | Justification |
|-----------|-------------|--------|------------|----------|---------------|
| T-001 | | | | | |
| T-002 | | | | | |
| T-003 | | | | | |
| T-004 | | | | | |
| T-005 | | | | | |

### Deliverable: 

Create a threat table with all threats sorted by priority.

**Consider these impact factors:**

**High impact scenarios:**
- Malicious code deployed to production serving customer data
- AWS credentials leaked allowing account takeover
- Supply chain compromise affecting all customers
- Source code exfiltration containing trade secrets

**Medium impact scenarios:**
- Temporary denial of deployments
- Exposure of non-sensitive configuration
- Delayed detection of security issues

**Low impact scenarios:**
- Information disclosure about build process
- Minor workflow disruption

## Lab Task 4: Map Controls

For the top 5 highest-priority threats:

1. List existing controls
2. Identify needed controls (preventive, detective, corrective)
3. Assign realistic owners (use roles: Dev Team Lead, DevOps Engineer, Security Lead, Engineering Manager)
4. Write evidence criteria

### Your Action Plan:

**Top Threat 1:**

    [[___________________________________________]]

Threat description:

    [[___________________________________________]]

Existing controls:

    [[___________________________________________]]

Needed controls:

    [[___________________________________________]]

Owner and deadline:

    [[___________________________________________]]

Evidence criteria:

**[Repeat for Top Threats 2-5]**

### Deliverable: 

Create an action plan table for your top 5 threats.

**Hint - Example control mapping:**

```
Threat: Malicious npm package introduced as dependency  
Existing controls:
- Package-lock.json pins versions
- Dependabot alerts enabled

Needed controls:
- Preventive: npm audit in CI pipeline (fail build on high/critical)
- Preventive: Require SRI hashes for external scripts
- Detective: Weekly dependency review by security lead
- Corrective: Incident response plan for supply chain compromise

Owner: Dev Team Lead (preventive controls), Security Lead (detective controls)

Evidence:
- CI pipeline job shows npm audit step
- Recent build logs show audit execution
- Security lead has calendar event for weekly review
- Incident response plan document includes supply chain section
```

## Lab Task 5: Produce Final Deliverables

Compile your work into two documents:

### 1. Threat Model Summary (1-2 pages)

**Contents:**
- System scope
- Key trust boundaries
- Asset inventory
- Top 5 threats with business impact description
- Risk acceptance statement for low-priority threats

### 2. Action Plan

**Contents:**
- Complete threat table (all threats, prioritized)
- Action plan table (top 5-10 threats with controls, owners, deadlines, evidence)
- Assumptions and limitations
- Recommended review frequency

### Deliverable: 

Two documents ready to share with your engineering manager.

## Review Checklist

Before completing your lab, verify:

- [ ] You defined at least 4 trust boundaries with clear descriptions
- [ ] Your asset table ranks criticality with justification
- [ ] You identified at least 10 specific threats (not generic)
- [ ] Each threat has impact and likelihood ratings with reasoning
- [ ] Your threat table is sorted by priority
- [ ] Top 5 threats have controls, owners, and evidence criteria
- [ ] Your action plan has realistic deadlines (2-4 weeks for critical)
- [ ] Deliverables are clear enough for a non-security stakeholder to understand

## Extension Activities

If you complete the core lab, try these:

**1. Add detective controls:**  
For your top 5 threats, identify what logs or alerts would indicate the threat is being exploited.

**2. Threat model a change:**  
Assume the team wants to add a new third-party static analysis tool to the pipeline. What new threats does that introduce?

**3. Create a review schedule:**  
Propose a schedule for reviewing and updating this threat model. What events would trigger an unscheduled review?

**4. Present findings:**  
Create a 5-slide presentation explaining your top 3 threats to non-technical stakeholders.

---

**Congratulations on completing the lab!**

You've now applied the complete threat modeling workflow to a realistic system. Use this same process for any system you're responsible for securing.

---

**Previous:** [Map Controls and Owners](lesson_5_map_controls_owners.md)  
**Next:** [Student Workbook](workbook_threat_modeling.md)  
**Return to:** [Course Home](README.md)
