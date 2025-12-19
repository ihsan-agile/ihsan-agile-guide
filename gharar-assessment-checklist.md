# Gharar Assessment Checklist

## Purpose

This checklist helps development teams evaluate technical debt through the Islamic lens of **gharar** (harmful uncertainty). By assessing uncertainty, disclosure, and responsibility, teams can determine whether technical shortcuts align with Islamic principles of transparency, justice, and stewardship.

---

## When to Use This Checklist

- **Before taking technical debt**: During sprint planning or technical discussions when shortcuts are being considered
- **During code reviews**: When evaluating whether existing shortcuts are properly documented
- **In retrospectives**: When reflecting on past decisions and their ethical implications
- **When inheriting code**: To assess and document previously undisclosed technical debt

---

## The Four Critical Questions

### 1. Disclosure: Is the uncertainty documented?

**Yes, fully documented:**
- Clear code comments explaining the shortcut
- Entry in technical debt register with ticket number
- Limitations explained in plain language
- Future maintainers will understand what they're working with

**Partially documented:**
- Some documentation exists but incomplete
- Comments present but lack context or reasoning
- No clear mitigation plan

**Not documented:**
- No code comments about the shortcut
- No entry in technical debt register
- Future maintainers will be surprised by limitations
- ⚠️ This creates **jahalah** (ignorance) and moves toward prohibited **gharar**

### 2. Knowledge: Does the receiving party know the risk?

**Internal stakeholders (team):**
- [ ] Product Owner is aware and has consented
- [ ] Technical Lead/Architect has reviewed and approved
- [ ] Team members understand the trade-off
- [ ] Future maintainers will have clear documentation

**External stakeholders (users):**
- [ ] Users are informed of limitations through UI warnings
- [ ] Documentation clearly states what scenarios are NOT supported
- [ ] No misleading claims about completeness or reliability
- [ ] Users can make informed decisions about whether to rely on the feature

**If either internal OR external stakeholders lack knowledge, this is undisclosed gharar.**

### 3. Impact: How severe is the potential harm?

**Minor impact (Gharar Yasīr - Tolerable):**
- Performance slightly slower than optimal
- Minor UX inconvenience
- Workaround exists and is documented
- Limited scope affecting few users
- Easy to fix when needed

**Moderate impact (Gharar Mutawassiṭ - Requires judgment):**
- Affects subset of users or use cases
- Noticeable but not critical limitation
- Requires careful evaluation of trade-offs
- May need escalation to leadership

**Severe impact (Gharar Fāḥish - Prohibited):**
- Critical functionality doesn't work properly
- Data loss or corruption possible
- Security vulnerabilities present
- Privacy violations likely
- For Islamic apps: Could cause Muslims to fail religious obligations
- Users could be seriously harmed or misled
- ⚠️ **This level of gharar cannot be justified by time pressure**

### 4. Necessity: Is there a legitimate reason for this shortcut?

**Valid necessity (may justify taking the debt):**
- [ ] Genuine business deadline with real consequences
- [ ] Market window that will close
- [ ] Critical bug requiring immediate hotfix
- [ ] Resource constraints during genuine crisis
- [ ] Learning experiment to validate assumptions before major investment

**Not necessity (does not justify the shortcut):**
- [ ] "We're always behind schedule" (systemic issue, not necessity)
- [ ] "Product Owner will be unhappy" (pressure, not necessity)
- [ ] "We want to look good in demo" (vanity, not necessity)
- [ ] "It's easier this way" (convenience, not necessity)
- [ ] "Someone else will fix it later" (passing burden, not necessity)

**Critical distinction:**
- Necessity may justify *taking* the debt
- Necessity does NOT justify *concealing* the debt
- Documentation takes 5 minutes and prevents **ẓulm** (injustice)

### 5. Mitigation: Is there a concrete plan to address it?

**Strong mitigation plan:**
- [ ] Specific ticket created (e.g., DEBT-042)
- [ ] Included in technical debt register
- [ ] Timeline committed (specific sprint or date)
- [ ] Resources allocated
- [ ] Owner assigned
- [ ] Interim workarounds documented
- [ ] Risk assessment completed

