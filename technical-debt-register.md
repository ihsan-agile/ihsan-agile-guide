# Technical Debt Register Guide

## Purpose

A Technical Debt Register is a structured, transparent system for documenting, tracking, and managing technical shortcuts in alignment with Islamic principles of disclosure, stewardship, and justice. This guide helps teams eliminate **jahalah** (ignorance) and prevent **ẓulm** (injustice) by ensuring all technical debt is visible and responsibly managed.

---

## Why a Technical Debt Register Matters

### The Islamic Principle

The Prophet Muhammad ﷺ said:

*"The Muslim is the brother of another Muslim, and it is not permissible for a Muslim to sell his brother goods in which there is a defect, without pointing that out to him."*  
— Sunan Ibn Mājah 2246

In software terms: **It's not permissible to pass code to your teammates (or users) with hidden defects.**

### The Problem It Solves

**Without a register:**
- Technical debt is hidden in // TODO comments scattered across the codebase
- Future maintainers don't know what's safe to change
- Users aren't aware of limitations
- The organisation has no visibility into total accumulated debt
- Shortcuts are taken and never addressed
- **Gharar** (harmful uncertainty) dominates the system

**With a register:**
- All technical debt is visible in one place
- Future maintainers can see the full picture before touching code
- Stakeholders can prioritise addressing debt
- Users are protected through disclosure requirements
- **Jahalah** (ignorance) is eliminated
- **Amānah** (trust) is upheld

---

## Core Components of a Technical Debt Entry

Each entry in the register should include:

### 1. Unique Identifier
- **Format:** `DEBT-XXX` (e.g., DEBT-042, DEBT-157)
- **Purpose:** Allows referencing in code, tickets, and discussions
- **Example in code comment:**
  ```javascript
  // DEBT-042: Using simplified algorithm that doesn't handle edge cases
  // See technical debt register for full details and mitigation plan
  ```

### 2. Creation Date & Creator
- **When:** Date the debt was introduced
- **Who:** Developer(s) who made the decision
- **Purpose:** Accountability and context for future discussions

### 3. Classification (Gharar Level)
Choose one:
- **Strategic** (Permissible - Mubāḥ): Conscious decision with full disclosure and concrete plan
- **Tactical** (Questionable - Makrūh): Pressure-driven, incomplete documentation, pattern emerging
- **Reckless** (Prohibited - Ḥarām): Undisclosed, no plan, deliberately concealed
- **Inherited** (Discovered): Found by current team, not created by them

### 4. Component/Module Affected
- **What:** Which part of the system contains this debt
- **Location:** File paths, functions, or modules
- **Example:** `src/calculations/zakat.js`, `UserAuthentication component`, `Database migration v.2.3`

### 5. Description of the Shortcut
**Be specific and honest:**

❌ **Bad:** "Quick fix for performance issue"

✅ **Good:** "Skipped input validation on authentication endpoint because emergency security patch needed deployment in 2 hours. Edge cases for international phone numbers not handled. SQL injection protection present but XSS sanitisation minimal."

### 6. Why It Was Taken (Necessity Assessment)
**Document the reasoning:**

- What was the business necessity?
- What deadline or constraint applied?
- What would have happened without the shortcut?
- Was there genuine **ḍarūrah** (necessity) or just convenience?

**Example:** "Critical security vulnerability discovered in production on Friday evening. Needed immediate hotfix to prevent data breach. Proper implementation would take 3 days; business couldn't wait. Temporary fix deployed to secure system while proper solution developed."

### 7. Known Limitations & Risks

**For internal stakeholders (team):**
- What doesn't work properly?
- What edge cases fail?
- What assumptions does the code make?
- What could break if someone changes related code?
- Performance implications?
- Security concerns?

**For external stakeholders (users):**
- How might users be affected?
- What scenarios will fail?
- What expectations might be violated?
- Could users be harmed or misled?

