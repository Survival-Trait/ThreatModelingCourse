<!--
author: SurvivalTrait Academy
email: contact@survivaltrait.academy
version: 1.0.0
language: en
narrator: US English Female

comment: Final Assessment - 12 scenario-based questions to validate threat modeling knowledge

@style
.lia-toc__bottom {
    display: none;
}
@end

-->

# Threat Modeling Foundations - Final Quiz

**Total Questions:** 12  
**Passing Score:** 9 correct (75%)  
**Time Limit:** 30 minutes (suggested)

## Instructions

Select the best answer for each question. Most questions present realistic scenarios requiring you to apply threat modeling principles.

---

## Question 1: Trust Boundary Analysis

You're threat modeling a new mobile app that stores user photos locally on the device and syncs them to a cloud backend. Which of the following is the MOST important trust boundary to analyze first?

    [( )] A) The network boundary between the mobile app and the internet
    [( )] B) The boundary between the mobile app and the device's photo library
    [(X)] C) The boundary between authenticated users and unauthenticated users in the cloud backend
    [( )] D) The boundary between the mobile app process and other apps on the device
***
**Explanation:** The boundary between authenticated and unauthenticated users in the cloud backend is most critical because it controls access to all user data. If this boundary fails, attackers could access any user's photos. While all boundaries matter, this one has the highest potential impact.
***

## Question 2: Threat Specificity

A developer tells you: "Our API could be hacked." Which response demonstrates proper threat modeling?

    [( )] A) "You're right, we should implement a WAF immediately."
    [(X)] B) "Can you be more specific? What attack mechanism are you concerned about, and what asset would be affected?"
    [( )] C) "That's a generic statement. APIs are always at risk, but we have firewalls."
    [( )] D) "We'll add that to the threat table as a high-priority item."
***
**Explanation:** Effective threat modeling requires specific, actionable threats. Asking for the attack mechanism and affected asset helps transform a vague concern into something you can analyze and address. Option A jumps to a solution without understanding the threat. Option C dismisses valid concern. Option D documents a generic threat that won't drive useful action.
***

## Question 3: STRIDE Classification

You've identified a threat where an attacker could inject malicious JavaScript into user profile fields that execute when other users view the profile. Using STRIDE, which category does this threat belong to?

    [( )] A) Spoofing
    [( )] B) Tampering
    [( )] C) Information Disclosure
    [(X)] D) Elevation of Privilege
***
**Explanation:** This describes a stored cross-site scripting (XSS) attack, which allows the attacker to execute code in the context of another user's session, potentially gaining their privileges. This is Elevation of Privilege. Tampering (B) might seem correct because data is being modified, but the primary threat is the privilege escalation when the script executes.
***

## Question 4: Prioritization Strategy

Your threat table shows: 10 Critical, 15 High, 22 Medium, and 8 Low priority threats. Your manager asks what to do. What's the most defensible response?

    [( )] A) "We need to address all 55 threats before launch."
    [(X)] B) "We'll focus on the 10 Critical threats immediately, plan the 15 High threats for next sprint, and defer Medium/Low threats for now."
    [( )] C) "With this many threats, we should redesign the entire system."
    [( )] D) "These numbers suggest we're overthinking it. Let's reduce each category by half."
***
**Explanation:** Effective threat modeling means prioritization and realistic action plans. Addressing critical threats immediately while planning for high-priority threats is defensible. Option A is unrealistic and creates analysis paralysis. Option C is an overreaction. Option D arbitrarily dismisses valid findings.
***

## Question 5: Likelihood Assessment

You're assessing the likelihood of a SQL injection attack against a public-facing search feature. The application uses string concatenation to build queries. What likelihood rating is most appropriate?

    [( )] A) Low - SQL injection requires advanced skills
    [( )] B) Medium - It's possible but the search feature isn't heavily used
    [(X)] C) High - SQL injection is easy to exploit and commonly attempted
    [( )] D) Medium - The application has a firewall
***
**Explanation:** SQL injection against string concatenation is trivial to exploit (automated scanners find it), commonly attempted, and requires minimal skill. This clearly rates as High likelihood. Option A is incorrect; SQL injection is well-understood and easy. Option B incorrectly factors usage into likelihood. Option D shows a misunderstanding; a network firewall doesn't prevent SQL injection.
***

## Question 6: Action Plan Quality

Your action plan lists: "Engineering team will implement input validation." Why is this problematic as written?

    [( )] A) Input validation is a detective control, not preventive
    [(X)] B) It lacks a specific owner, deadline, and evidence criteria
    [( )] C) The engineering team doesn't have security expertise
    [( )] D) Input validation isn't an appropriate control for most threats