**Weak mitigation plan:**
- [ ] Vague "we'll get to it when we can"
- [ ] No specific timeline
- [ ] No resources allocated
- [ ] "Hopefully next quarter"
- ⚠️ Weak plans often mean debt is never addressed

**No mitigation plan:**
- [ ] "We'll deal with it if it becomes a problem"
- [ ] "Not our problem, we'll be on another team"
- [ ] No discussion of how to address it
- ⚠️ This is reckless debt and violates **amānah** (trust)

### 6. Consent: Did stakeholders agree with full knowledge?

**Proper consent obtained:**
- [ ] Product Owner understands the limitation and accepts it
- [ ] Technical Lead/Architect has reviewed and approved
- [ ] Security/compliance teams consulted if relevant
- [ ] For external-facing features: User disclosure strategy agreed
- [ ] Team members comfortable with the decision
- [ ] Agreement documented in ticket or meeting notes

**Consent without full disclosure:**
- [ ] Stakeholders said "yes" but don't understand the implications
- [ ] Technical details glossed over in explanation
- [ ] Users not informed of limitations
- ⚠️ This is not true consent and creates **gharar**

**No consent sought:**
- [ ] Decision made unilaterally by developer
- [ ] "Better to ask forgiveness than permission"
- [ ] Stakeholders will only discover it when something breaks
- ⚠️ This violates **shūrā** (consultation) and **amānah** (trust)

---

## Gharar Classification

Based on your assessment above, classify the technical debt:

### Category 1: Strategic Debt (Permissible - Mubāḥ)
✅ **Characteristics:**
- Fully disclosed to all parties (internal AND external)
- Documented with clear mitigation plan
- Valid necessity exists
- Timeline and resources committed
- Stakeholders informed and consenting
- Users warned of limitations in the UI

**Example:** "MVP calculator that handles 80% of cases, with clear UI warning: 'Currently supports common scenarios. For complex cases, consult an expert.' Full implementation planned for Sprint 12."

### Category 2: Tactical Debt (Questionable - Makrūh)
⚠️ **Characteristics:**
- Taken primarily due to deadline pressure
- Some documentation but incomplete
- Vague mitigation plan
- Stakeholders aware but uncomfortable
- Becoming a pattern rather than exception

**Example:** "Skipped automated tests again this sprint. We'll add them next sprint. Probably. If we have time."

**What to do:**
- Recognise this is a warning sign
- Discuss systemic issues in retrospective
- Consider whether team is over-committing
- Make addressing debt truly exceptional, not routine

### Category 3: Reckless Debt (Prohibited - Ḥarām)
❌ **Characteristics:**
- Taken to benefit yourself at others' expense
- No meaningful documentation
- No mitigation plan
- Future team and/or users will be harmed
- "Not my problem" attitude
- Users exposed to undisclosed risks

**Example:** "Code that's fragile and will break, but developer doesn't document it and leaves the company. Next developer blamed when it inevitably fails. Users misled about reliability."

**Why it's ḥarām:**
- Creates **ẓulm** (injustice) through information asymmetry
- Violates **amānah** (trust placed in you)
- Harms both future maintainers and users
- You will be held accountable before Allah

**What to do:**
- Refuse to proceed without proper documentation
- Escalate to leadership if pressured to skip disclosure
- Remember: You're accountable for harm caused to others

### Category 4: Inherited Debt (Not sinful to discover, sinful to perpetuate)
🔄 **Characteristics:**
- You didn't create it
- You discovered it
- Now you must decide: address it or perpetuate it?

**Islamic principle:** Discovering debt doesn't make you guilty. But knowing about it and doing nothing makes you complicit.

**What to do:**
- Document what you found (turn hidden **gharar** into disclosed **gharar**)
- Add to technical debt register
- Raise with team in retrospective
- Create tickets for addressing it
- You've fulfilled your **amānah**

---

## Decision Framework

Use this framework to make ethical decisions about technical debt:

```
IF (severe impact) THEN
    → Cannot proceed without proper implementation
    → Time pressure does not justify endangering users
    → Escalate to leadership for additional resources

ELSE IF (moderate impact AND valid necessity) THEN
    → Proceed WITH full documentation
    → Obtain explicit stakeholder consent
    → Create concrete mitigation plan with timeline
    → Disclose limitations to users in UI
    → Add to technical debt register
    → Review in retrospective

ELSE IF (minor impact AND valid necessity) THEN
    → Proceed WITH documentation
    → Create mitigation plan
    → Inform stakeholders
    → Disclose to users if user-facing
    → Track in register

ELSE IF (no valid necessity) THEN
    → Don't take the shortcut
    → Discuss systemic issues (why are we always rushed?)
    → Consider whether team is over-committing
    
ELSE IF (weak documentation OR no mitigation plan) THEN
    → Pause and document properly (takes 5 minutes)
    → The necessity that justifies taking debt does NOT justify hiding debt
    → Refusing to document is refusing amānah
```

---

## Red Flags: When to Escalate

Escalate to leadership or refuse to proceed if you see:

- [ ] **Pattern of tactical debt**: Taking shortcuts 3+ sprints in a row
- [ ] **Normalising poor practices**: "We always skip tests, it's fine"
- [ ] **Pressure to hide limitations**: "Don't mention the bugs to the client"
- [ ] **Misleading users**: Claiming completeness when limitations exist
- [ ] **No time ever allocated to address debt**: Debt only accumulates, never reduces
- [ ] **Blame culture**: People punished for surfacing problems
- [ ] **"Not my problem" attitudes**: People passing burden to others
- [ ] **Severe impact with no mitigation**: Serious risks being ignored

These indicate systemic ethical problems that require intervention.

---

## Integration with Daily Practice

### Sprint Planning
Before committing to work with known shortcuts:
- Use this checklist to assess the **gharar** level
- Ensure proper documentation is part of the Definition of Done
- Allocate time for creating technical debt register entries
- Obtain stakeholder consent explicitly

### Code Review
Before approving code with shortcuts:
- Verify documentation is complete
- Confirm entry in technical debt register exists
- Check that mitigation plan is concrete
- Ensure user-facing limitations are disclosed in UI

### Retrospective (Muhāsabah)
Reflect on **gharar** introduced during the sprint:
- "Where did we embody transparency and stewardship?"
- "Where did we fall short in disclosure?"
- "What patterns of tactical debt are emerging?"
- "How can we address the systemic issues causing pressure?"

---

## Questions for Reflection

Before marking work as "Done," ask:

1. **Niyyah (Intention)**: "Would I want to explain this decision to Allah on the Day of Judgment?"

2. **Transparency**: "Have I disclosed everything a future maintainer needs to know?"

3. **User Protection**: "If I were the user, would I feel informed or deceived?"

4. **Stewardship**: "Am I treating this codebase as an **amānah** (trust) or just getting through my sprint?"

5. **Justice**: "Am I passing a burden to others that I wouldn't want passed to me?"

---

## Related Resources

- [Technical Debt Register Guide](./technical-debt-register.md) - Structured approach to documentation and disclosure
- [Ethical Definition of Done Checklist](./ethical-dod-checklist.md) - Expand your DoD with Islamic criteria
- [Muhāsabah Retrospective Template](./muhasabah-retrospective-template.md) - Reflect on ethics in retrospectives
- [Technical Debt as Gharar (Article)](https://ihsanagile.org/technical-debt-as-gharar) - Full theological framework

---

## Conclusion

Technical debt isn't inherently **ḥarām**. What matters is:

- **Disclosure**: Do future maintainers and users know what they're getting?
- **Justice**: Are you treating others as you'd want to be treated?
- **Stewardship**: Are you fulfilling the **amānah** placed in you?
- **Accountability**: Can you answer for this decision before Allah?

The difference between **acceptable** and **prohibited** technical debt isn't the shortcut itself—it's whether you've eliminated the **jahalah** (ignorance) that causes **ẓulm** (injustice).

---

*"All of you are guardians and responsible for your wards and the things under your care."*  
— Prophet Muhammad ﷺ (Ṣaḥīḥ al-Bukhārī 893)

---

**License:** [Creative Commons Attribution-ShareAlike 4.0 International](https://creativecommons.org/licenses/by-sa/4.0/)

**Maintained by:** [Ihsan Agile](https://ihsanagile.org)

**Feedback:** [getinvolved@ihsanagile.org](mailto:getinvolved@ihsanagile.org)