**Example:**
```
Internal risks:
- Calculation fails for income > $1M (assumes typical salary ranges)
- Doesn't handle cryptocurrency assets
- Performance degrades significantly with >100 transactions
- Not thread-safe (race condition possible under load)

External risks:
- Users with complex asset portfolios will get incorrect calculations
- High-income users may underpay zakat due to overflow bug
- Users with >100 transactions will experience slow load times
- Concurrent use by multiple family members may cause data corruption
```

### 8. Disclosure Status

**Internal disclosure:**
- [ ] Team members informed
- [ ] Product Owner consented
- [ ] Technical Lead/Architect reviewed
- [ ] Security/Compliance teams notified (if applicable)

**External disclosure (for user-facing features):**
- [ ] Limitations disclosed in user interface
- [ ] Documentation updated with caveats
- [ ] Support team briefed on limitations
- [ ] Users can make informed decisions

**If external disclosure is NOT required:** Explain why (e.g., "Internal API used only by other services, users never directly interact with it")

### 9. Mitigation Plan

**Concrete, actionable plan:**

❌ **Bad:** "We'll fix this when we have time"

✅ **Good:**
```
Mitigation Plan:
1. Immediate: UI warning added: "Currently supports simple portfolios. Contact support for complex cases."
2. Short-term (Sprint 12, 3 weeks): 
   - Add edge case handling for income >$1M
   - Implement cryptocurrency asset support
   - Add automated test suite for validation
3. Long-term (Q2 2025):
   - Full refactor to handle all asset types
   - Performance optimisation for large transaction sets
   - Add thread-safety mechanisms

Owner: @sarah-dev
Tickets: FEATURE-412, FEATURE-413, FEATURE-414
Budget: 40 story points total
Priority: High (affects 15% of users)
```

### 10. Impact Assessment

**Severity:** Minor / Moderate / Severe

**Affected Users:** Percentage or description

**Business Impact:** Revenue, reputation, compliance, etc.

**Technical Impact:** Maintenance burden, scalability, security

**Example:**
```
Severity: Moderate
Affected Users: ~15% (users with >$500K assets)
Business Impact: 
- Some users may get incorrect calculations
- Risk of reputation damage if users discover inaccuracy
- Potential compliance issues in regulated markets
Technical Impact:
- Blocks implementation of premium tier features
- Code complexity will increase until refactored
- 2-3 hours/week spent working around this limitation
```

### 11. Current Status

Track lifecycle:
- **Open**: Debt identified, documented, not yet addressed
- **In Progress**: Work underway to resolve
- **Mitigated**: Interim workaround in place
- **Resolved**: Fully addressed, debt eliminated
- **Accepted**: Team/stakeholders decided not to address (rare, requires senior leadership approval)

### 12. Review Date

- When should this debt be re-evaluated?
- Set reminders to ensure it doesn't get forgotten
- Review in retrospectives regularly

---

## Technical Debt Register Template

### Option 1: Spreadsheet/Table Format

| ID | Date | Creator | Classification | Component | Description | Necessity | Limitations | Disclosed? | Mitigation Plan | Impact | Status | Review Date |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DEBT-001 | 2024-12-15 | @sarah-dev | Strategic | zakat-calc | Simplified algorithm | Security hotfix deadline | >$1M income fails | ✅ Internal ✅ External (UI warning) | Sprint 12: Full fix | Moderate (15% users) | Open | 2025-01-15 |

### Option 2: Markdown Format (for Git repositories)