***
**Explanation:** "Engineering team" is too vague (which engineer?), there's no deadline (when?), and no evidence criteria (how do you prove it's done?). Without these, the control won't get implemented. Option A is incorrect; input validation is preventive. Option C makes an unfounded assumption. Option D is incorrect; input validation is fundamental.
***

## Question 7: Risk Acceptance

During threat modeling, you discover that the cloud provider controls the underlying hypervisor security. The team cannot implement additional controls. What should you do?

    [( )] A) Mark this as a Critical threat requiring immediate action
    [( )] B) Demand that the team migrate to a different provider with more control
    [(X)] C) Document this as an accepted risk after verifying the provider's security attestations
    [( )] D) Remove this from the threat model since it's outside your control
***
**Explanation:** When you can't implement controls (third-party managed infrastructure), you document the risk acceptance with appropriate due diligence (verifying provider attestations). Option A is inappropriate; you can't address what you don't control. Option B may not be feasible. Option D is dangerous; accepted risks should still be documented.
***

## Question 8: Evidence Criteria

A threat model states: "Control: Enable detailed logging. Evidence: Logging is turned on." What's the problem with this evidence criteria?

    [( )] A) Logging is a detective control and shouldn't require evidence
    [(X)] B) It doesn't specify what logs should contain, retention period, or how to verify
    [( )] C) Evidence criteria should only be defined after implementation
    [( )] D) Logging creates too much data and isn't practical to verify
***
**Explanation:** Good evidence criteria are specific and verifiable. "Logging is turned on" doesn't define what's being logged, how long it's retained, or how you verify it's working. Option A is incorrect; all controls need evidence. Option C is backwards. Option D is defeatist and irrelevant.
***

## Question 9: Impact Assessment

You're threat modeling a system that handles medical records. Impact assessment for "unauthorized access to patient data" should primarily consider:

    [( )] A) The number of patients affected
    [(X)] B) HIPAA violation fines, patient notification costs, and reputational damage
    [( )] C) Whether the attacker is internal or external
    [( )] D) The technical difficulty of the attack
***
**Explanation:** Impact assessment focuses on business consequences. For healthcare data, regulatory fines, mandatory breach notification, and reputation damage are the primary impacts. Option A is a factor but not primary. Options C and D affect likelihood, not impact.
***

## Question 10: When to Threat Model

Your team is building a new feature for an existing application. The project manager asks if you need to threat model it. When is threat modeling most justified?

    [( )] A) Always - every code change requires a full threat model
    [( )] B) Only if the feature handles sensitive data
    [(X)] C) If the feature introduces new trust boundaries or significantly changes existing ones
    [( )] D) Never - the application was already threat modeled
***
**Explanation:** Threat model when changes introduce new risks (new trust boundaries) or significantly alter existing risk profiles. This is proportional to the change. Option A wastes resources. Option B is too narrow. Option D is wrong; threat models must evolve with the system.
***

## Question 11: STRIDE Application

A database administrator has read access to all customer data. Using STRIDE, you identify: "DBA could export customer PII without detection." This is an example of which threat category?

    [( )] A) Spoofing - the DBA is pretending to have legitimate need
    [(X)] B) Repudiation - the DBA could deny exporting the data
    [( )] C) Information Disclosure - customer data is exposed
    [( )] D) Elevation of Privilege - the DBA is gaining unauthorized access
***
**Explanation:** The threat is "without detection," meaning the DBA could deny doing it (repudiation). The DBA already has legitimate access, so this isn't Spoofing (A) or Elevation of Privilege (D). While data does get disclosed (C), the primary security concern is the inability to prove the action occurred.
***

## Question 12: Living Documents

Six months after completing your threat model, a new ransomware variant targets your industry. Your threat model didn't include ransomware. What should you do?

    [( )] A) Nothing - threat models are point-in-time documents
    [( )] B) Start over with a completely new threat model
    [(X)] C) Add ransomware as a new threat, assess it, and update your action plan
    [( )] D) Wait until the next scheduled review to incorporate it
***
**Explanation:** Threat models are living documents. When the threat landscape changes, update your model to address new risks. Option A treats threat models as static, which is dangerous. Option B wastes previous work. Option D delays addressing an active, relevant threat.
***

---

## Scoring

**How many did you get correct?**

    [[___]]

**Enter your score (0-12):**

**Scoring Guidance:**

- **12 correct:** Excellent - You demonstrate strong threat modeling fundamentals
- **10-11 correct:** Good - You understand core concepts with minor gaps
- **9 correct:** Passing - You grasp the basics but should review areas you missed
- **Below 9:** Needs improvement - Review lesson materials and retake the quiz

---

**Congratulations on completing the quiz!**

If you passed, you're ready to apply these skills to real systems.

If you didn't pass this time, review the lesson materials and try again. The concepts become clearer with practice.

---

**Return to:** [Course Home](README.md)