```markdown
## DEBT-042: Simplified Zakat Calculation Algorithm

**Date:** 2024-12-15  
**Creator:** @sarah-dev  
**Classification:** Strategic (Permissible - Mubāḥ)  
**Component:** `src/calculations/zakat.js`

### Description
Using simplified income calculation that doesn't handle edge cases for very high incomes (>$1M) or cryptocurrency assets. Skipped complex asset type handling to meet security patch deadline.

### Necessity
Critical security vulnerability required immediate hotfix. Proper implementation would take 3 days; business couldn't wait due to active exploitation attempt. Temporary fix secured system while proper solution is being developed.

### Known Limitations

**Internal:**
- Calculation fails for income > $1M
- Doesn't handle cryptocurrency assets
- Performance degrades with >100 transactions
- Not thread-safe

**External (User-facing):**
- Users with complex portfolios will get incorrect results
- High-income users may underpay zakat
- Slow for users with many transactions

### Disclosure Status
✅ **Internal:** Team, PO, Tech Lead all informed and consented  
✅ **External:** UI warning added: "Currently supports simple portfolios only. For complex cases, consult a scholar."

### Mitigation Plan
1. **Immediate** (Done): UI warning added
2. **Sprint 12** (3 weeks): Edge case handling + crypto support
3. **Q2 2025**: Full refactor

**Owner:** @sarah-dev  
**Tickets:** FEATURE-412, FEATURE-413  
**Budget:** 40 story points

### Impact
**Severity:** Moderate  
**Affected Users:** ~15% (high-income or complex portfolios)  
**Business Impact:** Risk of reputation damage  
**Technical Impact:** Blocks premium features

### Status
**Current:** Open  
**Review Date:** 2025-01-15
```

### Option 3: Issue Tracker Format (Jira, GitHub, etc.)

Create a **Technical Debt** issue type with custom fields for all components above. Tag issues with `technical-debt` label.

---

## Register Maintenance Process

### Who Maintains the Register?

**Primary ownership:**
- Development team collectively
- Rotating responsibility (e.g., different developer each sprint)
- Or: Designated role (Ihsan Agile Facilitator, Tech Lead)

**Key principle:** Everyone responsible for adding their debt; someone responsible for ensuring process is followed.

### When to Update the Register

**Required updates:**

1. **When taking technical debt** (during development):
   - Create entry BEFORE merging code with shortcut
   - Link entry ID in code comments
   - Obtain stakeholder consent explicitly

2. **During code review**:
   - Reviewer verifies entry exists
   - Reviewer confirms documentation is complete
   - No approval without proper register entry

3. **In sprint retrospective**:
   - Review all debt created during sprint
   - Assess whether tactical debt is becoming pattern
   - Prioritise debt to address next sprint

4. **Weekly or bi-weekly** (regular cadence):
   - Update status of in-progress items
   - Check if review dates have passed
   - Escalate overdue items

5. **When inheriting code**:
   - Document discovered debt immediately
   - Don't wait for "perfect" time
   - Discovery itself is service to team

### Register Review Questions

**In retrospectives (Muhāsabah):**

1. "How much new debt did we introduce this sprint?"
2. "How much debt did we address?"
3. "Is our total debt increasing or decreasing?"
4. "Are we seeing tactical debt become a pattern?"
5. "Do we have concrete plans for our highest-impact debt?"
6. "Where did we embody transparency? Where did we fall short?"

**In quarterly planning:**

1. "What percentage of our capacity should we dedicate to debt reduction?"
2. "Which debts are blocking strategic initiatives?"
3. "Are there systemic issues causing debt accumulation?"

---

## Integration with Agile Ceremonies

### Sprint Planning

**Before committing to stories with known shortcuts:**

1. Use [Gharar Assessment Checklist](./gharar-assessment-checklist.md)
2. If proceeding with debt, ensure "Create register entry" is part of Definition of Done
3. Allocate time for documentation (typically 15-30 minutes per entry)
4. Review existing debt register: "Can we address any high-priority items this sprint?"

### Daily Standup

**Quick check:**
- "Did anyone introduce technical debt yesterday that needs documentation?"
- "Are any debt mitigation tasks blocked?"

### Sprint Review

**Transparency with stakeholders:**
- Show register to Product Owner and stakeholders
- Highlight any debt introduced during sprint
- Demonstrate user-facing disclosures implemented
- Discuss mitigation plans

### Sprint Retrospective (Muhāsabah)

**Ethical reflection:**
- "Where did we embody **iḥsān** (excellence) in managing debt?"
- "Where did we compromise on transparency?"
- "What patterns of tactical debt are emerging?"
- "How can we address systemic pressures causing debt?"

---

## Disclosure Requirements for User-Facing Features

When technical debt affects users, disclosure is mandatory:

### In the User Interface

**Clear, prominent warnings:**

✅ **Good examples:**
```
⚠️ Currently supports simple income scenarios only. 
For complex portfolios, please consult a qualified scholar.
[Learn more about limitations]

⚠️ Beta Feature: This tool is still in development. 
Results should be verified by an expert before use.
[View known limitations]

⚠️ Performance Notice: Calculating large transaction histories 
(>100 items) may take several minutes.
```

❌ **Bad examples:**
```
"Zakat Calculator" (no disclaimer - implies completeness)

Buried in FAQ: "Note: Some edge cases not supported"
(not prominent enough)

Modal on first use only, then never shown again
(users forget or new users never see it)
```

### In Documentation

- Dedicated "Known Limitations" section
- Specific scenarios that don't work
- Guidance on when to seek alternatives
- Contact information for support

### For Support Teams

- Briefing on limitations
- Scripts for handling user questions
- Escalation path for affected users

---

## Example: Complete Technical Debt Entry

```markdown
## DEBT-089: Simplified Email Notification System

**Date Created:** 2024-12-01  
**Creator:** @ahmad-dev, @fatima-dev  
**Classification:** Strategic (Permissible - Mubāḥ)  
**Component:** `src/services/notifications/email.js`  
**Status:** In Progress  
**Review Date:** 2025-01-15

### Description
Implemented basic email notification system using synchronous SMTP without queuing mechanism. Directly sends emails during request handling rather than using background job processor. Used simple template system instead of full email template engine.

### Necessity Assessment
Q4 deadline for MVP launch to secure Series A funding. Email notifications were must-have feature for launch but not core to initial user validation. Full implementation with queuing, retry logic, and template engine would require 2 additional weeks. Business decision: Launch with basic system, enhance post-funding.

**Decision makers:** CTO @yusuf-tech, CEO @maryam-lead, Product Owner @ali-product  
**Date decided:** 2024-11-28  
**Documentation:** Meeting notes in CONF-442

### Known Limitations & Risks

**Internal (Technical):**
- No queuing: Email sends block request thread
- No retry mechanism: Failed sends are lost
- No delivery tracking: Can't confirm receipt
- No rate limiting: Could trigger spam filters
- Templates are hard-coded in JavaScript: Changes require deployment
- Not horizontally scalable: Synchronous sends don't work with load balancing
- No email preview/testing capability in development

**External (User-facing):**
- Occasional delays in email delivery (1-5 seconds)
- No confirmation message when email fails to send
- Users with aggressive spam filters may not receive emails
- No way to resend missed notifications
- Notification preferences not customisable (all-or-nothing)

**Specific failure scenarios:**
- SMTP server timeout → User sees error, email never sent
- Invalid email address → Silent failure, user not notified
- Spam filter rejection → User thinks email sent but never receives it
- Server under load → All requests slow down due to email sending

### Disclosure Status

**Internal:**
✅ Team fully briefed on limitations  
✅ Product Owner consented with knowledge of risks  
✅ CTO approved technical approach  
✅ Support team trained on potential issues  
✅ Monitoring alerts set up for SMTP failures

**External:**
✅ Help Center article: "Email Notification Expectations"  
✅ User settings page disclaimer: "Email delivery may take a few moments"  
✅ Contact form adds: "If you don't receive confirmation, check spam folder"  
⚠️ No in-app UI warning (decision: not prominent enough to warrant it, will add if issues arise)

### Mitigation Plan

**Phase 1 - Immediate Improvements** (Sprint 15, Jan 2025):
- Add basic retry logic (3 attempts with exponential backoff)
- Implement better error handling and user feedback
- Add monitoring and alerting for failed sends
- Create admin tool to manually resend failed emails
- **Owner:** @ahmad-dev  
- **Tickets:** FEATURE-521, FEATURE-522  
- **Estimate:** 8 story points

**Phase 2 - Queue Implementation** (Q1 2025):
- Integrate Redis-based job queue
- Move email sending to background workers
- Add delivery tracking and status dashboard
- Implement retry logic with dead-letter queue
- **Owner:** @fatima-dev  
- **Tickets:** FEATURE-601  
- **Estimate:** 21 story points

**Phase 3 - Full Solution** (Q2 2025):
- Integrate professional email service (SendGrid/AWS SES)
- Implement rich email template system
- Add user preference controls (frequency, types)
- Build email preview/testing tools for dev team
- Analytics and deliverability monitoring
- **Owner:** TBD (hire backend engineer)  
- **Tickets:** EPIC-045  
- **Estimate:** 55 story points  
- **Budget:** Allocated in Q2 roadmap

### Impact Assessment

**Severity:** Moderate

**Affected Users:**  
- 100% of users receive emails (but with degraded experience)
- ~5% estimated to experience delays or failures based on beta testing

**Business Impact:**
- **Risk:** User dissatisfaction if emails unreliable
- **Risk:** Reputation damage if users miss critical notifications
- **Opportunity Cost:** Delays in implementing advanced notification features
- **Monitoring:** Weekly report on email delivery success rates

**Technical Impact:**
- Maintenance burden: ~2 hours/week monitoring and manual intervention
- Performance: Request latency increased by 200-500ms per email sent
- Scalability: Limits ability to handle >1000 concurrent users
- Blocks: Cannot implement bulk email campaigns, transactional emails with attachments

### Current Status

**Status:** In Progress  
**Phase 1:** 75% complete (retry logic done, monitoring in testing)  
**Phase 2:** Not started (Q1 2025)  
**Phase 3:** Not started (Q2 2025)

**Recent Updates:**
- 2024-12-15: Phase 1 retry logic completed and deployed
- 2024-12-20: Monitoring dashboard added to internal tools
- 2024-12-28: Support team reports 3 user complaints about delays (acceptable level)

**Next Actions:**
- Complete Phase 1 monitoring deployment (Sprint 15)
- Begin Phase 2 architecture design (Sprint 16)
- Monthly review of email delivery metrics

**Review Date:** 2025-01-15 (check Phase 1 effectiveness)  
**Long-term Review:** 2025-03-01 (assess need to accelerate Phase 2)

---

**Related Tickets:**
- DEBT-089: This technical debt entry
- FEATURE-521: Email retry logic
- FEATURE-522: Error handling improvements
- FEATURE-601: Queue implementation
- EPIC-045: Full email system overhaul

**Code References:**
- `src/services/notifications/email.js` (main implementation)
- `src/middleware/emailMiddleware.js` (request handler)
- `src/templates/emailTemplates.js` (template strings)

**Stakeholder Approvals:**
- @yusuf-tech (CTO): Approved 2024-11-28
- @maryam-lead (CEO): Approved 2024-11-28  
- @ali-product (PO): Approved 2024-11-28

---

**Last Updated:** 2024-12-28 by @ahmad-dev
```

---

## Common Pitfalls to Avoid

### 1. "We'll create the entry later"
**Problem:** Later never comes. The debt becomes undocumented.

**Solution:** Make register entry part of Definition of Done. Code with shortcuts doesn't get merged without documentation.

### 2. "It's just a tiny TODO, doesn't need a formal entry"
**Problem:** Hundreds of "tiny TODOs" accumulate into massive hidden debt.

**Solution:** If it's in the code as a TODO, it belongs in the register. No exceptions.

### 3. "Only senior developers can add entries"
**Problem:** Creates bottleneck and discourages junior developers from documenting.

**Solution:** Everyone can and should document debt they introduce. Senior developers review for quality.

### 4. "The register is too long, nobody reads it"
**Problem:** Register becomes graveyard of forgotten debt.

**Solution:**
- Regular grooming sessions
- Archive resolved items
- Dashboard showing key metrics (total debt, trend, high-priority items)
- Monthly summary reports for stakeholders

### 5. "We document but never address the debt"
**Problem:** Register becomes excuse rather than tool for improvement.

**Solution:**
- Reserve % of sprint capacity for debt reduction (e.g., 15-20%)
- Make debt reduction visible in sprint demos
- Celebrate debt elimination as much as feature delivery
- Track debt trend: is it increasing or decreasing?

---

## Success Metrics

Track these metrics to ensure register is valuable:

### Process Metrics
- **Coverage:** % of technical shortcuts that have register entries
- **Timeliness:** Average time between introducing debt and documenting it
- **Completeness:** % of entries with all required fields filled
- **Review cadence:** How often is register reviewed by team

### Outcome Metrics
- **Debt trend:** Is total debt increasing or decreasing over time?
- **Resolution rate:** How many debt items addressed per sprint/quarter?
- **Discovery rate:** How much inherited debt is being surfaced?
- **Impact reduction:** Are high-severity items being prioritised?

### Cultural Metrics
- **Transparency:** Do team members proactively document debt?
- **Psychological safety:** Do people feel comfortable surfacing problems?
- **Stakeholder awareness:** Do non-technical stakeholders understand debt landscape?
- **User protection:** Are user-facing limitations consistently disclosed?

---

## Tools & Technologies

Choose tools that fit your team's existing workflow:

### Simple Solutions
- **Markdown file in Git**: Version-controlled, easy to review in PRs
- **Spreadsheet**: Sortable, filterable, easy for non-technical stakeholders
- **Notion/Confluence**: Rich formatting, collaborative editing

### Integrated Solutions
- **Jira/GitHub Issues**: Links to code, automated workflows, reporting
- **Custom field in ticket system**: Adds "Technical Debt" checkbox and fields to standard issues
- **SonarQube**: Automated technical debt detection (complements manual register)

### Recommended: Hybrid Approach
- **Markdown file** for detailed documentation (lives with code)
- **Dashboard/tracker** for summary view and prioritisation
- **Code comments** with register IDs linking detailed docs

---

## Starting Your Register: First Steps

### Week 1: Setup
1. Choose your tool (spreadsheet, markdown, issue tracker)
2. Create template with all required fields
3. Document 1-2 examples to show the team
4. Add to team's Definition of Done: "Technical debt must be registered"

### Week 2: Discovery
5. Hold team session to identify existing technical debt
6. Each developer documents 3-5 known shortcuts in their areas
7. Don't aim for completeness—focus on high-impact items
8. Create entries, mark as "Inherited"

### Week 3: Integration
9. Update Definition of Done checklist
10. Add register review to retrospective agenda
11. Brief Product Owner and stakeholders on purpose
12. Establish weekly review cadence

### Week 4: Iteration
13. Retrospective: "How is the register working?"
14. Adjust template based on team feedback
15. Celebrate first debt items that get resolved
16. Plan capacity allocation for debt reduction

---

## Related Resources

- [Gharar Assessment Checklist](./gharar-assessment-checklist.md) - Evaluate whether technical debt is permissible
- [Ethical Definition of Done](./ethical-dod-checklist.md) - Include debt documentation in DoD
- [Muhāsabah Retrospective Template](./muhasabah-retrospective-template.md) - Reflect on debt in retrospectives
- [Technical Debt as Gharar (Article)](https://ihsanagile.org/technical-debt-as-gharar) - Theological framework

---

## Conclusion

A Technical Debt Register is not bureaucracy—it's **fulfillment of amānah** (trust).

By documenting shortcuts transparently:
- You eliminate **jahalah** (ignorance) that causes **ẓulm** (injustice)
- You protect future maintainers from hidden landmines
- You empower stakeholders to make informed decisions
- You enable users to trust your software
- You embody **iḥsān** (excellence) in your craft

The register transforms technical debt from hidden **gharar fāḥish** (prohibited uncertainty) into disclosed **gharar yasīr** (tolerable, managed uncertainty).

**Remember:**

*"It is not permissible for a Muslim to sell his brother goods in which there is a defect, without pointing that out to him."*

Your code is the "goods" you pass to your teammates. The register is how you "point out the defects."

This is not optional. This is **amānah**. This is **iḥsān**. This is worship through craft.

---

*"All of you are guardians and responsible for your wards and the things under your care."*  
— Prophet Muhammad ﷺ (Ṣaḥīḥ al-Bukhārī 893)

---

**License:** [Creative Commons Attribution-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)

**Maintained by:** [Ihsan Agile](https://ihsanagile.org)

**Feedback:** [getinvolved@ihsanagile.org](mailto:getinvolved@ihsanagile.org)
